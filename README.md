Kupiłem kominek na pellets Luois Air firmy IwonaPellets.
Sterownik tego kominka to RK-2014KH obsługujący ModBus (gniazdo RS-485).
Postanowiłem podłączyć go do Home Assistant.
Jako łącze RK-2014KH z HA wykorzystałem Elfin-EW11 RS-485 WiFi (z Chin ok. 40.- zł).
Parametry RS-485 powinny być ustawione takie same w RK-1014KH jak w EW11.
Nie miałem żadnych informacji o wykorzystanych adresach ModBus.
Sprawdziłem wszystkie adresy od 0 do 400 i ustaliłem, które wykorzystuje kominek.
Po uruchomieniu kominka co minutę (przez dwie godziny) testowałem wybrane adresy i ustaliłem, które czym sterują lub jakie parametry wyświetlają. Po wielu próbach utworzyłem plik kominek_ip.yaml, w którym zawarte są wszystkie dane do obsługi kominka. Na początku pliku w opcji modbus: w host: wpisz IP twojego EW-11.

W pliku configuration.yaml na początku umieść (zgodnie z zasadami yaml);

homeassistant:
  packages:
    kominek_package: !include kominek_ip.yaml

Drugi plik widok.yaml zawiera dane do wpisania w widoku kominka. Po utworzeniu nowego widoku i dodaniu nowej karty (np. Kominek) należy wejść w edytor yaml i wkleić jego zawartość.

Na pierwszej pozycji jest button Start/Stop.
Na drugiej pozycji jest status kominka (Stop – wyłączony). Pozostałe stany są wyświetlane tekstowo zgodnie ze stanem kominka (CZYSZCZENIE, ROZPALANIE, MOC MAKSYMALNA, MOC MODULOWANA, MOC MINIMALNA, DOPALANIE, WYGASZANIE, CZUWANIE i STOP)
Na pozycji trzeciej jest termostat ustawiający temperaturę w pomieszczeniu ( 5 do 30). Wyświetlane są; temperatura zmierzona i temperatura ustawiona. Jeśli temperatura w pomieszczeniu jest wyższa niż ustawiona, to kominek przechodzi w stan CZUWANIE i gdy temperatura  w pomieszczeniu się obniży, to kominek ponownie się rozpali i będzie grzał (zakres regulacji temperatury jest ustawiony na 0.5 stopnia C).
Na pozycji czwartej jest możliwość regulacji temperatury w komorze kominka (30 do 120). Wyświetlane są; temperatura zmierzona i temperatura ustawiona.
Pozostałe dane są informacyjne o poszczególnych urządzeniach jak wentylatory i termometry.
Część z nich jest tylko do moich testów, niepotzrbne można usuną i ustawić wg własnych potzreb.

Zrobiłem wiele testów i stwierdziłem, że na moje potrzeby wystarczy. Wygląd można to sobie upiększyć wg własnego gustu i umiejętności. Ja jestem zwolennikiem prostych widoków i pewnych działań.

Jeszcze nie testowałem dla palenia drewnem i pellets-drewno.

Warunki licencji MIT.

Jan Trzciński
e-mail: poljant@post.pl

