---
title: "Intrepid: WiFi Compaq F700 (AR242x) funcionando"
date: 2008-11-03
forum: Hardware
---

### Post by hictio on 2008-11-03
Hola,

Yo tengo una Compaq F700 con una tarjeta WiFi:
```

esteban@tango:~/Desktop$ lspci | grep Atheros
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
esteban@tango:~/Desktop$ 

```

Que trate por todos los medios en Hardy de hacer funcionar, pero, si bien la tarjeta era reconocida, y veia redes inalambricas, no me podia conectar a ningun Access Point, sin importar que tipo de seguridad tuviera, incluso los publicos.

Por suerte en Intrepid, hacerla funcionar es muy facil, son 4 pasos, y se necesita internet (aunque por lo que le en los release notes, los paquetes estan en el CD, pero no se instalan; de cualquier forma, yo lo hice bajandolos de internet).

1- Abrir **Hardware Drivers** ("System -> Administration -> Hardware Drivers".
2- Deshabilitar la opcion "*Support for Atheros 802.11 wireless LAN cards*".
3- Rebootear
4- Cuando la maquina esta nuevamente encendida, abrir un terminal ("Applications -> Accesories -> Terminal"), y tipear:
```

sudo aptitude install linux-backports-modules-intrepid-generic

```

Pide el password, e imprime en pantalla.
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  linux-backports-modules-2.6.27-7-generic{a} 
  linux-backports-modules-intrepid-generic 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1173kB of archives. After unpacking 3772kB will be used.
Do you want to continue? [Y/n/?] 

```

Tipear 'Y', para que instale todo.
Una vez que termina de instalar (el prompt vuelve a estar disponible), rebootear la maquina nuevamente.

Cuando vuelve nuevamente a la vida la maquina, la tarjeta ya tendria que estar funcionando.
Hay que seleccionar la red a la cual hay que conectarse, autenticarse (de ser necesario) y listo.

Esto lo probe en mi Compaq, con una instalacion fresca* de Intrepid, y me estoy conectando al Access Point del DI-614+ de casa (es lo que hay...), que tiene settea WPA-PSK como metodo de seguridad.

Espero que le sirva a mas gente, yo no puedo creer lo bueno de poder volver a usar la tarjeta WiFi.

*Es decir, instale Intrepid el Sabado a la noche, luego los updates que ya habia, y luego instale lo usual para hacer la maquina mas funcional; aunque no creo que tenga mayor importancia para hacer funcionar la tarjeta WiFi.

Consola:
emacs22-nox
openssh-server
build-essential
ssmtp
curl

GUI:
vlc
ubuntu-restricted-extras
flashplugin-nonfree libflashsupport
computertemp
compizconfig-settings-manager
emerald

---

### Post by faktorqm on 2008-11-04
Yo lo postie aca en el foro como hacerla andar, y nadie se quejo! :P salu2!!

---

### Post by luks911 on 2008-11-05
> **faktorqm said:**
> Yo lo postie aca en el foro como hacerla andar, y nadie se quejo! :P salu2!!

Jaja, claro Faktor. Pero ahora no hay que compilar nada. Ya con la última versión del kernel de Hardy (no recuerdo el número) funcionaban los backports y si tratabas de compilar madwifi había un conflicto que derivaba en un kernel panic. 

Saludos

---

### Post by luks911 on 2008-11-05
Ahora que lo pienso, no el nuevo módulo (ath5k) no funciona en modo monitor. Así que para eso podría servir compilar madwifi. Por otro lado, el ath5k es totalmente libre.

---

### Post by lega on 2008-11-05
Una pregunta, que pasaría si actualizo de hardy a intrepid, porque yo en la notebook en Hardy desinstalé network manager e instalé Wicd, además que los drivers para el wireless estan compilados con madwifi, esto se sobreescribirá? o complicara mas las cosas?

---

### Post by hictio on 2008-11-05
Como vas a hacer la actualizacion a Intrepid? Igualmente, el Network Manager y los modulos son parte del sistema, asi que se te va a re-escribir.
Pero... que laptop tenes? Que WiFi tiene instalada la notebook?

---

### Post by lega on 2008-11-05
via web o internet mejor dicho, siguiendo [esta guia]("http://www.ubuntu.com/getubuntu/upgrading")

la placa wireless es la misma que la tuya, la laptop es la compaq F755la y ahora en Hardy tiene los drivers de madwifi

---

### Post by luks911 on 2008-11-05
> **lega said:**
> via web o internet mejor dicho, siguiendo [esta guia]("http://www.ubuntu.com/getubuntu/upgrading")

la placa wireless es la misma que la tuya, la laptop es la compaq F755la y ahora en Hardy tiene los drivers de madwifi

Como en cada actualización del kernel, los drivers compilados van a desaparecer. O sea que te vas a quedar sin wifi. Vas a tener al menos dos opciones: instalar linux-backports-modules-intrepid o probar de volver a compilar madwifi.
En el caso de WICD, si hacés una actualización y no reinstalás, lo vas a tener intacto.

---

### Post by lega on 2008-11-05
Ok gracias

---

### Post by faktorqm on 2008-11-07
Aca lo publique para 8.04

[http://ubuntu-ar.org/tutoriales/ar5007eg](http://ubuntu-ar.org/tutoriales/ar5007eg)

salu2!

---

### Post by hictio on 2008-11-07
Ayer a noche instale estos updates:

```

2008-11-07 00:52:12 upgrade linux-image-2.6.27-7-generic 2.6.27-7.15 2.6.27-7.16
2008-11-07 00:52:31 upgrade gdm-guest-session 0.6 0.6.1
2008-11-07 00:52:32 upgrade human-theme 0.28.5 0.28.6
2008-11-07 00:52:32 upgrade libgphoto2-port0 2.4.2-0ubuntu2 2.4.2-0ubuntu3
2008-11-07 00:52:32 upgrade libgphoto2-2 2.4.2-0ubuntu2 2.4.2-0ubuntu3
2008-11-07 00:52:33 upgrade libtotem-plparser12 2.24.1-0ubuntu2 2.24.2-0ubuntu1
2008-11-07 00:52:33 upgrade linux-headers-2.6.27-7 2.6.27-7.15 2.6.27-7.16
2008-11-07 00:52:41 upgrade linux-headers-2.6.27-7-generic 2.6.27-7.15 2.6.27-7.16
2008-11-07 00:52:47 upgrade linux-libc-dev 2.6.27-7.15 2.6.27-7.16
2008-11-07 00:52:48 upgrade python-software-properties 0.68 0.68.1
2008-11-07 00:52:49 upgrade software-properties-gtk 0.68 0.68.1
2008-11-07 00:52:50 upgrade system-tools-backends 2.6.0-1ubuntu1 2.6.0-1ubuntu1.1
2008-11-07 00:52:51 upgrade totem-common 2.24.2-0ubuntu4 2.24.3-0ubuntu1
2008-11-07 00:53:07 upgrade totem-plugins 2.24.2-0ubuntu4 2.24.3-0ubuntu1
2008-11-07 00:53:07 upgrade totem-gstreamer 2.24.2-0ubuntu4 2.24.3-0ubuntu1
2008-11-07 00:53:08 upgrade totem 2.24.2-0ubuntu4 2.24.3-0ubuntu1
2008-11-07 00:53:08 upgrade totem-mozilla 2.24.2-0ubuntu4 2.24.3-0ubuntu1
2008-11-07 00:53:09 upgrade transmission-gtk 1.34-0ubuntu2 1.34-0ubuntu2.1
2008-11-07 00:53:09 upgrade transmission-common 1.34-0ubuntu2 1.34-0ubuntu2.1
2008-11-07 01:09:20 upgrade command-not-found-data 0.2.26ubuntu1 0.2.26ubuntu1.1
2008-11-07 01:09:20 upgrade command-not-found 0.2.26ubuntu1 0.2.26ubuntu1.1
2008-11-07 01:09:21 upgrade libdecoration0 1:0.7.8-0ubuntu4 1:0.7.8-0ubuntu4.1
2008-11-07 01:09:21 upgrade compiz-gnome 1:0.7.8-0ubuntu4 1:0.7.8-0ubuntu4.1
2008-11-07 01:09:32 upgrade compiz-plugins 1:0.7.8-0ubuntu4 1:0.7.8-0ubuntu4.1
2008-11-07 01:09:32 upgrade compiz-wrapper 1:0.7.8-0ubuntu4 1:0.7.8-0ubuntu4.1
2008-11-07 01:09:32 upgrade compiz-core 1:0.7.8-0ubuntu4 1:0.7.8-0ubuntu4.1
2008-11-07 01:09:33 upgrade compiz 1:0.7.8-0ubuntu4 1:0.7.8-0ubuntu4.1
2008-11-07 01:09:33 upgrade nvidia-96-modaliases 96.43.05-0ubuntu10 96.43.09-0ubuntu1
2008-11-07 01:09:33 upgrade rhythmbox 0.11.6svn20081008-0ubuntu4 0.11.6svn20081008-0ubuntu4.1

```

En la Compaq F700, con Intrepid, todo sigue andando perfecto. me preocupaba mucho el update de kernel, pero no hubo problemas con nada (NVIDIA, Compiz, suspend, etc).

---

### Post by vk-cdg on 2008-11-07
Veremos entonces de instalar Intrepid!

Me venía resistiendo por estar con un LTS, pero tiene 2 mejoras fundamentales. El tema de la hibernada y el tema de la autocompilación de los drivers luego de un update del kernel.

Me pareció leer por ahí (en este foro) que si hago un update desde la 8.04 no voy a tener la funcionalidad de autocompilación ¿esto es así?
No me jode demasiado hacer un frash install ya que como tengo el /home separado y no tengo nada importante en la notebook (porque la llevo de acá para allá).

---

### Post by hictio on 2008-11-07
No te sabria decir de la instalacion, yo la hice desde cero.
Con respecto, al suspend/ hibernate, etc, una aclaracion, en la Compaq, todo eso andaba Ok, el problema era que luego que la volvias a activar, los puertos USB no andaban.

---

### Post by luks911 on 2008-11-07
> **vk-cdg said:**
> Veremos entonces de instalar Intrepid!

Me venía resistiendo por estar con un LTS, pero tiene 2 mejoras fundamentales. El tema de la hibernada y el tema de la autocompilación de los drivers luego de un update del kernel.

Me pareció leer por ahí (en este foro) que si hago un update desde la 8.04 no voy a tener la funcionalidad de autocompilación ¿esto es así?
No me jode demasiado hacer un frash install ya que como tengo el /home separado y no tengo nada importante en la notebook (porque la llevo de acá para allá).

Cuento mi experiencia con la F754, aunque de la diferencia que comentás entre la reinstalación y la actualización no tengo la menor idea.
Primero hice una actualización usando un Alternate CD. Pero tuve algunos problemas. No sé por qué, pero tenía inconvenientes con el servicio Dbus y como consecuencia había cosas que no podía ejecutar: cambiar la frecuencia del procesador con el applet para eso, entrar a controladores de hardware, a veces no se montaban los cd, en fin. 
Traté de buscar la solución pero no hubo caso. Entre mi alta de conocimiento y la falta de paciencia, opté por reinstalar. 
Lo bueno: funciona bastante mejor que antes, el sistema de ahorro de energía hace que la máquina levante menos temperatura, con el alternate y teniendo el home en partición aparte la instalación se hizo muy rápido, fácil y conservando todas las configuraciones.
Lo malo: tengo que bajarme unos 350MB de paquetes y aplicaciones que tenía previa a la instalación. 
El saldo es positivo. 

Saludos

---

### Post by luks911 on 2008-11-18
> **hictio said:**
> Hola,

Yo tengo una Compaq F700 con una tarjeta WiFi:
```

esteban@tango:~/Desktop$ lspci | grep Atheros
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
esteban@tango:~/Desktop$ 

```

Que trate por todos los medios en Hardy de hacer funcionar, pero, si bien la tarjeta era reconocida, y veia redes inalambricas, no me podia conectar a ningun Access Point, sin importar que tipo de seguridad tuviera, incluso los publicos.

Por suerte en Intrepid, hacerla funcionar es muy facil, son 4 pasos, y se necesita internet (aunque por lo que le en los release notes, los paquetes estan en el CD, pero no se instalan; de cualquier forma, yo lo hice bajandolos de internet).

1- Abrir **Hardware Drivers** ("System -> Administration -> Hardware Drivers".
2- Deshabilitar la opcion "*Support for Atheros 802.11 wireless LAN cards*".
3- Rebootear
4- Cuando la maquina esta nuevamente encendida, abrir un terminal ("Applications -> Accesories -> Terminal"), y tipear:
```

sudo aptitude install linux-backports-modules-intrepid-generic

```

Pide el password, e imprime en pantalla.
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  linux-backports-modules-2.6.27-7-generic{a} 
  linux-backports-modules-intrepid-generic 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 1173kB of archives. After unpacking 3772kB will be used.
Do you want to continue? [Y/n/?] 

```

Tipear 'Y', para que instale todo.
Una vez que termina de instalar (el prompt vuelve a estar disponible), rebootear la maquina nuevamente.

Cuando vuelve nuevamente a la vida la maquina, la tarjeta ya tendria que estar funcionando.
Hay que seleccionar la red a la cual hay que conectarse, autenticarse (de ser necesario) y listo.

Esto lo probe en mi Compaq, con una instalacion fresca* de Intrepid, y me estoy conectando al Access Point del DI-614+ de casa (es lo que hay...), que tiene settea WPA-PSK como metodo de seguridad.

Espero que le sirva a mas gente, yo no puedo creer lo bueno de poder volver a usar la tarjeta WiFi.

Comento, para que quede "documentado", un inconveniente que tuve al utilizar linux-backports-modules-intrepid para poder utilizar la placa wifi, la misma 
```
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

La utilización de ese paquete y del driver ath5k que incluye se volvía obligatoria después de la última actualización del kernel en Hardy previa a la salida de Intrepid. Era porque el nuevo kernel entraba en conflicto con el driver madwifi compilado (el método que usaba antes y ahora para que funcione el wifi[0]), lo que derivaba en un kernel panic al cargar el módulo.
Al actualizar a Intrepid continué con backports, porque es más simple. Sin embargo, después de varios días de uso noté que la conexión a Internet se cortaba al dejar la máquina inactiva. No al suspenderse, sino que bastaba con que bajara la tapa de la notebook durante 20 o 30 minutos y al volver a levantarla me encontraba con que el aMSN se había desconectado y el torrent que había dejado descargando ya no lo hacía. Primero comprobé que no era un problema de mi conexión a internet. Luego vi que dmesg me devolvía algo relativo al driver ath5k. Hice mal en no copiar los mensajes que me resultaron indescifrables, pero opté por deshabilitarlo desde Controladores de Hardware y volver a compilar madwifi, lo que solucionó el problema de la interrupción en la conexión.  

Puede que la experiencia le sirva a alguien.

[0] [http://ubuntuforums.org/showpost.php?p=5633150&postcount=36](http://ubuntuforums.org/showpost.php?p=5633150&postcount=36) (tutorial de faktor para compilar madwifi)

---

### Post by hictio on 2008-11-19
Es raro, no me esta pasando en mi Compaq F700 con esa Atheros.
El uso normal de la maquina es una docena de Terminales con SSH a hosts, todos fuera del LAN, Evolution (abierto 24x7 con una cuenta IMAPS) y Firefox con unos 8 tabs de promedio; ademas del Pidgin.

Algunas sesiones de SSH en el Terminal, a veces abiertas por dias.

Lo unico que no uso en la laptop son Torrents, porque es muy animal para la pobrecita, se calienta mucho, ademas Ubuntu saca updates practicamente todos los dias, no es una buena plataforma para Torrents, especialmenete si la usas con GUI.

---

### Post by luks911 on 2008-11-19
> **hictio said:**
> Es raro, no me esta pasando en mi Compaq F700 con esa Atheros.
El uso normal de la maquina es una docena de Terminales con SSH a hosts, todos fuera del LAN, Evolution (abierto 24x7 con una cuenta IMAPS) y Firefox con unos 8 tabs de promedio; ademas del Pidgin.

Algunas sesiones de SSH en el Terminal, a veces abiertas por dias.

Lo unico que no uso en la laptop son Torrents, porque es muy animal para la pobrecita, se calienta mucho, ademas Ubuntu saca updates practicamente todos los dias, no es una buena plataforma para Torrents, especialmenete si la usas con GUI.

Puede ser que sea un problema que tenga que ver con alguna combinación o detalle de mi configuración, o con los programas específicos que estoy corriendo. Por supuesto que lo mío no es una prueba de laboratorio ni mucho menos, y lo comento por si le sirve a alguien. Aunque no estaría mal que trataramos de ver qué pasa. Y hablando de eso...
Faktor pedía en el otro thread ([http://ubuntuforums.org/showthread.php?t=887531](http://ubuntuforums.org/showthread.php?t=887531)), pero para que respondiéramos en este para no hacer lío, los detalles del chip. Y, te diré Faktor, que me parece que tenemos el mismo. Los resultados de lspci de Hictio y mío está más arriba. Lo repito:

```
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

el lshw:

```
 *-network
             description: Wireless interface
             product: AR242x 802.11abg Wireless PCI Express Adapter
             vendor: Atheros Communications Inc.
             physical id: 0
             bus info: pci@0000:03:00.0
             logical name: wifi0
             version: 01
             serial: 00:1f:3a:02:ce:0a
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
             configuration: broadcast=yes driver=ath_pci ip=192.168.1.33 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

```

Saludos y a ver qué se les ocurre :lolflag:

---

### Post by lega on 2008-11-19
si bien yo no he instalado Intrepid en la notebook, posteo el lspci por si sirve, Compaq F755

> Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by luks911 on 2008-11-19
> **lega said:**
> si bien yo no he instalado Intrepid en la notebook, posteo el lspci por si sirve, Compaq F755

Sí, todos los involucrados, je, tenemos Intrepid.

---

### Post by hictio on 2008-11-19
```

  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:1f:3a:4a:43:3a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=10.120.10.4 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg

```

```

tango:~$ lspci | egrep Atheros
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01) 

```

---

### Post by faktorqm on 2008-11-20
Che son identicos!! Encima todos dicen rev 01 asi que nada... lo unico que se me ocurre es que el kernel muestre siempre lo mismo para diferentes chipset con lo cual ahi si estamos en un problema, pero como no se como es el mecanismo de reconocimiento de hardware (y post muestra de informacion), mejor no digo nada.

Ubicacion de las antenas wifi? Capaz hictio tiene mejor "vista" o está muy cerca del nodo y vos no, o tenes una pared muy cerca y te hace de espejo, o tenes menos alcance por algun motivo, no se se me ocurre... salu2!

---

### Post by luks911 on 2008-11-20
> **faktorqm said:**
> Che son identicos!! Encima todos dicen rev 01 asi que nada... lo unico que se me ocurre es que el kernel muestre siempre lo mismo para diferentes chipset con lo cual ahi si estamos en un problema, pero como no se como es el mecanismo de reconocimiento de hardware (y post muestra de informacion), mejor no digo nada.

Ubicacion de las antenas wifi? Capaz hictio tiene mejor "vista" o está muy cerca del nodo y vos no, o tenes una pared muy cerca y te hace de espejo, o tenes menos alcance por algun motivo, no se se me ocurre... salu2!

No creo que sea tema de las antenas porque me pasaba lo mismo a dos metros (con entre 80 y 100 por ciento de señal) como a más distancia, con entre 40 y 50 por ciento de señal. 
Aparte no se perdía señal, sino que dejaba de transmitir datos. Es raro, pero levantaba la tapa de la máquina y me encontraba con el aMSN desconectado y tratando de conectar (no lo hacía y tenía que clickear en cancelar y volver a poner la contraseña) y el Deluge sin subir ni bajar y sin conexiones activas. Después, sin que tocara nada, sólo reconectando el aMSN, volvía a descargar. En una de ésas estoy diciendo huevadas debido a mi falta de conocimientos técnicos, eso es lo que yo veía. Culpé al driver porque era lo que tenía más a mano y el dmesg me devolvía unos mensajes con respecto al ath5k y, entre otras coasas, la palabra interrupt. Sí, ya sé debí copiarlos. 
Ahora estoy teniendo poco tiempo con la notebook, pero podría sacar madwifi y rehabilitar el ath5k para probar y ver qué pasa. Gracias por interesarte.

Un saludo

---

### Post by Hei Ku on 2008-11-20
cuando se te corte, podes probar de poner dmesg en una terminal
eso te tira el log de devices. capaz q ahi aparece algo.

---

### Post by hictio on 2008-11-20
Yo estoy cerca de Access Point, mi sospecha son los Torrents, voy a ver si el fin de semana me pongo a bajar algo a ver que pasa.

---

### Post by luks911 on 2008-11-20
> **Hei Ku said:**
> cuando se te corte, podes probar de poner dmesg en una terminal
eso te tira el log de devices. capaz q ahi aparece algo.

> **hictio said:**
> Yo estoy cerca de Access Point, mi sospecha son los Torrents, voy a ver si el fin de semana me pongo a bajar algo a ver que pasa.

Mañana (viernes) me va a ser imposible. Pero el fin de semana hago el cambio de driver y pruebo a ver qué sale.

---

### Post by luks911 on 2008-11-22
> **Hei Ku said:**
> cuando se te corte, podes probar de poner dmesg en una terminal
eso te tira el log de devices. capaz q ahi aparece algo.

Bien, hoy cambié el driver por el ath5k. Dejé la máquina conectada al aMSN y bajando con el Deluge. Bajé la tapa, una hora más tarde la abrí y el aMSN se había desconectado y el Deluge no descargaba. En unos segundos volvió a bajar pero el aMSN no se conectó. El dmesg me devuelve:

```
[12457.804421] WARNING: at /build/buildd/linux-backports-modules-2.6.27-2.6.27/debian/build/build-generic/compat-wireless-2.6/net/mac80211/rx.c:2200 lbm_cw___lbm_cw_ieee80211_rx+0x19f/0x600 [lbm_cw_mac80211]()
[12457.804453] Modules linked in: eeprom_93cx6 arc4 ecb crypto_blkcipher ath5k lbm_cw_mac80211 lbm_cw_cfg80211 led_class binfmt_misc af_packet ppdev powernow_k8 cpufreq_stats cpufreq_conservative cpufreq_ondemand cpufreq_powersave freq_table cpufreq_userspace sbs sbshc container pci_slot iptable_filter ip_tables x_tables parport_pc lp parport loop wlan_scan_sta ath_rate_sample wlan ath_hal(P) joydev ipv6 serio_raw pcspkr psmouse evdev nvidia(P) k8temp agpgart i2c_core uvcvideo compat_ioctl32 videodev v4l1_compat video output snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss wmi snd_seq_midi snd_rawmidi battery snd_seq_midi_event snd_seq ac snd_timer snd_seq_device button snd shpchp pci_hotplug soundcore snd_page_alloc ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif sg pata_amd ahci pata_acpi ata_generic libata ohci_hcd forcedeth ehci_hcd scsi_mod dock usbcore thermal processor fan fuse vesafb fbcon tileblit font bitblit softcursor compcache lzo_decompress lzo_compress tlsf [last unloaded: rtl8180]
[12457.804620] Pid: 0, comm: swapper Tainted: P        W 2.6.27-7-generic #1
[12457.804628]  [<c037c406>] ? printk+0x1d/0x1f
[12457.804646]  [<c0131de9>] warn_on_slowpath+0x59/0x90
[12457.804667]  [<c012a708>] ? enqueue_task_fair+0x48/0x50
[12457.804677]  [<c0120f97>] ? enqueue_task+0x57/0x70
[12457.804689]  [<c037dfae>] ? account_scheduler_latency+0xe/0x220
[12457.804699]  [<c0123454>] ? __enqueue_entity+0xd4/0x100
[12457.804709]  [<f93bf9af>] lbm_cw___lbm_cw_ieee80211_rx+0x19f/0x600 [lbm_cw_mac80211]
[12457.804742]  [<c02eae1c>] ? skb_put+0xc/0xa0
[12457.804752]  [<c012a708>] ? enqueue_task_fair+0x48/0x50
[12457.804761]  [<c0120f97>] ? enqueue_task+0x57/0x70
[12457.804772]  [<f9104c83>] ath5k_tasklet_rx+0x2e3/0x550 [ath5k]
[12457.804789]  [<c012b4ee>] ? try_to_wake_up+0xde/0x290
[12457.804798]  [<c0178244>] ? note_interrupt+0x14/0x140
[12457.804810]  [<c014e63b>] ? getnstimeofday+0x4b/0x100
[12457.804822]  [<c0137258>] tasklet_action+0x78/0x100
[12457.804832]  [<c0137682>] __do_softirq+0x92/0x120
[12457.804840]  [<c013776d>] do_softirq+0x5d/0x60
[12457.804847]  [<c01378e5>] irq_exit+0x55/0x90
[12457.804855]  [<c0106c1a>] do_IRQ+0x4a/0x80
[12457.804864]  [<c027747c>] ? acpi_os_read_port+0xc/0x4b
[12457.804876]  [<c0105003>] common_interrupt+0x23/0x30
[12457.804885]  [<c011aba5>] ? native_safe_halt+0x5/0x10
[12457.804909]  [<f8958ab4>] acpi_safe_halt+0x2f/0x47 [processor]
[12457.804931]  [<f8959501>] acpi_idle_do_entry+0x21/0x30 [processor]
[12457.804951]  [<f8959577>] acpi_idle_enter_c1+0x67/0x88 [processor]
[12457.804968]  [<c02dbf7b>] cpuidle_idle_call+0x7b/0xd0
[12457.804977]  [<c010288d>] cpu_idle+0x7d/0x140
[12457.804984]  [<c036edd3>] rest_init+0x53/0x60
[12457.804996]  =======================
[12457.805001] ---[ end trace 981eb16fdf81f1a7 ]---
[12475.552838] ------------[ cut here ]------------

```

La misma serie de mensajes se repite una y otra vez, capaz que con alguna leve variación. La parte que dice "[last unloaded: rtl8180]" es porque probé ese módulo por una pregunta en el foro, pero no tiene nada que ver con el problema.
Buscando partiendo del aviso de advertencia encontré un [thread]("http://ubuntuforums.org/showthread.php?t=973070")[0] en el foro que resultó irrelevante y un bug en [launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/289100")[1] donde aparece un mensaje igual. Allí alguien recomienda deshabilitar el soporte para atheros. Nunca tuve la posibilidad de habilitarlos siquiera, pero veo cargado el módulo ath_hal :confused: Como fuere, removí ese módulo y el problema continuó. Me parece que vuelvo a compilar madwifi.

Saludos


[0] [http://ubuntuforums.org/showthread.php?t=973070](http://ubuntuforums.org/showthread.php?t=973070)
[1] [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/289100](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/289100)

---

### Post by hictio on 2008-11-22
Una consulta al margen, porque le bajas la tapa? No entiendo esa parte, quiere decir que la  cerras totalmente? No se va hibernacion si haces eso? Y si la setteaste para que no haga eso, no te preocupa la temperatura de la laptop con la tapa cerrada? (estoy obsesionado con la temperatura, odio el calor)

---

### Post by luks911 on 2008-11-22
> **hictio said:**
> Una consulta al margen, porque le bajas la tapa? No entiendo esa parte, quiere decir que la  cerras totalmente? No se va hibernacion si haces eso? Y si la setteaste para que no haga eso, no te preocupa la temperatura de la laptop con la tapa cerrada? (estoy obsesionado con la temperatura, odio el calor)

Ni hiberna ni suspende, está seteada para que sólo se oscurezca la pantalla, que de hecho se apaga. Supongo que la bajo para que no quede la pantalla prendida cuando sé que no voy a usarla y para que no se le junte más mugre que la estrictamente necesaria.
La verdad es que es mi primera laptop, ¿se calienta más porque la cierre? Al menos, no lo noto. La temperatura es igual que si no la cierro. or supuesto, viéndola apenas la abro. 
Y desde que instalé Intrepid (pisando Hardy) la gestión de energía es mucho mejor: por medio de los applets que me muestran la temperatura y la frecuencia del procesador veo que labura al 100% menos que antes y como consecuencia calienta menos. Con el firefox abierto con unas cinco pestañas (a veces más, a veces menos), el aMSN y Deluge se mantiene entre 39° y 43°. Sube más al iniciarse alguna de esas aplicaciones o si a eso le sumo la reproducción de un video (entre 50 y 54). Y como mucho llega a 60 al compilar (lo hice con madwifi solamente), instalar algun paquete y creo que lo superó una vez que jugué al Urban Terror :-P Esto en días de calor como hoy, que llegamos a 30° y sin aire acondicionado. 
De todos modos, una vez buscando en la página de AMD decía que estos procesadores (Sempron Mobile 3600+ aguantan hasta 90°).

---

### Post by hictio on 2008-11-22
No pude ponerme a probar bajar Torrents al final, me colgue instalando FreeBSD en otra maquina, voy a ver si mas tarde dejo bajando un par de isos de Ubuntu que quiero tener (el 8.10 Server, y el Alternate) a ver si le pasa algo.

(Con respecto al calor, si, impresion es que se calienta mas con la tapa cerrada, especialmente el disco, que en la F700 esta debajo de la mano izquierda.
Como te dije :D soy un maniatico con el calor, me molesta al punto de ponerle un teclado externo (el mouse lo uso siempre) porque tipear con esa parte caliente de la maq. me es muy incomodo.)

---

### Post by hictio on 2008-11-23
Cuando me fui a dormir en la madrugada lo deje bajando Ubuntu Server y el Alternate, no tuve problemas, cuando me desperte la encontre en linea y no habia perdido conexion porque vi que fue bajando los emails durante toda la noche.
La verdad no se me ocurre cual puede ser el problema con la tarjeta WiFi y los backports.

---

### Post by vk-cdg on 2008-11-23
> **vk-cdg said:**
> Veremos entonces de instalar Intrepid!

Me venía resistiendo por estar con un LTS, pero tiene 2 mejoras fundamentales. El tema de la hibernada y el tema de la autocompilación de los drivers luego de un update del kernel.

Me pareció leer por ahí (en este foro) que si hago un update desde la 8.04 no voy a tener la funcionalidad de autocompilación ¿esto es así?
No me jode demasiado hacer un frash install ya que como tengo el /home separado y no tengo nada importante en la notebook (porque la llevo de acá para allá).

Bueno, volví a Hardy!
Les cuento... instalé Intrepid con una instalación desde cero (tengo el /home aparte). 
Luego de instalar todo y arrancar por primera vez con Intrepid queda en la barra de progreso por la mitad.. 20 minutos, una hora.... nada!
Si presiono (y mantengo apretada) la barra espaciadora o el enter termina de cargar intrepid y todo anda normal (digamos). Realmente no la probé mucho porque si el equipo no puede arrancar por si solo no me sirve.
Mas adelante habiendome sacado los finales de encima veré de actualizar desde Hardy, pero como la notebook la uso para rendir los parciales y finales de programación, la necesito.
No se que pueda ser...

---

### Post by luks911 on 2008-11-23
> **hictio said:**
> Cuando me fui a dormir en la madrugada lo deje bajando Ubuntu Server y el Alternate, no tuve problemas, cuando me desperte la encontre en linea y no habia perdido conexion porque vi que fue bajando los emails durante toda la noche.
La verdad no se me ocurre cual puede ser el problema con la tarjeta WiFi y los backports.

Y no aparece nada en los logs tampoco. Rarísimo. Salvo que sea el aMSN, pero como de lo que me devuelve dmesg no entiendo nada... cuando se actualice backports lo vuelvo a probar, a ver si hay cambios.

> **vk-cdg said:**
> Bueno, volví a Hardy!
Les cuento... instalé Intrepid con una instalación desde cero (tengo el /home aparte). 
Luego de instalar todo y arrancar por primera vez con Intrepid queda en la barra de progreso por la mitad.. 20 minutos, una hora.... nada!
Si presiono (y mantengo apretada) la barra espaciadora o el enter termina de cargar intrepid y todo anda normal (digamos). Realmente no la probé mucho porque si el equipo no puede arrancar por si solo no me sirve.
Mas adelante habiendome sacado los finales de encima veré de actualizar desde Hardy, pero como la notebook la uso para rendir los parciales y finales de programación, la necesito.
No se que pueda ser...

Otra rareza. Tenemos la misma máquina, ¿no? (Compaq F754). Yo tuve problemas al actualizar desde Hardy así que hice una instalación desde cero, también tengo el home aparte, y todo salió bien.

---

### Post by hictio on 2008-11-23
Tambien tengo el /home en una particion separada, instale Intrepid desde cero (la particion de /home la cree con esta instalacion)

---

### Post by vk-cdg on 2008-11-24
Creé este nuevo thread para no desvirtuar mas este.

[http://ubuntuforums.org/showthread.php?p=6240977](http://ubuntuforums.org/showthread.php?p=6240977)

Perdón!

---

### Post by vk-cdg on 2008-11-26
A los que tengan placa Atheros presten atención a esta noticia publicada en Ubuntu Life

[http://ubuntulife.wordpress.com/2008/11/26/solucionar-problemas-wifi-atheros/](http://ubuntulife.wordpress.com/2008/11/26/solucionar-problemas-wifi-atheros/)

Habrá que bajar la nueva iso y probarlo nomás!

---

### Post by hictio on 2008-11-28
Acabo de instalar (y rebootear :) ) todos estos updates:

```

2008-11-28 13:25:26 status installed man-db 2.5.2-2
2008-11-28 13:25:27 status installed doc-base 0.8.16
2008-11-28 13:25:28 status installed ufw 0.23.2
2008-11-28 13:25:29 status installed initramfs-tools 0.92bubuntu16
2008-11-28 13:26:22 status installed linux-image-2.6.27-9-generic 2.6.27-9.19
2008-11-28 13:26:34 status installed linux-backports-modules-2.6.27-9-generic 2.6.27-9.5
2008-11-28 13:26:34 status installed linux-restricted-modules-common 2.6.27-9.13
2008-11-28 13:26:47 status installed linux-restricted-modules-2.6.27-9-generic 2.6.27-9.13
2008-11-28 13:26:47 status installed xkb-data 1.3-2ubuntu4.2
2008-11-28 13:26:47 status installed libcups2 1.3.9-2ubuntu3
2008-11-28 13:26:47 status installed libcupsimage2 1.3.9-2ubuntu3
2008-11-28 13:26:47 status installed cups-common 1.3.9-2ubuntu3
2008-11-28 13:26:49 status installed cups 1.3.9-2ubuntu3
2008-11-28 13:26:49 status installed cups-client 1.3.9-2ubuntu3
2008-11-28 13:26:49 status installed cups-bsd 1.3.9-2ubuntu3
2008-11-28 13:26:49 status installed libgtkhtml-editor-common 1:3.24.1.1-0ubuntu1
2008-11-28 13:26:50 status installed libgtkhtml3.14-19 1:3.24.1.1-0ubuntu1
2008-11-28 13:26:50 status installed libgtkhtml-editor0 1:3.24.1.1-0ubuntu1
2008-11-28 13:26:50 status installed libwbclient0 2:3.2.3-1ubuntu3.3
2008-11-28 13:26:50 status installed libsmbclient 2:3.2.3-1ubuntu3.3
2008-11-28 13:26:50 status installed linux-backports-modules-intrepid-generic 2.6.27.9.13
2008-11-28 13:26:50 status installed linux-image-generic 2.6.27.9.13
2008-11-28 13:26:50 status installed linux-restricted-modules-generic 2.6.27.9.13
2008-11-28 13:26:50 status installed linux-generic 2.6.27.9.13
2008-11-28 13:26:50 status installed linux-headers-2.6.27-9 2.6.27-9.19
2008-11-28 13:26:52 status installed linux-headers-2.6.27-9-generic 2.6.27-9.19
2008-11-28 13:26:52 status installed linux-headers-generic 2.6.27.9.13
2008-11-28 13:26:52 status installed linux-libc-dev 2.6.27-9.19
2008-11-28 13:26:53 status installed samba-common 2:3.2.3-1ubuntu3.3
2008-11-28 13:26:53 status installed smbclient 2:3.2.3-1ubuntu3.3
2008-11-28 13:26:53 status installed language-pack-gnome-en 1:8.10+20081107
2008-11-28 13:26:53 status installed language-pack-gnome-en-base 1:8.10+20081107
2008-11-28 13:27:05 status installed initramfs-tools 0.92bubuntu16
2008-11-28 13:27:05 status installed libc6 2.8~20080505-0ubuntu7

```

Todo parece estar funcionando sin problemas, la Atheros conecto sin problemas. La verdad esta un poco preocupado por el update de kernel, y de backports, pero parece que la cosa sigue andando perfecto.

---

### Post by vk-cdg on 2008-11-28
Buen dato, ya me pongo a bajarla para ver que onda.

---

### Post by luks911 on 2008-11-29
> **hictio said:**
> Acabo de instalar (y rebootear :) ) todos estos updates:

```

2008-11-28 13:25:26 status installed man-db 2.5.2-2
2008-11-28 13:25:27 status installed doc-base 0.8.16
2008-11-28 13:25:28 status installed ufw 0.23.2
2008-11-28 13:25:29 status installed initramfs-tools 0.92bubuntu16
2008-11-28 13:26:22 status installed linux-image-2.6.27-9-generic 2.6.27-9.19
2008-11-28 13:26:34 status installed linux-backports-modules-2.6.27-9-generic 2.6.27-9.5
2008-11-28 13:26:34 status installed linux-restricted-modules-common 2.6.27-9.13
2008-11-28 13:26:47 status installed linux-restricted-modules-2.6.27-9-generic 2.6.27-9.13
2008-11-28 13:26:47 status installed xkb-data 1.3-2ubuntu4.2
2008-11-28 13:26:47 status installed libcups2 1.3.9-2ubuntu3
2008-11-28 13:26:47 status installed libcupsimage2 1.3.9-2ubuntu3
2008-11-28 13:26:47 status installed cups-common 1.3.9-2ubuntu3
2008-11-28 13:26:49 status installed cups 1.3.9-2ubuntu3
2008-11-28 13:26:49 status installed cups-client 1.3.9-2ubuntu3
2008-11-28 13:26:49 status installed cups-bsd 1.3.9-2ubuntu3
2008-11-28 13:26:49 status installed libgtkhtml-editor-common 1:3.24.1.1-0ubuntu1
2008-11-28 13:26:50 status installed libgtkhtml3.14-19 1:3.24.1.1-0ubuntu1
2008-11-28 13:26:50 status installed libgtkhtml-editor0 1:3.24.1.1-0ubuntu1
2008-11-28 13:26:50 status installed libwbclient0 2:3.2.3-1ubuntu3.3
2008-11-28 13:26:50 status installed libsmbclient 2:3.2.3-1ubuntu3.3
2008-11-28 13:26:50 status installed linux-backports-modules-intrepid-generic 2.6.27.9.13
2008-11-28 13:26:50 status installed linux-image-generic 2.6.27.9.13
2008-11-28 13:26:50 status installed linux-restricted-modules-generic 2.6.27.9.13
2008-11-28 13:26:50 status installed linux-generic 2.6.27.9.13
2008-11-28 13:26:50 status installed linux-headers-2.6.27-9 2.6.27-9.19
2008-11-28 13:26:52 status installed linux-headers-2.6.27-9-generic 2.6.27-9.19
2008-11-28 13:26:52 status installed linux-headers-generic 2.6.27.9.13
2008-11-28 13:26:52 status installed linux-libc-dev 2.6.27-9.19
2008-11-28 13:26:53 status installed samba-common 2:3.2.3-1ubuntu3.3
2008-11-28 13:26:53 status installed smbclient 2:3.2.3-1ubuntu3.3
2008-11-28 13:26:53 status installed language-pack-gnome-en 1:8.10+20081107
2008-11-28 13:26:53 status installed language-pack-gnome-en-base 1:8.10+20081107
2008-11-28 13:27:05 status installed initramfs-tools 0.92bubuntu16
2008-11-28 13:27:05 status installed libc6 2.8~20080505-0ubuntu7

```

Todo parece estar funcionando sin problemas, la Atheros conecto sin problemas. La verdad esta un poco preocupado por el update de kernel, y de backports, pero parece que la cosa sigue andando perfecto.

Tuve las mismas actualizaciones, claro, y volvi a los backports en lugar de compilar de nuevo madwifi. Al menos par aprobar si hay cambios con respecto a los cortes que tenía. Bueno, por ahora, la cosa mejoró. Siguen apareciendo esos mensajes en el dmesg pero con menos frecuencia y, lo más importante, no experimenté ningún corte de la conexión. Veremos cómo sigue.
Ah, me quedé sin la lucecita azul :lolflag:

---

### Post by luks911 on 2008-11-29
Pues volví adonde estaba. Sigo sin saber por qué, pero se volvió a cortar la conexión y a reproducirse como conejos los mensajes que recibía antes. Vuelvo a madwifi, vuelvo a la luz... azul.

---

### Post by hictio on 2008-11-29
Que mala pata! La mia siguio Ok, la use ayer en la madrugada, y hoy durante toda la ma~nana sin problemas.
Ahora la tengo apagada, apenas la prenda me fijo en el log (o en dmesg) para ver si tengo [esos mensajes tambien](http://ubuntuforums.org/showpost.php?p=6231298&postcount=26), creo haberlos visto, pero no estoy totalmente convencido.

---

### Post by niko_3100 on 2008-11-30
Muchachos y a todo esto como les funcionan las compaq? yo tengo una compaq v3614 y me anda barbaro, pero vieron que hubo una partida de compaq que vinieron todas falladas?? bueno quiero ver si todavia sigue o tienen algo de que quejarse.. yo de mi parte no tengo nada de que quejarme... jeje!! 
Si podrian postear el modelo y hace cuanto la tienen estaria joya asi vemos los usuarios de compaq si todavia siguen los problemas o no.

---

### Post by lega on 2008-11-30
La de mi señora anda bárbaro por ahora, ayer mi cuñado me comentó que la suya murió, me dijo que el modelo era "36nosecuanto" no se acordaba,yo no sabía que había una partida defectuosa, tenes idea que modelos son?

---

### Post by luks911 on 2008-11-30
La mía es una F754[0] a la que le agregué 1gb de RAM. No tuve ningún problema. Está bien que la uso sin la batería y no la muevo de casa, pero no me puedo quejar. La tengo desde marzo y es mi primera notebook. Salvo que otra vez el precio sea muy conveniente, haría todo lo posible por no volver a comprar una con win preinstalado, aunque sí volvería a HP. Y eso esta gente se lo debería agradecer en parte a Ubuntu, porque con Vista la máquina se arrastraba.
Y sí, ¿cómo es eso de partidas defectuosas?

[0] Pantalla de 15,4"
AMD Sempron Mobile 3600+
512 MB de RAM (ahora 1,5 GB)
Disco de 120 GB
Video Nvidia 7000M
Wifi Atheros AR5007EG
Webcam integrada

---

### Post by hictio on 2008-11-30
Yo tengo una F700 que me dieron en el trabajo, venia con 512 MB de RAM y el HDD de 80 GB con Vista Starter en Español, el agregaron 500 MB mas de RAM.
Le compre otro disco de 120 GB, y le saque el original, para poder instalar, desinstalar y formatear lo que se me ocurra...
Hasta ahora -la tengo desde principios de Abril de este año, la verdad- la máquina es un caño.
Lo unico que no me gusta, es que es muy plastica, ya empieza a tener un poco de "juego" la cosa, a ponerse esponjosa, pero bueno... 
La bateria es muy buena, en lo personal la c*g* a palazos, dura unas 3 hrs sin ponerme a ahorrar en nada.

Lo mejor de la laptop, conectarla a un monitor y teclado externo, es una verdadera masa.

---

### Post by niko_3100 on 2008-12-02
muchachos paso a contar, segun tengo entendido son modelos de la serie v3XXX o F5XX  habia una actualizacion de hp de la bios pero no lo solucionaba.. Yo tenia una v3415 con lo cual si estuve afectado, la lleve al servicio de hp compaq en luis maria campos y olleros y tardaron 20 dias en arreglarla, ahora esa misma notebook la tiene mi hermana y dice que no tiene ningun problema de nada, le anda re bien y rapidisima, tiene xp pero bueno... igual pase por una msi uqe no me termino de convencer por 2 meses (ojo son excelentes pero estaba super acostumbrado a las compaq), la vendi y me compre esta compaq v3614 y lo que hice por las dudas fue sacar una extension de la garnatia por un año mas directo en hp compaq, lo mejor uqe la saque en 6 cuotas sin itneres de $56 creo que eso fue un golazo. Supongo que si en dos años no tiene ningun problema, no va a tener en los siguientes años. 

Ahora como saber si su modelo esta dentro de los damnificados? Detras de las notebooks donde tienen el serial key del windows vista que les vino dice el modelo generico de la notebook, por ejemplo mi modelo es compaq presario v35XX con lo cual no es de la serie v3XXX damnificadas... las nuevas f7XX tampoco estan dentro de las notebooks damnificadas. Yo por ahora no tube ningun problema, le puse 2 gb mas de ram y me compre el control remoto de las hp pavillion y anda barbaro tanto en ubuntu como en vista...
La verdad que esta notebook la siento re comoda, el teclado, la pantalla todo me parece que por lo que la pague es un 10. El dia que esta no de para mas por viejita o por cag*da a palos sin duda va a ser otra compaq, yo estoy super conforme con las compaq.

Aca dejo los links directos de hp

v3xxx: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01318754&dlc=es&lc=es&cc=pe](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01318754&dlc=es&lc=es&cc=pe)

f5xx:  [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01489847&cc=es&lc=es&dlc=es](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01489847&cc=es&lc=es&dlc=es)

---

### Post by capa76 on 2008-12-07
Gracias viejo, me has liberado para siempre de Windows, ahora que el wifi me funciona (todo lo demás ya lo había hecho funcionar) nada me hará volver al lado de Microsoft.

Mil gracias y suerte.:D

---

### Post by eulins8 on 2009-03-15
Es la mejor opcion que hay en todo internet para solventar los problemas con este driver, mi equipo es un Compaq F755LA y la solucion es grandiosa. Probe con cuatro foros distintos donde habia que compilar hasta a su madre. Lo felicito por su aporte y mil gracias.

---

