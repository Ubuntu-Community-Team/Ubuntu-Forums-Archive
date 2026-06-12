---
title: "modem entel para ubuntu 11.10"
date: 2012-05-12
forum: Hardware
---

### Post by silverdrako on 2012-05-12
Me descargue el ultimate edition 3.2 que trae el ubuntu 11.10 y lo instale hasta ahy sin problema todo felicidad por que porfin me libraba del malevolo window......
 pero no puedo configurar correctamente el modem Huawei e 173 de entel(prepago).
aplique el [COLOR=Blue]sudo apt-get install usb-modeswitch usb-modeswitch-data[/COLOR]  sin problema lo reconoce como modem. Configure la coneccion de banda ancha como, chile, entel, apn:imovil.entelpcs.cl, y autenticacion CHAP, la autenticacion la deje con solo CHAP por que en la coneccion con el programa del win.... se conecta asi. Pero sigue sin conectar, reconose el modem como tal y la configuracion pero no conecta.....
si alguien pudiera echarme un cable se lo agradeceria sinceramente........

---

### Post by caravena on 2012-05-12
Descargue la versión 12.04, la versión 11.10 es ya anticuada.
[http://www.ubuntu.com]("http://www.ubuntu.com")

---

### Post by silex89 on 2012-09-15
Hola :)

Ambas versiones de Ubuntu (11.10 y 12.04) traen los paquetes necesarios para gestionar una conexión con modem 3G en la instalación por defecto (en escencia esos paquetes son usb_modeswitch y modemmanager).

Ahora estoy usando un modem Entel marca Huawei, y lo único que hay que hacer es crear una nueva conexión con el applet de network manager, seguir el asistente y contestar las preguntas que el programa hace. No es necesario cambiar ninguna configuración, porque con los ajustes por defecto funciona bien el modem (a menos que tengas un modem muy muy antiguo)

Saludos y suerte :D

---

