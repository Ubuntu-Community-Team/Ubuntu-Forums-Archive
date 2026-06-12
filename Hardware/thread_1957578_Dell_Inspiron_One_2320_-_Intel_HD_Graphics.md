---
title: "Dell Inspiron One 2320 - Intel HD Graphics"
date: 2012-04-12
forum: Hardware
---

### Post by aledruetta on 2012-04-12
Hola Comunidad!

Compré un Dell Inspiron One 2320. Pensé que siendo Dell y teniendo procesador y gráfica Intel no tendría problemas para instalar Ubuntu, pero sí, tuve problemas. Apenas pasa del primer menú del LiveCD "Probar sin instalar", la pantalla se apaga completamente. Por momentos, aparece como un flash, fracciones de segundo y vuelve a quedar completamente negra.

Intenté con la versión alternate y instalo todo, pero cuando aparece la pantalla de login, lo mismo, aparece una fracción de segundos y desaparece, aparece y desaparece. Desaparece tan rápido que no da tiempo a hacer nada, ni a ver la posición del cursor.

Me quiero matar! Alguien sabe qué se puede hacer?

---

### Post by granjero on 2012-04-13
que mala suerte che, yo tengo una dell 1440 y me anduvo todo de una. Que versión estas usando?

salud!

---

### Post by aledruetta on 2012-04-13
Probé con Oneiric y la última beta de Precise.

---

### Post by granjero on 2012-04-13
=(

[http://ubuntuforums.org/showthread.php?t=1903083](http://ubuntuforums.org/showthread.php?t=1903083)

> I have one and I can tell you that I'm having a lot of problems getting the graphics card working correctly. It does not recognize the resolution of the screen and I'm stuck with 1024x768. It seems to be poor support for the sandy bridge integrated graphics. Ubuntu will not show anything on the main screen during a boot, unless the 'nomodeset' option is added. OpenSuse boots fine, but the display is still limited to 1024x768. However the touchscreen and everything else works right off the bat.

---

### Post by elshell on 2012-04-21
Saludos si tu dell utiliza un tarjeta intel HD graphics prueba activando la opcion nomodeset en el cd live de ubuntu para esto cuando se te presente el menu de ubuntu donde te da la opcion de probar ubuntu sin instalarlo, presiona F6 y selecciona nomodeset luego arranca, y nos comentas como te fue, si esto te funciona te dejo el link para hacerlo permanente una vez instales ubuntu:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by aledruetta on 2012-04-22
Muchas gracias Granjero y elshell! Pude instalar Oneiric e inicializarlo, con una resolución menor y sin efectos gráficos, pero algo es algo.

Dejo el post a medio solucionar por si alguien más adelante encuentra la forma de que la resolución y los efectos se puedan usar correctamente.

Saludos

---

### Post by aledruetta on 2012-05-01
Algunas informaciones recopiladas sobre este tema:

Kernel Bug:
[https://bugzilla.kernel.org/show_bug.cgi?id=43181](https://bugzilla.kernel.org/show_bug.cgi?id=43181)

Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/912397](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/912397)

Descripción de otro usuario:
[http://www.grputland.com/2011/12/ubuntu-1204-alpha-1-sandy-bridge.html](http://www.grputland.com/2011/12/ubuntu-1204-alpha-1-sandy-bridge.html)

---

### Post by aledruetta on 2012-07-02
Bueno, por si alguien anda con los mismos problemas que yo, una buena noticia: instalé la Beta 2 de Quantal Quetzal y no fue necesario configurar el arranque con nomodeset y además reconoció al toque la configuración HD del monitor. Creo que es por el kernel 3.5.0-2-generic. Si todo sigue así, la próxima versión de Ubuntu va a resolver este asunto, qué bueno!!!

---

