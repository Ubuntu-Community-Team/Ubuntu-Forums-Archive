---
title: "Problema con tarjeta de Red"
date: 2011-08-22
forum: Hardware
---

### Post by gatusko on 2011-08-22
:( Esto me ta volviendo loco realmente xD. 
Hace dos meses que instale el ubuntu 11.04 en una portatil Hp TouchSmart tx2, pero no me reconoce la tarjeta de red que es:
- Broadcom 4322AG 802.11a/b/g/draft-n Wi-Fi Adapter
Pero nada de nada y una ayuda mas como Ejecuta en consola ? Me tiene loco, me dijieron que es como el cmd como windows pero no se como entrar ! Por favor ayudenme windows me tiene asqueado con sus virus o.o

---

### Post by gmunioz on 2011-08-23
Esto se debe a que los módulos no son cargados o no existen en el Kernel generico de Ubuntu. 
Conectado por cable, desde Synaptic activa todos los repositorios, recarga la información, busca luego y marca para instalar el paquete
bcmwl-kernel-source
Luego de instalado, reinicia la laptop, y ya tendrías que ver desde la interfaz NetworkManager Applet de gnome, que ya tienes acceso a conectarte a los ssids de las redes wireless de alrededor.

---

### Post by gatusko on 2011-08-23
Ahora se viene otro problema! Al conectar del modem adsl a mi notebook, no me reconoce el interet.  Se ve que se quiere conectar y despues me dice Cable desconectado! Waaa xD Trate hacerco con el internet de mi celular pero se me acabo el credito y me faltaba poco =(. Pero realmente gracias por la ayuda, ahora no se que hacer con esto que no me reconosca una red adsl ! :(

---

