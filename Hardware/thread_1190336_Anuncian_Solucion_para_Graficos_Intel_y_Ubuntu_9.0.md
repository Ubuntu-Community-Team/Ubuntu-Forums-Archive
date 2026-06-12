---
title: "Anuncian Solucion para Graficos Intel y Ubuntu 9.04"
date: 2009-06-17
forum: Hardware
---

### Post by Patriciologico on 2009-06-17
Leo en [Muy Linux]("http://www.muylinux.com/2009/06/12/solucion-a-los-conflictos-con-chipsets-graficos-intel/") que  Bryce Harrington, un desarrollador de Canonical que ha escrito un mensaje  a la lista de correo de desarrolladores en la que anuncia la disponibilidad de un controlador 2D aún algo inestable pero que debería resolver el problema con estos chips gráficos de Intel.

La solución pasa por:

1.- Instalar Kernel 2.6.30

2.- Instalar Drivers desde [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

3.- Habilitar UXA, como ya esta descrito en un [post de la semana]("http://ubuntucl.wordpress.com/2009/05/27/habilitar-aceleracion-uxa-en-tarjeta-grafica-intel/") de nuestro Blog Foro

Esta Solución implica instalar paquetes no oficiales de Canonical, por lo tanto abstenerse en entornos productivos o en caso de hacerlo, apuntar bien cada cambio realizado por si hay que dar vuelta atras.

Saludos!

Pd: Apenas lo aplique comento mi rendimiento.

---

### Post by Patriciologico on 2009-06-19
Después de usarlo un día, y haber probado otras soluciones, debo decir que la que mejor me ha resultado, sin ser optima, es usar los drivers Intel 2.4 de Intrepid. Ha sido una lastima, con tanto entusiasmo que actualice a Jaunty y no me rinde bien. (bueno no tanto entusiasmo, que esto de actualizar cada seis meses pierde un poco de emoción)

De todos modos hay quienes comentan maravillas de este metodo, lo que es a mi no me viene.

Saludos!

---

### Post by dnovai on 2009-06-19
Bueno, yo soy unos de los que se rindio intentando una solucion parche ya que no existe los controladores para ubuntu 9.04 de mi aceleradora gràfica (Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller). La mejor solucion que encontre es volver a intrepid 8.10.

Ojala se solucione luego este problemilla.

Saludos!

---

