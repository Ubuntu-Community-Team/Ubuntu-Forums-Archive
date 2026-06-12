---
title: "No tengo wifi ubuntu 10.04"
date: 2010-05-20
forum: Hardware
---

### Post by javier-2714 on 2010-05-20
Hola buenas tardes los molesto tengo una notebook HP 530 no puedo conectarme por wifi el icono me dice que esta activada pero no se conecta y no enciende la luz mi placa :

Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

instale linux-backports-modules-wireless2-6-32.22-generic pero no pasa nada en hardy me funcionaba perfecto gracias.

---

### Post by alfplayer on 2010-05-20
Está activada con la tecla de la notebook para encender y apagar wifi ?

---

### Post by javier-2714 on 2010-05-20
Si presiono el botón del wireless en el icono de red dice activada lo vuelvo a presionar y dice desactivada la luz no enciende en ningún caso y tampoco escanea ni se conecta no hace nada con hardy andaba perfecto ahora con lucid no quiere saludos.

---

### Post by guillermolisi on 2010-05-20
Si inicias la maquina con el LiveCD/pendrive, que sucede con la conexion WiFi ?

---

### Post by javier-2714 on 2010-05-21
Lo mismo dice activada la luz no enciende pero nada todo igual.

---

### Post by alfplayer on 2010-05-21
Con wifi activada con la tecla, abrí un terminal (se puede hacer desde el menú Aplicaciones) y ejecutá el comando *iwlist scan* para ver si aparecen detectadas las redes.

---

### Post by javier-2714 on 2010-05-21
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

En el icono de red dice activada.

---

