---
title: "internet movil con modem samsung B1110L (ENTEL) en Ubuntu"
date: 2009-10-22
forum: Hardware
---

### Post by cottita on 2009-10-22
oliiiii
ojalá puedan ayudarme
quería consultar si alguien sabe cómo instalar este modem en Ubuntu
si alguien lo usa en alguna versión

De antemano gracias me ayudarían mucho porque llevo mucho tiempo buscando :(

---

### Post by Carlos C on 2009-10-22
Hola. Por favor recuerda publicar en el subforo adecuado. He movido tu thread a "Hardware". En caso de que no estés segura de dónde escribir tus consultas puedes leer el [sticky]("http://ubuntuforums.org/showthread.php?t=1162708") publicado en cada subforo con el fin de resolver ese tipo de dudas.

Saludos.

---

### Post by bichopro on 2009-10-23
Y en sistema>conexiones de red>banda ancha movil>entel pcs

no funciona?

---

### Post by moreback on 2009-10-23
Yo tengo un B1100 (creo que el B1110 no existe) y tengo [una guía de como hacerlo para Ubuntu 8.10]("http://pcarmona.wordpress.com/2009/03/17/modem-3g-samsung-b1100-en-ubuntu-810/").

Para Ubuntu 9.04 es mucho más fácil ya que solo hay que agregar la conexión como dijo Bichopro, pero siempre hay que tener en cuenta que hay que expulsar el cd llamado B1100 (aunque también tengo [un método para hacer esto automáticamente]("http://pcarmona.wordpress.com/2009/09/27/automatizando-conexion-3g-con-modem-samsung-b1100/")).

Saludos.

---

### Post by cottita on 2009-10-24
perdón por postear mal el thread
y gracias por la ayuda!!
intentaré hacer lo que me dicen :)

---

### Post by cottita on 2009-10-25
no pude =/ no sé que hice mal
pero me costó mucho instalar los archivos del network manager
y resulta que al reiniciar el pc
ni siquiera me aparecen las Conexiones de Red

---

### Post by asterix77 on 2009-10-26
Cottita

Acá te dejo un link para que trates de conectarte con tu módem. Está hecho para intrepid, pero en Jaunty es igual. Ten cuidado eso sí porque en el ejemplo aparecen unos dns que no corresponden debes cambiarlos por estos

--> primary   DNS address 200.63.56.3
--> secondary DNS address 200.63.56.4


[http://joniux.x-red.com/2009/02/26/ubuntu-810-con-modem-huawei-e270-entel-pcs/](http://joniux.x-red.com/2009/02/26/ubuntu-810-con-modem-huawei-e270-entel-pcs/)

El problema en intrepid es que, como se comenta en el post uno escribe los dns, pero al reiniciar se borran y vuelven a aparecer los anteriores. Una forma de resolver esto es editar el fichero de configuración, pero es mejor usar gedit que vi

# sudo gedit  


Saludos

---

### Post by moreback on 2009-10-26
> **cottita said:**
> no pude =/ no sé que hice mal
pero me costó mucho instalar los archivos del network manager
y resulta que al reiniciar el pc
ni siquiera me aparecen las Conexiones de Red

Mmmmhh... la guía es para Ubuntu 8.10, ¿qué Ubuntu tienes tú?

Si es la 9.04 no es necesario instalar los paquetes que aparecen en el sitio, ya que el NM que viene con esta versión no tiene problemas con el modem.

Saludos.

---

### Post by HayatoJin on 2009-10-28
Yo tengo ese Modem...y uso 9.04...cuando lo conectas te aparece una unidad de CD "virtual" en el escritorio...boton derecho, expulsar y te lo detecta de una...solo tuve que seguir un asistente...

---

