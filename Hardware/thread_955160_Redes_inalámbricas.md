---
title: "Redes inalámbricas"
date: 2008-10-21
forum: Hardware
---

### Post by losoollenos on 2008-10-21
Hola que tal, yo acá de nuevo tratando de desaznarme un poco. Entusiasmado con Ubuntu se lo instalo en la compu de los chicos pero no logro conectarla a internet. Tiene una placa inalámbrica Encore y no me aparece en configuración de la red "conexiones inalámbricas", ni por ningún lado, supongo que no estará detectando la placa?, que tendría que hacer?

Muchas gracias y saludos

---

### Post by luks911 on 2008-10-22
Hola,
Si la placa es pci, ejecutá lspci en una terminal, si es usb, ejecutá lsusb, y pegá el resultado acá. Eso te va a devolver los componentes, pci o usb, conectados. Así vamos a saber qué placa es y podemos buscar info sobre cómo hacerla funcionar.

Saludos

---

### Post by losoollenos on 2008-10-22
Gracias luks911. Bueno la placa es pci, al ejecutar en la terminal probe con 1spci y Ispci (o sea 1 e i antes de spci, disculpa pero no se cual es la que va), en los dos casos me devolvio "orden no encontrada". Otra cosa que note es que al cerrar el sistema sale una pantalla negra que dice algo del "network manager", toda una pantalla como que chequea, pero pasa medio rapido y no lo pude frenar para ver algun detalle.

Saludos y gracias !!!!

---

### Post by lega on 2008-10-22
Hola, la orden que te pide lucas es con L lspci
Saludos

---

### Post by valucha on 2008-10-22
> **losoollenos said:**
> Gracias luks911. Bueno la placa es pci, al ejecutar en la terminal probe con 1spci y Ispci (o sea 1 e i antes de spci, disculpa pero no se cual es la que va), en los dos casos me devolvio "orden no encontrada". Otra cosa que note es que al cerrar el sistema sale una pantalla negra que dice algo del "network manager", toda una pantalla como que chequea, pero pasa medio rapido y no lo pude frenar para ver algun detalle.

Saludos y gracias !!!!
[COLOR="DarkOrchid"]Jajaja es Lpci, a mi también me pasa, cuando tengas duda, más fácil copialo y pegalo en la consola...
Para pegar en la consola es shift+ctrl+v al mismo tiempo.

Saludos.
[/COLOR]

---

### Post by chalito on 2008-10-22
Ojo con los typos! :)


El comando es "LSPCI" en minúsculas (lspci), y viene de "[COLOR="Teal"]L[/COLOR]i[COLOR="Teal"]s[/COLOR]t [COLOR="Teal"]PCI[/COLOR]"

---

### Post by santiagoward2000 on 2008-10-22
> **valucha said:**
> [COLOR="DarkOrchid"]Jajaja es Lpci, a mi también me pasa, cuando tengas duda, más fácil copialo y pegalo en la consola...
Para pegar en la consola es shift+ctrl+v al mismo tiempo.

Saludos.
[/COLOR]

[COLOR="DarkOrchid"]...o seleccionando lo que querés copiar a haciendo click con la ruedita en la consola.[/COLOR] (si Valu! Te plagié el color!)

---

### Post by losoollenos on 2008-10-22
Ahora sí, no se me había ocurrido la L. Bueno me tiró esto:

ubuntu@ubuntu-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 655 Host (rev 50)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)
ubuntu@ubuntu-desktop:~$ 

Creo que la tomó no?

Gracias y saludos

---

### Post by luks911 on 2008-10-22
> **losoollenos said:**
> Ahora sí, no se me había ocurrido la L. Bueno me tiró esto:

ubuntu@ubuntu-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 655 Host (rev 50)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 4000] (rev c1)
ubuntu@ubuntu-desktop:~$ 

Creo que la tomó no?

Gracias y saludos

Luego de la confusión :lolflag: te digo que no sos el único con la misma palca. [Acá [0]]("http://ubuntuforums.org/showthread.php?t=882266") cuentan que la hicieron funcionar usando ndiswrapper y los drivers de win. Nunca usé dnsiwrapper, pero parece fácil y hay una explicación en la [Guía Ubuntu [1]]("http://www.guia-ubuntu.org/index.php?title=Instalar_driver_de_tarjetas_WIFI_con_Ndiswrapper") y hasta hay un frontend si querés evitar la terminal (aunque no muerde) que está en los repositorios: ndisgtk.

Un saludo y espero que sirva


[0] [http://ubuntuforums.org/showthread.php?t=882266](http://ubuntuforums.org/showthread.php?t=882266)
[1] [http://www.guia-ubuntu.org/index.php?title=Instalar_driver_de_tarjetas_WIFI_con_Ndiswrapper](http://www.guia-ubuntu.org/index.php?title=Instalar_driver_de_tarjetas_WIFI_con_Ndiswrapper)

---

### Post by losoollenos on 2008-10-22
Mañana lo pruebo. Es verdad, hay bastante de este problema ya en el foro, lo que pasa es que recién me enteré de la placa que tengo, yo pensaba que era Encore.....después aviso.

Saludos y muchas gracias

---

### Post by luks911 on 2008-10-22
> **losoollenos said:**
> Mañana lo pruebo. Es verdad, hay bastante de este problema ya en el foro, lo que pasa es que recién me enteré de la placa que tengo, yo pensaba que era Encore.....después aviso.

Saludos y muchas gracias

Sí, por suerte la comunidad es grande y casi siempre se encuentra algo sobre el problema propio. Y si no es sobre Ubuntu es sobre otra distro. En el poco tiempo que llevo en Linux voy viendo lo importante de los comandos para conocer exactamente cuál es el hardware, sobre todo en estos casos.

Buscando un poco más encontré que Realtek tiene un driver para linux. Si lo querés probar, podés bajarlo de [este link]("ftp://66.104.77.130/cn/wlan/rtl8185_linux_26%5B1%5D.1027.0823.2007.tar.gz")[0]. Para instalarlo, si no entendí mal el readme, tenés que 
1) descomprimir el archivo donde quieras (con click derecho y extraer aquí)
2) en una terminal ir hasta la carpeta generada al descomprimir, por ejemplo
```
cd /home/tu_usuario/driver_wifi/rtl8185_linux_26.1027.0823.2007
```
3) ejecutar el script para compilar 
```
./makedrv
```
4) ejecutar el script para cargar el módulo
```
./wlan0up
```
si en este punto aparece un error que dice "insmod: error inserting 'r8180.ko': -File exists.", entonces tenés que ejecutar
```
./wlan0rmv
./wlan0down
./wlan0up

```
Supongo que después habría que poner el script que carga el módulo para que se ejecute al inicio, o sea en el archivo rc.local. Pero no estoy seguro.

Saludos y cualquier cosa preguntá

[0] [ftp://66.104.77.130/cn/wlan/rtl8185_linux_26%5B1%5D.1027.0823.2007.tar.gz](ftp://66.104.77.130/cn/wlan/rtl8185_linux_26%5B1%5D.1027.0823.2007.tar.gz)

---

### Post by losoollenos on 2008-10-22
Buenísimo, no me gustaba mucho la idea de tener que adaptar drivers de windows.....por suerte todavía no había empezado. Espero poder interpretar bien lo que me decís luks911, apenas pueda les comento....

Saludos y muchas gracias

---

### Post by adrian47153 on 2008-10-23
# esto es para una Notebook COMPAQ Presario F756LA con UBUNTU 8.04 de 32 bits QUE VINO con window$ vista y le SAQUE TODO
# pone el CD de ubuntu 8.04 y instala en TODO EL DISCO 
# [email]adrian47153@gmail.com[/email]
# UBUNTU8.04 usuario:41502366
# Para hacer funcionar la "WiFi" en ubuntu 8.04 32bits hice esto
Ve a Sistema, Administracion y da clic en controladores de hardware.
Vas a ver 2 controladores de Atheros, da clic en cada uno de ellos para deshabilitarlos.
Debes deshabilitar:
"Atheros Hardware Access Layer (HAL)"
"Support for Atheros 802.11 wireless LAN cards"

Reinicia tu computadora 

En el escritorio: Ir a "Aplicaciones", "Accesorios", "Terminal" enter
...en la terminal escribir:
$ sudo apt-get install linux-headers-$(uname -r) build-essential enter
$ sudo aptitude install checkinstall enter

despues escribir:

$ ls # para ver donde estoy, hago todo en mi /home/adrian 
copiar el driver de MADWIFI, yo lo tengo en mi pendrive

$ cp /media/disk/FLOPPY1/LINUX32/madwifi-hal-0.10.5.6-r3698-20080604.tar.gz /home/adrian/ enter

$ ls #para ver que copio el archivo y descomprimilo con "tar" ponele xzvf y el nombre del archivo && cd nombre del archivo y enter

$ tar  xzvf madwifi-hal-0.10.5.6-r3698-20080604.tar.gz && cd madwifi-hal-0.10.5.6-r3698-20080604 enter 
# te crea una carpeta y te pone dentro de ella

ó sino descargan de ACA:
# [http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz)
cd madwifi-hal-0.10.5.6-r3698-20080604 enter

# esto es para una Notebook COMPAQ Presario F756LA con UBUNTU 8.04 de 32 bits ¡OJO!

una ves hay, compilar el drive

$ make clean # limpiar anteriores compilaciones
$ make enter # para compilar
...si todo esta bien instala con sudo y checkinstall
$ sudo checkinstall enter # para chequear y si esta bien lo instala sin problemas

Cuando termines de instalar vuelve a habilitar los 2 controladores de atheros
reinicia tu computadora.

$ sudo gedit /etc/modules enter # editamos y escribimos:
			 "ath_pci" y despues:
$ Ctrl+S para grabar y Ctrl+Q para salir
# esto es para que se detecte la tarjeta al arrancar la Notebook o PC

Luego activamos la tarjeta
# sudo ifconfig ath0 up enter
# iwlist ath0 scan enter
# tenemos que sacar network-manager
sudo aptitude remove network-manager # para sacarlo
sudo aptitude install wicd # usar wicd para detectar las redes inalambricas
sudo reboot # para reiniciar la Notebook o PC

En el Escritorio doble clic en el icono de redes y debe de detectar las redes inalambricas con WICD.
# Suerte disfrutar ubuntu 8.04 con el WiFi activador :) COMO UNICO Sistema Operativo ;):d
# esto es para una Notebook COMPAQ Presario F756LA con UBUNTU 8.04 de 32 bits ¡VIVE LIBRE!
# ubuntu user: adrian47153 Nro:41502366 ESTO LO PONGO EN ubuntu-es.org y en ubuntu-ar.org

---

### Post by losoollenos on 2008-10-23
Gracias Adrian, parece más complicado........me asusta un poquito.
Luks911, por favor orientame como es para una conexión con clave wpa. Ahi en el readme lo explica, pero en inglés....

Muchas gracias

---

### Post by luks911 on 2008-10-24
> **losoollenos said:**
> Gracias Adrian, parece más complicado........me asusta un poquito.
Luks911, por favor orientame como es para una conexión con clave wpa. Ahi en el readme lo explica, pero en inglés....

Muchas gracias

Por lo que entiendo, el driver acepta los comandos corrientes para conectarse. Así que no deberías tener problemas en conectarte ya sea por consola o, más "normal", con el network manager o similar, como el WICD. 
Para manejar claves WPA, el readme habla de instalar wpasupplicant. Pero no hace falta compilarlo como dice ahí. Está en los repositorios, así que fijate en el synaptics si lo tenés instalado y si no lo tenés, lo instalás desde ahí o por terminal con

```
sudo apt-get install wpasupplicant
```

Eso debería ser todo. Cualquier cosa avisa.

PD: Todo bien con lo que posteó Adrián, pero no tiene nada que ver con lo que necesitás. Son instrucciones para otra placa que ya se publicaron un par de veces en el foro. En fin.

---

### Post by losoollenos on 2008-10-25
Por favor Luks911, indicame cómo sería la ruta para llegar al archivo, lo descomprimí en el escritorio. Lo único que obtuve probando varias formas fueron "orden no encontrada" y "no existe el fichero o directorio", mi usuario (el que escribo cuando inicia el sistema no?) es "ubuntu".

Te agradezco mucho

---

### Post by luks911 on 2008-10-25
Por lo que decís, la ruta sería 
```
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007
```

Ante la duda, entrá a la carpeta que descomprimiste con el nautilus y en la barra de direcciones vas a tener la ruta.

Saludos

---

### Post by luks911 on 2008-10-25
Y encontré algo que además de lo que ya sabía incluye cómo cargar los módulos en el inicio. Mirpa este link ([http://www.j0hnd0e.com.ar/?p=31](http://www.j0hnd0e.com.ar/?p=31)) desde el punto 6.

Saludos

---

### Post by losoollenos on 2008-10-25
Bueno, no pude avanzar mucho. Ya en el comando ./makedrv salieron un monton de errores, pego todo:

ubuntu@ubuntu-desktop:~$ cd /home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007
ubuntu@ubuntu-desktop:~/Escritorio/rtl8185_linux_26.1027.0823.2007$ ./makedrv
./ieee80211/
./ieee80211/ieee80211_module.c
./ieee80211/ieee80211_rx.c
./ieee80211/tags
./ieee80211/Makefile
./ieee80211/ieee80211_crypt_tkip.c
./ieee80211/ieee80211_softmac.c
./ieee80211/readme
./ieee80211/ieee80211_crypt_ccmp.c
./ieee80211/ieee80211.h
./ieee80211/ieee80211_tx.c
./ieee80211/ieee80211_softmac_wx.c
./ieee80211/ieee80211_crypt.h
./ieee80211/ieee80211_wx.c
./ieee80211/license
./ieee80211/ieee80211_crypt_wep.c
./ieee80211/ieee80211_crypt.c
rtl8185/
rtl8185/README.adhoc
rtl8185/r8180_sa2400.h
rtl8185/Makefile
rtl8185/copying
rtl8185/README.master
rtl8185/r8180.h
rtl8185/install
rtl8185/r8180_max2820.h
rtl8185/r8180_max2820.c
rtl8185/r8180_rtl8225.h
rtl8185/r8180_wx.h
rtl8185/authors
rtl8185/tags
rtl8185/r8180_pm.c
rtl8185/r8180_hw.h
rtl8185/r8180_gct.c
rtl8185/r8180_gct.h
rtl8185/r8180_rtl8225.c
rtl8185/readme
rtl8185/r8180_93cx6.h
rtl8185/ieee80211.h
rtl8185/license
rtl8185/r8180_pm.h
rtl8185/changes
rtl8185/r8180_rtl8225z2.c
rtl8185/r8180_wx.c
rtl8185/r8180_rtl8255.c
rtl8185/r8180_93cx6.c
rtl8185/r8180_sa2400.c
rtl8185/r8180_core.c
rtl8185/r8180_rtl8255.h
rtl8185/ieee80211_crypt.h
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/tmp
make -C /lib/modules/2.6.24-19-generic/build M=/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211 CC=gcc modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.o
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c: En la función ‘ieee80211_softmac_init’:
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2236: aviso: asignación desde un tipo de puntero incompatible
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2237: aviso: asignación desde un tipo de puntero incompatible
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2238: aviso: asignación desde un tipo de puntero incompatible
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2239: aviso: asignación desde un tipo de puntero incompatible
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2240: aviso: asignación desde un tipo de puntero incompatible
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac.c:2241: aviso: asignación desde un tipo de puntero incompatible
  CC [M]  /home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_rx.o
  CC [M]  /home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_tx.o
  CC [M]  /home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_wx.o
  CC [M]  /home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_module.o
  CC [M]  /home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt.o
  CC [M]  /home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.o
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c: En la función ‘ieee80211_ccmp_aes_encrypt’:
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:88: aviso: se pasa el argumento 1 de ‘crypto_cipher_encrypt_one’ desde un tipo de puntero incompatible
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c: En la función ‘ieee80211_ccmp_init’:
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:110: aviso: asignación desde un tipo de puntero incompatible
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:127: aviso: se pasa el argumento 1 de ‘crypto_free_cipher’ desde un tipo de puntero incompatible
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c: En la función ‘ieee80211_ccmp_deinit’:
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:144: aviso: se pasa el argumento 1 de ‘crypto_free_cipher’ desde un tipo de puntero incompatible
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c: En la función ‘ieee80211_ccmp_set_key’:
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_ccmp.c:422: aviso: se pasa el argumento 1 de ‘crypto_cipher_setkey’ desde un tipo de puntero incompatible
  CC [M]  /home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.o
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c: En la función ‘ieee80211_tkip_encrypt’:
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c:417: error: ‘struct scatterlist’ no tiene un miembro llamado ‘page’
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c: En la función ‘ieee80211_tkip_decrypt’:
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c:511: error: ‘struct scatterlist’ no tiene un miembro llamado ‘page’
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c: En la función ‘michael_mic’:
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c:613: error: ‘struct scatterlist’ no tiene un miembro llamado ‘page’
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.c:617: error: ‘struct scatterlist’ no tiene un miembro llamado ‘page’
make[2]: *** [/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211/ieee80211_crypt_tkip.o] Error 1
make[1]: *** [_module_/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/ieee80211] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
rm -f *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf /home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/rtl8185/tmp
make -C /lib/modules/2.6.24-19-generic/build M=/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/rtl8185 CC=gcc modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.o
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c: En la función ‘rtl8180_proc_module_init’:
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:588: error: ‘proc_net’ no se declaró aquí (primer uso en esta función)
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:588: error: (Cada identificador no declarado solamente se reporta una vez
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:588: error: para cada funcion en la que aparece.)
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c: En la función ‘rtl8180_proc_module_remove’:
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:594: error: ‘proc_net’ no se declaró aquí (primer uso en esta función)
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c: En la función ‘rtl8180_init’:
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:3159: aviso: asignación desde un tipo de puntero incompatible
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:3522: error: ‘SA_SHIRQ’ no se declaró aquí (primer uso en esta función)
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:3522: aviso: se pasa el argumento 2 de ‘request_irq’ desde un tipo de puntero incompatible
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c: En la función ‘rtl8180_pci_probe’:
/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.c:4213: error: declaración implícita de la función ‘SET_MODULE_OWNER’
make[2]: *** [/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/rtl8185/r8180_core.o] Error 1
make[1]: *** [_module_/home/ubuntu/Escritorio/rtl8185_linux_26.1027.0823.2007/rtl8185] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
ubuntu@ubuntu-desktop:~/Escritorio/rtl8185_linux_26.1027.0823.2007$ 


No me aflojes por favor....

---

### Post by luks911 on 2008-10-25
No estoy seguro, pero mientras sigo buscando, probá con esto

```
sudo apt-get install linux-headers-$(uname -r) build-essential
```

Es decir, instalar los paquetes necesarios para compilar. Me parece que te falta eso. Después volvé a probar con los pasos para la placa.

Saludos

Edito: seguí leyendo un poquito más por ahí y estoy nás seguro que antes :-P de que el problema es el que te decía, je. Vos dirás.

---

### Post by losoollenos on 2008-10-25
luks911 lo hice y me tiró esto:


ubuntu@ubuntu-desktop:~$ sudo apt-get install linux-headers-$(uname -r) build-essential
[sudo] password for ubuntu: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
linux-headers-2.6.24-19-generic ya está en su versión más reciente.
fijado linux-headers-2.6.24-19-generic como instalado manualmente.
El paquete build-essential no está disponible, pero algún otro paquete hace referencia
a él. Esto puede significar que el paquete falta, está obsoleto o sólo se
encuentra disponible desde alguna otra fuente
E: El paquete build-essential no tiene candidato para su instalación

Igual por las dudas intenté con el ./makedrv pero me contestó exactamente lo mísmo...

---

### Post by Hei Ku on 2008-10-25
Tenes algo muy mal, porque el build-essential es basico de la instalacion. Si no lo podes instalar es muy raro.

Postea tu /etc/apt/sources.list

---

### Post by losoollenos on 2008-10-25
Gracias Hei Ku:

ubuntu@ubuntu-desktop:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permiso denegado
ubuntu@ubuntu-desktop:~$

Saludos

---

### Post by luks911 on 2008-10-25
Lo que te pide Hei Ku es que nos muestres el contenido del sources.list. Ejecutá en una terminal

```
cat /etc/apt/sources.list
```

y copia y pegá acá todo lo que te devuelve.

---

### Post by losoollenos on 2008-10-25
Acá está:

ubuntu@ubuntu-desktop:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
ubuntu@ubuntu-desktop:~$ 

Miércole, si me dejan acá es cómo si me hubieran largado en la Luna.....ja ja ja !!!!

---

### Post by luks911 on 2008-10-25
Lo que veo son un par de diferencias con respecto al mí sources.list que tal vez ayuden. Vamos a probar: edita el archivo

```
sudo gedit /etc/apt/sources.list
```

y borrale el signo numeral (#) a las siguientes líneas
```

# deb http://ar.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://ar.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner
```

Lo guardás y después recargá los repositorios

```
sudo apt-get update
```

Y volvés a probar de instalar

```
sudo apt-get install build-essential
```

También fijate, antes de todo esto si querés, si en synaptic aparece el paquete build-essenntial. 

Capaz que Hei Ku tiene alguna otra idea.

Y trataremos de no dejarte en la Luna. :lolflag:

---

### Post by losoollenos on 2008-10-25
Bueno ya quité los # de las cuatro línea, pero para recargar los repositores tiene que estar con internet la máquina?, porque la tendría que llevar a donde conecto la mía, es en mi casa igual no hay drama, pero la de los chicos se conecta sólo por wireless.
Te digo esto porque la máquina está con el sistema tal cual quedó instalado, sin ninguna actualización ni nada (nunca se conectó) y por ahí tenga algo que ver con estas cosas que estarían faltando.....??

Saludos

---

### Post by luks911 on 2008-10-25
> **losoollenos said:**
> Bueno ya quité los # de las cuatro línea, pero para recargar los repositores tiene que estar con internet la máquina?, porque la tendría que llevar a donde conecto la mía, es en mi casa igual no hay drama, pero la de los chicos se conecta sólo por wireless.
Te digo esto porque la máquina está con el sistema tal cual quedó instalado, sin ninguna actualización ni nada (nunca se conectó) y por ahí tenga algo que ver con estas cosas que estarían faltando.....??

Saludos

Pero claro, ese es el problema, que no está conectada a internet. Para instalar build-essential necesita estar conectada. De hecho te van a aparecer unas cuantas actualizaciones. Ya me parecía cuando vi que todavía tenías la versión del kernel anterior, aunque se actualizó hace un par de días.
Yo creía que era la misma máquina desde la que posteabas y demás, jaja...
Eso pasa porque a veces se dan por entendidas cosas que no lo están. Es gracioso, en serio. En fin, no hay drama....
Conectala, instalá las actualizaciones que te pida, instalá build-essential y dale otra oportunidad al driver del wifi. A ver qué pasa.

EDITO: Como novato que soy me doy cuenta ahora de que hay una forma de hacerlo sin internet, aunque ese es el problema que tenías. Para eso necesitás tener sí un CD de Ubuntu 8.04. Abrís Synaptic vas a Configuración > Repositorios, y abajo de todo, en un recuadro, tiene que aparecer una casilla para marcar la opción "CD-ROM con Ubuntu 8.04", la marcás. Ponés tu CD en la lectora, cerrás el cuadro de diálogo y te va a pedir que recargues los repositorios, le das al botón "recargar", y cuando termina deberías poder instalar el build-essential desde el disco.

---

### Post by losoollenos on 2008-10-25
Y yo creí que estaba claro......bueno, igualmente ya había empezado a actualizar, son 173 en total, hasta ahora.
Por supuesto, los mantengo al tanto !!!

Saludos

---

### Post by losoollenos on 2008-10-25
Bueno ya actualizado el sistema, instalado build-essential (aunque en sinaptic no aparece), vuelvo con ./makedrv y obtengo el mísmo resultado de hoy.......un garrón, aparecen los mismos errores que ya copié más arriba en este punto.
Les paso esto para ver por dónde seguimos:

ubuntu@ubuntu-desktop:~$ sudo apt-get install linux-headers-$(uname -r) build-essential
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
linux-headers-2.6.24-21-generic ya está en su versión más reciente.
build-essential ya está en su versión más reciente.
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
ubuntu@ubuntu-desktop:~$ 

Muchas gracias

---

### Post by luks911 on 2008-10-25
Bien, qué joder, no nos va a ganar una placa de wifi... jaja

Seguí buscando y encontré un par de cosas. 

1) Como ya notamos, el bendito driver tiene problemas en la compilación con la versión del kernel que usamos en Ubuntu. Lo dice en este [blog]("http://www.willdaniels.co.uk/blog/tech-stuff/1-tech-stuff/1-rtl8185-problems")[0], cuyo autor se ha tomado la molestia de hacer un parche. Para aplicarlo, seguí exactamente los pasos de [este otro blog]("http://www.j0hnd0e.com.ar/?p=31")
[1], que incluye bajar un nuevo archivo con el driver, distinto al que ya tenés y que podés eliminar. Ese debería funciona.

2) Dicen que la placa va a funcionar de una en Intrepid. 

Saludos

[0] [http://www.willdaniels.co.uk/blog/tech-stuff/1-tech-stuff/1-rtl8185-problems](http://www.willdaniels.co.uk/blog/tech-stuff/1-tech-stuff/1-rtl8185-problems)
[1] [http://www.j0hnd0e.com.ar/?p=31](http://www.j0hnd0e.com.ar/?p=31)

---

### Post by losoollenos on 2008-10-26
Buen día luks911. No me funca el enlace a la guía........

Saludos

---

### Post by luks911 on 2008-10-26
> **losoollenos said:**
> Buen día luks911. No me funca el enlace a la guía........

Saludos

:-S A mí sí, te la pego acá abajo

```
   1. Asegurarse de tener las herraminetas de desarrollo necesarias para compilar:

      sudo aptitude install build-essential

   2. Descargar las fuentes del controlador:

      wget http://willdaniels.co.uk/attachments/rtl8185.zip

   3. Extraer los archivos y entrar en el directorio extraído:

      unzip rtl8185.zip
      cd rtl8185

   4. Compilar el controlador (no preocuparse por mensajes de warning, en tanto no haya ningún “fatal error” todo bien):

      ./makedrv

   5. Probar que el módulo cargue sin problemas:

      sudo ./wlan0up

   6. Si todo está funcionando, copiar los módulos compilados a una ubicación más conveniente:

      sudo cp rtl8185/*.ko /lib/modules/`uname -r`/kernel/net/wireless
      sudo cp ieee80211/*.ko /lib/modules/`uname -r`/kernel/net/wireless

   7. Actualizar las dependencias de los módulos:

      sudo depmod -a

Hay un paso final, para asegurarse que el módulo se cargue al momento del boot.

sudo -i
echo ieee80211_crypt_rtl >> /etc/modules
echo ieee80211_crypt_wep_rtl >> /etc/modules
echo ieee80211_crypt_tkip_rtl >> /etc/modules
echo ieee80211_crypt_ccmp_rtl >> /etc/modules
echo ieee80211_rtl >> /etc/modules
echo r8180 >> /etc/modules
exit

```

---

### Post by losoollenos on 2008-10-26
Salió esto:

ubuntu@ubuntu-desktop:~$ cd /home/ubuntu/Escritorio/rtl8185--------------------------------------1)
ubuntu@ubuntu-desktop:~/Escritorio/rtl8185$ ./makedrv
./ieee80211/
./ieee80211/ieee80211_module.c
./ieee80211/ieee80211_rx.c
./ieee80211/tags
./ieee80211/Makefile
./ieee80211/ieee80211_crypt_tkip.c
./ieee80211/ieee80211_softmac.c
./ieee80211/readme
./ieee80211/ieee80211_crypt_ccmp.c
./ieee80211/ieee80211.h
./ieee80211/ieee80211_tx.c
./ieee80211/ieee80211_softmac_wx.c
./ieee80211/ieee80211_crypt.h
./ieee80211/ieee80211_wx.c
./ieee80211/license
./ieee80211/ieee80211_crypt_wep.c
./ieee80211/ieee80211_crypt.c
rtl8185/
rtl8185/README.adhoc
rtl8185/r8180_sa2400.h
rtl8185/Makefile
rtl8185/copying
rtl8185/README.master
rtl8185/r8180.h
rtl8185/install
rtl8185/r8180_max2820.h
rtl8185/r8180_max2820.c
rtl8185/r8180_rtl8225.h
rtl8185/r8180_wx.h
rtl8185/authors
rtl8185/tags
rtl8185/r8180_pm.c
rtl8185/r8180_hw.h
rtl8185/r8180_gct.c
rtl8185/r8180_gct.h
rtl8185/r8180_rtl8225.c
rtl8185/readme
rtl8185/r8180_93cx6.h
rtl8185/ieee80211.h
rtl8185/license
rtl8185/r8180_pm.h
rtl8185/changes
rtl8185/r8180_rtl8225z2.c
rtl8185/r8180_wx.c
rtl8185/r8180_rtl8255.c
rtl8185/r8180_93cx6.c
rtl8185/r8180_sa2400.c
rtl8185/r8180_core.c
rtl8185/r8180_rtl8255.h
rtl8185/ieee80211_crypt.h
patching file ieee80211/ieee80211_crypt_tkip.c
patching file ieee80211/ieee80211_crypt_wep.c
patching file rtl8185/r8180_core.c
rm -f *.mod.c *.mod *.o .*.cmd *.ko 
rm -rf /home/ubuntu/Escritorio/rtl8185/ieee80211/tmp
make -C /lib/modules/2.6.24-21-generic/build M=/home/ubuntu/Escritorio/rtl8185/ieee80211 CC=gcc modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-21-generic'
  CC [M]  /home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_softmac.o
/home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_softmac.c: En la función ‘ieee80211_softmac_init’:
/home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_softmac.c:2236: aviso: asignación desde un tipo de puntero incompatible
/home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_softmac.c:2237: aviso: asignación desde un tipo de puntero incompatible
/home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_softmac.c:2238: aviso: asignación desde un tipo de puntero incompatible
/home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_softmac.c:2239: aviso: asignación desde un tipo de puntero incompatible
/home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_softmac.c:2240: aviso: asignación desde un tipo de puntero incompatible
/home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_softmac.c:2241: aviso: asignación desde un tipo de puntero incompatible
  CC [M]  /home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_rx.o
  CC [M]  /home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_tx.o
  CC [M]  /home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_wx.o
  CC [M]  /home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_module.o
  CC [M]  /home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_crypt.o
  CC [M]  /home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_crypt_ccmp.o
/home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_crypt_ccmp.c: En la función ‘ieee80211_ccmp_aes_encrypt’:
/home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_crypt_ccmp.c:88: aviso: se pasa el argumento 1 de ‘crypto_cipher_encrypt_one’ desde un tipo de puntero incompatible
/home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_crypt_ccmp.c: En la función ‘ieee80211_ccmp_init’:
/home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_crypt_ccmp.c:110: aviso: asignación desde un tipo de puntero incompatible
/home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_crypt_ccmp.c:127: aviso: se pasa el argumento 1 de ‘crypto_free_cipher’ desde un tipo de puntero incompatible
/home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_crypt_ccmp.c: En la función ‘ieee80211_ccmp_deinit’:
/home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_crypt_ccmp.c:144: aviso: se pasa el argumento 1 de ‘crypto_free_cipher’ desde un tipo de puntero incompatible
/home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_crypt_ccmp.c: En la función ‘ieee80211_ccmp_set_key’:
/home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_crypt_ccmp.c:422: aviso: se pasa el argumento 1 de ‘crypto_cipher_setkey’ desde un tipo de puntero incompatible
  CC [M]  /home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211-rtl.o
  LD [M]  /home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_crypt-rtl.o
  LD [M]  /home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_crypt_wep-rtl.o
  LD [M]  /home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_crypt_tkip-rtl.o
  LD [M]  /home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_crypt_ccmp-rtl.o
  Building modules, stage 2.
  MODPOST 5 modules
  CC      /home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211-rtl.mod.o
  LD [M]  /home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211-rtl.ko
  CC      /home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_crypt-rtl.mod.o
  LD [M]  /home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_crypt-rtl.ko
  CC      /home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_crypt_ccmp-rtl.mod.o
  LD [M]  /home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_crypt_ccmp-rtl.ko
  CC      /home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_crypt_tkip-rtl.mod.o
  LD [M]  /home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_crypt_tkip-rtl.ko
  CC      /home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_crypt_wep-rtl.mod.o
  LD [M]  /home/ubuntu/Escritorio/rtl8185/ieee80211/ieee80211_crypt_wep-rtl.ko
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.24-21-generic'
rm -f *.mod.c *.mod *.o .*.cmd *.ko *~
rm -rf /home/ubuntu/Escritorio/rtl8185/rtl8185/tmp
make -C /lib/modules/2.6.24-21-generic/build M=/home/ubuntu/Escritorio/rtl8185/rtl8185 CC=gcc modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-21-generic'
  CC [M]  /home/ubuntu/Escritorio/rtl8185/rtl8185/r8180_core.o
/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180_core.c: En la función ‘rtl8180_init’:
/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180_core.c:3167: aviso: asignación desde un tipo de puntero incompatible
/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180_core.c:3534: aviso: se pasa el argumento 2 de ‘request_irq’ desde un tipo de puntero incompatible
/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180_core.c: En el nivel principal:
/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180_core.c:579: aviso: se definió ‘r8180_get_wireless_stats’ pero no se usa
  CC [M]  /home/ubuntu/Escritorio/rtl8185/rtl8185/r8180_sa2400.o
  CC [M]  /home/ubuntu/Escritorio/rtl8185/rtl8185/r8180_93cx6.o
  CC [M]  /home/ubuntu/Escritorio/rtl8185/rtl8185/r8180_wx.o
  CC [M]  /home/ubuntu/Escritorio/rtl8185/rtl8185/r8180_max2820.o
  CC [M]  /home/ubuntu/Escritorio/rtl8185/rtl8185/r8180_gct.o
  CC [M]  /home/ubuntu/Escritorio/rtl8185/rtl8185/r8180_rtl8225.o
  CC [M]  /home/ubuntu/Escritorio/rtl8185/rtl8185/r8180_rtl8225z2.o
  CC [M]  /home/ubuntu/Escritorio/rtl8185/rtl8185/r8180_rtl8255.o
  LD [M]  /home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "ieee80211_softmac_stop_protocol_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "free_ieee80211_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_wap_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wake_queue_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_rx_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_mode_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_is_shortslot" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_freq_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_name_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_rate_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_rate_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_ps_tx_ack" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_freq_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_is_54g" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_stop_queue_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_scan_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_essid_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_scan_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wpa_supplicant_ioctl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_mode_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_get_beacon" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_rawtx_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_encode_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_stop_protocol_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_wap_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_power_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_get_encode_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_softmac_start_protocol_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wlan_frequencies_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_power_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "alloc_ieee80211_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_reset_queue" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_wx_set_essid_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
WARNING: "ieee80211_start_protocol_rtl" [/home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko] undefined!
  CC      /home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.mod.o
  LD [M]  /home/ubuntu/Escritorio/rtl8185/rtl8185/r8180.ko
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.24-21-generic'
ubuntu@ubuntu-desktop:~/Escritorio/rtl8185$ ./wlan0up-----------------------------------------------------------2)
insmod: error inserting 'ieee80211_crypt-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_wep-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_tkip-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_ccmp-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211-rtl.ko': -1 Operation not permitted
insmod: error inserting 'r8180.ko': -1 Operation not permitted
wlan0: ERROR mientras se obtenían las banderas de interfaz: No existe el dispositivo
ubuntu@ubuntu-desktop:~/Escritorio/rtl8185$ ./wlan0rmv-----------------------------------------------------------2)
bash: ./wlan0rmv: No existe el fichero ó directorio
ubuntu@ubuntu-desktop:~/Escritorio/rtl8185$ ./wlan0down----------------------------------------------------------2)
wlan0: ERROR mientras se obtenían las banderas de interfaz: No existe el dispositivo
ERROR: Module r8180 does not exist in /proc/modules
ERROR: Module ieee80211_rtl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_ccmp_rtl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_tkip_rtl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_wep_rtl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_rtl does not exist in /proc/modules
ubuntu@ubuntu-desktop:~/Escritorio/rtl8185$ ./wlan0up------------------------------------------------------------3)
insmod: error inserting 'ieee80211_crypt-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_wep-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_tkip-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211_crypt_ccmp-rtl.ko': -1 Operation not permitted
insmod: error inserting 'ieee80211-rtl.ko': -1 Operation not permitted
insmod: error inserting 'r8180.ko': -1 Operation not permitted
wlan0: ERROR mientras se obtenían las banderas de interfaz: No existe el dispositivo
ubuntu@ubuntu-desktop:~/Escritorio/rtl8185$ 


Te parece que reinstale en un rato el sistema y empezamos de cero, conectada, actualizada, etc?

Muchas gracias

---

### Post by luks911 on 2008-10-26
Sé que aparecen errores previos, pero probá de entrar al directorio del driver y repetir el ./wlan0up pero con sudo, o sea

```
sudo ./wlan0up
```

por si hay suerte.

Si no va, hay otro posible driver surgido de este proyecto: [http://rtl-wifi.sourceforge.net](http://rtl-wifi.sourceforge.net) Ahora veo si puedo pasar en limpio las instrucciones para instalarlo por si querés probarlo.
Personalmente, no me gusta mucho la idea de reinstalar todo pero es tu decisión y tampoco perdés nada. 
De última también queda el recurso a ndiswrapper y además el kernel de Intrepid, que sale en cuatro días, debería soportar esa placa sin mover un dedo.

---

### Post by luks911 on 2008-10-26
Voy entonces con la instalación del driver de [http://rtl-wifi.sourceforge.net/](http://rtl-wifi.sourceforge.net/), según indica su wiki en inglés. 

1) Preparación
```
sudo apt-get install build-essential subversion module-assistant
sudo module-assistant prepare

```
2) Bajar el driver
```
wget http://kjo.herbesfolles.org/docs/rtl818x-mod2.6.24.tar.bz2
```
3) descomprimirlo
```
tar -xvf rtl818x-mod2.6.24.tar.bz2 
```
4) remover módulos viejos que puedan crear conflictos
```
sudo rm -r /lib/modules/`uname -r`/kernel/net/ieee80211
sudo rmmod ieee80211
```
5) compilar el driver
```
cd rtl-wifi
make

```
6) insertar el módulo
```
sudo insmod ieee80211/ieee80211_crypt-rtl.ko
sudo insmod ieee80211/ieee80211_crypt_wep-rtl.ko
sudo insmod ieee80211/ieee80211_crypt_tkip-rtl.ko
sudo insmod ieee80211/ieee80211_crypt_ccmp-rtl.ko
sudo insmod ieee80211/ieee80211-rtl.ko
sudo insmod rtl818x-newstack/r8180.ko

```
7) levantar el dispositivo (después de este paso y si todo salió bien tendrías que tener conexión)
```
sudo ifconfig wlan0 up
```
8 ) cargar el módulo de forma permanente
Sin salir del directorio del driver
```
sudo make modules_install
```
si eso no funciona, entonces
```
sudo mkdir  /lib/modules/`uname -r`/kernel/net/ieee80211
sudo cp ieee80211/*.ko  /lib/modules/`uname -r`/kernel/net/ieee80211
sudo cp rtl8187-newstack/*.ko  /lib/modules/`uname -r`/kernel/net
sudo cp rtl818x-newstack/*.ko  /lib/modules/`uname -r`/kernel/net
sudo depmod -ae

```

Saludos

---

### Post by losoollenos on 2008-10-26
Gracias che. Sos de bs as?, yo soy de san miguel, desde ya la picada y las cervezas correspondientes te las dejo a tu disposición si estamos más o menos cerca.
Después te comento que pasó con la prueba. Cómo sería lo del Intrepid, tengo que bajarlo de algún lado o es una actualización que bajará sola?

Saludos

---

### Post by losoollenos on 2008-10-26
SSSSSSSIIIIIIIIII........NO.
Que pasó?, seguí esta última guía con la compu en cuestión conectada, descargué el driver, el paquete build...., todos los pasos perfecto no apareció ningún error salvo el 8, que lo tuve que hacer uno a uno como me pusiste ahí y todo bien; reviso arriba a la derecha en el ícono de red y espectacular !!! tengo las redes inalámbricas a mi disposición !!!!
Apago, desconecto y la llevo a su lugar para configurar la clave y no mucho más.....la prendo y ya no hay más nada, ninguna red inalámbrica ni nada.
Empiezo de nuevo la guía: los primeros pasos bien, lo que había limpiado seguía limpio y los drivers me decía que ya existían al igual que los módulos exepto el último "sudo insmod rtl818x-newstack/r8180.ko", este me dió un error que me olvidé de copiar (cualquier cosa lo hago).
No le dí bola y seguí con el paso 7 y:

ubuntu@ubuntu-desktop:~$ sudo ifconfig wlan0 up
wlan0: ERROR mientras se obtenían las banderas de interfaz: No existe el dispositivo
ubuntu@ubuntu-desktop:~$ 

Acá creí que ya no tenía sentido seguir porque antes no había tirado nada de eso y bue, acá estoy, creo que tiene que ser algún detalle no?

Saludos

---

### Post by luks911 on 2008-10-26
Mmmm...... decime qué te devuelve 
```
ifconfig
```
que te va a mostrar los dispositivos de red disponible.
Qué te dice
```
lsmod
```
eso te va a mostrar los módulos cargados en el kernel y podemos saber si está el que necesita el wifi.
Y si se repite el error que no copiaste, pegalo acá.

Por lo demás, soy de Lomas de Zamora. Y Intrepid Ibex es la versión 8.10 de Ubuntu que sale el 30 de octubre. El gestor de actualizaciones te va a avisar que está lista para actualizase y la descargás.

Saludos

---

### Post by losoollenos on 2008-10-26
Tengo unos parientes en Lavallol que voy a ir a visitar quizás el fin de semana que viene, por ahí arreglamos aunque sea un brindis por tanto laburo......

Bueno acá están las pruebas:

ubuntu@ubuntu-desktop:~$ cd /home/ubuntu/Escritorio/rtl-wifi
ubuntu@ubuntu-desktop:~/Escritorio/rtl-wifi$ sudo insmod ieee80211/ieee80211-rtl.ko------------**Acá pruebo (existe)**
[sudo] password for ubuntu: 
insmod: error inserting 'ieee80211/ieee80211-rtl.ko': -1 File exists
ubuntu@ubuntu-desktop:~/Escritorio/rtl-wifi$ sudo insmod rtl818x-newstack/r8180.ko-------------**Acá está el error**
insmod: error inserting 'rtl818x-newstack/r8180.ko': -1 Unknown symbol in module
ubuntu@ubuntu-desktop:~/Escritorio/rtl-wifi$ ifconfig------------------------------------------**ifconfig**
eth0      Link encap:Ethernet  direcciónHW 00:11:d8:b7:86:50  
          ARRIBA DIFUSIÓN MULTICAST  MTU:1500  Métrica:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupción:16 Dirección base: 0xe400 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:1302 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1302 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:65100 (63.5 KB)  TX bytes:65100 (63.5 KB)

ubuntu@ubuntu-desktop:~/Escritorio/rtl-wifi$ lsmod------------------------------------------------**ismod**
Module                  Size  Used by
nls_iso8859_1           4992  1 
nls_cp437               6656  1 
vfat                   14464  1 
fat                    54556  1 vfat
ipv6                  267780  8 
speedstep_lib           6532  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_conservative     8712  0 
cpufreq_ondemand        9740  0 
freq_table              5536  2 cpufreq_stats,cpufreq_ondemand
video                  19856  0 
output                  4736  1 video
sbs                    15112  0 
sbshc                   7680  1 sbs
dock                   11280  0 
container               5632  0 
battery                14212  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
lp                     12324  0 
parport_pc             36260  1 
parport                37832  2 lp,parport_pc
evdev                  13056  3 
snd_usb_audio          83936  1 
snd_usb_lib            18432  1 snd_usb_audio
sn9c102               127236  0 
snd_hwdep              10500  1 snd_usb_audio
serio_raw               7940  0 
compat_ioctl32          2304  1 sn9c102
videodev               29440  1 sn9c102
v4l1_compat            15492  1 videodev
v4l2_common            18304  2 sn9c102,videodev
psmouse                40336  0 
snd_intel8x0           35356  3 
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0 
nvidia               4718832  32 
pcspkr                  4224  0 
i2c_core               24832  1 nvidia
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
button                  9232  0 
ieee80211_rtl          80520  0 
ieee80211_crypt_ccmp_rtl     8064  1 ieee80211_rtl
ieee80211_crypt_tkip_rtl    11648  1 ieee80211_rtl
ieee80211_crypt_wep_rtl     6400  1 ieee80211_rtl
ieee80211_crypt_rtl     6788  4 ieee80211_rtl,ieee80211_crypt_ccmp_rtl,ieee80211_crypt_tkip_rtl,ieee80211_crypt_wep_rtl
mac80211              165652  0 
cfg80211               15112  1 mac80211
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  22 snd_usb_audio,snd_usb_lib,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
shpchp                 34452  0 
sis_agp                10116  1 
pci_hotplug            30880  1 shpchp
agpgart                34760  2 nvidia,sis_agp
ext3                  136840  2 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
usb_storage            73664  1 
libusual               19108  1 usb_storage
sg                     36880  0 
sd_mod                 30720  5 
sr_mod                 17956  0 
cdrom                  37408  1 sr_mod
pata_acpi               8320  0 
sata_sis                9732  3 
ata_generic             8324  0 
floppy                 59588  0 
ehci_hcd               37900  0 
ohci_hcd               26640  0 
pata_sis               15236  1 sata_sis
sis900                 24320  0 
mii                     6400  1 sis900
usbcore               146412  8 snd_usb_audio,snd_usb_lib,sn9c102,usb_storage,libusual,ehci_hcd,ohci_hcd
libata                159344  4 pata_acpi,sata_sis,ata_generic,pata_sis
scsi_mod              151436  5 usb_storage,sg,sd_mod,sr_mod,libata
thermal                16796  0 
processor              37384  1 thermal
fan                     5636  0 
fbcon                  42912  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50708  3 
ubuntu@ubuntu-desktop:~/Escritorio/rtl-wifi$ 

Saludos

---

### Post by luks911 on 2008-10-26
Bien, más noticias para este boletín. Una prueba más bastante sencilla.
Vas a instalar los linux-backports-modules. Conectado a internet, en una terminal ejecutás

```
sudo apt-get install linux-backports-modules-$(uname -r)
```

Después, cargás el módulo

```
sudo modprobe rtl8180
```

Si funciona, edita el archivo /etc/modules para que el módulo se cargue en cada inicio

```
sudo gedit /etc/modules
```

y agregale una línea al final que diga

```
rtl8180
```

Lo leí, recién ahora ](*,), [acá]("http://willdaniels.co.uk/articles/howto-guides/10-howto/15-rtl8180-hardy")

Avisame a ver si con esto va o si aparece algún error teniendo en cuenta todo el "manoseo" anterior.

Saludos

---

### Post by losoollenos on 2008-10-26
No funcionó:

ubuntu@ubuntu-desktop:~$ sudo apt-get install linux-backports-modules-$(uname -r)
[sudo] password for ubuntu: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se instalarán los siguientes paquetes NUEVOS:
  linux-backports-modules-2.6.24-21-generic
0 actualizados, 1 se instalarán, 0 para eliminar y 0 no actualizados.
Necesito descargar 1511kB de archivos.
Se utilizarán 4383kB de espacio de disco adicional después de desempaquetar.
Des:1 [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/main linux-backports-modules-2.6.24-21-generic 2.6.24-21.27 [1511kB]
Descargados 1511kB en 26s (57,2kB/s)                                           
Seleccionando el paquete linux-backports-modules-2.6.24-21-generic previamente no seleccionado.
(Leyendo la base de datos ...  
99637 ficheros y directorios instalados actualmente.)
Desempaquetando linux-backports-modules-2.6.24-21-generic (de .../linux-backports-modules-2.6.24-21-generic_2.6.24-21.27_i386.deb) ...
Configurando linux-backports-modules-2.6.24-21-generic (2.6.24-21.27) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-21-generic

ubuntu@ubuntu-desktop:~$ sudo modprobe rtl8180
WARNING: Error inserting lbm_cw_mac80211 (/lib/modules/2.6.24-21-generic/updates/lbm_cw-mac80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rtl8180 (/lib/modules/2.6.24-21-generic/updates/rtl8180.ko): Unknown symbol in module, or unknown parameter (see dmesg)
ubuntu@ubuntu-desktop:~$ A

Como a vos te parezca, reinstalo, espero el nuevo kernel, voy por el lado del ndiswrapper, o la seguimos?

Realmente muchas gracias....

---

### Post by luks911 on 2008-10-26
Yo uso los backports porque tienen otro driver que sirven para mi wifi y pude cargar el módulo que necesitás. Por supuesto no sé si funciona porque no tengo tu placa, pero se cargó sin problemas. Por eso estoy casi seguro de que el inconveniente viene de alguna de las cosas previas.
Me parece que hay más opciones. Una, sí, es esperar a Intrepid. Otra: donde vi lo de los backports dice que hay un repositorio con una versión más nueva de los backports y del kernel. Antes de reinstalar o esperar a la 8.10, perdido por perdido, podés cargar esos repositorios y actualizar el kernel (que de paso limpia todo el lío que hicimos antes) y los backports. 
Sería así:

1) Habilitás el repositorio editando sources.list

```
sudo gedit /etc/apt/sources.list
```

incluís al final la siguiente línea 

```
deb http://ppa.launchpad.net/timg-tpi/ubuntu hardy main
```

2) Recargás los repositorios

```
sudo apt-get update
```

3) Actualizás

```
sudo apt-get upgrade
```

4) Cargás el módulo

```
sudo modprobe rtl8180
```

con eso debería estar funcionando, no creo que haga falta un

```
sudo ifconfig wlan0 up
```

pero........

5) Si esta vez funcionó : -P agregás el módulo al inicio

```
sudo gedit /etc/modules
```

y agregás al final una línea que diga

```
rtl8180
```


Saludos

---

### Post by losoollenos on 2008-10-27
Error al cargar módulo sudo modprobe rtl8180:

ubuntu@ubuntu-desktop:~$ sudo gedit /etc/apt/sources.list
ubuntu@ubuntu-desktop:~$ sudo apt-get update
Obj [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy Release.gpg                                                                          
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/main Translation-es                                                                  
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/restricted Translation-es                                                            
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/universe Translation-es                                                              
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/multiverse Translation-es                                                            
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates Release.gpg                                                                  
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                                                                   
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/main Translation-es                                                          
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-es                                              
Obj [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                                   
Obj [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                                              
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/restricted Translation-es         
Obj [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-es                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-es                           
Des:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27,6kB]  
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/universe Translation-es
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-es
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages       
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages       
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/multiverse Translation-es
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-es
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports/main Translation-es
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-es
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Obj [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports/restricted Translation-es
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports/universe Translation-es
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports/multiverse Translation-es
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy Release
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates Release
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports Release
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/main Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/restricted Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/main Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/restricted Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/universe Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/universe Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/multiverse Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/multiverse Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/main Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/restricted Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/main Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/restricted Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/universe Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/universe Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/multiverse Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/multiverse Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports/main Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports/restricted Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports/universe Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports/multiverse Packages
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports/main Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports/restricted Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports/universe Sources
Obj [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-backports/multiverse Sources
Descargados 1B en 3s (0B/s)  
Leyendo lista de paquetes... Hecho
ubuntu@ubuntu-desktop:~$ sudo apt-get upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
ubuntu@ubuntu-desktop:~$ sudo modprobe rtl8180
FATAL: Module rtl8180 not found.
ubuntu@ubuntu-desktop:~$ 

Te copié el segundo intento, en el primero cargó y actualizó todo bien.....hasta el módulo.

Saludos

---

### Post by luks911 on 2008-10-27
Ok, asumo que, como decís, en el primer intento sí te actualizó el kernel y los backports, si fue así te tiene que haber pedido reiniciar la máquina para que tengan efecto los cambios. Probá de reiniciar.

---

### Post by luks911 on 2008-10-27
Me olvidaba, por supuesto después de reiniciar deberías poder cargar el módulo.

---

### Post by losoollenos on 2008-10-27
Si si, tuve que reiniciar antes de intentar cargar los modulos.....me olvide de aclararlo. Los intentos fueron despues de reiniciar.

---

### Post by luks911 on 2008-10-27
:-k:-k

1) Si tuviste que reinicar, entonces el kernel se actualizó. Para confirmar, ejecutá

```
uname -a
```

el número de kernel que te tire tiene que ser 2.6.24-22

2) ¿Seguro tenés instalados los backports? Asegurate con

```
sudo apt-get install linux-backports-modules-$(uname -r)
```

3) Si ninguna de las opciones anteriores sirve, probá con 

```
sudo modprobe lbm_rtl8180
``` 

porque en una de las versiones el módulo cambió de nombre, de rtl8180 a lbm_rtl8180, aunque ahora debería haber vuelto al original.

4) Si aún así no pasa nada bueno, intentá ejecutando

```
modconf
```

no sé bien cómo funciona, pero la idea es que te dé un listado de los módulos disponibles. Fijate si aparece algo que diga rtl. Si no tenés modconf

```
sudo apt-get install modconf
``` 

5) Ahora no puedo pprque no estoy en mi máquina, pero si todavía hace falta cuando llego a casa a la noche me instalo la versión del kernel y los backports del rpeositorio que t epasé, para ver qué onda.

Saludos

---

### Post by losoollenos on 2008-10-27
SSSSSSSiiiiiiiiiiiiiiiiiii!!!!!!!!!!!!!!!
Ahora si luks911, anda de lujo !!!!
Te comento porque no copié nada. El kernel estaba actualizado, me aparecía en el arranque este, el anterior y el de windows, igual seguí los pasos  
          1) uname -a
          2) sudo apt-get install linux-backports-modules-$(uname -r)este aparentemente se instaló de nuevo.......no se, hizo todo el proceso
          3)Acá volví al sudo modprobe rtl8180 pero aparentemente no pasaba nada, volvía a lo de ubuntu@ubuntu-desktop:~$ .....entonces revisé el ícono de red y otra vez estaba la red inalámbrica disponible, así que en sudo gedit /etc/modules agregué rtl8180 reinicié cargue la clave wpa y te estoy escribiendo con la conexión inalámbria !!!!

No se si le querés hacer algo más, digo por tanto manoseo o lo que sea....
Realmente agradezco mucho tu paciencia en explicarme como a un novato que soy y la perseverancia de tantos días.
Reitero lo de la picada, yo quizás vaya a Lavallol el sábado que viene y si te parece nos ponemos en contacto y arreglamos. No se si se puede poner dirección de correo acá o mandar MP decime vos......

Nuevamente muchísimas gracias y un gran abrazo !!!!!

---

### Post by luks911 on 2008-10-27
¡Genial! Me alegro de que finalmente haya funcionado.

Te comento, cuando cargaste el módulo y parecía que no paso nada, que no te devolvió nada la consola, es porque se cargó bien. Si no hay errores, no te informa.

Luego, no hay que hacer nada más. El manoseo afectó al kernel viejo, pero no al que estás usando ahora. Cuando quieras y si tenés ganas, podés eliminarlo para ganar algo de espacio en el disco y para que no se acumulen con las actualizaciones. [Acá]("http://tuxpepino.wordpress.com/2007/06/26/tip-eliminar-un-kernel-antiguo/")[0] una muy buena explicación de cómo hacerlo. Es sencillo.

Te agradezco la invitación a la picada. Soy de Llavallol, casualmente, pero no sé si el sábado voy a poder. De todos modos, la picada es lo de menos. Si puedo dar una mano, la doy. Es lo bueno de esta comunidad. Y la perseverancia, bah... en realidad es de terco nomás.

Un abrazo


[0] [http://tuxpepino.wordpress.com/2007/06/26/tip-eliminar-un-kernel-antiguo/](http://tuxpepino.wordpress.com/2007/06/26/tip-eliminar-un-kernel-antiguo/)

---

