---
title: "Se pega ubuntu 10.04 tls en Acer Aspire 5738"
date: 2010-11-08
forum: Hardware
---

### Post by Lutho on 2010-11-08
ya ha pasado 3 veces, durante la semana pasa. Y en realidad me gustaría saber como puedo averiguar la causa de porque se pega ubuntu 10.04 LTS 

El motivo de este post es para saber si existe algún comando para realizar dicha auditoria o búsqueda.

Cuando se congela ubuntu no funciona nada. y cambiar de escritorio ni tampoco abrir una consola nueva nada.. ni tampoco desactivar dispositivos.
Cierro el notebook y queda igual.

para salir del problema lo apago a la mala nomas

alguna orientación a este problema..

---

### Post by Patriciologico on 2010-11-08
Revisa los sucesos del sistema y ve que errores te marca. 

Ubicacion --> Menu/Sistema/Administracion/Visor de Archivos de Sucesos.

---

### Post by Lutho on 2010-11-24
proble aun persiste, pero me di cuenta que cuando cambio la imagen de fondo de pantalla es donde se queda pegado.

en el visor de sucesos no registra 
esto quedo registrado en el ultimo evento hasta que se pegara.

Nov 24 09:45:13 laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="797" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Nov 24 09:55:51 laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Nov 24 09:55:51 laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="812" x-info="http://www.rsyslog.com"] (re)start

:/

---

