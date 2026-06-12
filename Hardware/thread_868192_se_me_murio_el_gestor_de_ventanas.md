---
title: "se me murio el gestor de ventanas"
date: 2008-07-23
forum: Hardware
---

### Post by steve_ignorant on 2008-07-23
gente se me murio el gestor de ventanas. si lo inicio con el kernel de low latency, me queda la pantalla negra y el simbolito de que esta cargando.


si lo inicio en kernel generic, me figura que el servidor x no esta correctamente configurado... si me puede dar una data de como hacer. hasta que me llegue el cd de hardy. y ahi le hago un formateo completo a la pc.

---

### Post by Mauro22 on 2008-07-23
Que version es ? Ubuntu - Kubuntu - Xubuntu etc...

---

### Post by FlyerDie on 2008-07-23
y que fue lo ultimo que hiciste antes de esa booteada fatal?

---

### Post by steve_ignorant on 2008-07-23
> **Mauro22 said:**
> Que version es ? Ubuntu - Kubuntu - Xubuntu etc...


es ubuntu 7.04 con beryl.  con una  placa geforce fx 6200 de 256 ddr2.


com el kernel el 2....16

---

### Post by Mauro22 on 2008-07-23
Probaste instalando metacity otra vez?

sudo apt-get install metacity   :confused:

No se si sera asi, sino primero un:

sudo apt-cache search metacity y ahi ves los paquetes.


Es imposible iniciar el servicio grafico??

---

### Post by steve_ignorant on 2008-07-23
> **Mauro22 said:**
> Probaste instalando metacity otra vez?

sudo apt-get install metacity   :confused:

No se si sera asi, sino primero un:

sudo apt-cache search metacity y ahi ves los paquetes.


Es imposible iniciar el servicio grafico??


es imposible y no tengo internet como para poner un sudo aptget. salvo que se pueda hacer de algun cd o algo asi?, hasta que venga el cd de hardy.

---

### Post by steve_ignorant on 2008-07-24
> **FlyerDie said:**
> y que fue lo ultimo que hiciste antes de esa booteada fatal?

mira lo ultimo que hice fue cambiar el escritorio, es decir mover los paneles, cambiar fondo de pantalla y agregar un par de cosas con el beryl, y el emerald. lo que vi hoy que me puse a ver porq decia queno estaba configurado el servidor X, era porq me sigue figurando la placa vieja la geforce TI 4200. 

tendria que reconfigurarlo y hacer que tome la configuracion de la nueva placa, y casi seguro reinstalar drivers. 

lo que quiero ver es si puedo realizar una configuracion con la consola, si m pueden decir como es el comando.

---

### Post by FlyerDie on 2008-07-24
ahh..lo el cambio de la placa no habias dicho nada pillo! :lolflag:

---

### Post by steve_ignorant on 2008-07-24
perdon, no pense que era por eso, porq cuando me fije si tenia que reinstalar el driver, me reconocia la placa joya, entonces, no hice nada. y cuando, hoy pude ver con mas tiempo el error me figuraba qu el servidor X esta con la placa vieja. el problema que no tengo internet en mi casa, sino en la casa de mi vieja. hable con un compañero de laburo, recien y me dijo que pruebe pasandolo a vesa para tener al menos algo grafico y de ahi levantarlo.  lo que pasa es que no se si para pasarlo a vesa, tengo que tipear algo mas que esto:

vim /etc/x11/xorg.conf

si me pueden decir si tego que hacer algo mas... .

---

### Post by Hei Ku on 2008-07-24
Desde la consola:

sudo dpkg-reconfigure xserver-xorg

---

