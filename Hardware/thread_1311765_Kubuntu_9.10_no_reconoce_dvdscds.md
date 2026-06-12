---
title: "Kubuntu 9.10 no reconoce dvds/cds"
date: 2009-11-02
forum: Hardware
---

### Post by Piti on 2009-11-02
Hola, tengo este problema: tenía instalado Ubuntu 9.04. La grabadora de dvd andaba perfecto, en Windows también. El otro dia formateé la partición e instalé Kubuntu 9.10 desde cero, desde un cd-r. Lo raro es que ahora, con el sistema instalado y funcionando bien, no reconoce la grabadora. Pongo un dvd de datos, nada. Probe el cd de Kubuntu, y tampoco me muestra nada. Aca hay una captura de mis directorios /media y /dev, y el contenido de /etc/fstab:

[ATTACH]134414[/ATTACH]


Veo que en el fstab aparece /dev/scd0 correspondiendo a /media/cdrom0, pero en el directorio /dev no aparece scd0. No se cual podrá ser el dev correcto.

Gracias de antemano, saludos.

---

### Post by guillermolisi on 2009-11-02
Proba con > guille@guillepc:~$ ls -al /dev/sr*
brw-rw----+ 1 root cdrom 11, 0 2009-10-23 10:33 **/dev/sr0** en lugar de scd0.

---

### Post by Piti on 2009-11-02
Gracias por responder tan rápido. Probé lo que pusiste, pero no hay nada con sr. El unico que me parece que podria ser el cd es /dev/sg0, lo cambie en el fstab pero no funciono. Puse ls -al en /dev y me llama la atencion que ninguna entrada dice cdrom (choclo de texto a continuacion, si no va lo edito):

```
eml@bebop:/dev$ ls -al
total 4               
drwxr-xr-x  15 root root        3660 2009-11-02 19:11 .
drwxr-xr-x  21 root root        4096 2009-10-31 17:12 ..
crw-rw----+  1 root audio    14,  12 2009-11-02 19:11 adsp
crw-rw----+  1 root audio    14,   4 2009-11-02 19:11 audio
crw-rw----   1 root root     10,  59 2009-11-02 16:11 binder
drwxr-xr-x   2 root root         640 2009-11-02 16:11 block 
drwxr-xr-x   3 root root          60 2009-11-02 16:11 bus   
drwxr-xr-x   2 root root        3140 2009-11-02 19:11 char  
crw-------   1 root root      5,   1 2009-11-02 19:11 console
lrwxrwxrwx   1 root root          11 2009-11-02 19:11 core -> /proc/kcore
crw-rw----   1 root root     10,  58 2009-11-02 16:11 cpu_dma_latency    
drwxr-xr-x   6 root root         120 2009-11-02 16:11 disk               
crw-rw----+  1 root audio    14,   3 2009-11-02 19:11 dsp                
crw-rw----   1 root root     10,  62 2009-11-02 16:11 ecryptfs           
lrwxrwxrwx   1 root root          13 2009-11-02 19:11 fd -> /proc/self/fd
brw-rw----   1 root floppy    2,   0 2009-11-02 16:11 fd0                
crw-rw-rw-   1 root root      1,   7 2009-11-02 16:11 full               
crw-rw-rw-   1 root fuse     10, 229 2009-11-02 16:11 fuse               
crw-rw----   1 root root     10, 228 2009-11-02 16:11 hpet               
drwxr-xr-x   3 root root         100 2009-11-02 19:11 .initramfs         
-rw-r--r--   1 root root           0 2009-11-02 16:11 .initramfs-tools   
drwxr-xr-x   3 root root         240 2009-11-02 19:11 input              
crw-rw----   1 root root      1,  11 2009-11-02 16:11 kmsg               
srw-rw-rw-   1 root root           0 2009-11-02 19:11 log                
brw-rw----   1 root disk      7,   0 2009-11-02 16:11 loop0              
brw-rw----   1 root disk      7,   1 2009-11-02 16:11 loop1              
brw-rw----   1 root disk      7,   2 2009-11-02 16:11 loop2              
brw-rw----   1 root disk      7,   3 2009-11-02 16:11 loop3              
brw-rw----   1 root disk      7,   4 2009-11-02 16:11 loop4              
brw-rw----   1 root disk      7,   5 2009-11-02 16:11 loop5              
brw-rw----   1 root disk      7,   6 2009-11-02 16:11 loop6              
brw-rw----   1 root disk      7,   7 2009-11-02 16:11 loop7              
drwxr-xr-x   2 root root          60 2009-11-02 16:11 mapper             
crw-rw----   1 root root     10, 227 2009-11-02 16:11 mcelog             
crw-r-----   1 root kmem      1,   1 2009-11-02 16:11 mem                
crw-rw----+  1 root audio    14,   0 2009-11-02 19:11 mixer              
drwxr-xr-x   2 root root          60 2009-11-02 19:11 net                
crw-rw----   1 root root     10,  57 2009-11-02 16:11 network_latency    
crw-rw----   1 root root     10,  56 2009-11-02 16:11 network_throughput 
crw-rw-rw-   1 root root      1,   3 2009-11-02 16:11 null               
crw-rw-rw-   1 root root    195,   0 2009-11-02 19:11 nvidia0            
crw-rw-rw-   1 root root    195, 255 2009-11-02 19:11 nvidiactl          
crw-rw----   1 root root      1,  12 2009-11-02 16:11 oldmem             
drwxr-xr-x   2 root root          60 2009-11-02 16:11 pktcdvd            
crw-r-----   1 root kmem      1,   4 2009-11-02 16:11 port               
crw-------   1 root root    108,   0 2009-11-02 16:11 ppp                
crw-rw----   1 root root     10,   1 2009-11-02 16:11 psaux              
crw-rw-rw-   1 root tty       5,   2 2009-11-02 20:06 ptmx               
drwxr-xr-x   2 root root           0 2009-11-02 16:11 pts                
brw-rw----   1 root disk      1,   0 2009-11-02 16:11 ram0               
brw-rw----   1 root disk      1,   1 2009-11-02 16:11 ram1               
brw-rw----   1 root disk      1,  10 2009-11-02 16:11 ram10              
brw-rw----   1 root disk      1,  11 2009-11-02 16:11 ram11              
brw-rw----   1 root disk      1,  12 2009-11-02 16:11 ram12              
brw-rw----   1 root disk      1,  13 2009-11-02 16:11 ram13              
brw-rw----   1 root disk      1,  14 2009-11-02 16:11 ram14              
brw-rw----   1 root disk      1,  15 2009-11-02 16:11 ram15              
brw-rw----   1 root disk      1,   2 2009-11-02 16:11 ram2               
brw-rw----   1 root disk      1,   3 2009-11-02 16:11 ram3               
brw-rw----   1 root disk      1,   4 2009-11-02 16:11 ram4               
brw-rw----   1 root disk      1,   5 2009-11-02 16:11 ram5               
brw-rw----   1 root disk      1,   6 2009-11-02 16:11 ram6               
brw-rw----   1 root disk      1,   7 2009-11-02 16:11 ram7               
brw-rw----   1 root disk      1,   8 2009-11-02 16:11 ram8               
brw-rw----   1 root disk      1,   9 2009-11-02 16:11 ram9               
crw-rw-rw-   1 root root      1,   8 2009-11-02 16:11 random             
crw-r--r--   1 root root     10,  63 2009-11-02 16:11 rfkill             
lrwxrwxrwx   1 root root           4 2009-11-02 16:11 rtc -> rtc0        
crw-rw----   1 root root    254,   0 2009-11-02 16:11 rtc0               
brw-rw----   1 root disk      8,   0 2009-11-02 16:11 sda                
brw-rw----   1 root disk      8,   1 2009-11-02 19:39 sda1               
brw-rw----   1 root disk      8,   2 2009-11-02 16:11 sda2               
brw-rw----   1 root disk      8,   3 2009-11-02 16:11 sda3               
brw-rw----   1 root disk      8,   4 2009-11-02 16:11 sda4               
crw-rw----+  1 root audio    14,   1 2009-11-02 19:11 sequencer          
crw-rw----+  1 root audio    14,   8 2009-11-02 19:11 sequencer2         
crw-rw----   1 root disk     21,   0 2009-11-02 16:11 sg0                
drwxrwxrwt   2 root root          60 2009-11-02 19:11 shm                
crw-rw----   1 root root     10, 231 2009-11-02 16:11 snapshot           
drwxr-xr-x   3 root root         240 2009-11-02 19:11 snd                
lrwxrwxrwx   1 root root          24 2009-11-02 19:11 sndstat -> /proc/asound/oss/sndstat
lrwxrwxrwx   1 root root          15 2009-11-02 19:11 stderr -> /proc/self/fd/2          
lrwxrwxrwx   1 root root          15 2009-11-02 19:11 stdin -> /proc/self/fd/0           
lrwxrwxrwx   1 root root          15 2009-11-02 19:11 stdout -> /proc/self/fd/1          
crw-rw-rw-   1 root tty       5,   0 2009-11-02 19:43 tty                                
crw--w----   1 root root      4,   0 2009-11-02 16:11 tty0                               
crw-------   1 root root      4,   1 2009-11-02 19:11 tty1                               
crw--w----   1 root tty       4,  10 2009-11-02 16:11 tty10                              
crw--w----   1 root tty       4,  11 2009-11-02 16:11 tty11                              
crw--w----   1 root tty       4,  12 2009-11-02 16:11 tty12                              
crw--w----   1 root tty       4,  13 2009-11-02 16:11 tty13                              
crw--w----   1 root tty       4,  14 2009-11-02 16:11 tty14                              
crw--w----   1 root tty       4,  15 2009-11-02 16:11 tty15                              
crw--w----   1 root tty       4,  16 2009-11-02 16:11 tty16                              
crw--w----   1 root tty       4,  17 2009-11-02 16:11 tty17                              
crw--w----   1 root tty       4,  18 2009-11-02 16:11 tty18                              
crw--w----   1 root tty       4,  19 2009-11-02 16:11 tty19                              
crw-------   1 root root      4,   2 2009-11-02 19:11 tty2                               
crw--w----   1 root tty       4,  20 2009-11-02 16:11 tty20                              
crw--w----   1 root tty       4,  21 2009-11-02 16:11 tty21                              
crw--w----   1 root tty       4,  22 2009-11-02 16:11 tty22                              
crw--w----   1 root tty       4,  23 2009-11-02 16:11 tty23                              
crw--w----   1 root tty       4,  24 2009-11-02 16:11 tty24                              
crw--w----   1 root tty       4,  25 2009-11-02 16:11 tty25                              
crw--w----   1 root tty       4,  26 2009-11-02 16:11 tty26                              
crw--w----   1 root tty       4,  27 2009-11-02 16:11 tty27                              
crw--w----   1 root tty       4,  28 2009-11-02 16:11 tty28                              
crw--w----   1 root tty       4,  29 2009-11-02 16:11 tty29                              
crw-------   1 root root      4,   3 2009-11-02 19:11 tty3                               
crw--w----   1 root tty       4,  30 2009-11-02 16:11 tty30                              
crw--w----   1 root tty       4,  31 2009-11-02 16:11 tty31                              
crw--w----   1 root tty       4,  32 2009-11-02 16:11 tty32                              
crw--w----   1 root tty       4,  33 2009-11-02 16:11 tty33                              
crw--w----   1 root tty       4,  34 2009-11-02 16:11 tty34                              
crw--w----   1 root tty       4,  35 2009-11-02 16:11 tty35                              
crw--w----   1 root tty       4,  36 2009-11-02 16:11 tty36                              
crw--w----   1 root tty       4,  37 2009-11-02 16:11 tty37                              
crw--w----   1 root tty       4,  38 2009-11-02 16:11 tty38                              
crw--w----   1 root tty       4,  39 2009-11-02 16:11 tty39                              
crw-------   1 root root      4,   4 2009-11-02 19:11 tty4                               
crw--w----   1 root tty       4,  40 2009-11-02 16:11 tty40                              
crw--w----   1 root tty       4,  41 2009-11-02 16:11 tty41                              
crw--w----   1 root tty       4,  42 2009-11-02 16:11 tty42                              
crw--w----   1 root tty       4,  43 2009-11-02 16:11 tty43                              
crw--w----   1 root tty       4,  44 2009-11-02 16:11 tty44                              
crw--w----   1 root tty       4,  45 2009-11-02 16:11 tty45                              
crw--w----   1 root tty       4,  46 2009-11-02 16:11 tty46                              
crw--w----   1 root tty       4,  47 2009-11-02 16:11 tty47                              
crw--w----   1 root tty       4,  48 2009-11-02 16:11 tty48                              
crw--w----   1 root tty       4,  49 2009-11-02 16:11 tty49                              
crw-------   1 root root      4,   5 2009-11-02 19:11 tty5                               
crw--w----   1 root tty       4,  50 2009-11-02 16:11 tty50                              
crw--w----   1 root tty       4,  51 2009-11-02 16:11 tty51                              
crw--w----   1 root tty       4,  52 2009-11-02 16:11 tty52                              
crw--w----   1 root tty       4,  53 2009-11-02 16:11 tty53                              
crw--w----   1 root tty       4,  54 2009-11-02 16:11 tty54                              
crw--w----   1 root tty       4,  55 2009-11-02 16:11 tty55                              
crw--w----   1 root tty       4,  56 2009-11-02 16:11 tty56                              
crw--w----   1 root tty       4,  57 2009-11-02 16:11 tty57                              
crw--w----   1 root tty       4,  58 2009-11-02 16:11 tty58                              
crw--w----   1 root tty       4,  59 2009-11-02 16:11 tty59                              
crw-------   1 root root      4,   6 2009-11-02 19:11 tty6                               
crw--w----   1 root tty       4,  60 2009-11-02 16:11 tty60                              
crw--w----   1 root tty       4,  61 2009-11-02 16:11 tty61                              
crw--w----   1 root tty       4,  62 2009-11-02 16:11 tty62                              
crw--w----   1 root tty       4,  63 2009-11-02 16:11 tty63
crw--w----   1 root root      4,   7 2009-11-02 16:11 tty7
crw--w----   1 root tty       4,   8 2009-11-02 19:11 tty8
crw--w----   1 root tty       4,   9 2009-11-02 16:11 tty9
crw-rw----   1 root dialout   4,  64 2009-11-02 16:11 ttyS0
crw-rw----   1 root dialout   4,  65 2009-11-02 16:11 ttyS1
crw-rw----   1 root dialout   4,  66 2009-11-02 16:11 ttyS2
crw-rw----   1 root dialout   4,  67 2009-11-02 16:11 ttyS3
drwxr-xr-x   6 root root         140 2009-11-02 19:11 .udev
crw-rw-rw-   1 root root      1,   9 2009-11-02 19:11 urandom
crw-rw----   1 root root    253,   0 2009-11-02 16:11 usbmon0
crw-rw----   1 root root    253,   1 2009-11-02 16:11 usbmon1
crw-rw----   1 root root    253,   2 2009-11-02 16:11 usbmon2
crw-rw----   1 root root    253,   3 2009-11-02 16:11 usbmon3
crw-rw----   1 root root    253,   4 2009-11-02 16:11 usbmon4
crw-rw----   1 root root    253,   5 2009-11-02 16:11 usbmon5
crw-rw----   1 root root    253,   6 2009-11-02 16:11 usbmon6
crw-rw----   1 root root    253,   7 2009-11-02 16:11 usbmon7
crw-rw----   1 root root    253,   8 2009-11-02 16:11 usbmon8
crw-rw----   1 root tty       7,   0 2009-11-02 16:11 vcs
crw-rw----   1 root tty       7,   1 2009-11-02 16:11 vcs1
crw-rw----   1 root tty       7,   2 2009-11-02 16:11 vcs2
crw-rw----   1 root tty       7,   3 2009-11-02 16:11 vcs3
crw-rw----   1 root tty       7,   4 2009-11-02 16:11 vcs4
crw-rw----   1 root tty       7,   5 2009-11-02 16:11 vcs5
crw-rw----   1 root tty       7,   6 2009-11-02 16:11 vcs6
crw-rw----   1 root tty       7,   7 2009-11-02 19:11 vcs7
crw-rw----   1 root tty       7,   8 2009-11-02 16:11 vcs8
crw-rw----   1 root tty       7, 128 2009-11-02 16:11 vcsa
crw-rw----   1 root tty       7, 129 2009-11-02 16:11 vcsa1
crw-rw----   1 root tty       7, 130 2009-11-02 16:11 vcsa2
crw-rw----   1 root tty       7, 131 2009-11-02 16:11 vcsa3
crw-rw----   1 root tty       7, 132 2009-11-02 16:11 vcsa4
crw-rw----   1 root tty       7, 133 2009-11-02 16:11 vcsa5
crw-rw----   1 root tty       7, 134 2009-11-02 16:11 vcsa6
crw-rw----   1 root tty       7, 135 2009-11-02 19:11 vcsa7
crw-rw----   1 root tty       7, 136 2009-11-02 16:11 vcsa8
crw-rw-rw-   1 root root      1,   5 2009-11-02 16:11 zero

```

Despues probé con cat /proc/sys/dev/cdrom/info , pero me pone esto:

```
eml@bebop:/dev$ cat /proc/sys/dev/cdrom/info
CD-ROM information, Id: cdrom.c 3.20 2003/12/17

drive name:
drive speed:
drive # of slots:
Can close tray:
Can open tray:
Can lock tray:
Can change speed:
Can select disk:
Can read multisession:
Can read MCN:
Reports media changed:
Can play audio:
Can write CD-R:
Can write CD-RW:
Can read DVD:
Can write DVD-R:
Can write DVD-RAM:
Can read MRW:
Can write MRW:
Can write RAM:

```

Como si no existiese la unidad.

---

### Post by guillermolisi on 2009-11-02
En una terminal/consola ingresa ```
sudo lshw
``` y busca si aparece alguna seccion similar a la que muestro a continuacion
> *-ide:1                                                               
             description: IDE interface                                       
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE 
             vendor: VIA Technologies, Inc.                                   
             physical id: f.1                                                 
             bus info: pci@0000:00:0f.1                                       
             logical name: scsi2                                              
             version: 07                                                      
             width: 32 bits                                                   
             clock: 33MHz                                                     
             capabilities: ide pm bus_master cap_list emulated                
             configuration: driver=pata_via latency=32                        
           *-cdrom                                                            
                description: DVD writer                                       
                product: DVDRW SHW-160P6S                                     
                vendor: LITE-ON                                               
                physical id: 0.0.0                                            
                bus info: scsi@2:0.0.0                                        
                logical name: /dev/cdrom                                      
                logical name: /dev/cdrw                                       
                logical name: /dev/dvd                                        
                logical name: /dev/dvdrw                                      
                logical name: /dev/scd0                                       
                logical name: /dev/sr0                                        
                version: PS0C                                                 
                capabilities: removable audio cd-r cd-rw dvd dvd-r            
                configuration: ansiversion=5 status=nodisc
lo que pase corresponde a una unidad IDE de CDRom/DVD.
Si no aparece, revisaria conectores de datos y alimentacion de la unidad, por las dudas.

---

### Post by Piti on 2009-11-02
No aparece nada que diga cd/dvd/etc. Solo aparece esto:

>       *-ide:1
             description: IDE interface
             product: 82801JI (ICH10 Family) 2 port SATA IDE Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:19 ioport:b000(size=8) ioport:ac00(size=4) ioport:a880(size=8) ioport:a800(size=4) ioport:a480(size=16) ioport:a400(size=16)


En ide:0 esta mi disco rigido, y aparecen los 4 volumenes (ntfs, ntfs, ext4 y swap). Ah, el disco y la grabadora son SATA.

Por ahi tendria que ver en la Bios alguna opcion? Porque los esta tomando como IDE (o es asi?), por lo que se ve ahi.

Cuando pueda revisaría el tema de las conexiones, aunque sería medio raro ya que en Win y Ubuntu 9.04 anda bien. Incluso, Kubuntu 9.10 lo instale usando esta grabadora.

---

### Post by moreback on 2009-11-02
Prueba quitando la línea que habla del grabador de tu **/etc/fstab**, yo creo que eso puede estar causando confusión.

---

### Post by Piti on 2009-11-04
Acabo de prender la pc, y ahora resulta que el cd esta funcionando. Vaya uno a saber.

Igualmente, muchas gracias por responder.

---

