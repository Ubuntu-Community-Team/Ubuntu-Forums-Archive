---
title: "Desactivar unidad de DVD o saltarse el proceso en el inicio."
date: 2009-06-25
forum: Hardware
---

### Post by Fisaulerod on 2009-06-25
Hola. Sucede que la unidad DVD de mi notebook está mala o suelta. A veces el sistema la reconoce y a veces no, y me refiero a que ni el BIOS reconoce la unidad. 
Según lo que he buscado, es probable que un cable IDE o parecido esté mal conectado (pues energía le llega, sí abre mientras estoy en el BIOS, no así cuando me meto a un SO), así que debo abrilo y conectarlo bien o de plano sacarlo.
El problema es que no puedo meterme a Ubuntu con este problema, como que Ubuntu trata de reconocer la unidad al iniciar y no puede y al final se queda en una pantalla negra.
¿Cómo puedo saltarme el proceso de reconocer la unidad mientras inicio Ubuntu para poder entrar a él?, o, si no se puede, ¿cómo puedo desactivar la unidad?, porque el Bios no me deja.
La cuestión es que por ahora no tengo herramientas para abrir el notebook y necesito urgentemente hacer una tarea con un programa de Linux...entonces necesito meterme a él...
Gracias de antemano.

---

### Post by Patriciologico on 2009-06-27
Que raro debieras poder desde la bios desactivarla. 

Desde ubuntu abre fstab

```
sudo gedit /etc/fstab
```

y comenta la linea donde aparezca la unidad de cd/dvd, por ejemplo la mía es

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0      0
```

Comentar significa anteponer el signo # con eso el sistema ignora dicha linea. El mio quedaría así

```
#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0   0
```

Saludos!

---

### Post by radixs on 2009-06-27
> **Patriciologico said:**
> Que raro debieras poder desde la bios desactivarla. 


yep, desde ahí es la solución para desactivarla

---

### Post by Fisaulerod on 2009-06-29
Sip, pero mi Bios es un poco inútil. Dice que se desactiva con <Crtl>+1, pero sólo suena el pito del computador. En realidad el Bios de mi notebook tiene muy pocas opciones, y lo digo porque he visto muchos otros Bios y este no me deja hacer casi nada.
Pero bueno, gracias, con el fstab funciona :P.

---

### Post by Patriciologico on 2009-06-29
Fijate que hay BIOS que traen opciones ocultas (para protejer al descuidado usuario) y se activa aveces Ctrl+F1 cosas asi, deberias buscar mas info de tu BIOS.

Saludos!

---

