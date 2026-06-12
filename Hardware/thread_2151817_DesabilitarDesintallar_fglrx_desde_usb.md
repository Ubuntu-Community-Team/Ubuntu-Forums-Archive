---
title: "Desabilitar/Desintallar fglrx desde usb"
date: 2013-06-05
forum: Hardware
---

### Post by Fistandantilus on 2013-06-05
Hola!, Como andan?

Necesito por favor si me pueden dar una mano xq ya no se que hacer :(

Le instale a mi viejo en su laptop, HP Pavilion G4, ubuntu 13.04. 
Funco todo joya, hasta que le instale los drivers privativos de amd por medio de "Controladores adicionales".
Desde ese momento no se puede iniciar ubuntu, se ve todo como defasado y no termina de iniciar el x.org.
Probe de iniciar como modo single-user y tambien se ve todo defasado, a tal punto que no se llega a leer nada.
Intente de ejecutar el comando: "sudo apt-get remove --purge fglrx-updates fglrx-amdcccle-updates" desde single-user con la ante última opción sin ningun resultado. Todo al aire por que no llego a leer lo que escribo.
Desde un usb edite el archivo /etc/modprobe.d/blacklist.conf y le agregue "blacklist fglrx" y tampoco funco.
Ya no se que probar.

Alguna idea?


[ATTACH=CONFIG]243554[/ATTACH]

---

### Post by dirty fingers on 2013-06-22
Y si apretas "ctrl + alt + F" para pasar a las terminales (tty), quizas están en otra resolución y podes ver?
Creo que viene 6 activadas en ubuntu. por ejemplo ctrl + alt + F1 te llevaría a la primera y ctrl + alt + F7 volverías al entorno gráfico.

---

