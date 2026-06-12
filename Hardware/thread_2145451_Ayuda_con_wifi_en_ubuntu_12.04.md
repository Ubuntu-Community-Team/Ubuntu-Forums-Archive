---
title: "Ayuda con wifi en ubuntu 12.04"
date: 2013-05-15
forum: Hardware
---

### Post by sinapsisnotfound on 2013-05-15
Hola gente, soy nuevo en la comunidad y este es mi primer tema, tenia muchas ganas de pasarme a ubuntu y hace como dos meses me decidi, formatee e instale ubuntu 12.04 como mi unico so, tengo un serio problema con el tema del wifi, no me funciona, me reconoce la red, me contecto, abro el navegador y cuando quiero entrar a alguna pagina queda cargando, nunca termina de cargar.. tengo una portatil compaq presario cq40-705LA.
si alguien pudiera darme una mano para solucionar este tema, la verdad es muy incomodo tener q estar conectado al cable. desde ya gracias.
-pd: soy totalmente novato en linux, asi q necesito q sean lo mas especificos posibles

---

### Post by gmunioz on 2013-05-17
Abre una terminal.
Ejecuta en ella:
> sudo su
ifconfig -a
ifconfig
iwconfig
lspci
lsusb
Copia y pega las salidas en el post.

---

