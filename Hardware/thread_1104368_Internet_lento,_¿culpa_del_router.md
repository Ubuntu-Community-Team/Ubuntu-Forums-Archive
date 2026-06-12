---
title: "Internet lento, ¿culpa del router?"
date: 2009-03-23
forum: Hardware
---

### Post by ramiro_md on 2009-03-23
Buenas, posteo con una inquietud que me tiene desde el viernes. REsulta que el viernes por la tarde compré un router inalámbrico para que mi hermana tenga internet con su laptop en cualquier rincón de la casa (logrando que deje de invadir mi cuarto).
Conecté el artefacto como corresponde, y pobré satisfactoriamente en cada una de las 3 maquinas a las que reparto internet si funcionaba la conexión.
El tema es el siguiente. EL sabado me pongo a descargar unos cds de T! (descarga directa) y veo que la tasa de transferencia no superó los 20 kb/s (cuando me debería andar a casi 80 kb/s)..lo primero que se me cruzó por la mente fue: mi viejo y mi hermana están conectando y deben estár bajando algo de seguro...pero esa teoría quedó descartada al comprobar que no se encontraban en casa y que sus computadoras estaban apagadas :? .Probé en la pc de mi viejo (con window$ 2000) y la tasa no superaba los 25 kb/s. Lo segundo que pensé (y que aún no descarto) es me están tobando wifi..pero le puse clave y filtrado de MAC como sugería la "guía de instalación".
Probé conectando el modem directamente al pc pero jamás conectó ¬ por lo que estoy en ascuas :S.
No sé si será un problema de cconfiguración o me estan robando señal de wifi...pero la cuestión que probé en XP. W2K, Ubuntu y Debian y el problema es similar en los 4 sistemas.
Recurro a los foros porque sé que hay gente que entiende un poquito más de esto y tal vez pueda darme una idea.
Un saludo y gracias.

---

### Post by pablo.s on 2009-03-23
Hola: A continuación una rafaga de preguntas para orientar:

Que modelo de router es?
De que servidor bajabas los archivos? Rapidshare?
El router tiene firewall? Tiene puertos que cierra por default?
El proveedor de internet no estaba fallando?

---

### Post by ramiro_md on 2009-03-23
> **pablo.s said:**
> Que modelo de router es?
TP-LINK WR340G
> De que servidor bajabas los archivos? Rapidshare?
Rapidshare, Megaupload, Mediafire, páginas de descargas de archivos como  Softonic y demás.
> El router tiene firewall? Tiene puertos que cierra por default?
Obvio que tiene, pero no lo tengo activado.
> El proveedor de internet no estaba fallando?
NO creo, 4 dias fallando ? flash es croto pero no para tanto jeje

---

### Post by sergiom99 on 2009-03-23
Antes como estaban conectadas las PC?
Proba de buscar en la configuracion del router la opcion para clonar MAC Address y que clone la de la PC que estaba directo al modem.
Asi para el ISP, "sigue conectado igual que antes".
Esto hace que el router muestre esa MAC Address, para el caso de los ISP que validan la MAC de la placa que se conecto por primera vez.

Y sino llama al soporte a ver que dicen.
Otra prueba para testear velocidad de conexion: [http://www.dslreports.com/speedtest](http://www.dslreports.com/speedtest)

---

### Post by ramiro_md on 2009-03-23
> **sergiom99 said:**
> Antes como estaban conectadas las PC?
Proba de buscar en la configuracion del router la opcion para clonar MAC Address y que clone la de la PC que estaba directo al modem.
Asi para el ISP, "sigue conectado igual que antes".
Esto hace que el router muestre esa MAC Address, para el caso de los ISP que validan la MAC de la placa que se conecto por primera vez.

Y sino llama al soporte a ver que dicen.
Otra prueba para testear velocidad de conexion: [http://www.dslreports.com/speedtest](http://www.dslreports.com/speedtest)

> Antes como estaban conectadas las PC?
Antes estaban conectadas a traves de un ruteador alámbrico, y andaba todo joya.

> Proba de buscar en la configuracion del router la opcion para clonar MAC Address y que clone la de la PC que estaba directo al modem.
Asi para el ISP, "sigue conectado igual que antes".
Esto hace que el router muestre esa MAC Address, para el caso de los ISP que validan la MAC de la placa que se conecto por primera vez.
Gracias por el dato, lo voy a probar.

> Y sino llama al soporte a ver que dicen.
Llame una vez para que me ayuden con un problema con el router viejo y me dijeron que solo daban soporte si tenía un router suyo. El otro día me comuniqué con ellos para ver si me podían proporcionar un modem o router inálambrico y evitarme nuevos problemas con el soporte técnico, pero me dijeron que no tenían stock por eso recurrí a comprarme uno por mi lado...son chantas o no ?

> [http://www.dslreports.com/speedtest](http://www.dslreports.com/speedtest)
Ya probé en una página parecida y me dió como resultado una velocidad equivalente a 256 kbs cuando deberia ser de 612 kbs

---

### Post by ramiro_md on 2009-03-23
Probé lo de clonar la MAC..me dejó sin internet por completo..esperé 15 minutos y nada..asique la reestablecí.

---

### Post by sergiom99 on 2009-03-23
> **ramiro_md said:**
> Probé lo de clonar la MAC..me dejó sin internet por completo..esperé 15 minutos y nada..asique la reestablecí.

mmm que raro, en lo de mi novia (con cablemodem de flash) al poner el router wifi nos quedamos sin internet, asi que clonamos la MAC de la PC y apagamos modem+router, prendimos modem, router y PC y volvio a andar perfecto hasta ahora.

---

### Post by pablo.s on 2009-03-23
Te sugiero algo **PERO CORRE EN TU ENTERA RESPONSABILIDAD:**

Probá con una actualización de Firmware, puede resultar en una
mejor performance del router, yo lo hice con el mio y mejoró un
poco (pero no tenia el problema que tenias vos).

Si lo hacés que sea con cautela y siguiendo las instrucciones.
Saludos.

---

