---
title: "Modem/Router Edimax AR-7064Sg+"
date: 2009-06-08
forum: Hardware
---

### Post by alejandro.mc on 2009-06-08
Hola gente, tengo el siguiente problema, tengo un Modem/Router Edimax AR-7064Sg+, Arnet y Ubuntu 8.10. Sucede que cada vez que levantan el telefono la conexion se corta y el modem aparece como resolviendo el problema, titila la lucesita, y despues quedan prendidas como antes pero internet no funciona mas. Hay algo que este mal configurado? Como hago para que se conecte solo nuevamente? Y que funcione asi constantemente..

Gracias saludos!!

---

### Post by gmunioz on 2009-06-09
Hola ale....:

¿Quién te instaló el modem/router?

Los modems adsl, deben conectarse a la entrada 

de la línea telefónica. 

A continuación de este, previo un filtro, recien 

conectar las centrales o los aparatos telefónicos.

De no hacerse así al tomar tono un dispositivo

telefónico se interrumpe la conexión adsl.

Saludos.
Gabriel.
**Solo doy soporte para Ubuntu - 22 - Mad Karmic & Gnome-shell User.**

---

### Post by layevska on 2009-06-09
ami me pasa algo igual. solamente que con el internet inalambrico

cuando hablan por el telefono inalambrico

el internet se desconecta. y el modem dice que todoo biem

pero no xdd

---

### Post by Hei Ku on 2009-06-09
Cambiá el telefono inalambrico, porque debe estar funcionando en la misma frecuencia que tu Wifi. Gralmente, 2.4GHz. Podes probar de cambiar ambos de canal tambien.

---

### Post by alejandro.mc on 2009-06-14
Gracias por las respuestas gente! 

Claro yo tengo inalambrico tambien, pero no tengo internet inalambrica =)

Entonces no veo como lo podria estar afectando no?

Yo hice la conexion, mas o menos algo entiendo y conecte todo como debe estar, filtros, config del modem, es algo en Ubuntu el tema, porque en Wingarch apago y prendo el router --> pongo reparar conexion y se repara. En Ubuntu apago y prendo el router y despues haga lo que es imposible volver a levantar internet, tengo que apagar TODO y volver a prender TODO. 

Saludos!

---

### Post by Mauro22 on 2009-06-15
Para volver a conectar hace:

Sudo /etc/init.d/network restart


Sería más o menos el "reparar" del que-no-debe-ser-mencionado.

---

### Post by alejandro.mc on 2009-06-21
Gracias, igual el tema es que no debería colgarse si atiendo el telefono, y no se porque sucede.

Saludos!

---

### Post by Hei Ku on 2009-06-21
Es un tema de hardware. Seguramente te falta algun filtro para el modem. Eso deberías verlo con los proveedores del modem.

---

