---
title: "Broadcom BCM4312 802.11b/g No Funciona"
date: 2009-11-03
forum: Hardware
---

### Post by RafaelG on 2009-11-03
Hola Bueno despues de haber hecho el Upgrade de Karmic ocurre que no puedo utilizar mi Wireless card.

06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

 Cuando deseo Activar mi Broadcom wireless desde Hardwares Drivers pasa algo peculiar que aunque haga click en activar no se activa la Broadcom STA que aparece. he probado instalando B43fvcutter desde synapcis y no aparece en Hardwares Drives.

Aca les dejo una foto de mi Hardware Drivers: 
[http://img262.imageshack.us/img262/7079/screenshot1xz.png]("http://img262.imageshack.us/img262/7079/screenshot1xz.png")

---

### Post by RafaelG on 2009-11-04
[COLOR="Red"]_SOLUCIONADO_[/COLOR]
Hola Antes que todo Agradecer la Ayuda a todos los Companeros Ubunteros. 

SOLUCION:
Proporcionada Por **Janitux**

```
sudo apt-get install linux-headers-$(uname -r)
```


```
sudo dpkg-reconfigure bcmwl-kernel-source
```

Y Finalmente Activar la **Broadcom STA** desde Hardware Drivers

---

### Post by VonlisT on 2009-11-06
> **RafaelG said:**
> [COLOR=Red]_SOLUCIONADO_[/COLOR]
Hola Antes que todo Agradecer la Ayuda a todos los Companeros Ubunteros. 

SOLUCION:
Proporcionada Por **Janitux**

```
sudo apt-get install linux-headers-$(uname -r)
```
```
sudo dpkg-reconfigure bcmwl-kernel-source
```Y Finalmente Activar la **Broadcom STA** desde Hardware Drivers

Efectivamente, pero debo decir que este driver disminuye la potencia del hardware en un 20%. Es esta una de las razones por las que aún tengo el kernel 2.6.28 en mi ubuntu 9.04 con el driver nativo del kernel. Hice muchas pruebas con el kernel 2.6.30 [compilando el driver de broadcom] en ubuntu 9.04 y es realmente notable, con el 2.6.28 tiene más alcance.
:p

---

### Post by RafaelG on 2009-11-08
> **VonlisT said:**
> Efectivamente, pero debo decir que este driver disminuye la potencia del hardware en un 20%. Es esta una de las razones por las que aún tengo el kernel 2.6.28 en mi ubuntu 9.04 con el driver nativo del kernel. Hice muchas pruebas con el kernel 2.6.30 [compilando el driver de broadcom] en ubuntu 9.04 y es realmente notable, con el 2.6.28 tiene más alcance.
:p

Disculpeme falto una pequena explicacion de por que si estoy Utilizando Ubuntu karmic no me funciona el Kernel de este mismo la razon es que mi tarjeta inalambrica se encuentra en progreso para este nuevo kernel por este motivo tuve que reconfigurar y utilizar el Kernel antes mencionado en mi Solucion

Saludos Grandes.

---

### Post by donmatas on 2009-11-15
gracias!

salud
DM

pd: otro pc liberado!

---

