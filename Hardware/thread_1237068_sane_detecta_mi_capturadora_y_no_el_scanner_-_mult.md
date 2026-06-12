---
title: "sane detecta mi capturadora y no el scanner - multifuncional epson tx 115"
date: 2009-08-10
forum: Hardware
---

### Post by cahv on 2009-08-10
:KS hola amigos es primera vez que escribo asi que espero tener suerte

tengo una multifuncional epson tx 115, scanner e impresora, el tema es que sane me detecta una capturadora que tengo la fly 2000 y no el scanner y no se como configurar este tema para poder escanear si alguien me puede ayudar estare agradecido, la impresora la logre configurar no se muy bien como debo decir que soy bastante novato en esto y estoy usando jaunty kubuntu amd64 de todas manera para la impresora parti jugando con esta pagina que me imagino muchos ya conocen

[http://localhost:631/](http://localhost:631/)

que al parecer configura la impresora en forma remota, no me resulto pero probando y probando al final funciono no se si esta al 100% pero funciona, ahora me interesa jugar con el scanner para aprobechar bien todo esto ya que la verda windows hace bastante tiempo no lo ocupo ya que prefiero linux aunque al principio para uno novato es para bastantes dolores de cabeza jejej :P

---

### Post by Carlos C on 2009-08-14
Algunos multifuncionales epson necesitan del paquete libsane-extras, que trae "epkowa" para funcionar correctamente con sane.

---

### Post by cahv on 2009-08-17
gracias por contestar 

ya lo instale y no paso nada he estado investigando por ahi y al parecer el problema es el sane.rc, aun no lo he visto del todo se supone que debo configurarlo pero no se como si encuentro la forma lo publicare por si a alguien le pasa lo mismo igual dejo la inquietud.

en todo caso por si alguien sabe en mi carpeta personal tengo un archivo ubicado en sane que al editarlo dice algo asi como NOname y sale el nombre de la capturadora y es .drc, este aparece cuando me meto al xsane y trato de cargar el archivo sane.rc que tengo, al cargarlo me da un error, otra cosa como comentario este archivo sane.rc no esta con el punto adelante como oculto no se sieso influira tambien:P:P

seguiremos por ahi buscando en algun momento resultara

---

### Post by welias on 2009-09-24
En una Terminal, 
sudo xsane
Y a pesar de la advertencia, dale ok y a ver si lo detecta.
Saludos

---

