# ProjektaDarbs231RDB409

## Projekta uzdevuma apraksts
Šīs programmas uzdevums ir automatizēt tīmekļa izmantošanu, aizstājot man ikdienā ļoti aktuālu problēmu, kas ir akciju vērtības izsekošana, lai noteiktu pareizo mirkli, kurā pārdot vai pirkt akcijas. Tas man ikdienā var nākties darīt ļoti bieži, varbūt pat simtiem reižu. Es secināju, ka būtu iespējams ietaupīt ļoti daudz mana ikdienas laika un darbību, ja es šo procesu varētu kaut kā automatizēt, un man pašam būtu jāizseko līdzi tikai tam, vai man ir atnācis paziņojums uz manu telefonu.

Šīs programmas uzdevums ir automatizēt tīmekļa izmantošanu tieši specifiski akciju vērtību izsekošanu un to cenu informācijas apskatīšanu, kā arī datu reģistrēšanu, kas sevī iekļauj cenas grieztu un zema līmeņa atzīmēšanu. Tas ietver arī šo datu saglabāšanu excel tabulas formātā, lai ar šiem datiem nākotnē būtu iespējams veikt vēl kādas tālākas manipulācijas.

Galvenais programmas izstrādes mērķis bija informācijas ieguve un brīdinājumu izsūtīšana uz savu epastu automatizēšana

### Kļūdas paziņojumu izvade
Diemžēl man nepietiek laika atrisināt visas problēmas ar kļūdas paziņojumu izvadi. Kods, slēdzoties klāt yahoo mājaslapai, reizēm izvada kļūdas paziņojumus, kas saistīti ar chrome pārlūka izmantošanu. Cik es saprotu, tie ir grafisku elementu ielādes kļūdas paziņojumi, kas dažreiz rodas brīžos, kad mājaslapa atjauno grafisko tabulu, kas norāda cenu diapazonu dienas garumā, laikā kad pārlūks veic datu ieguvi no attiecīgās mājaslapas.

Piemērs chrome/yahoo.com:
[26700:9992:0117/221316.522:ERROR:ssl_client_socket_impl.cc(975)] handshake failed; returned -1, SSL error code 1, net_error -101

Kā arī kļūdas paziņojumi kodam, kad pārlūks slēdzas klāt ēpastam.

Piemērs Epasts:
[7412:19156:0117/205831.386:ERROR:mcs_client.cc(702)] Error code: 401 Error message: Authentication Failed: wrong_secret [7412:19156:0117/205831.386:ERROR:mcs_client.cc(704)] Failed to log in to GCM, resetting connection.

Tomēr šie kļūdas paziņojumi būtiski nemaina ne koda izpildes procesu, ne arī izpildes laiku.


## Izmantotās bibliotēkas un to izmantošanas skaidrojums

### time
Bibliotēka, kas atļauj uzstādīt gaidīšanas laiku starp programmas koda izpildes darbībām. Attiecīgi uzdevumā, automātiski pildot darbības ar pārlūku, ir nepieciešams uzstādīt atbilstošu laiku, kas atļauj veikt pārlūkā izpildāmās darbības līdz to galam, netraucējot tālāku darbību izpildi.

### selenium
Bibliotēka, ar kuras pieslēgšanu un pareizu uzstādīšanu ir iespējams veikt pārluka programmas izmantošanas automatizāciju, simulējot lietotāja darbības ar attiecīgo pārlūku. Šajā gadījumā tas ietver pieslēgšanos pārlūkam, datu iegūšanu, kā arī atkārtotu pieslēgšanos pārlūkam, lai caur epastu varētu nosūtīt iegūtos datus

### openpyxl
Bibliotēka, kas ļauj izmantot, veidot un veikt manipulācijas ar excel tipa failiem, izmantojot Python programmēšanas valodu. Šajā gadījumā tas ietver jauna faila izveidošanu un iegūto datu saglabāšanu excel tabulā.

### os un sys
Bibliotēkas, ko es izmantoju, lai apstrādātu jeb noņemtu ar Python chrome pārluka atvērto logu ģenerētās kļūdas ievades terminālī koda izpildes laikā


## Lietošanas instrukcija un secinājumi

### Lietošanas instrukcija
Lai pilnībā spētu izmantot šī koda veiktās darbības es iesaku ar telefonu aplikācijā Gmail pievienoties "projektadarbsoskars@gmail.com" parole"Dro$aParole123" un iespējot paziņojumus kas atļaus lietotājam uz savu telefonu saņemt attiecīgos paziņojumus par šanemtajiem epastiem kuri sevī iekļauj notektajām akciju vērtībām sasniegtās augstās vai zemās robežas.

1.Palaist kodu

2.Ievadīt akciju simbolus (Drukātiem burtiem) atdalot tos ar komatu, ja vēlaties vairākus vienlaikus.
Piemēram: BTC-USD, INTC, TSLA, SOL-USD, NVDA. 
Ir vēlams, bet ne obligāti, šos simbolus ievadīt visus ar vienādām valūtām, lai Excel dati būtu atbilstoši viens otram (vienam un tam pašam uzņēmumam, atšķiroties valūtas kursam, atšķirsies arī akciju simbols). Kad šis solis ir izpildīts, nospiediet taustiņu ENTER.

3.Katram akciju simbolam var iestatīt attiecīgo cenas augstāko kā arī zemāko vērtību pēc kuras kods sekos līdzi vai izvadīs paziņojumu par viena no šo kritēriju izpildīšanu. Pēc katra skaitļa ievadīšanas attiecīgajā laukā jānospiež taustiņš ENTER. 

4.Pēc pēdējā simbola cenu robežas iestatīšanas atliek tikai vērot koda darbību līdz tā laika beigām.
(šobrīd darbības laiks ir 20 minūtes, bet excel_piemers laiks bija 2 stundas).

### Secinājumi
Kods izpilda visus uzdevuma mērķī noteiktās darbības.

Laigan šobrīd kods savā ziņā ir diezgan primitīvs un spēj veikt tikai datu saglabāšanu excel tabulā, kā arī brīdinājuma paziņojumu nosūtīšanu uz epastu, es domāju, ka ar laiku manām programmēšanas zināšanām un spējām attīstoties, es to papildinot vai pat iespējams pilnībā nomainot, bet saglabājot tā ideju, iespējams spēšu automatizēt pārlūkā veiktās darbības ne tikai ar paziņojumu izvadi, bet pieslēdzot ar atlasītiem datiem apmācītu mākslīgo intelektu, automatizēt arī akciju tirgus darbību veikšanu (pirkšanu un pārdošanu) ar potenciālu ģenerēt papildus ienākumus lietotājam.

**Liels jums paldies par uzmanību**
