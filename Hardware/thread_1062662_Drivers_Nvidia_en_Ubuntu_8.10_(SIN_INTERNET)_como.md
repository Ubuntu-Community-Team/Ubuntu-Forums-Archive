---
title: "Drivers Nvidia en Ubuntu 8.10 (SIN INTERNET) como?"
date: 2009-02-07
forum: Hardware
---

### Post by atari130xe on 2009-02-07
Estimados...A mi hna le instale la 8.10 en su PC pero eh aqui que al no tener internet, no sé como instalarle los drivers de su Nvidia GeForce 8400
Me tomé el laburo de bajarme los 6 DVDs con los repos de Ubuntu 8.10 (si alguien por alguna razon desea hacerlo el link es el siguiente:

[ftp://tuma.ui.edu/pub/ubuntu-repository/8.10/](ftp://tuma.ui.edu/pub/ubuntu-repository/8.10/) esos son para desktop x86)

Alguien me puede dar una mano con el tema? asi le instalo el driver correspondiente y puede tener aceleracion gráfica, gracias!

---

### Post by Hei Ku on 2009-02-07
No probaste bajar los drivers desde la pagina de nvidia?
No usa los privativos para esa placa?

---

### Post by atari130xe on 2009-02-07
si los bajé y bueno sé que hay que darle al sh .... pero... no sé si hay hacen falta más paquetes... por eso pregunto

---

### Post by faktorqm on 2009-02-09
Hola, te hacen falta varios, build-essential para empezar y un par del kernel. Yo siempre instalaba asi y andaba joya, pero si podes instalate envy, y le pasas a donde tenes el archivo de nvidia, y configuras en origenes de software que te tome las cosas del dvd. Ahi no te deberia faltar nada. Abrazo!

---

### Post by atari130xe on 2009-02-10
> **faktorqm said:**
> Hola, te hacen falta varios, build-essential para empezar y un par del kernel. Yo siempre instalaba asi y andaba joya, pero si podes instalate envy, y le pasas a donde tenes el archivo de nvidia, y configuras en origenes de software que te tome las cosas del dvd. Ahi no te deberia faltar nada. Abrazo!


Te joderia mucho si te pido los pasos exactos? una vez que lo aprendo ya està, mil gracias Martin!

---

### Post by faktorqm on 2009-02-13
es que no se exactamente que paquetes necesitabas para instalar eso.... te puse "un par del kernel" por que ni idea, igual si tenes el dvd no pasa nada, tendrias que hacer algo como esto.

1) bajar envy
2) bajar driver de nvidia
3) leer en [http://www.albertomilone.com/](http://www.albertomilone.com/) como se hace para instalar off line (creo que tenias que poner el driver en el mismo directorio que el envy, algo asi)
4) Cambiar los repos de ubuntu para que use los del dvd, ir a origenes del software y cambiarlo a mano.
5) poner el dvd
6) correr el envy e instalar el driver.

Creo que asi tenes que salir andando. Cualquier duda pregunta, salu2!

---

