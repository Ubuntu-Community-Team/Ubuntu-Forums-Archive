---
title: "Error NOAPIC"
date: 2008-09-05
forum: Hardware
---

### Post by smbarrionuevo on 2008-09-05
Tengo un problema al iniciar el UBUNTU 8.04, instale el SO como NO APIC, termina de instalar y al reiniciar me dice que bootee como NOAPIC el sistema operativo en el disco duro, alguien sabe como hacerlo?. Gracias!!!.

---

### Post by euzkoarima on 2008-09-05
1. entra a la bios y ponele noapic para que entre a ubuntu sin problemas
2. alt-F2 y como comando ```
gksu gedit /boot/grub/menu.lst
``` ahí buscas la primer entrada, en caso dice > title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=77cec7e4-db4a-490c-bfbf-23105de56fa7 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet


en la linea de kernel le agregás noapic al final y listo.
3. deja la bios como estaba antes, sobre todo si tenes win en la misma pc

Saludos

---

### Post by Hei Ku on 2008-09-05
> **euzkoarima said:**
> 1. entra a la bios y ponele noapic para que entre a ubuntu sin problemas
2. alt-F2 y como comando ```
gksu gedit /boot/grub/menu.lst
``` ahí buscas la primer entrada, en caso dice 

en la linea de kernel le agregás noapic al final y listo.
3. deja la bios como estaba antes, sobre todo si tenes win en la misma pc

Saludos

Esto esta mal, porque la proxima vez que actualice el kernel se le va a borrar la entrada y va a tener problemas para iniciar otra vez.

Lo correcto es:
```
gksu gedit /boot/grub/menu.lst
```

Buscar estas lineas:
```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash noapic nolapic

```

y en #defoptions le agregas no apic, como esta arriba.

Grabas y despues en la consola pones:

```

sudo update-grub

```

y reinicias.

Si no podes iniciar la primera vez, apretas e, despues elegis la 3er o 4ta linea que es la de booteo, apretas de vuelta e, le agregas noapic y apretas b para bootear. Luego seguis estas instrucciones.

El problema con las instrucciones anteriores es que se sobreescriben despues de una actualizacion de kernel.

---

### Post by euzkoarima on 2008-09-05
> **Hei Ku said:**
> Esto esta mal, porque la proxima vez que actualice el kernel se le va a borrar la entrada y va a tener problemas para iniciar otra vez.



Cierto!!
Como lo explico Hei Ku te va a quedar arreglado para siempre

Saludos

---

### Post by faktorqm on 2008-09-08
> **Hei Ku said:**
> Buscar estas lineas:
```

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash noapic nolapic

```

y en #defoptions le agregas no apic, como esta arriba.


¿Por que sos tan grosso? Mirá que si seguis siendo tan grosso el kernel se da cuenta y te entra un virus eh!! :lolflag:

Ahora, la pregunta. Vos pones ahi que en #defoptions agregue los parametros, pero no queda como comentario eso? 
yo me autorespondo (decime si esta bien o esta mal): cuando haces update-grub el tipo siempre se fija en el comentario, y lo agrega a cada entrada del kernel. Cuando actualiza, en realidad tambien se ejecuta el mismo comando, asi que pasa lo mismo. En cambio si yo lo pongo en la entrada del kernel directo, el actualizador va al update-grub, éste va a al comentario, directamente re-arma la linea sin tu opcion (por que no esta en el defoptions) y acto seguido vas y lo editas por que no esta tu opcion previa puteada. Salu2!

---

### Post by Hei Ku on 2008-09-08
> **faktorqm said:**
> ¿Por que sos tan grosso? Mirá que si seguis siendo tan grosso el kernel se da cuenta y te entra un virus eh!! :lolflag:


Lo aprendí a la fuerza. Mi mother adelantaba la hora si no arrancaba con noapic, y jugaba al ogame donde necesitaba un reloj exacto.  :lolflag:

> 
Ahora, la pregunta. Vos pones ahi que en #defoptions agregue los parametros, pero no queda como comentario eso? 
yo me autorespondo (decime si esta bien o esta mal): cuando haces update-grub el tipo siempre se fija en el comentario, y lo agrega a cada entrada del kernel. Cuando actualiza, en realidad tambien se ejecuta el mismo comando, asi que pasa lo mismo. En cambio si yo lo pongo en la entrada del kernel directo, el actualizador va al update-grub, éste va a al comentario, directamente re-arma la linea sin tu opcion (por que no esta en el defoptions) y acto seguido vas y lo editas por que no esta tu opcion previa puteada. Salu2!

Exactamente!

---

### Post by faktorqm on 2008-09-08
y te tuve que dar una medalla no me quedo otra...:(

---

### Post by zeroadrenaline on 2008-09-08
Jajajaja es un tirapluma el tipo, che el corrector de insultos me saco de un post la palabra f u n _k (el estilo musical) porque penso que era el insulto famoso de la F en ingles. Malisimo, y recontra of topic, perdon!.

---

