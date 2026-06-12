---
title: "Ubuntu 9.04 partitioning problem"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by SourceV on 2009-04-26
Hi,

I have a similar problem to post [http://ubuntuforums.org/showthread.php?t=1137972](http://ubuntuforums.org/showthread.php?t=1137972).

I wonder if you could you please help me fixing this frustrating problem.


Here is the output:
```

ronen@RonenLT:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7f20ebf6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+   7  HPFS/NTFS
/dev/sda2            1825       13833    96462292+   5  Extended
/dev/sda3           13834       14593     6104700    7  HPFS/NTFS
/dev/sda4           13460       13833     3004123+  82  Linux swap / Solaris
/dev/sda5            1825        3040     9767457   83  Linux
/dev/sda6            3041        8511    43945776   83  Linux
/dev/sda7            8512       13459    39744778+  83  Linux

Partition table entries are not in disk order
ronen@RonenLT:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7f20ebf6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    29302559    14651248+   7  HPFS/NTFS
/dev/sda2        29302560   222227144    96462292+   5  Extended
/dev/sda3       222227145   234436544     6104700    7  HPFS/NTFS
/dev/sda4       216218898   222227144     3004123+  82  Linux swap / Solaris
/dev/sda5        29302686    48837599     9767457   83  Linux
/dev/sda6        48837663   136729214    43945776   83  Linux
/dev/sda7       136729278   216218834    39744778+  83  Linux

Partition table entries are not in disk order
ronen@RonenLT:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 29302497, Id= 7, bootable
/dev/sda2 : start= 29302560, size=192924585, Id= 5
/dev/sda3 : start=222227145, size= 12209400, Id= 7
/dev/sda4 : start=216218898, size=  6008247, Id=82
/dev/sda5 : start= 29302686, size= 19534914, Id=83
/dev/sda6 : start= 48837663, size= 87891552, Id=83
/dev/sda7 : start=136729278, size= 79489557, Id=83
ronen@RonenLT:~$

```


Thanks.

Please let me know if you need further information.

---

### Post by meierfra. on 2009-04-26
Download the attached file "PT.txt" to your Desktop and open a terminal. Rewrite your partition table via


```

sudo sfdisk -f --no-reread  -O ~/Desktop/OldPT.save /dev/sda < ~/Desktop/PT.txt

```

Post the output of that commmand.
Just as a precaution, copy the file OldPT.save to a save place outside your hard drive (Flashdrive, online storage, email account,...)

---

### Post by SourceV on 2009-04-27
It worked.

Thank you so much.

---

### Post by meierfra. on 2009-04-27
> It worked.
Great.

> Thank you so much.
You are welcome.

---

### Post by O-pos on 2009-04-29
I have the same problem. Ubuntu 9.04 does not recognize any of my partitions.

Here is the output:
 ```

:~$ sudo fdisk -l
[sudo] password for pos: 
omitting empty partition (5)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0d27c8b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            3736       27587   191591190    5  Extended
/dev/sda3           27102       27587     3903795   83  Linux
/dev/sda4           27588       29654    16603177+  83  Linux
/dev/sda5            3736       27100   187679299+  83  Linux
:~$
 
```

 ```

:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf0d27c8b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    41945714    20972826    7  HPFS/NTFS
/dev/sda2        60002775   443185154   191591190    5  Extended
/dev/sda3       435377565   443185154     3903795   83  Linux
/dev/sda4       443185155   476391509    16603177+  83  Linux
/dev/sda5        60002901   435361499   187679299+  83  Linux
:~$ 
 
```

I would like to have an overview of these partitions to have an opportunity to adjust / keep them as needed, as it was the case with previous ubuntu installers. How can I change my PT file?

---

### Post by meierfra. on 2009-04-29
Could you also post the output of

```
sudo sfdisk -d
sudo grub
```

and at the "grub>" prompt

```
find /boot/grub/stage2
find /grub/stage2 
```

---

### Post by armagumen on 2009-05-02
Hi guys, i've got the same problem while trying to install 9.04, could you please help me fix this? I've tried with Gparted & partition magic, but none of them recogize the partitions.

```

armando@AgDell1520:~$ sudo fdisk -l
[sudo] password for armando:

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pistas, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0000000

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *       19131       19458     2627777    c  W95 FAT32 (LBA)
/dev/sda2              14        1319    10490419+   7  HPFS/NTFS
/dev/sda3   *        1320       14562   106374397+   7  HPFS/NTFS
/dev/sda4           14563       19131    36699281    f  W95 Ext'd (LBA)
La partición 4 no termina en un límite de cilindro.
/dev/sda5           19131       19458     2620416   dd  Desconocido
/dev/sda6   *       14563       18937    35142124+  83  Linux
/dev/sda7           18938       19130     1550241   82  Linux swap / Solaris



``````

armando@AgDell1520:~$ sudo fdisk -lu

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pistas, 19457 cilindros, 312581808 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Disk identifier: 0xd0000000

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *   307337216   312592769     2627777    c  W95 FAT32 (LBA)
/dev/sda2          208896    21189734    10490419+   7  HPFS/NTFS
/dev/sda3   *    21189735   233938529   106374397+   7  HPFS/NTFS
/dev/sda4       233938654   307337215    36699281    f  W95 Ext'd (LBA)
La partición 4 no termina en un límite de cilindro.
/dev/sda5       307337216   312578047     2620416   dd  Desconocido
/dev/sda6   *   233938656   304222904    35142124+  83  Linux
/dev/sda7       304222968   307323449     1550241   82  Linux swap / Solaris


``````

armando@AgDell1520:~$ sudo sfdisk -d
Atención: la partición extendida no empieza en un límite de cilindro.
DOS y Linux interpretarán el contenido de forma diferente.
# tabla de particiones de /dev/sda
unit: sectors

/dev/sda1 : start=307337216, size=  5255554, Id= c, bootable
/dev/sda2 : start=   208896, size= 20980839, Id= 7
/dev/sda3 : start= 21189735, size=212748795, Id= 7, bootable
/dev/sda4 : start=233938654, size= 73398562, Id= f
/dev/sda5 : start=307337216, size=  5240832, Id=dd
/dev/sda6 : start=233938656, size= 70284249, Id=83, bootable
/dev/sda7 : start=304222968, size=  3100482, Id=82


``````

grub> find /boot/grub/stage2
 (hd0,5)

``````

grub> find /grub/stage2

Error 15: File not found



```By the way i have vista & Hardy Heron installed. Thanks!

---

### Post by meierfra. on 2009-05-02
```
[COLOR="Red"]/dev/sda1   *   307337216   [COLOR="Blue"]312592769 [/COLOR]    2627777    c  W95 FAT32 [/COLOR](LBA)
/dev/sda2          208896    21189734    10490419+   7  HPFS/NTFS
/dev/sda3   *    21189735   233938529   106374397+   7  HPFS/NTFS
/dev/sda4       233938654   307337215    36699281    f  W95 Ext'd (LBA)
La partición 4 no termina en un límite de cilindro.
[COLOR="Red"]/dev/sda5       307337216   [COLOR="Blue"]312578047 [/COLOR]    2620416   dd  Desconocido[/COLOR]
```


Your Media Direct partition seems to be listed twice on your partition table, but with slightly different end  points.

So I suggested to use testdisk to figure out  what the correct ending is:

Download the [testdisk package](http://www.cgsecurity.org/testdisk-6.11.1.linux26.tar.bz2) to your desktop, and then do:

```

cd ~/Desktop
tar xvf testdisk-6.11.1.linux26.tar.bz2
sudo testdisk-6.11/linux/testdisk_static /dev/sda

```

After starting testdisk with the above command, choose
"Proceed",
"Intel",
"Analyze",
"Quick search",
Press "Y" or "N" (depending whether you have any partition created by Vista)
Press "Enter" to continue,
select "Deeper Search" (so it does a deeper search, which could take a while)

Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing.

---

### Post by armagumen on 2009-05-03
[B] Hi! Deeper Search shows this:
[/B]```

Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1    12 254 63     208782 [DellUtility]
D FAT32 LBA               13   0  1  4190 254 63   67119570 [NO NAME]
D HPFS - NTFS             13   0 52  1318 107  5   20971520 [RECOVERY]
[COLOR=Red]D HPFS - NTFS           1318 107  5  2623 213 21   20971520
D HPFS - NTFS           1318 107  6 14561 106 58  212748785
D HPFS - NTFS           1318 107  6 19130 185 63  286154752[/COLOR]
D HPFS - NTFS           1319   0  1 14561 254 63  212748795 [OS]
D Linux                14562   2  1 18936 254 62   70284248
[COLOR=Red]D Linux                14569 139 35 18944 137 33   70284248
D Linux                14570   2  1 18944 254 62   70284248[/COLOR]
D Linux Swap           18937   1  1 19129 254 45    3100464
P FAT32 LBA            19130 218 33 19457  21 20    5240832 [MEDIADIRECT]
Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT16, 106 MB / 101 MiB

```
 Those on red showed me that cannot read filesystem, that may be corrupted

Linux Swap did not showed anything whe i pressed "p".

---

### Post by meierfra. on 2009-05-03
At the screen with  the results of the Deep search, use the arrrow keys to mark the partitions as follows:

```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1    12 254 63     208782 [DellUtility]
D FAT32 LBA               13   0  1  4190 254 63   67119570 [NO NAME]
[COLOR="Red"]P[/COLOR] HPFS - NTFS             13   0 52  1318 107  5   20971520 [RECOVERY]
D HPFS - NTFS           1318 107  5  2623 213 21   20971520
D HPFS - NTFS           1318 107  6 14561 106 58  212748785
D HPFS - NTFS           1318 107  6 19130 185 63  286154752
[COLOR="Red"]P[/COLOR] HPFS - NTFS           1319   0  1 14561 254 63  212748795 [OS]
[COLOR="Red"]L[/COLOR] Linux                14562   2  1 18936 254 62   70284248
D Linux                14569 139 35 18944 137 33   70284248
D Linux                14570   2  1 18944 254 62   70284248
[COLOR="Red"]L[/COLOR] Linux Swap           18937   1  1 19129 254 45    3100464
[COLOR="Red"]L[/COLOR] FAT32 LBA            19130 218 33 19457  21 20    5240832 [MEDIADIRECT]
```

Then press "enter" to continue.

If you have an "extd part" tab in the bottom row,  select it and press enter to minimize the size of the extended parttiton.

Then  choose "write".

---

### Post by armagumen on 2009-05-04
Hi , i did it and there is a poblem loading the grub, it shows me *Error 17* while trying to load, i also tried to install ubuntu 9.04 but still not recognises partitions

---

### Post by meierfra. on 2009-05-04
> Hi , i did it and there is a poblem loading the grub, it shows me *Error 17* while trying to load,

Sorry, I should have told you to reinstall grub. Boot from the Ubuntu LiveCD, open a terminal and type

```
sudo grub
```

and at the grub prompt:

```
find /boot/grub/stage2
```
this should return  "(hd0,4)"

```
root (hd0,4)   (use whatever was returned by "find")
setup (hd0)
quit
```

This should take care of grub error 17.


> ubuntu 9.04 but still not recognises partitions 
Strange. Please post the output

```
sudo fdisk -lu
sudo sfdisk -d
sudo parted /dev/sda print
```

---

### Post by armagumen on 2009-05-04
Grub fixed, but it can't mount Hardy Heron partition, Error 17 when trying to do it.
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       307337216   312578047     2620416    c  W95 FAT32 (LBA)
/dev/sda2          208896    21180415    10485760    7  HPFS/NTFS
/dev/sda3   *    21189735   233938529   106374397+   7  HPFS/NTFS
/dev/sda4       233938530   312592769    39327120    f  W95 Ext'd (LBA)
/dev/sda5       233938656   304222903    35142124   83  Linux
/dev/sda6       304222968   307323431     1550232   82  Linux swap / Solaris
/dev/sda7       307337216   312578047     2620416    c  W95 FAT32 (LBA)


```

```

ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=307337216, size=  5240832, Id= c
/dev/sda2 : start=   208896, size= 20971520, Id= 7
/dev/sda3 : start= 21189735, size=212748795, Id= 7, bootable
/dev/sda4 : start=233938530, size= 78654240, Id= f
/dev/sda5 : start=233938656, size= 70284248, Id=83
/dev/sda6 : start=304222968, size=  3100464, Id=82
/dev/sda7 : start=307337216, size=  5240832, Id= c

```

```

ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: Can't have a partition outside the disk! 

```

---

### Post by meierfra. on 2009-05-04
> but it can't mount Hardy Heron partition, Error 17 when trying to do it.

Sorry, I did not realize you were using Hardy. Hardy still uses "root" instead of "uuid" on menu.lst and you will need to edit "menu.lst".

 Do this:

at the grub menu at boot-up select "ubuntu". But do not press "enter". Press "E" instead. At the next screen press "E" again.  Change

root (hd0,5)

to

root (hd0,4)

Press "enter" to get back to the previous screen and then "b" to boot.
This should boot you into ubuntu.

Open a terminal in Ubuntu and open the file "menu.lst" via

```
gksudo gedit /boot/grub/menu.lst
```

Change

# groot=(hd0,5)

to

# groot=(hd0,4)

Save the file. Back in the terminal type

```
sudo update-grub
```


That should be enough to cure your Grub error 17.


Your partition table is messed up again:
 ```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1       307337216   312578047     2620416    c  W95 FAT32 (LBA)
/dev/sda7       307337216   312578047     2620416    c  W95 FAT32 (LBA)
```

Did you use the Media direct button after you fixed the partition table with testdisk?


Also testdisk made your extended partition to large.  So let's use "sfdisk" to fix your partition table. Download the attached file PT.txt to your desktop. Then

```

sudo sfdisk -f --no-reread  -O ~/Desktop/OldPT.save /dev/sda < ~/Desktop/PT.txt

```


Just as a precaution, post the output of that command. Also  copy the file
OldPT.save to a save place outside your hard drive (Flashdrive, online
storage,email account,...)

You should now be able to install Ubuntu 9.04.  **Do not use the Media Direct button** until after you install Ubuntu 9.04.

---

### Post by armagumen on 2009-05-05
Hi! In first place THANK YOU SO MUCH =D it worked perfectly, I'm posting from 9.04 !! & I think I've learned a little in the meantime. 

And sorry, I did press the button when noticed the grub was not working , and it fixed the grub, but still not recognising partitions, so i followed all the steps again, but thiss time did't worked.

After that I did exactly what you told me and worked perfect! I'll post the output just in case as you said
```

rmando@AgDell1520:~/Escritorio$ sudo sfdisk -f --no-reread -O ~/Escritorio/OldPT.save /dev/sda < ~/Escritorio/PT.txt

Disco /dev/sda: 19457 cilindros, 255 cabezas, 63 sectores/pista
Situación anterior:
Unidades = cilindros de 8225280 bytes, bloques de 1024 bytes, contando desde 0

   Disp.  Inic. Princ.   Fin   Nºcil    Nºbloq.   Id  Sistema
/dev/sda1          0+     12      13-    104391    6  FAT16
/dev/sda2         13+   1318-   1306-  10485760    7  HPFS/NTFS
/dev/sda3   *   1319   14561   13243  106374397+   7  HPFS/NTFS
/dev/sda4      14562   19457    4896   39327120    f  W95 Ext'd (LBA)
/dev/sda5      14562+  18936-   4375-  35142124   83  Linux
/dev/sda6      18937+  19129-    193-   1550232   82  Linux swap / Solaris
/dev/sda7      19130+  19457-    327-   2620416    c  W95 FAT32 (LBA)
Atención: el tamaño dado (5240832) supera el tamaño máximo permitido (5239489)
Situación nueva:
Unidades = sectores de 512 bytes, contando desde 0

   Disp.  Inicio  Principio   Fin   Nº sect.  Id  Sistema
/dev/sda1     307337216 312578047    5240832   c  W95 FAT32 (LBA)
/dev/sda2        208896  21180415   20971520   7  HPFS/NTFS
/dev/sda3   *  21189735 233938529  212748795   7  HPFS/NTFS
/dev/sda4     233938530 307323431   73384902   f  W95 Ext'd (LBA)
/dev/sda5     233938656 304222903   70284248  83  Linux
/dev/sda6     304222968 307323431    3100464  82  Linux swap / Solaris
Atención: la partición 1 finaliza más allá del final del disco
La nueva tabla de particiones se ha escrito correctamente

Volviendo a leer la tabla de particiones...
BLKRRPART: Dispositivo ó recurso ocupado
La orden para volver a leer la tabla de particiones ha fallado.
Reinicie el sistema ahora, antes de utilizar mkfs.

Si ha creado o modificado una partición DOS, como /dev/foo7, utilice dd(1)
para poner a cero los 512 primeros bytes: dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(Véase fdisk(8).)

```

THANK YOU AGAIN!!! I hope i can contribute to the forum in the future

---

