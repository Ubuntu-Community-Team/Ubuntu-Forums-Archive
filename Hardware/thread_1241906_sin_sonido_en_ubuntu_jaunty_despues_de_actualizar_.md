---
title: "sin sonido en ubuntu jaunty despues de actualizar alsa"
date: 2009-08-16
forum: Hardware
---

### Post by martin1717 on 2009-08-16
hola necesito su ayuda. me pase de windows xp a ubuntu jaunty. todo bien excepto una cosa, el sonido. primero andaba re mal y googleando encontre q tenia q actualizar alsa a la version 1.0.20. lo hice y despues me quede sin sonido. subi el volumen en el panel de control, en preferencias, en el alsamixer por medio de una terminal, y nada. instale los codecs para formatos q no son de linux y nada. mi compu es una notebook toshiba satellite m55-s141 y la placa de sonido creo q es una ati ixp. por favor ayudenme porq estoy en b***s, y porq no quiero volver a windows. desde ya, muchas gracias!

---

### Post by martin1717 on 2009-08-16
bueno les comento q acabo de solucionar el problema de no tener sonido, subiendolo. es decir. desde el panel de sonido active todos los controles, luego los subi, y por ultimo los desactive, los deje no visibles. y volvio el sonido. lamentablemente aparecio otro problema, q esta oculto. el sonido se tilda. el de inicio queda colgado, y cuando pongo un tema se escuhca bien hasta q lo pauso o lo detengo y ahi queda tiltado, o sea, se escucha un tatatatatatatatatatatatatatatatatatatatatatatatatata....... no es muy agradable jaja. me ayudan por favor????? 
Gracias de antemano!

---

### Post by sikamaniaco on 2009-08-16
[https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems](https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems)
Proba con esto a ver.

---

### Post by martin1717 on 2009-08-16
estoy trabado en la seccion 
**Is ALSA using the correct model?**

no encuentro lo q el autor llama 5stack, correspondiente a mi placa, porq la seccion de hda-intel es larguisima y dice un monton de cosas, pero la de ati ixp no dice nada parecido. por lo q lei tengo q agregarle una linea al archivo de config de alsa, pero tengo q saber el modelo correspondiente a mi placa. no sabes si hay otra forma de hacerlo?
gracias por responder, ya me sentia solo ja

---

### Post by martin1717 on 2009-08-18
a alguien se le ocurre algo?

---

### Post by josecuervo86 on 2009-08-18
para saber el modelo de tu placa en una teminal pone lo siguiente:

```
 lspci | grep Audio 
```

---

### Post by martin1717 on 2009-08-20
bueno les comento q el otro dia se actualizo mi ubuntu y de ahi en mas empezo a funcionar bien el sonido. al parecer cuando se actualizo se desactivo el escritorio multiple, y eso era justamente lo q me generaba el problema. bueno ahora estoy contento. no tanto porq tengo problemas con una impresora en windows, pero bueno ese es otro tema.

---

