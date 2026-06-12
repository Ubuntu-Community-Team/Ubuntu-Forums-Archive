---
title: "¿Como conectar el teléfono con Ubuntu?"
date: 2009-02-23
forum: Hardware
---

### Post by carcar8 on 2009-02-23
Hola, Saludos

Se puede conectar una linea telefónica con Ubuntu?
No estoy hablando de Skype o Ekiga.
Mi pregunta concreta es si se puede conectar una linea
de Telefónica o Telecom por ejemplo.
Leí algo sobre instalar una centralita telefónica con Asterix.
(con varias lineas y derivaciones o internos)
Pero quiero dar mis primeros pasos con algo mas sencillo y menos 
sofisticado (si es que existe una herramienta sencilla en Ubuntu para esto)

Supongo que necesitare entre otras cosas un Moden/Fax con entrada
para linea telefónica.

Gracias

Carcar8

---

### Post by guillermolisi on 2009-02-24
> **carcar8 said:**
> Hola, Saludos

Se puede conectar una linea telefónica con Ubuntu?
No estoy hablando de Skype o Ekiga.
Mi pregunta concreta es si se puede conectar una linea
de Telefónica o Telecom por ejemplo.
Leí algo sobre instalar una centralita telefónica con Asterix.
(con varias lineas y derivaciones o internos)
Pero quiero dar mis primeros pasos con algo mas sencillo y menos 
sofisticado (si es que existe una herramienta sencilla en Ubuntu para esto)

Supongo que necesitare entre otras cosas un Moden/Fax con entrada
para linea telefónica.

Gracias

Carcar8
Personalmente solo conozco Asterix y se que en Ubuntu funciona muy bien.

La aplicacion es buenisima, hay que leer mucho y configurar bastante (en relacion directa con la complejidad funcional que se pretende de la red de telefonos) pero una vez en marcha, anda solo.

---

### Post by carcar8 on 2009-02-25
Hola, Saludos

Gracias Guillermo ;)
 
Encontré una Wiki bastante interesante sobre Asterix por lo tanto lo comparto:

[http://info.linuxmall.cl/wiki/index.php/Asterisk_primeros_pasos](http://info.linuxmall.cl/wiki/index.php/Asterisk_primeros_pasos)


Seguramente Asterix es una excelente herramienta pero me parece demasiado sofisticada para lo que yo prentendo (experimentar con una centralita hogareña sencilla)
Por el momento supera mis conocimientos técnicos, (tendré que sentarme y leer, leer, leer) si aparece algo mas sencillo lo agradeceré.

Nota:
OSX de Mac y Windows poseen herramientas simples y sencillas para conectar lineas telefónicas, que quedan incluso vinculadas a la agenda personal y contactos telefónicos, no puedo creer que en GNU/Linux no exista.
Y si no existe, ¿No es un pequeño desafío para los desarrolladores de la comunidad GNU?

Carcar8

---

### Post by sajnox on 2009-02-25
No me queda claro la parte de pequeño....

---

### Post by javdie on 2009-03-04
Hola Amigo, te cuento que yo soy un "recien estrenado" en el mundo de Linux. trabajo en comunicaciones, y estoy por comenzar a desarrollar soft para Asterix, por eso mi sambullida a ubuntu ;)
No se mucho aun sobre el sistema, pero si sobre telefonica IP que es lo que tu quieres hacer. Te cuento que para poder conectar la linea telefonica de tierra (es decir, las de telefonica, telecom, etc.) vas a necesitar lo que se llama una placa FXO. tambien se conoce como ATA (puedes encontrarlas en mercadolibre a costos relativamente bajos). Estas placas lo que hacen es comvertir la señal analogica que usan los telefonos comunes, y pasarlas a protocolos VoIP (Voz sobre IP) como es SIP (el mejor de todos a mi parecer) el H.323; el H.225...etc...etc...
En resumen, esta placa te haria de "raductor" entre tu maquina y la linea telefonica.
Entonces, vos configurarias la central Asterix (o cualquier otra salida de voz) para llamar a traves de una IP (la cual se la asignas a la placa FXO) y con eso ya tendrias conectada la linea de telefono a la compu. Eso si, deberas tomarte un rato para configurar bien la FXO y la compu...

Espero que esto te haya servido de ayuda, y si necesitas algo mas, no dudes en consultarme.

              Exitos!!!

---

### Post by carcar8 on 2009-03-18
Gracias Javdie!!  ;)

Ahora por lo menos se donde queda el norte.
Tu info es de gran ayuda.
Agradecere todo tipo de información sobre el tema de telefonos
Un detalle: hay modelos de Mac que ya vienen con una entrada para linea telefonica incorporada, supongo que se trata de una placa "traductora" o interface.

Carcar8

---

### Post by carcar8 on 2009-03-18
Hola Sajnox, Salu2

Lo de "pequeño desafio" lo digo con todo respeto.
Me parece admirable la capacidad y voluntad, el trabajo en equipo que demuestran constantemente los desarrolladores del ambiente GNU/Linux.

Han sido capaces de afrontar y superar grandes desafios.
Y me parece que comparando, simplificar la conexion de telefonos para el simple usuario de Ubuntu por ejemplo, no es un "gran" desafio.
No digo que es facil, debe tener desde el punto de vista del desarrollo y programacion sus dificultades.
Seria bueno que sobre este tema y otros alguien recoja el guante, y los simples y humildes usuarios agradecidos,  es todo lo que quise decir

Quedo un poco mas claro?

Carcar8

---

### Post by carcar8 on 2009-03-20
Hola, Salu2

No se si lo conocen, pero encontre un foro en castellano bastante interesante en Yahoo sobre TrixBox y Asterisk.

[http://espanol.groups.yahoo.com/group/trixbox_esp/](http://espanol.groups.yahoo.com/group/trixbox_esp/)

Carcar8

---

