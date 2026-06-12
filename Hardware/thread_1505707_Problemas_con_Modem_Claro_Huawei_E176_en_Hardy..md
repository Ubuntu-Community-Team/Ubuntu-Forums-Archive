---
title: "Problemas con Modem Claro Huawei E176 en Hardy."
date: 2010-06-09
forum: Hardware
---

### Post by Lobo_Gris on 2010-06-09
Buenas,

Pues ampliando lo que dice el titulo del post, el problema es que el modem no es reconocido, y por ende no me conecta.

No se que hacer, además no tengo otra conexión que no sea ese modem por lo que necesito resolver este tema sin conectarme.

O sea, estos mensajes los escribo de la oficina.

¿Ideas?

Muchas gracias, saludos,
Gonzalo.

---

### Post by asterix77 on 2010-06-09
Instala los siguientes paquetes de la siguiente página en el orden que sigue.

[https://forge.betavine.net/frs/?group_id=12](https://forge.betavine.net/frs/?group_id=12)

(debes escoger según versión)

1) ozerocdoff
2) usb-modeswitch
3) vodafone-mobile-connect


Debiera servirte en Hardy, a mi me ha resultado al menos en Intrepid-Karmic y Lucid

Saludos

---

### Post by Lobo_Gris on 2010-06-11
Pues el usb-modeswitch no ha servido,
Me detecta el USB pero no lo detecta como medio de conexión.
Creí que era tema de que quizás estaba desactivado, me lo dio una amiga que no lo usa hace un tiempo, pero lo conecte a la maquina de la oficina que tiene windoze y lo pude utilizar tranquilamente.

Por otro lado no pude averiguar el pass del profile, ¿saben como sacarlo? ¿o si tengo que pedirlo a claro?

¿Hay otra forma de que lo detecte?

Saludos,
Gonzalo.

---

### Post by Lobo_Gris on 2010-06-11
Creo que debo haber estado bastante dormido cuando escribi los dos mensajes.
¿Tu te referias a que instale TODOS esos paquetes en el EXACTO orden en que me los dabas no?

:S

Pues ni modo, ya me los estoy bajando para probar lo que me has dicho.

Saludos.

---

### Post by asterix77 on 2010-06-14
Perdón por la tardanza, pero si, me refería a realizarlo en ese orden.

Con respecto al user y pass, al momento de ejecutar la aplicación, solo responde las preguntas realizadas, ya que son standar según pais, proveedor. No tienes que averguar nada, salvo en algunos casos el codigo PIN o PUK.

Saludos

---

### Post by Lobo_Gris on 2010-06-14
Pues hola, instale los dos primeros, pero, lamentablemente, cuando voy a instalar el paquete de Vodafone me pide unos 15 paquetes mas que son dependencias de este, por lo que no continua la instalación.
Ahora tengo que detecta el USB, pero no como modem, o por lo menos no entiendo como configurarlo.
¿Podré sacar esas dependencias de otro disco como de la versión 10.04? ¿O es demasiado Frankenstein?
Creo que son todas dependencias python, pero no estoy seguro.
¿Ideas?
Instalar este Modem sin acceso a internet debería ser el titulo. :p

Saludos, y gracias de ante mano.

---

### Post by asterix77 on 2010-06-16
Cuando instalé esta aplicación, recuerdo que el vodafone me pidió otras dependencias, pero me las descargó en forma automática (bueno pero para eso estaba conectado a internet a través de una Lan).

Una alternativa sería registrar los nombres de paquetes y descargarlos, e instalarlos en forma manual (Si es que no tienes acceso a Internet de alguna forma).

¿Puedes contar con acceso a internet por otra vía?

Lo anterior es una alternativa, existe otra que uso a veces, que es mediante wvdial, para instalarlo debes escribir

#sudo apt-get install wvdial

De todos modos, con el modem enchufado ejecuta lsusb en la terminal y pégalo acá

Saludos

---

