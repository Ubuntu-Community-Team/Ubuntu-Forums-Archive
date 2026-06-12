---
title: "Creación de un punto de acceso en lucid"
date: 2012-04-10
forum: Hardware
---

### Post by asterix77 on 2012-04-10
Buenas a todos

Quisiera poder crear un punto de acceso en lucid para compartir internet a varios dispositivos móviles, y de esta forma no tener que recurrir  a un gasto en datos. Para ello dispongo de dos dispositivos wireless, uno propio de mi notebook 

"Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)"

Y uno usb tp-link TL-WN322G (ID 0ace:1215 ZyDAS WLA-54L 802.11bg)

El asunto es que para convertirlos en AP debo dejarlo en modo master, pero tengo entendido que no todos los dispositivos wireless soportan esto, y no sé si estos modelos lo soportan. Y es por ello que recurro a ustedes para ver si me pueden ayudar.


Desde ya saludos

---

### Post by dirty fingers on 2012-04-30
La ultima vez que lo hice fue tan simple como correr un servidor proxy indicando una interfaz como entrada y la otra como salida. Lastima que fue hace mucho y no recuerdo los detalles.

   Igual no veo la diferencia de gastos entre todos los dispositivos a un router y luego a un modem (o todo integrado en uno) contra todos los dispositivos a tu notebook (con dos redes) y luego al modem.

   Quizas te estoy interpretando mal la pregunta.

---

### Post by asterix77 on 2012-05-18
Bueno.... no me dado por vencido con este tema, he seguido intentando y creo haber logrado al menos cierto avance....

He instalado hostapd el cual si me ha convertido mi usb tp-link en un punto de acceso

shmv@shmvw7nt:/etc/hostapd$ iwconfig
ppp0      no wireless extensions.

lo        no wireless extensions.

wlan1     IEEE 802.11bg  Mode:Master  Frequency:2.462 GHz  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Managementoff
          
mon.wlan1  IEEE 802.11bg  Mode:Monitor  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thrff   Fragment thrff
          Power Managementn
          
eth0      no wireless extensions.


Mi archivo de configuración es el siguiente:

$cat /etc/hostapd/hostapd.conf

interface=wlan1
driver=nl80211
ssid=MyAP
hw_mode=g
channel=11
wpa=1
wpa_passphrase=XXXXX


Al buscar el AP con mi smartphone detecta mi AP del notebook, intenta obtener una dirección ip y la obtiene, pero me aparece con conectividad limitada y no obtengo navegación alguna.

[http://ubuntuforums.org/attachment.php?attachmentid=218226&stc=1&d=1337357258](http://ubuntuforums.org/attachment.php?attachmentid=218226&stc=1&d=1337357258)

Agradecería cualquier comentario.

Saludos

---

