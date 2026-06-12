---
title: "Extraño problema con Jaunty"
date: 2009-03-19
forum: Hardware
---

### Post by z37a on 2009-03-19
Ayer actualice el aplpha de Jaunty, baje unos paquetes por 100MB casi y entre ellos me pregunto en el update sobre como actualizar un paquete que se llamaba algo de checkbox, seleccione que se utilice los confs del paquete y no los que poseía yo. El tema ahora es que no me levanta la interfaz gráfica de ninguna forma, ni siquiera en safe mode, y la herramienta de raparacion tanto de paquete como de la reparación gráfica no me funciono. Puede ser que este usando una gráfica AMD(ATI) y que tal ez por ahí viene el error. A alguien le paso lo mismo, tiene alguna idea?

---

### Post by pablo.s on 2009-03-19
Te aparece algún tipo de advertencia de error? Me fijé en el paquete checkbox y la descripción dice: [B]This project provides an extensible interface for system testing. The
results can then be sent to Launchpad.[/B] No me da la impresión de que sea la causa del problema. El sistema se queda en prompt?
Guarda que también actualizaron paquetes de XOrg. Yo te propongo que leas xorg.conf para ver que se modificó. Saludos

---

### Post by eldragon on 2009-03-19
uhmmm... no se si sera esto, pero por las dudas pregunto:

algo que se actualizo, es xorg a la version 1.6?

tenes una placa ati? usas fglrx?

si respondiste si a todas estas preguntas. entonces tas muerto, proba los drivers open source de ati o vesa.

no sabria decirte que se actualizo porque no uso JJ.

si posteas el resultado de 
```

$ cat /var/log/Xorg.0.log | grep EE > errores_xorg.txt

```

podemos obtener algo de informacion.

---

### Post by z37a on 2009-03-19
Ahora mismo esta corriendo un apt-get upgrade que esta actualizando 198 megas! y como no tengo init 2 no me puse a ver el log, asi que mañana apenas termine saco un cat del log y lo posteo, a menos claro que alguno de estos paquetes me reparen el problema.

Ahora con el Xorg ya se que es el 1.6, tambien se que no hay drivers propietarios de amd aun, solo soportan xorg 1.5 por lo tanto no hay, esta con los drivers genericos y estoy usando la opcion de video VESA, pero es seguro que driver de video no es, es algun otro paquete, aunque podria ser algun paquete relacionado con el driver, pero no se aun que onda eso, termino de actualizar me fijo y posteo en log en caso de que no funcione!

PD: Muchas gracias pro sus respuestas!!!!

---

### Post by infernus92 on 2009-03-19
sion intenta volver a la version 1.5... es mejor estar un poco desactualizado y que funcione bien la computadora

---

### Post by z37a on 2009-03-20
aca dejo el cat del log:

```
	[    0.000661] (WW) warning, [    0.000670] (EE) error, [    0.000679] (NI) not implemented, [    0.000687] (??) unknown.
[    0.031009] (II) Loading extension MIT-SCREEN-SAVER
```

PD: Como puedo poner el Xorg 1,5?

---

### Post by Hei Ku on 2009-03-20
La version del Xorg de Jaunty es 1.6, que no anda bien con las ultimas placas de ATI.
Que modelo es tu placa de video? Postea el lspci.

---

### Post by eldragon on 2009-03-20
> **z37a said:**
> aca dejo el cat del log:

```
	[    0.000661] (WW) warning, [    0.000670] (EE) error, [    0.000679] (NI) not implemented, [    0.000687] (??) unknown.
[    0.031009] (II) Loading extension MIT-SCREEN-SAVER
```

PD: Como puedo poner el Xorg 1,5?

hmmm, es raro, xorg no tiene ningun error....

edita /etc/X11/xorg.conf y cambia tu placa de video por "vesa"

es decir, 
```

Device "vesa"

```

y reinicia el xserver con 
```

# /etc/init.d/gdm restart

```

si no levanta, entonces no es la tarj de video.

---

### Post by z37a on 2009-03-20
> **eldragon said:**
> hmmm, es raro, xorg no tiene ningun error....

edita /etc/X11/xorg.conf y cambia tu placa de video por "vesa"

es decir, 
```

Device "vesa"

```

y reinicia el xserver con 
```

# /etc/init.d/gdm restart

```

si no levanta, entonces no es la tarj de video.

Es justo lo primero que hice apenas aparecio el error. Mi placa de video es una Ati HD3200 de las onboard! Igualmente voy a probar reinstalando a ver que onda y actualizando por pauetes, de paso asi encuentro cual es el que afecto la configuracion


Agrego: Para no poner otro post, acabo de reinstalar con el alpha6, a la hora de realizar el update soloccione mantener los archivos de configuracion actuales en el checkbox y checkbox-gtk, ahora esta funcionando de 10(salvo por que es un alpha y tiene sus errores)

---

### Post by z37a on 2009-03-28
Bien lo arruine de nuevo, pero esta vez ya identifique pro donde anda el problema, al parecer es con el driver de video, ya se que jaunty es beta peor hoy se lanzo el catalist 9.3 con soporte para xorg 7.4, si bien la instalacion automatica no funciono segui el proceso del wiki de ati linux y bueno me rompio las X, ahora ni idea como volver atras ya que hize backup del xorg antes peor al recargarlo no me lo deja iniciar, asi que nuevo format e install esta vez usando el cd del beta por lo menos!!!! Asi que si quiero usar Jaunty me resigno a esperar para solucionar los problemas de video.

PD: Es que uso 1680x1050 de resolucion y con e ldriver libre anda para atras mal!!! y ni hablar de la falta de 3D aunque lei por ahi que el driver libre va a soportar 3D al parecer para cuando este el ubuntu 9.10, espero asi sea!!!

---

### Post by euzkoarima on 2009-03-31
Medio OT pero comento, ayer me entere de la versión 9.3 y que en 64 bits arreglaba problemas de reproducción de videos. Lo bajé, instalé y todo ok.

No le había prestado atención a que funciona con xorg 7.4 , pero buenísimo.
Yo también uso 1650x1080 y anda joya (aunque no uso los efectos, por ahora al menos)

Saludos,
Eduardo

---

### Post by z37a on 2009-04-18
[SIZE="5"]Tema solucionado!!!![/SIZE]

No sean ratas como yo que le baje la RAM al vídeo y le puse solo 32MB, por que ahí estaba mi problema, le metí 256(en la bios) y ahora anda de 10!!!!

Si bien el driver de video me anda muchísimo mejor sigo con algunos problemillas, pero iré solucionando de a poco.

---

