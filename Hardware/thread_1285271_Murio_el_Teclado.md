---
title: "Murio el Teclado"
date: 2009-10-07
forum: Hardware
---

### Post by Applelnx on 2009-10-07
Hola, recien estaba usando Kubuntu 9.04 64 bits y me di cuenta que el teclado no funcionaba mas. Probe todas las teclas y nada. Reinicie para ver si se solucionaba, pero para mi desgracia el problema persistio. 

Probando con el Bloq. Num. averigue que el teclado deja de funcionar en el momento en que terminan de cargarse todos los elementos en el inicio (no se como se llama, antes de que aparezca el escritorio).

Tengo una notebook HP Pavilion dv4-1225dx y nunca me habia pasado nada similar con el teclado. No se que hacer :( HELP

---

### Post by guillermolisi on 2009-10-07
> **Applelnx said:**
> Hola, recien estaba usando Kubuntu 9.04 64 bits y me di cuenta que el teclado no funcionaba mas. Probe todas las teclas y nada. Reinicie para ver si se solucionaba, pero para mi desgracia el problema persistio. 

Probando con el Bloq. Num. averigue que el teclado deja de funcionar en el momento en que terminan de cargarse todos los elementos en el inicio (no se como se llama, antes de que aparezca el escritorio).

Tengo una notebook HP Pavilion dv4-1225dx y nunca me habia pasado nada similar con el teclado. No se que hacer :( HELP
Proba agregando en el grub lo siguiente:
```
title           Ubuntu 9.04, kernel 2.6.28-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=af49d7b3-6884-4c37-94ec-37388136d3af ro [COLOR=Blue]**acpi=off**[/COLOR] quiet splash
initrd          /boot/initrd.img-2.6.28-15-generic
quiet
``` y fijate que pasa.

Tengo dos maquinas con el mismo sintoma y que origino que informe del bug en Ubuntu.bug y luego a Bugzilla porque, para mi, hay una regresion en los kernels 2.6.28 que, supuestamente, se soluciona con el kernel 2.6.31. La regresion es que no resuelve bien el acceso a las funciones ACPI de la motherboard, cosa que con el kernel 2.6.24 funcionaba de primera.

---

### Post by ALEXEX on 2009-10-07
creo que la identificacion como en cualquier otro SO es hacer el metodo prueba y error, trat de instalar otro teclado con un puerto usb, y decir que paso.

Posiblemente no carga todos los drivers (desconozco como se dija en termino ubuntu), y no te permite o identifica en este caso el teclado, o como dice guillermo tenga un bug el kernel, en cuanto a compatibilidad con tu notebook.

---

### Post by Applelnx on 2009-10-07
Hola, gracias por repsonder. En primer lugar, le agregue el "acpi=off" al archivo /boot/grub/menu.lst pero el problema no se soluciono. Solo me aparece que la bateria esta desactivada.

No me di cuento pero el problema surgio justo despues de aplicar unas actualizaciones disponibles... habra manera de volver para atras?

Por ahora ando con el teclado usb de mi hno. Saludos

---

### Post by guillermolisi on 2009-10-07
> **Applelnx said:**
> Hola, gracias por repsonder. En primer lugar, le agregue el "acpi=off" al archivo /boot/grub/menu.lst pero el problema no se soluciono. Solo me aparece que la bateria esta desactivada.

No me di cuento pero el problema surgio justo despues de aplicar unas actualizaciones disponibles... habra manera de volver para atras?

Por ahora ando con el teclado usb de mi hno. Saludos
Podrias postear el contenido de /var/log/dmesg y /var/log/messages habiendo iniciado sin el acpi=off ? Si son muy largos, comprimilos y adjuntalos.

---

### Post by Applelnx on 2009-10-07
Ahi los subi.
Solo por las dudas si no entendi bien: saque la parte de acpi=off, reinicie y despues copie estos dos archivos.

---

### Post by Applelnx on 2009-10-08
Pregunta bienintencionada, mas o menos de cuanto tiempo estamos hablando para que corrijan uno de estos errores? Del orden de dias, semanas, meses? Mas o menos quiero saber para ver si formateo y es mas rapido. Saludos :)

---

### Post by guillermolisi on 2009-10-08
De la salida de dmesg rescato lo siguiente:
> [    6.163277] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    6.209319] serio: i8042 KBD port at 0x60,0x64 irq 1
[    6.209326] serio: i8042 AUX port at 0x60,0x64 irq 12
[    6.220582] mice: PS/2 mouse device common for all mice


[   17.127098] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input11
[   17.204096] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input12
Y no vi algo, algun indicio de problemas para con el teclado con lo cual quedaria por ver que hace el X-server al respecto.

En la salida del messages rescato:
> Oct  7 17:44:49 apple-laptop kernel: [    6.163277] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Oct  7 17:44:49 apple-laptop kernel: [    6.209319] serio: i8042 KBD port at 0x60,0x64 irq 1
Oct  7 17:44:49 apple-laptop kernel: [    6.209326] serio: i8042 AUX port at 0x60,0x64 irq 12
Oct  7 17:44:49 apple-laptop kernel: [    6.220582] mice: PS/2 mouse device common for all mice

O sea que en ambos hay un correcto reconocimiento del teclado y mouse, asi que la cosa, para mi, pasa por otro lado.

OT: Vi que en el archivo messages hay cantidad de eventos referidos al teclado pero anteriores al inicio previo la generacion de las muestras que enviaste.
Tambien una advertencia sobre permisos inadecuados para con PulseAudio.

---

### Post by Applelnx on 2009-10-09
En realidad el teclado se cuelga justo despues de que cargue (ver imagen)

[IMG]http://img3.imageshack.us/img3/9479/kubuntu.jpg[/IMG]

Cuando carga el escritorio se cuelga.
Lo del audio mientras funcione todo bien, prefiero no tocar.

---

### Post by guillermolisi on 2009-10-09
> **Applelnx said:**
> En realidad el teclado se cuelga justo despues de que cargue (ver imagen)

[IMG]http://img3.imageshack.us/img3/9479/kubuntu.jpg[/IMG]

Cuando carga el escritorio se cuelga.
Lo del audio mientras funcione todo bien, prefiero no tocar.
Estas aun con KDE 4.0 o es una imagen vieja ?

Si estas aun en 4.0, actualiza ya mismo a 4.3.2 !!

---

### Post by Applelnx on 2009-10-10
No, esa imagen la saque de internet. Estoy con KDE 4.2, el que vino por default en Kubuntu 9.04. Actualizo al 4.3?

---

### Post by guillermolisi on 2009-10-10
> **Applelnx said:**
> No, esa imagen la saque de internet. Estoy con KDE 4.2, el que vino por default en Kubuntu 9.04. Actualizo al 4.3?
Si, totalmente. Hay muchisimos arreglos entre cada subversion y si bien no tengo la certeza de que la actualizacion solucione tu problema tampoco sera negativa, ya que funciona mas rapido y mucho mas estable que sus antecesoras.

---

### Post by Applelnx on 2009-10-10
Actualice, pero el teclado seguia sin responder. Trate de configurar un par de cosas del network manager y despues de un reinicio, volvio el teclado :)

Gracias tocayo ;)

PD: le pongo solved aunque no se bien como :P

---

