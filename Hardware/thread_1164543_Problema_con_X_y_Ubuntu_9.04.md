---
title: "Problema con X y Ubuntu 9.04"
date: 2009-05-19
forum: Hardware
---

### Post by VashTheStampede on 2009-05-19
Tengo una Phenom X4 9550 con una mother ASUS M3A78-EM con placa de video integrada ATI Radeon HD 3200, 2Gb de RAM, disco Samsung SATA II de 320 Gb y monitor LCD ViewSonic de 19''. Yo tenía el Ubuntu 8.10 y no tenía problemas. Ahora al pasarme al 9.04 (instalado desde cero, no actualize desde el anterior) cuando termino de instalarlo funciona bien pero al hacerle las actualizaciones que me pide se estropea el X. Si no hago las actualizaciones pero instalo el driver de ATI bajado de la pagina oficial, al reiniciar o deslogearme el X se estropea, me pone el monitor como fuera de rango.

Alguien me puede dar una mano? No se que está pasando. Gracias!!

---

### Post by guillermolisi on 2009-05-19
Los drivers de ATI no son buenos por ahora. Si pudieras conseguir el driver que estabas usando con la version 8.10 y probar posiblemente tengas una solucion.

Probaste usando EnvyNG (esta en los repositorios) ?
Puede que te ofrezca como alternativa al ultimo driver el anterior. Cambialo, proba y conta que tal te fue.

No vas a romper nada porque lo unico que se podria romper ya esta roto (X server).

---

### Post by Hei Ku on 2009-05-19
La solucion es o instalar el X Server de Intrepid, o esperar los nuevos drivers de ATI. Hicieron un cambio de version de X server a ultimo momento y ATI largo unos drivers que andan bien o mal depende el modelo de placa. Las HD3xxx parece que tienen bastantes problemas. Una solucion posible es volver al X Server anterior y a los drivers que usabas antes hasta que se solucionen estos problemas.

---

### Post by z37a on 2009-05-20
Tengo la misma placa madre, te coemnto que es lo que paso, pro lo menos en mi caso, tenia puesto solo 32MB en el video y utilizaba una resolucion muy alta, proba de ver si podes meterle 256MB y contame que me parece que con eso seguro lo solucionas!!!!

PD: Igualmente el 2D anda mejor el driver libre, al aumentar la memoria de video mejoro muchisimo el rendikmiento, pero con el privativo anda medio mal, igual te da aceleracion 3D, pero no se si vale la pena(por lo menos en mi caso)

---

### Post by VashTheStampede on 2009-06-08
Probé lo de los 256 mb pero sigue sin funcionar. Lo raro es que tampoco me funcionan los drivers que vienen con linux. Siempre tengo el mismo problema. ¿Hay algo más que pueda probar? ¿Algo de bios que deba cambiar además de lo de los 256 mb? Me volví loco instalando paquetes, sacando paquetes...nada funciona. No puedo lograr que funcione.

---

### Post by Hei Ku on 2009-06-08
Hace unos días salió el driver 9.5 de ATI. Podés probar de instalar ese a ver qué pasa.

---

### Post by saibof on 2009-06-13
hola, de igual forma tengo una placa ati 3200,  me pasa algo similar. habia escuchado por alguna parte que tienes que compilar tus propios drivers para la distribucion (honestamente yo no lo probé), ya que a mi solo me da el problema si la suspendo o la hiberno, ya he reinstalado Jaunty 4 veces, la ultima 64 bits, esta es su ultima oportunidad. si no me cambiaré a sus origenes (Debian!!) pero al parecer todo esta bien! 
Saludos

---

