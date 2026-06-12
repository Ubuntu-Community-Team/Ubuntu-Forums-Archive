---
title: "presentacion y problemas con placa de audio en Xubuntu"
date: 2011-06-16
forum: Hardware
---

### Post by pepelilo on 2011-06-16
Hola gente,soy pepelilo y soy nuevo en ubuntu.Anteriormente usaba linux mint,y la verdad es que funcionaba 10 puntos,nunca tuve que instalar ningun controlador;pero ahora decidi  probar xubuntu 10.04 en otra maquina que me compre,y no tengo sonido.Descargue el   driver realltek high definition audio,pero no lo puedo instalar,puede alguien ayudarme,por favor?Por lo demas ,todo funciona de maravillas.GRACIAS!!

---

### Post by josecuervo86 on 2011-06-16
Las instrucciones para instalarlo estan en el README dentro del .tar.bz2. Tenes que desempaquetarlo y despues desde terminal te moves hasta la carpeta y le das
```
./install
```

---

### Post by ruben_linux on 2011-06-18
yo tengo ubuntu 10.04 en un  hp dv6, y también me fallaba el sonido al principio, di con la solución, usando: 

sudo alsaconf

y la barra de sonido estaba a cero, la cambie y listo. 

Prueba:):)

---

### Post by guillermolisi on 2011-06-18
> **ruben_linux said:**
> yo tengo ubuntu 10.04 en un  hp dv6, y también me fallaba el sonido al principio, di con la solución, usando: 

sudo alsaconf

y la barra de sonido estaba a cero, la cambie y listo. 

Prueba:):)
Es "alsaconf" o "alsamixer" ?

Pregunto porque mencionas los niveles y eso se visualiza con alsamixer.

---

