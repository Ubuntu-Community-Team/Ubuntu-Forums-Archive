---
title: "solo puedo imprimir en draft modo con hp 2055dn"
date: 2010-07-09
forum: Hardware
---

### Post by cseljatib on 2010-07-09
estimados amigos,
uso ubuntu 10.04 y por anhos he usado ubuntu, no tengo problemas para imprimir y encontrar impresoras con el software hplip de linux, sin embargo, ahora me he dado cuenta que con la impresora hp 2055dn y aunque si puedo emplear las opciones de imprimir por lado y lado de esta impresora, solo puedo imprimir en modo de borrador, aunque cambie la configuracion de la impresora en

system->administration->printing->hp2055dn->printer options->

ahi en printout mode lo dejo en 'High quality'

me pueden ayudar a mejorar o regular la calidad de mi impresora desde ubuntu?

obviamente ya he probado la impresora desde windows, y funciona sin ningun problema
c

---

### Post by cseljatib on 2010-07-09
lo siento amigos, pero ya encontré la solucion, instale la impresora no desde la opción printing desde sistema-administracion, sino que tan solo ejecutando el siguiente comando
$ sudo hp-setup
y segui el paso a paso y listo!!!
ahi cuando seleccione la mejor opcion de imprimido funciono sin problemas

gracias

---

### Post by Carlos C on 2010-07-12
Movido a "[Hardware]("http://ubuntuforums.org/showthread.php?t=1162711")".

---

