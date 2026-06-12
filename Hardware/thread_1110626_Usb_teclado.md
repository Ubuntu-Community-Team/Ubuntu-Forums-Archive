---
title: "Usb teclado"
date: 2009-03-30
forum: Hardware
---

### Post by 1412 on 2009-03-30
Hola, bueno, les comento que si escribo esto es porque evidentemente ya utilize a "San Google" y no rindio los resultados que yo esperaba, tengo un problema y es que recientemente formatie la PC, instale winXP y hice una particion de unos cuantos GBs a Ubuntu. Todo iba bien hasta que ubuntu me creo la pantalla de arranque, el problema esta aca; no puedo usar mi teclado USB, ya probe todo, active el USB KEYboard desde el BIOS, y nada, teoricamente segun las ayudas brindadas por SANGOOGLE me tendria que funcionar tanto para el bios (cosa que no hace) como para el arranque del sistema, asi que, tengo dos opciones, o me robo este teclado que es prestado, o solo puedo acceder al SO por defecto, que es Ubuntu, pero con mi USB no puedo elegir SO, porque no lo reconoce, ni el arranque ni el BIOS, repito, ya puse en Enable el <USB Keyboard Support> Asi como tambien probe poner en enable el <USB Mouse Support> pero nada, en un foro de por ahi, lei que probara cambiando el teclado de USB y nadaaaaaaaaaaaa... asi que, esto me deja en preguntar, WHAT UP!? que debo hacer si alguien tiene la solucion, y la solucion es del tipo <.aisdh> en consola dsp, "moasdasdausd.asd" en no se que, le explico que me lo explique bien como si fuera gorila porque es la primera ves que uso ubuntu y me gusta y no quiero empezar a odiarlo tempranito :P
jajja asi que desde ya muchas gracias , salu2

---

### Post by |Porsche on 2009-03-30
Probaste otro puerto usb? Usa un teclado virtual y dale el comando lsusb | grep -i keyboard. Mira a ver si te sale el teclado. Si no te sale el teclado pues robate el que estas usando gorila!!

---

### Post by Hei Ku on 2009-03-30
El teclado no te funciona solamente durante el arranque? Despues, cuando ya arrancó Linux te funciona bien?

En ese caso, tenes que probar con distintas combinaciones en tu BIOS. Ademas, es importante saber qué version de Ubuntu instalaste, porque esas cosas mejoraron mucho recien en las ultimas versiones.

---

### Post by guillermolisi on 2009-03-30
> **Hei Ku said:**
> El teclado no te funciona solamente durante el arranque? Despues, cuando ya arrancó Linux te funciona bien?

En ese caso, tenes que probar con distintas combinaciones en tu BIOS. Ademas, es importante saber qué version de Ubuntu instalaste, porque esas cosas mejoraron mucho recien en las ultimas versiones.
He visto maquinas en las que el teclado y mouse USB no funcionan hasta que algun SO carga drivers.

De hecho, para acceder a la configuracion del BIOS tuve que conectar un teclado PS/2.
Logicamente, tampoco podes usarlos cuando estas en el Boot Manager porque en ese punto aun no hay drivers USB cargados.

---

### Post by |Porsche on 2009-03-30
Yo creo que ese es el problema que el tiene. La solución mas barata, después de robarse el teclado prestado, es un adaptador usb/ps2 no creen?

---

### Post by Hei Ku on 2009-03-30
Depende de la combinacion de mother y teclado.
Que marca y modelo es el mother?
Que marca y modelo es el teclado?

---

### Post by josecuervo86 on 2009-03-30
Yo entiendo que le carga Ubuntu (que es el predeterminado) pero tampoco puede usar el teclado. Tendra los puertos usb activados??
Yo tengo un Genius Slimstar 250 USB pero me vino con un adaptador PS/2 asique lo uso para dejar los USB libres y anda perefecto

---

### Post by NickCis on 2009-03-31
A un amigo le instale Ubuntu Intrepid, y le reconece el teclado y mouse Usb inalambricos perfectamente. Claro, andan cuando Ubuntu carga los drivers para el grub si o si un teclado ps2.

Fijate que vercion de Ubuntu instalas por que las mas nuevas ya casi no tienen problemas con los teclados Usb...

Saludos.

---

