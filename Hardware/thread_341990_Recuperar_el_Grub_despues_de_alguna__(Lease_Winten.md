---
title: "Recuperar el Grub despues de alguna ***** (Lease Wintendo)"
date: 2007-01-19
forum: Hardware
---

### Post by oberonking on 2007-01-19
La forma de recuperar el grub que está en casi todos lados es booteando un live cd, hacer un chroot en nuestra partición de ubuntu e instalar grub, pero la verdad es que de esa forma nunca lo pude recuperar, para hacerlo siempre tuve que poner algunos comandos más, aquí los dejo para los que les pase lo mismo que a mi:
Primero que nada bootear el live cd de ubuntu, y abrir una consola (aplicaciones/accesorios/terminal) en la cual escribimos ésto (recuerden que los símbolos "$" son para indicarnos las lineas separadas y no se escriben).

En mi caso ubuntu está en /dev/hda3 si lo tienen en otra partición simplemete lo cambian, para ver la lista de particiones se escribe: sudo sudo fdisk /dev/hda

$ sudo su
$ mkdir /media/ubuntu
$ mount /dev/hda3 /media/ubuntu
$ mount --bind /dev /media/ubuntu/dev
$ mount --bind /proc /media/ubuntu/proc
$ mount --bind /sys /media/ubuntu/sys
$ chroot /media/ubuntu/
$ grub-install /dev/hda

Si tienen la /boot por separado, y no en una carpeta de la partición root ( / ), que no es lo normal, antes de ejecutar grub-install /dev/hda se monta la partición de esta forma:

$ mount /boot

Eso es todo, espero que les halla servido.

---

### Post by lavaramano on 2007-01-19
buenisi.
yo el otro dia tuve un problema similar por una rotura de fstab ;P

---

### Post by DuckMan on 2007-01-19
la prox vez q cague el MBR lo pruebo y te digo, si funciona te ganas una remera gratis

---

### Post by oberonking on 2007-01-19
> **DuckMan said:**
> la prox vez q cague el MBR lo pruebo y te digo, si funciona te ganas una remera gratis

Las 3 veces que tuve que reinstalar Wintendo, me anduvo de maravilla..... y en casas de amigos tambien 
Esperemos que a todos les ande igual, por que nadie esta libre de reinstalar Win$

---

### Post by MeduZa on 2007-01-19
> **oberonking said:**
> Las 3 veces que tuve que reinstalar Wintendo, me anduvo de maravilla..... y en casas de amigos tambien 
Esperemos que a todos les ande igual, por que nadie esta libre de reinstalar Win$

eso te pasa por andar metiendo kk en la pc, siempre lo dije wintendo es un virus no metan el cd en la pc o se les arruina :lolflag:

---

### Post by felipelerena on 2007-01-19
que joraca es wintendo?

---

### Post by MeduZa on 2007-01-19
> **felipelerena said:**
> que joraca es wintendo?

un virus que anda rondando por ahi en varias verciones la ultima y mas peligrosa se llama win (tendo) dows Vista

es windows pero lo lei por ahi y me dio risa, es como la mescla de windows con nintendo (alta compania) pero como hace solo consolas de juegos y el windows solo sirver para jugar.... salio la idea, pero si no te gusta le dijo windo y listo para no ofender a nadie ;)

---

### Post by kowal on 2007-01-20
Otra opción es usar Super Disco Grub (funciona de perlas):

[http://adrian15.raulete.net/grub/tiki-index.php?page=Es](http://adrian15.raulete.net/grub/tiki-index.php?page=Es)

Saludos!

---

### Post by Nemesis Teufel on 2007-01-20
Buenisimo, gracias a todos, siempre hay algun yo que hace ****** con los grubs.

Ahora.. yo quiero hacer lo mismo pero al revez.. o sea.. quiero desactivar el grub. Mi vieja.. mi queridisima vieja........ descubrio que si reinicia la pc y cambia a Windows, puede jugar a las picas x inet... ******* a mi las cosas que estoy bajando y demas... Entonces, con la excusa de que saque al "otro" por q me traia viruses y me rompia la pese, lo "saqué".

Como haria para cambiarle la ruta y no acceder a windows?
Como hago para luego poder volver a poner la ruta y volver a windows?..

gracias d antemano x pedir ****.
(todo sea x ubuntu)

---

### Post by oberonking on 2007-01-20
O sea que lo que queres hacer es que si tu madre reinicia la PC no pueda entrar en Wintendo?, que no salga en el grub?

Eso es asi, pon esto en un terminal:

$ sudo gedit /boot/grub/menu.list

Ahi vas hasta el final y comentas todas las lineas que dicen "windows**" (poner "#" delante de las lineas).
Guardas y listo....

Para revertir esto vuelves a editar el "menu.list" y borras los "#" que pusiste...

Espero que eso sea lo que querias hacer y te sirva...

Saludos :lolflag:

---

### Post by Nemesis Teufel on 2007-01-20
mmm.. cuando ejecuto:
 ```
sudo gedit /boot/grub/menu.list
```

Se abre el editor de texto, pero esta en blanco.. **** se me creo en otro lugar me imagino.. ya que debo tener un menu list de mi grub.... :S

offtopic:
Isla avalon rlz.
Que buena quedo la page. Quien es el artista d la pic?

---

### Post by oberonking on 2007-01-20
hmmmm, veo que mi estupidez y me memoria estan a full.
Creo que le erre feo, error mio, perdon

No es menu.list, es menu.lst, mil perdones :roll: 

Prueba ahora

offtopic
Si te refieres a la señorita, es de un juego japones (no saber quien hacerlo)
Si te refieres al banner de arriba ese fui yo

Gracias por el comentario!!!

---

### Post by Nemesis Teufel on 2007-01-23
Ahi esta! de maravilla!
Mi mamá me pregunto al otro dia:" que le paso al otro? puedo entrar al.. ubuntu ese.. pero al otro no" pronuncia ubuntu con miedo jaja.
Y le dije:" ahh xq el otro me rompe la pc, me pone virus y dps se rompe (?)" que en cierta forma algo de razon hay.

Adoro ser malvado en estas cosas!
I got the power

---

### Post by griever-nux on 2007-02-09
lo mas facil es bajarse un programa que se llama SUPER GRUB, lo grabas en un cd y lo haces bootear y te arregla todo

saludos

---

### Post by jpmorelli on 2007-02-10
Cuando tuve el problema del Grub baje el Disco Super Grub y... o soy medio ***** o no me funcionó porque la verdad que no lo pude hacer... si ya sé que soy medio *** pero bueno, espero que otro lo entienda y logré usarlo como corresponde. :popcorn:

---

### Post by barnisimo on 2009-03-12
> **oberonking said:**
> la forma de recuperar el grub que está en casi todos lados es booteando un live cd, hacer un chroot en nuestra partición de ubuntu e instalar grub, pero la verdad es que de esa forma nunca lo pude recuperar, para hacerlo siempre tuve que poner algunos comandos más, aquí los dejo para los que les pase lo mismo que a mi:
Primero que nada bootear el live cd de ubuntu, y abrir una consola (aplicaciones/accesorios/terminal) en la cual escribimos ésto (recuerden que los símbolos "$" son para indicarnos las lineas separadas y no se escriben).

En mi caso ubuntu está en /dev/hda3 si lo tienen en otra partición simplemete lo cambian, para ver la lista de particiones se escribe: Sudo sudo fdisk /dev/hda

$ sudo su
$ mkdir /media/ubuntu
$ mount /dev/hda3 /media/ubuntu
$ mount --bind /dev /media/ubuntu/dev
$ mount --bind /proc /media/ubuntu/proc
$ mount --bind /sys /media/ubuntu/sys
$ chroot /media/ubuntu/
$ grub-install /dev/hda

si tienen la /boot por separado, y no en una carpeta de la partición root ( / ), que no es lo normal, antes de ejecutar grub-install /dev/hda se monta la partición de esta forma:

$ mount /boot

eso es todo, espero que les halla servido.

--------------------------------------

grande papá!!!! Funciona de 10....

---

