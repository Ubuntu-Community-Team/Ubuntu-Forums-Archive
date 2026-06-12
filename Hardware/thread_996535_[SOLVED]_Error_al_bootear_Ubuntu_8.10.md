---
title: "[SOLVED] Error al bootear Ubuntu 8.10"
date: 2008-11-28
forum: Hardware
---

### Post by fedeavila on 2008-11-28
Buenas gente, a ver si alguien tiene una idea de lo que pasa.
La cuestión es la siguiente, hoy me llegó el CD de Intrepid y lo instalé en mi disco que ya tenía XP.
Al parecer se instaló lo más bien pero cuando reinicio la PC y entro en el menú para elegir el OS, me aparecen como cinco.
Por lo que leí aparecen dos versiones de kernel's. De las cuales de esas dos, lo acompañan sus versiones "fail/safe" más Windows XP.
Bueno, elijo el primero de todos, o sea la versión más reciente, y se pone la pantalla negra con ese mensaje que adjunté en una imagen.
Por lo que busqué en Google, "podría" llegar a estar relacionado con los discos y los cables IDE, casualmente yo tengo un disco de 160GB-SATA y otro de 40GB-IDE que esta vacío, lo uso para hacer backups y otras cosas.
Ahora estoy escribiendo desde Ubuntu, elijo el kernel más viejo y ANDA pero: 1) Tengo que reiniciar dos veces para que no me aparezca esa notificación (ni idea por qué) y 2) Me gustaría saber que onda, es un error después de todo...

-----------
De paso ya que estoy, hago otra pregunta, se puede instalar XP teniendo Ubuntu ya instalado en todo el disco? O sea, Formatear todo el disco, instalar Ubuntu en el disco completo, y después poner XP en un espacio pequeño para el Office y el Messenger, etc...


Gracias!

---

### Post by fedeavila on 2008-11-29
Perdón gente, ya se arregló "solo"...

Lo único que hice fue desconectar el cable plano y volverlo a enchufar y no me tiró más el mensaje...

Un saludo :)

---

### Post by Hernán-Amaya on 2008-11-29
Con lo primero no te puedo ayudar mucho, a mi me pasó lo mismo pero por que había instalado el Grub2 se ve que rompió algo en el booteo. Lo solucioné desinstalando el Grub2 e instalando el grub. 

Para usar M$-Office y el messenger tenés en Gnu/Linux el Open Office, Amsn, emesene, y varios mas. Si aún así querés seguir usando las versiones de windows, te conviene virtualizar el windows y listo.

---

### Post by fedeavila on 2008-11-30
> **Hernán-Amaya said:**
> Con lo primero no te puedo ayudar mucho, a mi me pasó lo mismo pero por que había instalado el Grub2 se ve que rompió algo en el booteo. Lo solucioné desinstalando el Grub2 e instalando el grub. 

Para usar M$-Office y el messenger tenés en Gnu/Linux el Open Office, Amsn, emesene, y varios mas. Si aún así querés seguir usando las versiones de windows, te conviene virtualizar el windows y listo.

Hola Hernán, como va?
Te comento que ya conozco las alternativas a Windows, lo que busco es otra cosa y, específicamente lo que vos nombraste a lo último. Virtualizar.
Ahora... Conocés algún instructivo sencillo para poder realizarlo?

Un saludo

---

### Post by Hernán-Amaya on 2008-12-01
fijate en la guía ubuntu siempre me salvo cuando era mas novato 

[http://www.guia-ubuntu.org/index.php?title=VirtualBox](http://www.guia-ubuntu.org/index.php?title=VirtualBox)

---

