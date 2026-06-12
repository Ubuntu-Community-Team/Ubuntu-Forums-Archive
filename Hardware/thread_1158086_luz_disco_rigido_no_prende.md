---
title: "luz disco rigido no prende"
date: 2009-05-13
forum: Hardware
---

### Post by dirty fingers on 2009-05-13
Algún buen motivo para que la luz del disco no funcione en ubuntu ?

tengo un motherboard asus con chiset nvida y controlador sata promise.

---

### Post by guillermolisi on 2009-05-13
> **dirty fingers said:**
> Algún buen motivo para que la luz del disco no funcione en ubuntu ?

tengo un motherboard asus con chiset nvida y controlador sata promise.
Notebook, Desktop ?

Se supone que estaba funcionando con otras versiones u otrso SOs, cierto ?
Tambien se supone que los drivers del chipset estan instalados, o no ?

Dejo de funcionar de un dia para el otro o fue a partir de que instalaste/actualizaste a JJ ?

---

### Post by dirty fingers on 2009-05-13
> **guillermolisi said:**
> Notebook, Desktop ?
desktop
> **guillermolisi said:**
> Se supone que estaba funcionando con otras versiones u otrso SOs, cierto ?
funciona en windows y minipe
> **guillermolisi said:**
> Tambien se supone que los drivers del chipset están instalados, o no ?
ubuntu arranca sobre un disco sata si no están los driver sata instalados ?
> **guillermolisi said:**
> Dejo de funcionar de un dia para el otro o fue a partir de que instalaste/actualizaste a JJ ?
nunca funciono desde que instale.


esta bueno no ;) jajaja no se por donde empezar. ni logro imaginarme el problema.

---

### Post by guillermolisi on 2009-05-13
> **dirty fingers said:**
> desktop

funciona en windows y minipe

ubuntu arranca sobre un disco sata si no están los driver sata instalados ?

nunca funciono desde que instale.


esta bueno no ;) jajaja no se por donde empezar. ni logro imaginarme el problema.
Sehhh ... son esas cosas que te dejan vivir pero pican todo el tiempo ... ;)

Es que los drivers SATA estan en el kernel, si a eso te referis.
Con respecto a los drivers del chipset, los mencione porque siendo nVidia podria ser que alguna funcion sea tan particular que sin esos drivers funciona pero no sea lo esperado (mientras digo esto recuerdo unas maquinas con chipset Nforce 400 y 500. mother Asus M2N DeLuxe).

Lo que no me cierra y que por eso mencione los driver del chipset, es que ese led supuestamente lo maneja la controladora de discos de la motherboard con las señales que se generan por los requerimeintos del SO (y si no es asi, por favor corregirme).

---

### Post by dirty fingers on 2009-05-13
a mi pone loco que pensaba que el pin del mother que va al led hdd estaba tomando señal directo del bus. sin ningun soft o chip de por medio.
y mas loco que la web esta plagada de gente que dice que el led no se les apaga en ubuntu jajaja voy contra la marea.

---

### Post by guillermolisi on 2009-05-13
> **dirty fingers said:**
> a mi pone loco que pensaba que el pin del mother que va al led hdd estaba tomando señal directo del bus. sin ningun soft o chip de por medio.
y mas loco que la web esta plagada de gente que dice que el led no se les apaga en ubuntu jajaja voy contra la marea.
Bueno, fijate que tengo JJ corriendo en dos maquinas con la misma mother Asus pero con chipset VIA (que maravilla !), ambas con discos de la misma marca y modelo de tecnologia SATAII, y en las dos el led funciono y funciona desde el primer boot con JJ.

Por eso tome para el lado del chipset.

Si esta informado como bug seguramente le daran la prioridad mas baja que exista :D, asi que paciencia.

---

### Post by staar on 2009-05-13
chee, no es algo que me desvele, pero me pasa lo mismo, mother asus con chipset via (! :-D), pero discos ide...

y ahora que hago memoria, no funca en arch tampoco :-( , tendría que ver si funciona en win, porque ya ni me acuerdo...

saludos

---

### Post by Hei Ku on 2009-05-14
Eso es generalmente tema de chipset, no de sistema operativo. 

Distinto es la temperatura, o alguna otra medicion que el sistema operativo tenga que mostrar. Quizas haya algun caso en particular, pero me parece que usualmente en esto el SO no tiene nada que ver.

---

### Post by dirty fingers on 2009-05-14
vamos a empezar a descartar entonces. 
voy a iniciar en otro linux con livecd por ejemplo opensuse. a ver si tiene que ver con la manera en que maneja el hard linux en general o es algo especifico de los driver que vienen en ubuntu.


--------------------------------------------------------------------------------------------------------------------------------------------------------


no prende tampoco en opensuse.

---

### Post by dirty fingers on 2009-08-13
hay algo en linux en general que hace que no prenda. ya probe otras distribuciones para sacarme la duda.
:(

---

### Post by staar on 2009-08-13
el otro día saque el rígido, y al volverlo a poner la luz volvió a funcionar, por lo menos en arch, no probé en ubuntu todavía (el problema es que ya me había acostumbrado y ahora me molesta :-P)

saludos

---

