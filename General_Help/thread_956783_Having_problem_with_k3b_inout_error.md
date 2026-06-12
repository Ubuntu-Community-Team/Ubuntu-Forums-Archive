---
title: "Having problem with k3b in/out error"
date: 2008-10-23
forum: General Help
---

### Post by Kover on 2008-10-23
Hello you guys,

I have a problem on k3b ¨fatal error at startup: input/output error"
Have search this forum and with Google but I cant find a solution.
(I want to install osx86 :))

```
System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.24-19-generic
Devices
-----------------------
Optiarc DVD RW AD-7173S 1-00 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R96R, Restricted Overwrite, Layer Jump]

Burned media
-----------------------
DVD-RW Restricted Overwrite

Used versions
-----------------------
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
:-[ READ TRACK INFORMATION failed with SK=5h/ASC=24h/ACQ=00h]: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2294272 -speed=4 -use-the-force-luke=bufsize:32m 


```

---

### Post by Kover on 2008-10-25
Bump!

---

### Post by CorneliusBear on 2009-06-12
I also have this problem when trying to burn DVD iso files to DVD+R dual layer mediums using k3b.  The error message in k3b is similar to that posted above.

Here's some additional output from ```
dmesg | tail -n 10
```:

```
[1230722.098235] cdrom: This disc doesn't have any tracks I recognize!
[1230722.109091] end_request: I/O error, dev sr1, sector 0
[1230722.109098] Buffer I/O error on device sr1, logical block 0
[1230722.134321] end_request: I/O error, dev sr1, sector 0
[1230722.134331] Buffer I/O error on device sr1, logical block 0
[1230784.159978] warning: `growisofs' uses 32-bit capabilities (legacy support in use)
```

Anyone been able to resolve this?

Here's my output from lshw:

```
*-cdrom:1                                                                                                        
         description: DVD reader                                                                                     
                product: DVD+RW ND-3100AD                                                                                   
                vendor: _NEC                                                                                                
                physical id: 0.1.0                                                                                          
                bus info: scsi@4:0.1.0                                                                                      
                logical name: /dev/cdrom                                                                                    
                logical name: /dev/cdrw                                                                                     
                logical name: /dev/dvd                                                                                      
                logical name: /dev/scd1                                                                                     
                logical name: /dev/sr1                                                                                      
                version: 107E                                                                                               
                serial: [_NEC    DVD+RW ND-3100AD107E04061100                                                               
                capabilities: removable audio cd-r cd-rw dvd                                                                
                configuration: ansiversion=5 status=ready                                                                   
              *-medium                                                                                                      
                   physical id: 0                                                                                           
                   logical name: /dev/cdrom
```

---

### Post by CorneliusBear on 2009-06-12
Also, the output of k3b:

```
System
-----------------------
K3b Version: 1.0.5

KDE Version: 3.5.10
QT Version:  3.3.8b
Kernel:      2.6.28-11-generic
Devices
-----------------------
HL-DT-ST DVD-ROM GDR8163B 0D20 (/dev/sr0, ) [CD-ROM, DVD-ROM] [DVD-ROM, CD-ROM] [None]

_NEC DVD+RW ND-3100AD 107E (/dev/sr1, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96R, RAW/R96R]
Burned media
-----------------------
DVD+R Dual Layer

Used versions
-----------------------
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/sr1 obs=32k seek=0'
/dev/sr1: splitting layers at 2003456 blocks
:-[ SEND DVD+R DOUBLE LAYER RECORDING INFORMATION failed with SK=3h/NO SEEK COMPLETE]: Input/output error
```

---

### Post by albinootje on 2009-06-12
> **Kover said:**
>  I have a problem on k3b ¨fatal error at startup: input/output error"

Can you burn without problems in other programs ?

Please post the output of the following :
```

dpkg -l|grep cdrecord
dpkg -l|grep wodim
dpkg -l|grep k3b
lsb_release -r

```

---

