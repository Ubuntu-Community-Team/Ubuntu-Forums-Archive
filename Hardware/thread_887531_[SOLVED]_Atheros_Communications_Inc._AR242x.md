---
title: "[SOLVED] Atheros Communications Inc. AR242x"
date: 2008-08-12
forum: Hardware
---

### Post by vk-cdg on 2008-08-12
En primer lugar, tengo que decir que me siento un salame ya que encontré mas de 15 tutos (todos muy similares) y aún no puedo hacer andar mi placa wifi. Grrrrrrrrrr :(

Vamos despacio y en detalle paso a paso con lo que hice.

En primer lugar hago un lspci | grep Ath y me devuelve lo siguiente:

```
Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

Acto seguido sigo las instrucciones de cualquiera de los tutos que hay por ahí:

1- Deshabilito todos los controladores restringidos de la wifi (la imagen muestra uno habilitado porque la tomé al final del proceso, cuando hay que levantar nuevamente los módulos)
[LIST]
[*]Atheros Hardware Access Layer (HAL).
[*]Support for Atheros 802.11 wireless LAN cards.
[/LIST]

[IMG]http://img243.imageshack.us/img243/281/controladoresdehardwareaa7.png[/IMG]

Luego de esto reinicio el equipo.

2- Instalo las dependencias para compilar el driver

```
sudo aptitude install build-essential
```

3- Descargo el driver

```
wget http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz
```

*Acá tengo que hacer una aclaración. Al bajar el driver, me di cuenta (luego de un rato) que el archivo comprimido recién descargado) solo tiene un archivo README comentando que hay un nuevo procedimiento para instalar y menciona algo del HAL. Mi ingles no es tan bueno así que recurrí al driver que tenía descargado antes de que cambiaran el archivo en el servidor para seguir con este mismo procedimiento.*

4- Descomprimo el archivo y entro en la carpeta.

```
[LIST]
[*]tar -xzvf madwifi-nr-r3366+ar5007.tar.gz
[*]cd madwifi-ng-r3366+ar5007
[/LIST]
```

5- Elimino todo rastro anterior de Madwifi:

```
sudo rm -rf /lib/modules/$(uname -r)/madwifi
```

6- Compilo e instalo el driver

```
[LIST]
[*]sudo make
[*]sudo make install
[/LIST]

```

7- Habilito nuevamente los controladores restringidos en Sistema > Administración > Controladores de hardware.

8- Reinicio.

Al volver a levantar el equipo veo que detecta la placa, veo el dispositivo de redes wifi y veo las redes en mi zona de alcance pero no conecta a ninguna, no me muestra el botón de conectar.

[IMG]http://img80.imageshack.us/img80/4363/configuracindelaredvy3.png[/IMG]

[IMG]http://img227.imageshack.us/img227/9026/propiedadesdeath0hh4.png[/IMG]

Resumiendo un poco, lo que hice fue esto:

- Deshabilitar los controladores privativos de Atheros (reiniciar), descargar nuevos controladores de aquí, ejecutar el siguiente código:

- sudo aptitude install build-essential
- tar -xzvf madwifi-nr-r3366+ar5007.tar.gz && cd madwifi-ng-r3366+ar5007
- sudo make
- sudo rm -rf /lib/modules/$(uname -r)/madwifi
- sudo make install

Habilitar de nuevo los controladores privativos (reiniciar).

Con esto no funciona. 
Buscando en varios tutos por internet, encontré variantes al procedimiento este, las cuales también hice.

Una de ellos es la siguiente:

*Terminado el procedimiento anterior y reiniciado la PC, abrir de nuevo la herramienta de controladores y habilitar sólo el soporte wireless para Atheros. Dejar desactivado el "Atheros Hardware Access Layer - HAL". *

Tampoco funciona.

Otra variante es esta:

Luego del último paso del procedimiento original hacer lo siguiente

```
sudo modprobe ath_pci
```

Si no nos devuelve nada este comando vamos por buen camino  así que procedemos a cargar los modulos para el arranque

```
sudo gedit /etc/modules
```

y al final del archivo agregamos las siguientes lineas:

```
#inicia configuracion de gíreles
ath_pci
#finaliza configuracion de wireless
```

Luego guardamos y procedemos a activar la tarjeta, con el siguiente comando, aunque lo mejor seria reiniciar:

```
sudo ifconfig ath0 up
```


Tampoco anda! :(


El tuto original lo saqué de Ubuntu-es posteado por lukas911, que fue el que siguieron Flechagorda y Lega de nuestro foro, en el caso de ellos exitosamente.

[http://www.ubuntu-es.org/index.php?q=node/87675](http://www.ubuntu-es.org/index.php?q=node/87675)

Menciono a Flecha y a Lega porque ellos tienen exactamente la misma notebook que yo (Compaq F756la)

Los demás tutos de acá:

[http://chamangt.wordpress.com/2008/05/08/activar-wireless-atheros-en-ubuntu-con-madwifi/](http://chamangt.wordpress.com/2008/05/08/activar-wireless-atheros-en-ubuntu-con-madwifi/)
[http://rchicangana.blogspot.com/2008/05/wifi-atheros-ar5007-en-laptop-compaq.html](http://rchicangana.blogspot.com/2008/05/wifi-atheros-ar5007-en-laptop-compaq.html)
[http://idloco.blogspot.com/2008/08/activar-wifi-compaq-f756la-ubuntu.html](http://idloco.blogspot.com/2008/08/activar-wifi-compaq-f756la-ubuntu.html)
[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)


Sinceramente no se que mas hacer, mas que nada porque sigo los pasos tal cual están en los tutos pero no anda. 
Otro detalle es que en el panel, no me pone el medidor de señal y la lista de redes en mi alcance como para poder elegir a a cual conectarme.

Si alguien me puede dar una mano, estaré eternamente agradecido!

---

### Post by vk-cdg on 2008-08-12
Hago un doble post para separar los tantos.

Arriba mencioné que cuando descargo el driver desde el link que menciona cualquiera de los tutos, baja un archivo que no tiene el driver y solo tiene un README.

Yo tenía el driver descargado desde antes y por eso pude seguir con el procedimiento original.

Lo que dice el README es esto:

[I]You most likely downloaded this tarball since you are looking for a version of MadWifi which supports the AR5007 chipset family, which is for example used in the EeePC.

However, since you've downloaded this tarball, you've followed outdated
instructions. The code that this tarball once contained is now obsolete.
Please follow these instructions to enable your AR5007-based WLAN device:
[http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

If you have any questions about it, please contact our regular support
channels:
[http://madwifi.org/wiki/Support](http://madwifi.org/wiki/Support)

Thanks.[/I]

Por lo que entiendo con mi limitado ingles es que el driver del archivo original es obsoleto y que hay que seguir las instrucciones que mencionan acá [http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

Ahora me pondré con estas instrucciones a ver que puedo entender.

---

### Post by niko_3100 on 2008-08-12
que notebook tenes??

---

### Post by vk-cdg on 2008-08-12
Googleando un poco encontré este post en este mismo foro (en inglés).

Por lo que pude endender, el amigo Kajaste hizo un script que "automatiza" el proceso descargando el driver correspondiente y no se cuantas cosas mas. 

Cuando llegue a casa lo probaré.

---

### Post by vk-cdg on 2008-08-12
> **niko_3100 said:**
> que notebook tenes??

Una Compaq F756la

---

### Post by lega on 2008-08-12
Por lo que yo entiendo del nuevo driver de madwifi, tambien en mi ingles limitado es que deberias usar ahora este driver [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6-current.tar.gz) si queres probar con el driver de el tutorial de Ubuntu-es puedo pasartelo, avisame

---

### Post by vk-cdg on 2008-08-12
El driver ese lo tengo, lo bajé en su momento antes de tener la notebook, y es con ese con el que no me anda. 
Me da bronca porque a vos y a flecagorda les andubo y tenemos la misma note.

Voy a probar con este nuevo driver a ver que pasa.

---

### Post by niko_3100 on 2008-08-12
puede que tengan la misma notebook pero no la misma placa wifi...

---

### Post by vk-cdg on 2008-08-12
En este caso tenemos la misma placa, ya esta chequeado. 

Voy por el lado de que estoy haciendo algo mal yo. :(

---

### Post by lega on 2008-08-12
estaba leyendo mas detenidamente los pasos que hiciste y la diferencia con lo que yo hice es que una vez instalado el driver de madwifi yo no habilito los  drivers restringidos de Ubuntu,es la unica diferencia que encuentro, yo los deshabilité y no los habilité nunca más.

---

### Post by vk-cdg on 2008-08-12
Ok, veo de probar con eso ahora mismo.

---

### Post by luks911 on 2008-08-12
Buenas, tengo la misma placa. Y tanto el driver viejo, que ya tenías, como el nuevo ([http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/)) funcionan. Yo había instalado uno y después lo actualicé sólo para molestar. 
El procedimiento que hacés está bien, al menos hasta donde entiendo, sólo me genera duda esto último de volver a habilitar los drivers restringidos. Creo que eso no hace falta y alcanza con agregar el módulo en el archivo /etc/modules. Una forma de terminar con esa duda es ir a Synaptic y desinstalar el paquete linux-restricted-modules, siempre que no uses el driver de Nvidia, por ejemplo, en ese caso podés reemplazarlo por el driver privativo.
No obstante, no creo que el problema sea el driver. O sea, lo instalás bien, te detecta la placa y las redes, listo. Hay alguna otra cosa. ¿Y si en las conexiones habilitás el modo itinerante?
Un saludo

---

### Post by faktorqm on 2008-08-12
Hola, por lo que lei, instalaste algo que no va. El archivo ese que vos decias que no sabias que decia, dice que si tenes el chip 5007 no tenes que instalar ese tarball por que hay un nuevo HAL, que vayas a una direccion que ahi te dicen que hacer. 

Creo que esto va a ser largo, asi que manos a la obra! Te aviso desde el vamos que este procedimiento es solo para 32 bits, ya que madwifi no esta hecho para 64 bits. si tenes 64 bits tenes que usar ndiswrapper.

primero veamos en que situacion estas, por que ahora tenemos que borrar el viejo y poner el nuevo. Asi que **deshabilita desde controladores restringidos todo lo que tenga que ver con wifi** y tira en una terminal:

```
lsmod | grep ath
```

eso lo que hace es listar el contenido de todos los modulos cargados en el sistema que contengan la palabra "ath". te va a salir algo parecido a esto: 

```
wlan 207728 1 ath_pci 
ath_pci 101024 0
```

digo parecido x q pueden cambiar los numeros. 
si esto no te sale, no hay nada que bajar de memoria, segui leyendo.
si esto te sale, entonces los bajamos con:

```
sudo modprobe -r wlan
```
```
sudo modprobe -r ath_pci
```

(me olvide como era para hacerlo en una sola linea, creo que era con -a)
y no te tiene que tirar ningun cartel de nada. entonces ahora lo que tenemos que hacer es setearle que no se cargue de vuelta cuando reinicie la pc, tonces editamos un archivo:

```
sudo gedit /etc/default/linux-restricted-modules-common
```

y te aparece:

```
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables the three nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES=""
```

y te tiene que quedar asi: (le agregamos el modulo que no queremos que cargue al final)

```
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables the three nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES="ath_hal"
```

guardamos y salimos. 

Ahora lo mandamos a lista negra de los modulos con:

```
echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
```

We, yo creo que hasta aca estamos. En un sitio lei que tambien habia que hacer

```
sudo apt-get remove madwifi-tools --purge
```

pero la verdad que no estoy seguro, por las dudas, hacelo ;)

Supongo que ya lo hiciste esto, pero nunca esta de mas tener las herramientas de compilacion a mano:

```
sudo apt-get update && sudo aptitude install build-essential gcc binutils autoconf automake
```

Ahora si arrancamos el proceso de instalacion, para esto nos bajamos el driver:

```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
```

descomprimimos:

```
tar xzf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
```

entramos en el directorio:

```
cd madwifi-hal-0.10.5.6-r3835-20080801
```

compilamos (NO hace falta SUDO):

```
make
```

instalamos:

```
sudo make install
```

Ahora levantamos los modulos a memoria:

```
sudo modprobe -a ath_pci wlan_scan_sta
```

[esto no se si realmente hace falta pero de ultima no hace nada...]

```
sudo ifconfig ath0 up
```

y teoricamente ya deberias estar conectado. Ahora, asegurate de que la conexion a la cual te estes conectando ande y etcetcetc.

Ahora lo ultimo, hay que poner el modulo nuevo a /etc/modules para que lo levante cada vez que arranca:

```
echo "ath_pci" | sudo tee -a /etc/modules
```

y ¡¡listo!!. Ahora posteame que fue todo lo que no te anduvo xD

En algunos lados, dicen que el network-manager de gnome trae conflictos y que hay que usar un coso que se llama wicd. ```
sudo apt-get install wicd
``` Ahora, que es? ni idea... te lo dejo de tarea para el hogar...

bibliografia consultada:

bug en launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196843](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196843)
ubuntu chile: [http://foros.ubuntu-cl.org/viewtopic.php?p=31909](http://foros.ubuntu-cl.org/viewtopic.php?p=31909)
ubuntu españa: [http://www.ubuntu-es.org/index.php?q=node/83598](http://www.ubuntu-es.org/index.php?q=node/83598)
ubuntu en ingles: [http://ubuntuforums.org/showthread.php?t=766529](http://ubuntuforums.org/showthread.php?t=766529)
lista de chipsets reconocidos por el kernel: [http://kerneltrap.org/mailarchive/madwifi-devel/2008/2/18/890124](http://kerneltrap.org/mailarchive/madwifi-devel/2008/2/18/890124)
OBVIO: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)
[http://snapshots.madwifi.org/special/](http://snapshots.madwifi.org/special/)
blogs: [http://chamangt.wordpress.com/2008/05/08/activar-wireless-atheros-en-ubuntu-con-madwifi/](http://chamangt.wordpress.com/2008/05/08/activar-wireless-atheros-en-ubuntu-con-madwifi/)

Espero que te haya servido. Salu2!!!!:KS


EDITO: Algo así se ve la compilación, lo compilé para ver si tenia problemas pero compiló bien. No lo instalé por que estoy en casa, si te da "miedito" lo instalo en la pc del laburo que es la de "pruebas" jajaj

```

faktorqm@the-edge:~$ wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
--22:48:35--  http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
           => `madwifi-hal-0.10.5.6-r3835-20080801.tar.gz'
Resolviendo snapshots.madwifi.org... 217.24.1.134
Conectando a snapshots.madwifi.org|217.24.1.134|:80... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 4.417.874 (4.2M) [application/x-gzip]

100%[====================================>] 4.417.874     60.83K/s    ETA 00:00

22:49:56 (54.02 KB/s) - `madwifi-hal-0.10.5.6-r3835-20080801.tar.gz' guardado [4417874/4417874]

faktorqm@the-edge:~$ tar xzf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
faktorqm@the-edge:~$ cd madwifi-hal-0.10.5.6-r3835-20080801
faktorqm@the-edge:~/madwifi-hal-0.10.5.6-r3835-20080801$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath_radar.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath_hal_extensions.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath_pci.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/ath_pci.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/ah_os.o
  HOSTCC  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode
  UUDECODE /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/i386-elf._hal.o
  UNMANGLE /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/i386-elf.hal.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/ath_hal.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr/amrr.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel/minstrel.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel/ath_rate_minstrel.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe/onoe.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample/sample.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample/ath_rate_sample.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/if_media.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_skb.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_beacon.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_crypto.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_crypto_none.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_input.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_node.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_output.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_power.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_proto.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_scan.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_wireless.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_linux.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_monitor.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_rate.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_acl.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_crypto_ccmp.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_scan_ap.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_scan_sta.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_crypto_tkip.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_crypto_wep.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_xauth.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_wep.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_tkip.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_ccmp.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_acl.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_xauth.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_sta.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_ap.o
  Building modules, stage 2.
  MODPOST 14 modules
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/ath_pci.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/ath_pci.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/ath_hal.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/ath_hal.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr/ath_rate_amrr.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr/ath_rate_amrr.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel/ath_rate_minstrel.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel/ath_rate_minstrel.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe/ath_rate_onoe.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe/ath_rate_onoe.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample/ath_rate_sample.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample/ath_rate_sample.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_acl.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_acl.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_ccmp.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_ccmp.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_ap.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_ap.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_sta.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_sta.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_tkip.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_tkip.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_wep.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_wep.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_xauth.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_xauth.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make -C ./tools all || exit 1
make[1]: Entering directory `/home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
gcc -g -O2 -W -Wall -c ath_info.c
gcc -g -O2 -W -Wall  -o ath_info ath_info.o
make[2]: Leaving directory `/home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
gcc -o athstats -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal -I../ath  athstats.c
gcc -o 80211stats -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  80211stats.c
gcc -o athkey -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athkey.c
gcc -o athchans -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athchans.c
gcc -o athctrl -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athctrl.c
gcc -o athdebug -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athdebug.c
gcc -o 80211debug -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  80211debug.c
gcc -o wlanconfig -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  wlanconfig.c
gcc -o wpakey -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  wpakey.c
make[1]: Leaving directory `/home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/tools'
faktorqm@the-edge:~/madwifi-hal-0.10.5.6-r3835-20080801$ 

```

Salu2!!!!

---

### Post by luks911 on 2008-08-12
faktorqm, no es por contradecirte ;), pero el archivo que indicás ([http://snapshots.madwifi.org/special/madwifi-ng-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r3366+ar5007.tar.gz)), ya no tiene el driver, sino un readme que dice que lo último para el Atheros AR5007 está en [http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192). De allí se puede descargar el madwifi-hal-0.10.5.6, que ahora sí sirve para versiones de 64bits.
Lo demás, sí es lo mismo: desinstalar restricted modules, compilar e instalar el driver y cargar el módulo.

Un saludo

---

### Post by faktorqm on 2008-08-12
> **luks911 said:**
> faktorqm, no es por contradecirte ;), pero el archivo que indicás ([http://snapshots.madwifi.org/special/madwifi-ng-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r3366+ar5007.tar.gz)), ya no tiene el driver, sino un readme que dice que lo último para el Atheros AR5007 está en [http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192). De allí se puede descargar el madwifi-hal-0.10.5.6, que ahora sí sirve para versiones de 64bits.
Lo demás, sí es lo mismo: desinstalar restricted modules, compilar e instalar el driver y cargar el módulo.

Un saludo

Si tenes razón, gracias!!, lo que pasa es que me marié entre tantos tutos y links y terminé haciendo mal las cosas. La próxima prometo prestar mas atención, sepan disculpar. Salu2!!!! :popcorn:

---

### Post by luks911 on 2008-08-13
> **faktorqm said:**
> Si tenes razón, gracias!!, lo que pasa es que me marié entre tantos tutos y links y terminé haciendo mal las cosas. La próxima prometo prestar mas atención, sepan disculpar. Salu2!!!! :popcorn:

Todo bien. No es para que andes pidiendo perdón. 
Y sí, hay tutoriales por todos lados de eso. Entre las distintas versiones y parches del madwifi, y que cada uno pregunta por su modelo de notebook en lugar de por la placa, pfffffff... pero bueh, más vale que so... sobre a que fa... falte
Saludos
:lolflag:

---

### Post by faktorqm on 2008-08-13
Claro pero si encima que lo estoy ayudando lo ayudo mal, se come un garron el por que no le funciona, y luego me lo morfo yo por que tengo que revisar todos los pasos de vuelta a ver en cual me equivoque.... gracias de vuelta! salu2!

---

### Post by vk-cdg on 2008-08-14
> **luks911 said:**
> El procedimiento que hacés está bien, al menos hasta donde entiendo, sólo me genera duda esto último de volver a habilitar los drivers restringidos. Creo que eso no hace falta y alcanza con agregar el módulo en el archivo /etc/modules.

Lo de volver a habilitar los drivers restringidos lo hice porque lo decía el tuto, solo por eso, me sonaba medio raro pero bue, a todos les anda así.



> **luks911 said:**
> Una forma de terminar con esa duda es ir a Synaptic y desinstalar el paquete linux-restricted-modules, siempre que no uses el driver de Nvidia, por ejemplo, en ese caso podés reemplazarlo por el driver privativo.

Como figura en la imagen de los controladores restringidos, no lo tengo habilitado, instalé el driver con el Envy y tengo efectos de escritorio, compiz y todo.
Puedo eliminar entonces el paquete linux-restricted-modules?



> **luks911 said:**
> o. Hay alguna otra cosa. ¿Y si en las conexiones habilitás el modo itinerante?

Si habilito el modo itinerante tampoco pasa nada, no conecta.

---

### Post by vk-cdg on 2008-08-14
De antemano les agradezco a ambos por tan detallada ayuda. Aclaro que todavía no lo probé porque tengo a la beba enferma (nada grave, resfrío y fiebre alta que controlar) y eso pesa mas que hacer andar la wifi en la notebook. 

Esta noche si mi gordita se puso mejor lo pruebo y les aviso.

Otra vez, inmensamente agradecido. 

Che, a propósito, por donde andan, porque les mandaría una docenita de facturas por la tan detallada y desinteresada ayuda! 
Hoy lo hablaba con un compañero de trabajo, hace un tiempo, cunado estaba con el tema de la sintonizadora de TV, me dijeron que pruebe Mandriva, que detectaba todo mejor que Ubuntu, así fue, LiveCD mediante probé y levantó todo de una, aún con sonido en la sintonizadora, cosa que ahora con Ubuntu sigue sin andar. 
Cuando consulté y busqué los foros de Mandriva, me encontré que no hay una comunidad como la que tiene Ubuntu y sin dudarlo me quedé acá, aún con cosas sin andar.
No saben la tranquilidad que es para un novato tener una comunidad de habla hispana que te ayude y mas, una comunidad como la de argentina, con ayudas de este tipo. Flacos como por ejemplo Faktorqm (entre otros), que ni siquiera tienen la misma placa que se pongan a compilar un driver merecen el Ubuntu de Otro. 

Gracias mil!!!!

---

### Post by luks911 on 2008-08-14
EDITO:
Primero, gracias por todo lo anterior (estaba escribiendo el post mientras vos el tuyo, parece). Yo también soy muy novato y no sé qué haría si no fuera por la ayuda que se encuentra en toda la comunidad. Y lo de Faktorqm parece fanatismo, ja, un grande :) 

> **vk-cdg said:**
> Lo de volver a habilitar los drivers restringidos lo hice porque lo decía el tuto, solo por eso, me sonaba medio raro pero bue, a todos les anda así.

Sí, en realidad si el driver ya no existe, que figure o no habilitado no debería ser problema.

> **vk-cdg said:**
> Como figura en la imagen de los controladores restringidos, no lo tengo habilitado, instalé el driver con el Envy y tengo efectos de escritorio, compiz y todo.
Puedo eliminar entonces el paquete linux-restricted-modules?

Sí, porque envy te instala el driver de Nvidia.

> **vk-cdg said:**
> Si habilito el modo itinerante tampoco pasa nada, no conecta.

Mmmm... ¿probaste con una red abierta? Digo porque más allá de todo lo anterior el driver está funcionando. Si no funciona, no te detcta la placa ni las redes, y vos las ves. A mí me pasó que la primera vez que instalé el Madwifi lo hice con la versión normal, que no funciona para esta placa, y ni siquiera la detectaba. 
Por eso se me ocurre que el problema podría estar en las restricciones de las redes a las que querés conectarte. No sé, el tipo de clave, un filtrado MAC.

---

### Post by vk-cdg on 2008-08-14
> **luks911 said:**
> EDITO:
Primero, gracias por todo lo anterior (estaba escribiendo el post mientras vos el tuyo, parece). Yo también soy muy novato y no sé qué haría si no fuera por la ayuda que se encuentra en toda la comunidad. Y lo de Faktorqm parece fanatismo, ja, un grande :) 

La comunidad es fantástica, me hace sentir seguro! jajaja


> **luks911 said:**
> Sí, porque envy te instala el driver de Nvidia.

Y el restrictivo que sugiere Ubuntu no es de nVidia también?


> **luks911 said:**
> Mmmm... ¿probaste con una red abierta? Digo porque más allá de todo lo anterior el driver está funcionando. Si no funciona, no te detcta la placa ni las redes, y vos las ves. A mí me pasó que la primera vez que instalé el Madwifi lo hice con la versión normal, que no funciona para esta placa, y ni siquiera la detectaba. 
Por eso se me ocurre que el problema podría estar en las restricciones de las redes a las que querés conectarte. No sé, el tipo de clave, un filtrado MAC.

Mirá, la red a la que quiero conectarme es a la de casa, mi red. Tengo seteado seguridad con WPA2, una password inpronunciable (mayúsculas, minúsculas y numeros) y un access list por MAC (con la MAC de mi note habilitada obvio). Desde el vi$ta me conecto normalmente. 
Volviendo a Ubuntu, detecto en casa solo dos redes, una de ellas abierta y la otra es la mia. Cuando abro el WiFi-Radar, me lista las redes a mi alcance pero no me habilita el botón de conectar. 
Adjunto una imagen que NO es mía. El botón que resalté yo no lo tengo...

[IMG]http://img225.imageshack.us/img225/2238/wifiradaril1.png[/IMG]

Eso es lo que me hace pensar que algo no quedó bien.

---

### Post by luks911 on 2008-08-14
Che, me metiste la duda con lo del driver Nvidia. Me hacés pensar que es el mismo pero instalado de otro modo, pero no estoy seguro :confused: Después me fijo en mi Synaptic a ver si encuentro una pista porque en una búsqueda rápida por la web no llegué a nada. (Ahora estoy en el laburo con Win).

En cuanto al Wifi. Yo uso para conectarme el network-manager-gnome, bastante parecedio al wifi radar. Podés probar sacándoile el WPA2 a ver qué pasa, al menos para ver si es eso. Con filtrado MAC solo no tengo drama.  
Otra posibilidad: hay en el foro un paso a paso muy completo para instalar los drivers de esta placa ([http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)) y ahí veo lo que decía antes Faktorqm sobre un tal wicd. El howto dice (copio y pego porque, recordemos, estoy en el laburo :p):

> OPTIONAL BASED ON WHETHER THE STANDARD NETWORK MANAGER WORKS FOR YOU OR NOT
After all that I still found that the standard network manager software didn't work right for me so I uninstalled it ( Dont do it yourself now wait and follow below as it will be done for you when you install wicd as they conflict with each other and the system will remove) and I now use WICD to manage my network connections and it works like a charm to connect to my encrypted connection and saves my settings properly as well. Just follow directions below and when you get to the install part it will tell you it wants to remove the other network managers upon WICD install so just let it do it. Once installed WICD will be under applications tool bar tab in the internet menu ( you might want to just drag that up to a empty space on your top tool bar so it will be there as well for easy access.

WICD INSTALL INFO

Installing Wicd in Ubuntu is very simple. You just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

LINE FOR HARDY IS

deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras

Then WICD will be available for install in synaptic package manager so install from there or with following command in a terminal.

sudo apt-get install wicd

Once WICD is installed go to Applications -> Internet -> WICD and open it to setup your Wireless network connections.

Parece que le pasó lo mismo que a vos y lo solucionó instalando el wicd ese. Ahí está el repositorio. Habría que ver.

Saludo

---

### Post by lega on 2008-08-14
con respecto al wicd yo lo instalé,la razón era que cada vez que iniciaba Ubuntu al querer conectarme Network-Manager me pedía la clave de administrador para desbloquear el anillo, despues me enteré (cosas de burro/novato) que eso se puede habilitar entrando en la configuracion del anillo de contraseñas y dandole permiso a la clave en cuestion para que salga del anillo libremente cuando se necesite, pero ya era tarde y había desinstalado Network-manager e instalado wicd, otra cosa que me pasaba con Network-manager es que conectaba directo con la conexion del vecino que la tiene sin clave :) y no encontré o no me fijé demasiado la forma de poner una conexion por defecto.

Yo concuerdo con luks911 que el driver esta bien instalado porque ves tu red y las redes vecinas, debe haber otra cosa por ahí que estamos pasando por alto.

---

### Post by niko_3100 on 2008-08-14
probaste de poner tu router sin ninguna seguridad a ver si se conecta? o de ir a algun lugar con wifi sin seguridad? o por lo menos por solo clave wpa o wep, porque tenes recontra reseguro todo y por ahi es eso... wpa2 me suena a que por el driver no lo toma bien, proba por lo menos wpa o wep que son los standares de hoy en dia o mejor sin seguridad total lo importante es que se conecte, cuando se conecte y veas que anda bueno... entonces sabes que por lo menos la placa wifi anda.

---

### Post by vk-cdg on 2008-08-14
Voy a probar sacarle la seguridad, como para descartar pero no creo que ande porque a la otra red que detecta en casa, que no tiene seguridad tampoco conecta. 

Eso me da la pauta que algo no anda.

---

### Post by vk-cdg on 2008-08-15
> **faktorqm said:**
> ...y ¡¡listo!!. Ahora posteame que fue todo lo que no te anduvo xD

Algo puede fallar decía tusam y falló! :(

De entrada arrancamos complicados....
Hago esto

```
lsmod | grep ath
```


Y tira algo parecido a lo que vos pusiste, no lo anoté porque es similar a lo que debía dar.

```
wlan 207728 1 ath_pci 
ath_pci 101024 0
```

Ahora el problema aparece cuando quiero hacer esto:

```
sudo modprobe -r wlan
sudo modprobe -r ath_pci
```

Me dice:

```
FATAL: wlan is in use
```


Lo curioso es lo siguiente, cuando voy al administrador de controladores restringidos me aparecen ambos destildados pero en uso ¿¿WTF??
Voy a probar (no lo hice porque era tarde) desinstalar como dijo lukas911 el paquete linux-restricted-modules a ver que pasa!

---

### Post by Hei Ku on 2008-08-16
deshabilita la interfaz antes de remover el modulo.

---

### Post by vk-cdg on 2008-08-18
Bueno, les cuento que finalmente ya tengo funcionando wifi en la note. La alegría que se siente es indescriptible!!!!

Quiero agradecer a todos los que me dieron una mano, desde la mas detallada hasta la mas escueta, gracias... TOTALES!!!

---

### Post by lega on 2008-08-18
Buenisimo!!:):) contá que hiciste!

---

### Post by vk-cdg on 2008-08-18
Seguí al pié de la letra el post de faktorqm. 
Me salía un error de que dos módulos estaban en uso así que los tube que bajar con:
```

rmmod wlan
rmmod ath_pci
```

Luego de eso seguí el post al pié de la letra.


En este momento estoy en la cama con la note a upa.

Gracias a todos nuevamente.

---

### Post by faktorqm on 2008-08-19
Me alegro mucho haber sido de ayuda una vez mas :KS salu2!

---

### Post by vk-cdg on 2008-08-19
Yo estoy mucho mas alegre, eso dalo por hecho. :lolflag:

---

### Post by luks911 on 2008-08-19
¡Genial¡ Tenía que funcionar. 

> **vk-cdg said:**
> En este momento estoy en la cama con la note a upa.

Y todo para que el señor se la pase tirado en la cama, jaja... En serio, a esta altura una notebook sin wifi es un gran desperdicio. 

Saludos

---

### Post by vk-cdg on 2008-08-19
Tal cual.

Una vez mas gracias a todos!!!

PD: marco como SOLVED del post.

---

### Post by niko_3100 on 2008-08-20
Pera podrias postear aca claramente los pasos que hiciste? no importa que pongas un copiar y pegar de otro tutorial ponele y comentanos un poquito mas please jeje, asi queda bien clara la solucion final. Gracias.

---

### Post by faktorqm on 2008-08-20
Primero **deshabilita desde controladores restringidos todo lo que tenga que ver con wifi** y tira en una terminal:

```
lsmod | grep ath
```

eso lo que hace es listar el contenido de todos los modulos cargados en el sistema que contengan la palabra "ath". te va a salir algo parecido a esto: 

```
wlan 207728 1 ath_pci 
ath_pci 101024 0
```

digo parecido x q pueden cambiar los números. 
si esto no te sale, no hay nada que bajar de memoria, segui leyendo.
si esto te sale, entonces los bajamos con:

```
sudo rmmod wlan
sudo rmmod ath_pci
```

y luego:

```
sudo modprobe -r wlan
```
```
sudo modprobe -r ath_pci
```

y no te tiene que tirar ningún cartel de nada. 

Entonces ahora si tenemos los módulos bajados y lo que tenemos que hacer es setearle que no se cargue de vuelta cuando reinicie la pc, tonces editamos un archivo:

```
sudo gedit /etc/default/linux-restricted-modules-common
```

y te aparece:

```
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables the three nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES=""
```

y te tiene que quedar asi: (le agregamos el modulo que no queremos que cargue al final)

```
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables the three nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES="ath_hal"
```

guardamos y salimos. 

Ahora lo mandamos a lista negra de los módulos con:

```
echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
```

Luego debemos eliminar rastros de la versión vieja:

```
sudo apt-get remove madwifi-tools --purge
```

Nunca esta de mas tener las herramientas de compilacion a mano:

```
sudo apt-get update && sudo aptitude install build-essential gcc binutils autoconf automake
```

Ahora si arrancamos el proceso de instalacion, para esto nos bajamos el driver:

```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
```

descomprimimos:

```
tar xzf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
```

entramos en el directorio:

```
cd madwifi-hal-0.10.5.6-r3835-20080801
```

compilamos (NO hace falta SUDO):

```
make
```

Algo así se ve la compilación, lo compilé para ver si tenia problemas pero compiló bien.

```

faktorqm@the-edge:~$ wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
--22:48:35--  http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
           => `madwifi-hal-0.10.5.6-r3835-20080801.tar.gz'
Resolviendo snapshots.madwifi.org... 217.24.1.134
Conectando a snapshots.madwifi.org|217.24.1.134|:80... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 4.417.874 (4.2M) [application/x-gzip]

100%[====================================>] 4.417.874     60.83K/s    ETA 00:00

22:49:56 (54.02 KB/s) - `madwifi-hal-0.10.5.6-r3835-20080801.tar.gz' guardado [4417874/4417874]

faktorqm@the-edge:~$ tar xzf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
faktorqm@the-edge:~$ cd madwifi-hal-0.10.5.6-r3835-20080801
faktorqm@the-edge:~/madwifi-hal-0.10.5.6-r3835-20080801$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath_radar.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath_hal_extensions.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath_pci.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/ath_pci.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/ah_os.o
  HOSTCC  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode
  UUDECODE /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/i386-elf._hal.o
  UNMANGLE /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/i386-elf.hal.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/ath_hal.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr/amrr.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel/minstrel.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel/ath_rate_minstrel.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe/onoe.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample/sample.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample/ath_rate_sample.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/if_media.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_skb.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_beacon.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_crypto.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_crypto_none.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_input.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_node.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_output.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_power.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_proto.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_scan.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_wireless.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_linux.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_monitor.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_rate.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_acl.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_crypto_ccmp.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_scan_ap.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_scan_sta.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_crypto_tkip.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_crypto_wep.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_xauth.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_wep.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_tkip.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_ccmp.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_acl.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_xauth.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_sta.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_ap.o
  Building modules, stage 2.
  MODPOST 14 modules
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/ath_pci.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/ath_pci.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/ath_hal.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/ath_hal.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr/ath_rate_amrr.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr/ath_rate_amrr.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel/ath_rate_minstrel.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel/ath_rate_minstrel.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe/ath_rate_onoe.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe/ath_rate_onoe.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample/ath_rate_sample.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample/ath_rate_sample.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_acl.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_acl.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_ccmp.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_ccmp.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_ap.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_ap.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_sta.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_sta.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_tkip.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_tkip.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_wep.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_wep.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_xauth.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_xauth.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make -C ./tools all || exit 1
make[1]: Entering directory `/home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
gcc -g -O2 -W -Wall -c ath_info.c
gcc -g -O2 -W -Wall  -o ath_info ath_info.o
make[2]: Leaving directory `/home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
gcc -o athstats -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal -I../ath  athstats.c
gcc -o 80211stats -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  80211stats.c
gcc -o athkey -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athkey.c
gcc -o athchans -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athchans.c
gcc -o athctrl -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athctrl.c
gcc -o athdebug -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athdebug.c
gcc -o 80211debug -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  80211debug.c
gcc -o wlanconfig -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  wlanconfig.c
gcc -o wpakey -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  wpakey.c
make[1]: Leaving directory `/home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/tools'
faktorqm@the-edge:~/madwifi-hal-0.10.5.6-r3835-20080801$ 

```

instalamos:

```
sudo make install
```

Ahora levantamos los modulos a memoria:

```
sudo modprobe -a ath_pci wlan_scan_sta
```

Ahora levantamos la interfaz:

```
sudo ifconfig ath0 up
```

y teoricamente ya deberias estar conectado. Ahora, asegurate de que la conexion a la cual te estes conectando ande y etcetcetc.

Ahora lo ultimo, hay que poner el modulo nuevo a /etc/modules para que lo levante cada vez que arranca:

```
echo "ath_pci" | sudo tee -a /etc/modules
```

y ¡¡listo!!

bibliografia consultada:

bug en launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196843](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196843)
ubuntu chile: [http://foros.ubuntu-cl.org/viewtopic.php?p=31909](http://foros.ubuntu-cl.org/viewtopic.php?p=31909)
ubuntu españa: [http://www.ubuntu-es.org/index.php?q=node/83598](http://www.ubuntu-es.org/index.php?q=node/83598)
ubuntu en ingles: [http://ubuntuforums.org/showthread.php?t=766529](http://ubuntuforums.org/showthread.php?t=766529)
lista de chipsets reconocidos por el kernel: [http://kerneltrap.org/mailarchive/madwifi-devel/2008/2/18/890124](http://kerneltrap.org/mailarchive/madwifi-devel/2008/2/18/890124)
OBVIO: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)
[http://snapshots.madwifi.org/special/](http://snapshots.madwifi.org/special/)
blogs: [http://chamangt.wordpress.com/2008/05/08/activar-wireless-atheros-en-ubuntu-con-madwifi/](http://chamangt.wordpress.com/2008/05/08/activar-wireless-atheros-en-ubuntu-con-madwifi/)

Espero que te haya servido. Salu2!!!!:KS

---

### Post by niko_3100 on 2008-08-21
bueno faktorqm me hubiera conformado con mucho menos pero te pasaste, el sabado voy a ir a buscar mi nueva compaq v3614 no se que placa wifi tiene seguro es o atheros o broadcom, yo con mi anterior compaq v3415 tube que depender de ndiswrapper y el driver para xp del wifi pero andaba 100 puntos, espero que ahora solo tenga que instalar madwifi y chau tema, pero sino... este tutorial lo voy a tener mas que en cuenta. Ahora es raro porque te paso a vos, hay un par de usuarios con la compaq f756 que instalo madwifi y levanto todo de una, que raro....

---

### Post by luks911 on 2008-08-21
> **niko_3100 said:**
> bueno faktorqm me hubiera conformado con mucho menos pero te pasaste, el sabado voy a ir a buscar mi nueva compaq v3614 no se que placa wifi tiene seguro es o atheros o broadcom, yo con mi anterior compaq v3415 tube que depender de ndiswrapper y el driver para xp del wifi pero andaba 100 puntos, espero que ahora solo tenga que instalar madwifi y chau tema, pero sino... este tutorial lo voy a tener mas que en cuenta. Ahora es raro porque te paso a vos, hay un par de usuarios con la compaq f756 que instalo madwifi y levanto todo de una, que raro....

Mmmmmm... viene con Broadcom. Mirá, un howto ([http://www.tuxi.com.ar/2008/07/15/howto-configurar-placas-wifi-broadcom-bcm43xx-en-ubuntu-y-debian/](http://www.tuxi.com.ar/2008/07/15/howto-configurar-placas-wifi-broadcom-bcm43xx-en-ubuntu-y-debian/)). Ojo, apenas lo leí y mucho menos lo probé, claro.

Saludos

---

### Post by vk-cdg on 2008-08-21
Perdón, no expliqué los pasos detalladamente porque estaban en el post de la 2° página de Faktorqm. 

Respecto de las partes que puso faktorqm en el último post en rojo, las hice todas, con la pequeña diferencia de que al ejecutar estos comandos

```
sudo modprobe -r wlan
sudo modprobe -r ath_pci
```

Me salía 

```
FATAL: wlan is in use
```

Y lo mismo con el ath_pci. Tuve que hacer esto

```
sudo rmmod ath_pci
sudo rmmod wlan
```

Y luego si las siguientes instrucciones

```
sudo modprobe -r wlan
sudo modprobe -r ath_pci
```

De ahí en mas, seguí al pié de la letra el post de faktorqm (el anterior y este, que son iguales). Lo único que no hice fue instalar el wcid, ya que el que viene por defaul está fuera del anillo y anda bien (por ahora)

Aclaro que yo antes había tratado de compilar el driver viejo sin éxito.

---

### Post by vk-cdg on 2008-08-21
> **niko_3100 said:**
> ...el sabado voy a ir a buscar mi nueva compaq v3614 no se que placa wifi tiene seguro es o atheros o broadcom...

Vos no tenías una MSI???
La Compaq esa no tiene Atheros, tiene un modelo de Broadcom. Yo no la compré por ese motivo. La diferencia no era mucho en plata y viene con 2 GB de RAM. Es de 14 también y tiene lector de tarjetas.


> **niko_3100 said:**
> Ahora es raro porque te paso a vos, hay un par de usuarios con la compaq f756 que instalo madwifi y levanto todo de una, que raro....

Si, la verdad que es muy raro. Lo adjudico a que en mi "novatez" no hice algún paso de los que están supuestos implicitos, ya que los pasos que están explícitamente escritos los hice todos y en el órden indicado. En fin, ahora con el driver nuevo está andando.

---

### Post by lega on 2008-08-21
La luz prende? o sigue en rojo?

---

### Post by vk-cdg on 2008-08-21
Nop, sigue en rojo!
:(
:confused:
:mad:

PD: Soy un histérico de los detalles.

---

### Post by faktorqm on 2008-08-21
actualizado! gracias vikingo por probarlo! salu2!

---

### Post by niko_3100 on 2008-08-22
se me cayo la compaq v3614... la gente de techbiz le estaba haciendo pruebas de calidad y resulta que tenia errores, no paso las pruebas y no iban a entregarmela asi, y era la ultima. Con razon estos modelos de compaq tienen tantos problemas, hay mucha gente que se esta quejando de problemas y mas del soporte de hp... y bueno... asi es la vida. Se la vendi a un amigo la msi jojo!! Ahora estoy entre la acer 4220 y la acer 4315...

---

### Post by vk-cdg on 2008-08-22
Que no te gustó de la MSI? te duró poco!

Una DELL no te va?
Por 3500 mangos conseguís una Inspiron bastante buena y DELL no te hace drama por el SO que le pongas con el tema de la garantía. Tengo 2 compañeros que tienen DELL (una Inspiron y una XPS) y no tuvieron drama con el hardware al instalar Ubuntu, reconoció todo de una.

---

### Post by niko_3100 on 2008-08-24
Bueno al final consegui una compaq v3614 y aca estoy con vista... mañana domingo le instalo hardy y supongo que el unico problema va a ser la placa wifi broadcom que voy a tener que usar ndiswrapper pero bueno vere.. la verdad que esta hermosa la compaq esta. De msi no me gusto algunas boludeces por ejemplo el teclado se hundian las teclas que estaban alrededor de la tecla que presionabas o que los puertos usb estaban al reves.. la lectora de dvd cuando grababa hacia un ruido medio raro pero bueno en realidad sera que estoy super acostumbrado a las compaq espero no tener problemas y disfrutar esta notebook con hardy y luego con intrepid y asi....

---

### Post by vk-cdg on 2008-08-24
Me asusté un poco cuando vi que querías comprar otra compaq y dije, apa, que pasó con la MSI que tanta fama le hicieron.

Yo de mi compaq no tengo quejas por el momento, a excepción de tener que compilar el driver de la wifi cada vez que se actualiza el kernel.

---

### Post by niko_3100 on 2008-08-24
nono, la msi estaba excelente pero siempre me gusto compaq, de notebooks y pcs de escritorio es mi marca preferida, aunque de maquinas de escritorio no compro una de marca ni loco, me la armo yo jeje!! peor que notebook tenes vk-cdg??

---

### Post by vk-cdg on 2008-08-25
Yo tengo una Compaq F756la

Athlon Tk55
1 Gb Ram
120 Disco

---

### Post by niko_3100 on 2008-08-26
Y que tal como te anda la compaq? pudiste correrla con xp o vista, ademas de ubuntu? mi compaq v3614 levanto ubuntu de una, salvo el video por los drivers y el wifi todo joya, el wifi al ser broadcom tuve que usar los driver de xp con wine y ndiswrapper, pero quedo andando joya, total que son los drivers?? Secuencias de unos y ceros que interpreta el SO para hacer funcionar hardware, esta bien la definicion? Entonces que importan si son de xp si de ultima terminan siendo unos y ceros de todas formas... Yo le puse dos gb de ram mas y la deje con 2,5 gb de ram, seguro que tu f756 tambien se banca modulos de 2 gb de ram.

---

### Post by vk-cdg on 2008-08-26
La mía anda de 10. Viene con 1 GB (dos módulos de 512). En cuanto consiga un poco mas de fluidez monetaria (o logre vender la EPSON LX 300) le pongo 2 GB de RAM.
La placa wifi con madwifi anda bien.

Además de Ubuntu le dejé el vista original con dual boot por un tema de la garantía y por ciertos programas que debo usar para la facu.

No me puedo quejar, un chiche!

---

### Post by niko_3100 on 2008-08-26
en cuanto a temperaturas como viene? tenes idea que temperatura trabaja el cpu y gpu? Fijate que yo a mi compaq v3614 le deje 512 y le puse un modulo de 2 gb y levanto de una cuando en realidad hp dice que soporta 2 gb de ram como maximo.

---

### Post by juanelmagnifico on 2008-11-16
> **faktorqm said:**
> Primero **deshabilita desde controladores restringidos todo lo que tenga que ver con wifi** y tira en una terminal:

```
lsmod | grep ath
```

eso lo que hace es listar el contenido de todos los modulos cargados en el sistema que contengan la palabra "ath". te va a salir algo parecido a esto: 

```
wlan 207728 1 ath_pci 
ath_pci 101024 0
```

digo parecido x q pueden cambiar los números. 
si esto no te sale, no hay nada que bajar de memoria, segui leyendo.
si esto te sale, entonces los bajamos con:

```
sudo rmmod wlan
sudo rmmod ath_pci
```

y luego:

```
sudo modprobe -r wlan
```
```
sudo modprobe -r ath_pci
```

y no te tiene que tirar ningún cartel de nada. 

Entonces ahora si tenemos los módulos bajados y lo que tenemos que hacer es setearle que no se cargue de vuelta cuando reinicie la pc, tonces editamos un archivo:

```
sudo gedit /etc/default/linux-restricted-modules-common
```

y te aparece:

```
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables the three nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES=""
```

y te tiene que quedar asi: (le agregamos el modulo que no queremos que cargue al final)

```
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables the three nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES="ath_hal"
```

guardamos y salimos. 

Ahora lo mandamos a lista negra de los módulos con:

```
echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
```

Luego debemos eliminar rastros de la versión vieja:

```
sudo apt-get remove madwifi-tools --purge
```

Nunca esta de mas tener las herramientas de compilacion a mano:

```
sudo apt-get update && sudo aptitude install build-essential gcc binutils autoconf automake
```

Ahora si arrancamos el proceso de instalacion, para esto nos bajamos el driver:

```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
```

descomprimimos:

```
tar xzf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
```

entramos en el directorio:

```
cd madwifi-hal-0.10.5.6-r3835-20080801
```

compilamos (NO hace falta SUDO):

```
make
```

Algo así se ve la compilación, lo compilé para ver si tenia problemas pero compiló bien.

```

faktorqm@the-edge:~$ wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
--22:48:35--  http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
           => `madwifi-hal-0.10.5.6-r3835-20080801.tar.gz'
Resolviendo snapshots.madwifi.org... 217.24.1.134
Conectando a snapshots.madwifi.org|217.24.1.134|:80... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 4.417.874 (4.2M) [application/x-gzip]

100%[====================================>] 4.417.874     60.83K/s    ETA 00:00

22:49:56 (54.02 KB/s) - `madwifi-hal-0.10.5.6-r3835-20080801.tar.gz' guardado [4417874/4417874]

faktorqm@the-edge:~$ tar xzf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
faktorqm@the-edge:~$ cd madwifi-hal-0.10.5.6-r3835-20080801
faktorqm@the-edge:~/madwifi-hal-0.10.5.6-r3835-20080801$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath_radar.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath_hal_extensions.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath_pci.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/ath_pci.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/ah_os.o
  HOSTCC  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode
  UUDECODE /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/i386-elf._hal.o
  UNMANGLE /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/i386-elf.hal.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/ath_hal.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr/amrr.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel/minstrel.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel/ath_rate_minstrel.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe/onoe.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample/sample.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample/ath_rate_sample.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/if_media.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_skb.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_beacon.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_crypto.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_crypto_none.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_input.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_node.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_output.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_power.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_proto.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_scan.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_wireless.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_linux.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_monitor.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_rate.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_acl.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_crypto_ccmp.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_scan_ap.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_scan_sta.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_crypto_tkip.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_crypto_wep.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_xauth.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_wep.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_tkip.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_ccmp.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_acl.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_xauth.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_sta.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_ap.o
  Building modules, stage 2.
  MODPOST 14 modules
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/ath_pci.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/ath_pci.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/ath_hal.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/ath_hal.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr/ath_rate_amrr.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr/ath_rate_amrr.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel/ath_rate_minstrel.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel/ath_rate_minstrel.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe/ath_rate_onoe.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe/ath_rate_onoe.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample/ath_rate_sample.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample/ath_rate_sample.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_acl.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_acl.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_ccmp.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_ccmp.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_ap.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_ap.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_sta.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_sta.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_tkip.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_tkip.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_wep.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_wep.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_xauth.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_xauth.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make -C ./tools all || exit 1
make[1]: Entering directory `/home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
gcc -g -O2 -W -Wall -c ath_info.c
gcc -g -O2 -W -Wall  -o ath_info ath_info.o
make[2]: Leaving directory `/home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
gcc -o athstats -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal -I../ath  athstats.c
gcc -o 80211stats -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  80211stats.c
gcc -o athkey -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athkey.c
gcc -o athchans -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athchans.c
gcc -o athctrl -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athctrl.c
gcc -o athdebug -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athdebug.c
gcc -o 80211debug -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  80211debug.c
gcc -o wlanconfig -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  wlanconfig.c
gcc -o wpakey -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  wpakey.c
make[1]: Leaving directory `/home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/tools'
faktorqm@the-edge:~/madwifi-hal-0.10.5.6-r3835-20080801$ 

```

instalamos:

```
sudo make install
```

Ahora levantamos los modulos a memoria:

```
sudo modprobe -a ath_pci wlan_scan_sta
```

Ahora levantamos la interfaz:

```
sudo ifconfig ath0 up
```

y teoricamente ya deberias estar conectado. Ahora, asegurate de que la conexion a la cual te estes conectando ande y etcetcetc.

Ahora lo ultimo, hay que poner el modulo nuevo a /etc/modules para que lo levante cada vez que arranca:

```
echo "ath_pci" | sudo tee -a /etc/modules
```

y ¡¡listo!!

bibliografia consultada:

bug en launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196843](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196843)
ubuntu chile: [http://foros.ubuntu-cl.org/viewtopic.php?p=31909](http://foros.ubuntu-cl.org/viewtopic.php?p=31909)
ubuntu españa: [http://www.ubuntu-es.org/index.php?q=node/83598](http://www.ubuntu-es.org/index.php?q=node/83598)
ubuntu en ingles: [http://ubuntuforums.org/showthread.php?t=766529](http://ubuntuforums.org/showthread.php?t=766529)
lista de chipsets reconocidos por el kernel: [http://kerneltrap.org/mailarchive/madwifi-devel/2008/2/18/890124](http://kerneltrap.org/mailarchive/madwifi-devel/2008/2/18/890124)
OBVIO: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)
[http://snapshots.madwifi.org/special/](http://snapshots.madwifi.org/special/)
blogs: [http://chamangt.wordpress.com/2008/05/08/activar-wireless-atheros-en-ubuntu-con-madwifi/](http://chamangt.wordpress.com/2008/05/08/activar-wireless-atheros-en-ubuntu-con-madwifi/)

Espero que te haya servido. Salu2!!!!:KS

saludos. he seguido los pasos del poste #36 para la version 8.04 de ubuntu y me servido de maravilla; pero he realizado una actualizacion a la version 8.10 y no dejo de funcionar la red inalambrica y no hay modo en que la eche andar. me he enterado que en la version 8.10 hay controladores libres que ya funcionan con esta tarjeta. lo puedes ver en esta direccion

[http://ubuntuforums.org/showthread.php?t=970717&highlight=atheros+ar242x+802.11abg+wireless+pci+express+adapter](http://ubuntuforums.org/showthread.php?t=970717&highlight=atheros+ar242x+802.11abg+wireless+pci+express+adapter)

sin embargo, al seguir estos pasos no funciona mi pc y pieenso que es porque no puedo desintalar eel controlador que habia instalado en el poste #36 de faktorum. ¿podria desintalar este controlador que compile para que funcione el nuevo de los repositorios?

---

### Post by luks911 on 2008-11-16
Para desinstalar el driver que compilaste tenés que moverte hasta el directorio desde el que hiciste la compilación, en este caso había sido:

```
cd madwifi-hal-0.10.5.6-r3835-20080801
```

y allí ejecutar

```
sudo make uninstall
```

No sé cuál fue el problema que tuviste, pero en caso de que tu sistema no arranque podés iniciar en Recovery Mode e ir a una terminal en modo root para poder desisntalar el driver como te expliqué. 

Saludos

---

### Post by faktorqm on 2008-11-18
Hictio posteo aca como se hacia para 8.10: [http://ubuntuforums.org/showthread.php?t=970055](http://ubuntuforums.org/showthread.php?t=970055)

Salu2!!!

---

### Post by luks911 on 2008-11-18
> **faktorqm said:**
> Hictio posteo aca como se hacia para 8.10: [http://ubuntuforums.org/showthread.php?t=970055](http://ubuntuforums.org/showthread.php?t=970055)

Salu2!!!

No es por cortamambos :-P, pero acabo de postear[0] en ese thread por qué tuve que volver a madwifi, je. Ahí lo expliqué, pero básicamente con backports la conexión se interrumpía y con madwifi, no.
Así que volvemos a compilar y a tu tutorial faktor.

Saludos


[0] [http://ubuntuforums.org/showthread.php?p=6203174#post6203174](http://ubuntuforums.org/showthread.php?p=6203174#post6203174)

---

### Post by faktorqm on 2008-11-18
ahh buenisimo, la verdad no lo sabia. Entonces en el de hictio posteen que el que va es el mio de vuelta y no ese, asi no hay confusiones. O incluso poner un link a este thread y que algun admin cierre ese thread asi no hay mas lio. Salu2!!

---

### Post by luks911 on 2008-11-18
> **faktorqm said:**
> ahh buenisimo, la verdad no lo sabia. Entonces en el de hictio posteen que el que va es el mio de vuelta y no ese, asi no hay confusiones. O incluso poner un link a este thread y que algun admin cierre ese thread asi no hay mas lio. Salu2!!

Sí, ya postee ahí la aclaración y el link a tu tuto. No sé si da para cerrarlo... digo, fue abierto de buena fe, yo también creía que el backports era una nueva solución y por otro lado hay que ver cómo evoluciona el driver.

Saludos

---

### Post by lega on 2008-11-19
de todas formas compilar el driver de madwifi en Intrepid ya no tendría el inconveniente que teníamos en Hardy de tener que compilar de nuevo con cada actualización del kernel no? por esa nueva función que tiene Intrepid que recompila los driver con el nuevo kernel que no me acuerdo como se llama?

---

### Post by hictio on 2008-11-19
> **luks911 said:**
> Sí, ya postee ahí la aclaración y el link a tu tuto. No sé si da para cerrarlo... digo, fue abierto de buena fe, yo también creía que el backports era una nueva solución y por otro lado hay que ver cómo evoluciona el driver.

Saludos

Que raro, yo sigo con backports, con todos los updates que distribuyeron hasta el momento para Intrepid instalados, y no tengo problemas con caidas de conexion ni nada con la Atheros.

---

### Post by faktorqm on 2008-11-19
Yo tengo un par de dudas con respecto a eso. Justo estabamos comentando el tema con WanderingKnight, que revision de chipset tiene cada uno? por que varian me parece. Posteen por favor lspci o lshw a ver a donde esta la diferencia. Gracias y salu2!

EDITO: che muchachos si no se enojan propongo que abandonemos este thread y con todo lo dicho nos mudemos a [http://ubuntuforums.org/showthread.php?t=970055](http://ubuntuforums.org/showthread.php?t=970055) por que sino me estan volviendo loco, hay 2 conversaciones abiertas sobre el mismo tema, y esta esta solved, asi que mejor vayamonos ahi donde puse. Muchas gracias! ^^

---

### Post by Hei Ku on 2008-11-20
La discusion continúa en este thread: [http://ubuntuforums.org/showthread.php?t=970055](http://ubuntuforums.org/showthread.php?t=970055)

---

### Post by principexus on 2008-12-19
Excelente tutorial...
Tengo exactamente 5 horas de haber entrado en el mundo linux...
Estaba perdiendo los estribos con la configuración de mi wifi (poseo una sony vaio vgn-nr120e , con una tarjeta atheros ar5006x ) Y este tutorial dio justo en clavo... excelente...
Pero.... (siempre un pero) 
Hay q cambiar la direccion para descargar el archivo... es decir: en vez de 

** wget  [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz)     

Se debe colocar:
wget [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz)

Segun recuerdo xq cambiaron de hosting la gente de madwifi.com

** Por tanto: al descomprimir 

tar xzf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz

Debemos colocar:

tar xzf madwifi-hal-0.10.5.6-r3875-20081105.tar.gz

** Al entrar al directorio:

cd madwifi-hal-0.10.5.6-r3835-20080801

cambia a: cd madwifi-hal-0.10.5.6-r3875-20081105

Del resto... Espectacular...!

Gracias por el tutorial... y espero que mi aporte ayude a novatos como YO...!! 
jejejeje

EXITOS faktorqm...!!

---

### Post by faktorqm on 2008-12-21
Primero **deshabilita desde controladores restringidos todo lo que tenga que ver con wifi** y tira en una terminal:

```
lsmod | grep ath
```

eso lo que hace es listar el contenido de todos los modulos cargados en el sistema que contengan la palabra "ath". te va a salir algo parecido a esto: 

```
wlan 207728 1 ath_pci 
ath_pci 101024 0
```

digo parecido x q pueden cambiar los números. 
si esto no te sale, no hay nada que bajar de memoria, segui leyendo.
si esto te sale, entonces los bajamos con:

```
sudo rmmod wlan
sudo rmmod ath_pci
```

y luego:

```
sudo modprobe -r wlan
```
```
sudo modprobe -r ath_pci
```

y no te tiene que tirar ningún cartel de nada. 

Entonces ahora si tenemos los módulos bajados y lo que tenemos que hacer es setearle que no se cargue de vuelta cuando reinicie la pc, tonces editamos un archivo:

```
sudo gedit /etc/default/linux-restricted-modules-common
```

y te aparece:

```
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables the three nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES=""
```

y te tiene que quedar asi: (le agregamos el modulo que no queremos que cargue al final)

```
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables the three nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES="ath_hal"
```

guardamos y salimos. 

Ahora lo mandamos a lista negra de los módulos con:

```
echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
```

Luego debemos eliminar rastros de la versión vieja:

```
sudo apt-get remove madwifi-tools --purge
```

Nunca esta de mas tener las herramientas de compilacion a mano:

```
sudo apt-get update && sudo aptitude install build-essential gcc binutils autoconf automake
```

Ahora si arrancamos el proceso de instalacion, para esto nos bajamos el driver:

```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz
```

descomprimimos:

```
tar xzf madwifi-hal-0.10.5.6-r3875-20081105.tar.gz
```

entramos en el directorio:

```
cd madwifi-hal-0.10.5.6-r3875-20081105
```

compilamos (NO hace falta SUDO):

```
make
```

Algo así se ve la compilación, lo compilé para ver si tenia problemas pero compiló bien.

```

faktorqm@the-edge:~$ wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
--21:26:00--  http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
           => `madwifi-hal-0.10.5.6-r3835-20080801.tar.gz'
Resolviendo snapshots.madwifi.org... 217.24.1.134
Conectando a snapshots.madwifi.org|217.24.1.134|:80... conectado.
Petición HTTP enviada, esperando respuesta... 301 Moved Permanently
Ubicación: http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz [siguiente]
--21:26:01--  http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
           => `madwifi-hal-0.10.5.6-r3835-20080801.tar.gz'
Resolviendo snapshots.madwifi-project.org... 217.24.1.134
Reusando conexión existente a snapshots.madwifi.org:80.
Petición HTTP enviada, esperando respuesta... 404 Not Found
21:26:03 ERROR 404: Not Found.

faktorqm@the-edge:~$ wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz
--21:29:45--  http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz
           => `madwifi-hal-0.10.5.6-r3875-20081105.tar.gz'
Resolviendo snapshots.madwifi-project.org... 217.24.1.134
Conectando a snapshots.madwifi-project.org|217.24.1.134|:80... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 4.421.372 (4.2M) [application/x-gzip]

100%[====================================>] 4.421.372     59.33K/s    ETA 00:00

21:31:31 (42.08 KB/s) - `madwifi-hal-0.10.5.6-r3875-20081105.tar.gz' guardado [4421372/4421372]

faktorqm@the-edge:~$ tar xzf madwifi-hal-0.10.5.6-r3875-20081105.tar.gz
faktorqm@the-edge:~$ cd madwifi-hal-0.10.5.6-r3875-20081105
faktorqm@the-edge:~/madwifi-hal-0.10.5.6-r3875-20081105$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-22-generic/build SUBDIRS=/home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-22-generic'
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath/if_ath.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath/if_ath_radar.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath/if_ath_hal_extensions.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath/if_ath_pci.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath/ath_pci.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath_hal/ah_os.o
  HOSTCC  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath_hal/uudecode
  UUDECODE /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath_hal/i386-elf._hal.o
  UNMANGLE /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath_hal/i386-elf.hal.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath_hal/ath_hal.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath_rate/amrr/amrr.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath_rate/minstrel/minstrel.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath_rate/minstrel/ath_rate_minstrel.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath_rate/onoe/onoe.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath_rate/sample/sample.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath_rate/sample/ath_rate_sample.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/if_media.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/ieee80211_skb.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/ieee80211.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/ieee80211_beacon.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/ieee80211_crypto.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/ieee80211_crypto_none.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/ieee80211_input.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/ieee80211_node.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/ieee80211_output.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/ieee80211_power.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/ieee80211_proto.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/ieee80211_scan.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/ieee80211_wireless.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/ieee80211_linux.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/ieee80211_monitor.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/ieee80211_rate.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/ieee80211_acl.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/ieee80211_crypto_ccmp.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/ieee80211_scan_ap.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/ieee80211_scan_sta.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/ieee80211_crypto_tkip.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/ieee80211_crypto_wep.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/ieee80211_xauth.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/wlan.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/wlan_wep.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/wlan_tkip.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/wlan_ccmp.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/wlan_acl.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/wlan_xauth.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/wlan_scan_sta.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/wlan_scan_ap.o
  Building modules, stage 2.
  MODPOST 14 modules
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath/ath_pci.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath/ath_pci.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath_hal/ath_hal.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath_hal/ath_hal.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath_rate/amrr/ath_rate_amrr.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath_rate/amrr/ath_rate_amrr.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath_rate/minstrel/ath_rate_minstrel.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath_rate/minstrel/ath_rate_minstrel.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath_rate/onoe/ath_rate_onoe.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath_rate/onoe/ath_rate_onoe.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath_rate/sample/ath_rate_sample.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/ath_rate/sample/ath_rate_sample.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/wlan.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/wlan.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/wlan_acl.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/wlan_acl.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/wlan_ccmp.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/wlan_ccmp.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/wlan_scan_ap.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/wlan_scan_ap.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/wlan_scan_sta.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/wlan_scan_sta.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/wlan_tkip.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/wlan_tkip.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/wlan_wep.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/wlan_wep.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/wlan_xauth.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/net80211/wlan_xauth.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-22-generic'
make -C ./tools all || exit 1
make[1]: Entering directory `/home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/tools/ath_info'
gcc -g -O2 -W -Wall -c ath_info.c
gcc -g -O2 -W -Wall  -o ath_info ath_info.o
make[2]: Leaving directory `/home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/tools/ath_info'
gcc -o athstats -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal -I../ath  athstats.c
gcc -o 80211stats -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  80211stats.c
gcc -o athkey -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athkey.c
gcc -o athchans -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athchans.c
gcc -o athctrl -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athctrl.c
gcc -o athdebug -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athdebug.c
gcc -o 80211debug -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  80211debug.c
gcc -o wlanconfig -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  wlanconfig.c
gcc -o wpakey -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  wpakey.c
make[1]: Leaving directory `/home/faktorqm/madwifi-hal-0.10.5.6-r3875-20081105/tools'
faktorqm@the-edge:~/madwifi-hal-0.10.5.6-r3875-20081105$

```

instalamos:

```
sudo make install
```

Ahora levantamos los modulos a memoria:

```
sudo modprobe -a ath_pci wlan_scan_sta
```

Ahora levantamos la interfaz:

```
sudo ifconfig ath0 up
```

y teoricamente ya deberias estar conectado. Ahora, asegurate de que la conexion a la cual te estes conectando ande y etcetcetc.

Ahora lo ultimo, hay que poner el modulo nuevo a /etc/modules para que lo levante cada vez que arranca:

```
echo "ath_pci" | sudo tee -a /etc/modules
```

y ¡¡listo!!

bibliografia consultada:

bug en launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196843](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196843)
ubuntu chile: [http://foros.ubuntu-cl.org/viewtopic.php?p=31909](http://foros.ubuntu-cl.org/viewtopic.php?p=31909)
ubuntu españa: [http://www.ubuntu-es.org/index.php?q=node/83598](http://www.ubuntu-es.org/index.php?q=node/83598)
ubuntu en ingles: [http://ubuntuforums.org/showthread.php?t=766529](http://ubuntuforums.org/showthread.php?t=766529)
lista de chipsets reconocidos por el kernel: [http://kerneltrap.org/mailarchive/madwifi-devel/2008/2/18/890124](http://kerneltrap.org/mailarchive/madwifi-devel/2008/2/18/890124)
OBVIO: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)
[http://snapshots.madwifi.org/special/](http://snapshots.madwifi.org/special/)
blogs: [http://chamangt.wordpress.com/2008/05/08/activar-wireless-atheros-en-ubuntu-con-madwifi/](http://chamangt.wordpress.com/2008/05/08/activar-wireless-atheros-en-ubuntu-con-madwifi/)

21/12/2008: actualizado gracias a principexus

Espero que te haya servido. Salu2!!!!:KS

---

### Post by moonport on 2009-02-10
> **faktorqm said:**
> Primero **deshabilita desde controladores restringidos todo lo que tenga que ver con wifi** y tira en una terminal:

```
lsmod | grep ath
```

eso lo que hace es listar el contenido de todos los modulos cargados en el sistema que contengan la palabra "ath". te va a salir algo parecido a esto: 

```
wlan 207728 1 ath_pci 
ath_pci 101024 0
```

digo parecido x q pueden cambiar los números. 
si esto no te sale, no hay nada que bajar de memoria, segui leyendo.
si esto te sale, entonces los bajamos con:

```
sudo rmmod wlan
sudo rmmod ath_pci
```

y luego:

```
sudo modprobe -r wlan
```
```
sudo modprobe -r ath_pci
```

y no te tiene que tirar ningún cartel de nada. 

Entonces ahora si tenemos los módulos bajados y lo que tenemos que hacer es setearle que no se cargue de vuelta cuando reinicie la pc, tonces editamos un archivo:

```
sudo gedit /etc/default/linux-restricted-modules-common
```

y te aparece:

```
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables the three nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES=""
```

y te tiene que quedar asi: (le agregamos el modulo que no queremos que cargue al final)

```
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables the three nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES="ath_hal"
```

guardamos y salimos. 

Ahora lo mandamos a lista negra de los módulos con:

```
echo "blacklist ath_pci" | sudo tee -a /etc/modprobe.d/blacklist
```

Luego debemos eliminar rastros de la versión vieja:

```
sudo apt-get remove madwifi-tools --purge
```

Nunca esta de mas tener las herramientas de compilacion a mano:

```
sudo apt-get update && sudo aptitude install build-essential gcc binutils autoconf automake
```

Ahora si arrancamos el proceso de instalacion, para esto nos bajamos el driver:

```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
```

descomprimimos:

```
tar xzf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
```

entramos en el directorio:

```
cd madwifi-hal-0.10.5.6-r3835-20080801
```

compilamos (NO hace falta SUDO):

```
make
```

Algo así se ve la compilación, lo compilé para ver si tenia problemas pero compiló bien.

```

faktorqm@the-edge:~$ wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
--22:48:35--  http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
           => `madwifi-hal-0.10.5.6-r3835-20080801.tar.gz'
Resolviendo snapshots.madwifi.org... 217.24.1.134
Conectando a snapshots.madwifi.org|217.24.1.134|:80... conectado.
Petición HTTP enviada, esperando respuesta... 200 OK
Longitud: 4.417.874 (4.2M) [application/x-gzip]

100%[====================================>] 4.417.874     60.83K/s    ETA 00:00

22:49:56 (54.02 KB/s) - `madwifi-hal-0.10.5.6-r3835-20080801.tar.gz' guardado [4417874/4417874]

faktorqm@the-edge:~$ tar xzf madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
faktorqm@the-edge:~$ cd madwifi-hal-0.10.5.6-r3835-20080801
faktorqm@the-edge:~/madwifi-hal-0.10.5.6-r3835-20080801$ make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath_radar.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath_hal_extensions.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/if_ath_pci.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/ath_pci.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/ah_os.o
  HOSTCC  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/uudecode
  UUDECODE /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/i386-elf._hal.o
  UNMANGLE /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/i386-elf.hal.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/ath_hal.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr/amrr.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel/minstrel.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel/ath_rate_minstrel.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe/onoe.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample/sample.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample/ath_rate_sample.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/if_media.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_skb.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_beacon.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_crypto.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_crypto_none.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_input.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_node.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_output.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_power.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_proto.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_scan.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_wireless.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_linux.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_monitor.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_rate.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_acl.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_crypto_ccmp.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_scan_ap.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_scan_sta.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_crypto_tkip.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_crypto_wep.o
  CC [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/ieee80211_xauth.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_wep.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_tkip.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_ccmp.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_acl.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_xauth.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_sta.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_ap.o
  Building modules, stage 2.
  MODPOST 14 modules
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/ath_pci.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath/ath_pci.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/ath_hal.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_hal/ath_hal.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr/ath_rate_amrr.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/amrr/ath_rate_amrr.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel/ath_rate_minstrel.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/minstrel/ath_rate_minstrel.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe/ath_rate_onoe.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/onoe/ath_rate_onoe.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample/ath_rate_sample.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/ath_rate/sample/ath_rate_sample.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_acl.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_acl.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_ccmp.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_ccmp.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_ap.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_ap.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_sta.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_scan_sta.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_tkip.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_tkip.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_wep.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_wep.ko
  CC      /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_xauth.mod.o
  LD [M]  /home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/net80211/wlan_xauth.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make -C ./tools all || exit 1
make[1]: Entering directory `/home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/tools'
for d in ath_info; do \
		make -C $d || exit 1; \
	done
make[2]: Entering directory `/home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
gcc -g -O2 -W -Wall -c ath_info.c
gcc -g -O2 -W -Wall  -o ath_info ath_info.o
make[2]: Leaving directory `/home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/tools/ath_info'
gcc -o athstats -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal -I../ath  athstats.c
gcc -o 80211stats -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  80211stats.c
gcc -o athkey -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athkey.c
gcc -o athchans -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athchans.c
gcc -o athctrl -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athctrl.c
gcc -o athdebug -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  athdebug.c
gcc -o 80211debug -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  80211debug.c
gcc -o wlanconfig -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  wlanconfig.c
gcc -o wpakey -g -O2 -Wall -I. -I../hal -I.. -I../ath_hal  wpakey.c
make[1]: Leaving directory `/home/faktorqm/madwifi-hal-0.10.5.6-r3835-20080801/tools'
faktorqm@the-edge:~/madwifi-hal-0.10.5.6-r3835-20080801$ 

```

instalamos:

```
sudo make install
```

Ahora levantamos los modulos a memoria:

```
sudo modprobe -a ath_pci wlan_scan_sta
```

Ahora levantamos la interfaz:

```
sudo ifconfig ath0 up
```

y teoricamente ya deberias estar conectado. Ahora, asegurate de que la conexion a la cual te estes conectando ande y etcetcetc.

Ahora lo ultimo, hay que poner el modulo nuevo a /etc/modules para que lo levante cada vez que arranca:

```
echo "ath_pci" | sudo tee -a /etc/modules
```

y ¡¡listo!!

bibliografia consultada:

bug en launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196843](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/196843)
ubuntu chile: [http://foros.ubuntu-cl.org/viewtopic.php?p=31909](http://foros.ubuntu-cl.org/viewtopic.php?p=31909)
ubuntu españa: [http://www.ubuntu-es.org/index.php?q=node/83598](http://www.ubuntu-es.org/index.php?q=node/83598)
ubuntu en ingles: [http://ubuntuforums.org/showthread.php?t=766529](http://ubuntuforums.org/showthread.php?t=766529)
lista de chipsets reconocidos por el kernel: [http://kerneltrap.org/mailarchive/madwifi-devel/2008/2/18/890124](http://kerneltrap.org/mailarchive/madwifi-devel/2008/2/18/890124)
OBVIO: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)
[http://snapshots.madwifi.org/special/](http://snapshots.madwifi.org/special/)
blogs: [http://chamangt.wordpress.com/2008/05/08/activar-wireless-atheros-en-ubuntu-con-madwifi/](http://chamangt.wordpress.com/2008/05/08/activar-wireless-atheros-en-ubuntu-con-madwifi/)

Espero que te haya servido. Salu2!!!!:KS

Tenía el problema con el *Atheros* en mi notebook **Compaq**. Llevaba tiempo sin poder solucionarlo.
Seguí los pasos de tu artículo y todo salió andando perfectamente.
Muchas gracias por la ayuda. 
Slds.

---

### Post by tony#17 on 2009-12-15
que tal faktorqm, tengo un problema, sigo todos los pasos al pie de la letra, pero en este paso:
> Ahora levantamos la interfaz:

```
sudo ifconfig ath0 up
```me sale este error:
```
tony@tony-laptop:~$ sudo ifconfig ath0 up
ath0: ERROR mientras se obtenían las banderas de interfaz: No existe el dispositivo
```porque puede ser? si antes no me dio ningun tipo de error?

desde ya gracias por su ayuda

---

### Post by luks911 on 2009-12-15
Si seguiste los pasos de este tutorial, entonces tenés que haber recibido algún error. ¿Por qué? Porque la orden para bajar el driver
```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz

```
Apunta a un archivo que ya no existe. Así que se genera un archivo pero que nisiquiera podés descomprimir. Ahora la orden es ```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
```

Del mismo modo, hay que hacer algunos cambios en las órdenes posteriores.
Para descomprimir es
```
tar xzf madwifi-hal-0.10.5.6-current.tar.gz
```

Y para entrar a la carpeta que se genero es
```
cd madwifi-hal-0.10.5.6-r4100-20090929
```

Lo que sigue, desde el make, queda igual.

---

### Post by tony#17 on 2009-12-16
> **luks911 said:**
> Si seguiste los pasos de este tutorial, entonces tenés que haber recibido algún error. ¿Por qué? Porque la orden para bajar el driver
```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz

```Apunta a un archivo que ya no existe. Así que se genera un archivo pero que nisiquiera podés descomprimir. Ahora la orden es ```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
```Del mismo modo, hay que hacer algunos cambios en las órdenes posteriores.
Para descomprimir es
```
tar xzf madwifi-hal-0.10.5.6-current.tar.gz
```Y para entrar a la carpeta que se genero es
```
cd madwifi-hal-0.10.5.6-r4100-20090929
```Lo que sigue, desde el make, queda igual.

si, se me habia olvidado decir que habia cambiado la direccion:
```
wget http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3835-20080801.tar.gz

```por esta (si no me equivoco):
```
wget http://snapshots.madwifi-project.org/madwifi-0.9.4-current.tar.gz
```y me daba este error:
```
tony@tony-laptop:~$ sudo ifconfig ath0 up
ath0: ERROR mientras se obtenían las banderas de interfaz: No existe el dispositivo
```ahora probe con esta:
```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
```y va de maravilla:P sin ningun error ni nada parecido

gracias por su ayuda

---

### Post by luks911 on 2009-12-16
Claro, es que la versión 0.9.4, que es la que viene con Ubuntu, no soporta esta placa. Sí lo hace la otra, que instalaste.
Genial

---

