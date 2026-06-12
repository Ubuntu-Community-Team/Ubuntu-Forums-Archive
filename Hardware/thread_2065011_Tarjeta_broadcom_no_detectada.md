---
title: "Tarjeta broadcom no detectada"
date: 2012-09-30
forum: Hardware
---

### Post by capcabgue on 2012-09-30
Hola:

Tengo un notebook dell inspiron 1525, con Ubuntu 12.04 de 64 bits con gestor de escritorio lxde.
Hoy (30 Septiembre 2012) hice un update, y al reiniciar no me reconoce la tarjeta wifi.
Si voy a preferencias y veo additional Drivers, efectivamente me sale que no esta habilitada la tarjeta broadcom, si pongo activar me arroja el siguiente error "Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log"

Borre de las lista negra todo el bcw43xx, pero aún así sigue el problema.
Ahora si hago lspci -vnn | grep Wire
Me arroja los siguientes resultados:

02:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05) (prog-if 10 [OHCI])
	Subsystem: Dell Wireless 1395 WLAN Mini-Card [1028:000b]


Ojala alguien pueda ayudarme.

---

