---
title: "Xubuntu LL: Se me cuelga el entorno grafico"
date: 2010-10-12
forum: Hardware
---

### Post by sergiom99 on 2010-10-12
Hola gente, hace un par de dias me empezo a suceder que se cuelga violentamente el entorno grafico, no responde a ningun tipo de teclas, pero sigo pudiendo entrar por ssh.
Datos utiles extraidos con fuch [0]


```

Distributor ID:    Ubuntu
Description:	Ubuntu 10.04.1 LTS
Release:	10.04
Codename:	lucid

#aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: CMI8738 [C-Media CMI8738], dispositivo 0: CMI8738 [C-Media PCI DAC/ADC]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: CMI8738 [C-Media CMI8738], dispositivo 1: CMI8738 [C-Media PCI 2nd DAC]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: CMI8738 [C-Media CMI8738], dispositivo 2: CMI8738 [C-Media PCI IEC958]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

#lspci | grep -i audio
00:0a.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

#asoundconf list

#cat /proc/asound/cards
 0 [CMI8738        ]: CMI8738 - C-Media CMI8738
                      C-Media CMI8738 (model 37) at 0xe000, irq 10

#lsmod | grep -i snd
snd_cmipci             30437  4 
gameport                9089  1 snd_cmipci
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  2 snd_pcm_oss
snd_pcm                70694  2 snd_cmipci,snd_pcm_oss
snd_page_alloc          7076  1 snd_pcm
snd_opl3_lib            8966  1 snd_cmipci
snd_hwdep               5412  1 snd_opl3_lib
snd_mpu401_uart         5617  1 snd_cmipci
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  3 snd_pcm,snd_opl3_lib,snd_seq
snd_seq_device          5700  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  18 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  2 snd

#lsof /dev/snd/controlC0 /dev/snd/pcmC0D0c /dev/snd/pcmC0D0p
                        /dev/snd/pcmC0D1p /dev/snd/pcmC0D2c /dev/snd/seq /dev/snd/timer
COMMAND    PID   USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
xfce4-vol 1355 sergio    9u   CHR 116,11      0t0 3562 /dev/snd/controlC0
pulseaudi 1357 sergio   20u   CHR 116,11      0t0 3562 /dev/snd/controlC0
pulseaudi 1357 sergio   26u   CHR 116,11      0t0 3562 /dev/snd/controlC0

#df -h
S.ficheros            Tamaño Usado  Disp Uso% Montado en
/dev/sda1             8,3G  3,0G  4,9G  38% /
none                  245M  264K  245M   1% /dev
none                  249M  180K  249M   1% /dev/shm
none                  249M  320K  249M   1% /var/run
none                  249M     0  249M   0% /var/lock
none                  249M     0  249M   0% /lib/init/rw
/dev/sdb1              38G   19G   18G  53% /home

#free -tm
             total       used       free     shared    buffers     cached
Mem:           497        438         59          0         52        238
-/+ buffers/cache:        147        350
Swap:         1056          0       1056
Total:        1554        438       1116

#mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdb1 on /home type ext3 (rw)

#fdisk -l

Disco /dev/sda: 10.1 GB, 10110320640 bytes
255 cabezas, 63 sectores/pista, 1229 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x1c4c4d2f

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        1095     8789062+  83  Linux
/dev/sda2            1095        1230     1082368   82  Linux swap / Solaris

Disco /dev/sdb: 41.1 GB, 41110142976 bytes
255 cabezas, 63 sectores/pista, 4998 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x16341634

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1        4998    40146403+  83  Linux

#ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:01:02:78:76:06  
          Direc. inet:192.168.1.55  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::201:2ff:fe78:7606/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:3983 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:5614 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:299489 (299.4 KB)  TX bytes:4472110 (4.4 MB)
          Interrupción:11 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:16 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:16 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:960 (960.0 B)  TX bytes:960 (960.0 B)


#dmesg |grep eth
[   42.526899] eth0:  setting full-duplex.
[   53.192038] eth0: no IPv6 routers present

#cat /etc/network/interfaces
auto lo
iface lo inet loopback


#cat /etc/resolv.conf
# Generated by NetworkManager
domain HUSKY01
search HUSKY01
nameserver 208.67.222.222
nameserver 208.67.220.220
nameserver 192.168.1.1

#lspci|grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX200] (rev b2)

#cat /var/log/Xorg.0.log|grep EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) AIGLX error: dlopen of /usr/lib/dri/nouveau_vieux_dri.so failed (/usr/lib/dri/nouveau_vieux_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering

#cat /var/log/messages |grep error

#cat /var/log/syslog |grep error
Oct 12 17:51:45 desktop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Oct 12 17:51:49 desktop gnome-session[955]: WARNING: Could not launch application 'metacity.desktop': Unable to start application: Ha ocurrido un error al ejecutar el proceso hijo «metacity» (No existe el archivo o directorio)
Oct 12 17:51:49 desktop gnome-session[955]: WARNING: Could not launch application 'gnome-power-manager.desktop': Unable to start application: Ha ocurrido un error al ejecutar el proceso hijo «gnome-power-manager» (No existe el archivo o directorio)
Oct 12 21:21:53 desktop NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Oct 12 21:21:57 desktop gnome-session[996]: WARNING: Could not launch application 'metacity.desktop': Unable to start application: Ha ocurrido un error al ejecutar el proceso hijo «metacity» (No existe el archivo o directorio)
Oct 12 21:21:57 desktop gnome-session[996]: WARNING: Could not launch application 'gnome-power-manager.desktop': Unable to start application: Ha ocurrido un error al ejecutar el proceso hijo «gnome-power-manager» (No existe el archivo o directorio)

#lsmod |grep drm
drm_kms_helper         29297  1 nouveau
drm                   162409  4 nouveau,ttm,drm_kms_helper
agpgart                31724  3 ttm,drm,via_agp

#lsmod |grep agp
via_agp                 5310  1 
agpgart                31724  3 ttm,drm,via_agp

#glxinfo |grep direct

#iwconfig

#cat /proc/net/wireless
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22

#lsmod |grep wlan && lsmod |grep ath && lsmod |grep ra

#cat /etc/network/interfaces
auto lo
iface lo inet loopback




```

Alguien se le ocurre donde puedo empezar a buscar algo?



[0]http://ubuntuforums.org/showthread.php?t=1211568

---

### Post by guillermolisi on 2010-10-13
Si no lei mal, estas usando driver Noveau para la placa de video y en algun lugar menciona que fallo 
Antes estabas con un driver nVidia ?

Tambien fallo la carga de gnome-power-manager (y Metacity, pero esto puede ser por el driver de video).

No hay errores relacionados con ACPI en los logs de arranque ?

---

### Post by sergiom99 on 2010-10-13
de ACPI no se ve nada, puede ser que haya empezado despues de alguno de estos updates:

```

Start-Date: 2010-10-08  23:15:35
Upgrade: dmsetup (1.02.39-1ubuntu4, 1.02.39-1ubuntu4.1), libkrb5-3 (1.8.1+dfsg-2ubuntu0.2, 1.8.1+dfsg-2ubuntu0.3), libkrb5support0 (1.8.1+dfsg-2ubuntu0.2,
 1.8.1+dfsg-2ubuntu0.3), python-software-properties (0.75.10, 0.75.10.1), avahi-daemon (0.6.25-1ubuntu6, 0.6.25-1ubuntu6.1), libavahi-common-data (0.6.25-
1ubuntu6, 0.6.25-1ubuntu6.1), screen (4.0.3-14ubuntu1, 4.0.3-14ubuntu1.2), cups-driver-gutenprint (5.2.5-0ubuntu1, 5.2.5-0ubuntu1.1), avahi-utils (0.6.25-
1ubuntu6, 0.6.25-1ubuntu6.1), libdevmapper1.02.1 (1.02.39-1ubuntu4, 1.02.39-1ubuntu4.1), libk5crypto3 (1.8.1+dfsg-2ubuntu0.2, 1.8.1+dfsg-2ubuntu0.3), core
utils (7.4-2ubuntu2, 7.4-2ubuntu3), python-imaging (1.1.7-1, 1.1.7-1ubuntu0.1), gdm (2.30.2.is.2.30.0-0ubuntu3, 2.30.2.is.2.30.0-0ubuntu4), libavahi-gobje
ct0 (0.6.25-1ubuntu6, 0.6.25-1ubuntu6.1), libgutenprint2 (5.2.5-0ubuntu1, 5.2.5-0ubuntu1.1), avahi-autoipd (0.6.25-1ubuntu6, 0.6.25-1ubuntu6.1), tar (1.22
-2, 1.22-2ubuntu1), software-properties-gtk (0.75.10, 0.75.10.1), libavahi-client3 (0.6.25-1ubuntu6, 0.6.25-1ubuntu6.1), libgksu2-0 (2.0.13~pre1-1ubuntu4,
 2.0.13~pre1-1ubuntu4.1), libssl0.9.8 (0.9.8k-7ubuntu8.1, 0.9.8k-7ubuntu8.3), openssl (0.9.8k-7ubuntu8.1, 0.9.8k-7ubuntu8.3), libavahi-glib1 (0.6.25-1ubun
tu6, 0.6.25-1ubuntu6.1), libgssapi-krb5-2 (1.8.1+dfsg-2ubuntu0.2, 1.8.1+dfsg-2ubuntu0.3), libavahi-common3 (0.6.25-1ubuntu6, 0.6.25-1ubuntu6.1), libavahi-
ui0 (0.6.25-1ubuntu6, 0.6.25-1ubuntu6.1), libavahi-core6 (0.6.25-1ubuntu6, 0.6.25-1ubuntu6.1)
End-Date: 2010-10-08  23:19:58
Start-Date: 2010-10-11  12:15:19
Install: linux-image-2.6.32-25-generic (2.6.32-25.44)
Upgrade: linux-image-generic (2.6.32.24.25, 2.6.32.25.27), tzdata-java (2010l-0ubuntu0.10.04, 2010m-0ubuntu0.10.04), tzdata (2010l-0ubuntu0.10.04, 2010m-0ubuntu0.10.04), linux-generic (2.6.32.24.25, 2.6.32.25.27)
End-Date: 2010-10-11  12:20:06

```


Siempre use los nVidia, es una placa viejita en una PIII viejita.
Como uso Xubuntu, nunca le di bola al error de gnome.

Gracias Guille!

---

### Post by sergiom99 on 2010-10-13
Parece que viene por otro lado.
Recien estaba descomprimiendo un rar en varias partes, habia parado el gdm y estaba desde TTY1, asi que solo consola texto. 
De repente se congelo todo y quedaron las luces de CAPS LOCK y NUM LOCK titilando, no respondia nada y tampoco se veia actividad de disco.

No se que log mirar, porque el /var/log/messages arranca desde que lo rebooteo.

Lo que habia comentado antes desde el Xfce era dejandola prendida con un programita .jar liviano corriendo (Jdownloader), no es que la estaba usando y tenia muchas cosas abiertas.

ideas?

---

### Post by juancarlospaco on 2010-10-13
Hace en una terminal:
**sudo touch /forcefsck && sudo reboot**

Va a reiniciar la PC, luego Bootea desde LiveCD y pasale full el MemTest86+

:)

---

### Post by sergiom99 on 2010-10-14
> **juancarlospaco said:**
> Hace en una terminal:
**sudo touch /forcefsck && sudo reboot**

Va a reiniciar la PC, luego Bootea desde LiveCD y pasale full el MemTest86+

:)

OK, el primer reboot lo dejo normal, no? para que corra el chequeo de discos y despues le paso el memtest?

Gracias JC!

---

### Post by juancarlospaco on 2010-10-14
Si.

Se viene el calor, limpien las PC adentro, 
un destornillador y un aerosol de aire comprimido deshumidificado sale $30, 
*una placa madre nueva y micro ni  te cuento...*

---

### Post by guillermolisi on 2010-10-14
El orden de estos factores no altera el producto, podes pasar primero el memtest y despues correr el fsck. De hecho, si sospechara de las memorias, pasaria primero el memtest para evitar problemas cuando corra el fsck por errores en la RAM.

---

### Post by sergiom99 on 2010-10-14
Afirmativamente, un modulo de memoria tira errores. Ahora tengo que ver cual es y empezar a revolver la chatarra a ver si consigo alguno que vaya en este mother.

Gracias!

---

### Post by juancarlospaco on 2010-10-14
*Jejeje...* Me parecia por los sintomas, suerte con eso!

---

### Post by guillermolisi on 2010-10-14
> **sergiom99 said:**
> Afirmativamente, un modulo de memoria tira errores. Ahora tengo que ver cual es y empezar a revolver la chatarra a ver si consigo alguno que vaya en este mother.

Gracias!
Que tipo de memoria necesitas ?

---

### Post by sergiom99 on 2010-10-15
Creo que son modulos DIMM PC133, para un mother de PIII.
Consegui 2x512Mb (duplique!) en el esqueleto de un server, que estoy probando ahora mismo con el Memtest86+ v4.0.

Gracias Guille!

---

