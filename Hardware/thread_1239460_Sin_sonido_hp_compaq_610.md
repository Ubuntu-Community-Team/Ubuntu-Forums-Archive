---
title: "Sin sonido hp compaq 610"
date: 2009-08-13
forum: Hardware
---

### Post by vikingo on 2009-08-13
tengo el siguiente problema. no sale sonido de mis parlantes y aparentemene tengo bien la placa de sonido instalaa (el ALSAMIXER me indica que esta todo al maximo). que es lo que me esta suceciendo? alguna idea?

---

### Post by sergiom99 on 2009-08-13
Hola vikingo, antes de que moderen el post, te aviso que esta seccion es solo de habla inglesa. Si queres pasate por el foro de Argentina [1] o por algun otro de habla hispana [2]

[1] [http://ubuntuforums.org/forumdisplay.php?f=189](http://ubuntuforums.org/forumdisplay.php?f=189)
[2] [http://ubuntuforums.org/forumdisplay.php?f=183](http://ubuntuforums.org/forumdisplay.php?f=183)

---

### Post by eggdeng on 2009-08-13
Empieza por ```
aplay -l
```
para averiguar la tarjeta que tienes.

---

### Post by joseangelini on 2009-09-12
I solved it updating ALSA. Look at this
  
[https://help.ubuntu.com/community/So...otingProcedure](https://help.ubuntu.com/community/So...otingProcedure)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[http://monespaceperso.org/blog-en/20...u-jaunty-9-04/](http://monespaceperso.org/blog-en/20...u-jaunty-9-04/)

---

