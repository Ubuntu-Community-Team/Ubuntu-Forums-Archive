---
title: "no anda placa wifi (soy nuevo)"
date: 2013-04-10
forum: Hardware
---

### Post by eduardo108 on 2013-04-10
Hola que tal?

Les cuento que soy nuevo en ubuntu

Acabo de instalar 12.04 y la notebook no me reconoce las redes wifi, si la conecto por cable si, pero wifi no.

Alguna forma de solucionarlo??

Saludos y gracias

---

### Post by gmunioz on 2013-04-11
Abre una terminal y ejecuta en ella:
> sudo su
lspci
lsusb
ifconfig -a
iwconfig
Copia y pega las salidas en el post.

---

### Post by eduardo108 on 2013-04-11
muchas gracias por la respuesta!

aca va lo q me salió

[IMG]http://imageshack.us/a/img580/9774/89024095.png[/IMG]

[IMG]http://imageshack.us/a/img213/3581/79426142.png[/IMG]

[IMG]http://imageshack.us/a/img201/8388/21411258.png[/IMG]

[IMG]http://imageshack.us/a/img507/6754/23352752.png[/IMG]

Saludos!

---

### Post by gmunioz on 2013-04-12
Aqui la solución:
[http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized/154935#154935](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized/154935#154935)
Indican resumidamente abrir una terminal conectado por cable a internet y ejecutar en ella
You'll need to install these packages first to build the driver:
> 
sudo su
apt-get install build-essential linux-headers-generic linux-headers-`uname -r`
wget -O- [http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz](http://dl.dropbox.com/u/57056576/DRIVERS/REALTEK/rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz)
tar -xvz rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012.tar.gz
cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012
make
make install
cd rtl_92ce_92se_92de_8723ae_linux_mac80211_0006.0514.2012/firmware/rtlwifi
cp rtl8723fw.bin /lib/firmware/rtlwifi/ 
cp rtl8723fw_B.bin  /lib/firmware/rtlwifi/ 
modprobe rtl8723e
reboot


---

### Post by eduardo108 on 2013-04-12
gracias por la respuesta pero me aparecen unos errores cuando pongo make

[IMG]http://img163.imageshack.us/img163/8586/54759695.png[/IMG]

---

### Post by eduardo108 on 2013-04-12
intenté hacer esto que dice en el link q me pasaste

[INDENT][I]Commenting out/removing the IEEE80211_HW_BEACON_FILTER (line 320 in base.c) makes it    possible to compile when using the 3.4 kernel. So far I haven't experienced any problems. The    card seems to work as it did before, although it might be less power-efficient. I can't    guarantee it won't cause any problems, but it's better than nothing.
[/I]
[/INDENT]*Well, then here's some new feedback for ya: I did all of the above  and got the same compile error and fixed it with your suggestion. Then  the driver worked ONCE. After rebooting, no longer it could open any  wireless connections. Tried booting into windows 7 and still, no longer it can detect any  wireless connections.*


Pero no me deja modificar el archivo porque me dice q no tengo los permisos necesarios

:(:(:(

---

### Post by gmunioz on 2013-04-12
En el sitio dice que:
para el caso de kernels mayores a 3.3 (tienes el 3.5) debes usar este driver:
[http://www.liteon.com/UserFiles/driver/Module/Network/WLAN/RTL/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz](http://www.liteon.com/UserFiles/driver/Module/Network/WLAN/RTL/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz)
adapta las ordenes al nuevo archivo

---

### Post by eduardo108 on 2013-04-12
sos un capo!!!

ya estoy conectado al wifi!!!:p

muchas gracias!!!

---

### Post by eduardo108 on 2013-04-14
disculpas, no caer pesado, pero dejó de andar el wifi:confused:

la cosa es que estuve usando la compu, primero me apareció un error, el cual notifiqué y seguí usando la compu

pongo imagen de error por las dudas que tenga algo que ver(o ya q estamos si se puede resolver)

[IMG]http://imageshack.us/a/img809/8327/20240413.png[/IMG]

despues de eso al rato me apareció de repente una pantalla de texto y se trabó por completo la compu, la tuve que apagar desde el boton y cuando la volví a prender ya no andaba mas la placa wifi

[IMG]http://imageshack.us/a/img32/7738/83152692.jpg[/IMG]
[IMG]http://imageshack.us/a/img547/4173/42038072.jpg[/IMG][IMG]http://imageshack.us/a/img208/1245/12092311.jpg[/IMG]


volví a realizar el procedimiento para instalar el controlador y sigue sin andar

saludos

---

