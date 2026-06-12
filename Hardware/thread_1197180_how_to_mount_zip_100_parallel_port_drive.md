---
title: "how to mount zip 100 parallel port drive"
date: 2009-06-25
forum: Hardware
---

### Post by makoshark55 on 2009-06-25
I have been looking for information on how to use my zip drive and have found some pages, but none of them are in newbish so I don't know how to implement them. I have got as far as creating the directory /usr/src/linux$ but I don't know how to do the xconfig.
here are the sources I have been using [http://www.ibiblio.org/pub/Linux/docs/HOWTO/ZIP-Drive](http://www.ibiblio.org/pub/Linux/docs/HOWTO/ZIP-Drive) and [http://www.tldp.org/HOWTO/ZIP-Drive-3.html](http://www.tldp.org/HOWTO/ZIP-Drive-3.html).
cinfigure the kernel:
```
·  cd /usr/src/linux


  ·  make xconfig

  ·  scsi support = Y

  ·  scsi disk support = Y

  ·  Iomega zip support as a module

  ·  printer support also as a module

  ·  save it and exit

  ·  make dep

  ·  make clean

  ·  make zImage or zlilo or zdisk

  ·  make modules

  ·  make modules_install

  Now to use the drive:

  ·  load the module insmod ppa

  ·  build a mounting point. mkdir /zip

  ·  insert a preformatted windoze type disk into the drive.

  ·  mount the disk.  mount -t vfat /dev/sda4 /zip

  ·  use any standard file commands as in  l /zip, ls /zip, df, cp,

  ·  when you are finished  umount /zip

``` and > You must begin the process of building a kernel with the configuration step.  Here, you identify the specific kernel components that you need. First step  cd /usr/src/linux. There are several ways to actually do the configuration. Under X windows I use  **make xconfig**. There is also make menuconfig or make config for command line prompts. The easiest way  is with xconfig.  
In the section **SCSI Support** set **SCSI support = Y**. Also set **SCSI disk support = Y**. 
In the section **SCSI low-level drivers** you want to set  **IOMEGA Parallel Port ZIP drive SCSI support = M**. The M stands for modules.  
In the section **Character Devices** find and set  **Parallell Printer support = M** 
If you are a bit unsure about any of this, use zdisk for the make step. This will build and install the kernel to floppy. If you  screw it up somehow, you still have a good bootable system on the hard drive.  
Now build the kernel with these steps: 

[LIST]
[*] make dep
[*] make clean
[*] make zImage or zlilo or zdisk
[*] make modules
[*] make mdoules_install
[/LIST]
 **hint** if you want to create an output log of the make zImage step you can use[INDENT]    make zImage 2>&1 | tee zImage.out
   [/INDENT][INDENT] I am just a little lost. any help would be great [/INDENT]

---

### Post by Manoel on 2009-06-28
Hi there. I don't know if it could help you but I found this page when trying to put my Iomega ZIP to work with Ubuntu: [https://help.ubuntu.com/community/IomegaZIPDrive](https://help.ubuntu.com/community/IomegaZIPDrive)

HTH

---

### Post by mark bower on 2009-06-28
I am using Ubuntu 9.04 and it automatically detects my internal Iomega Zip 100.  Hope this helps.

---

### Post by sdrisk8262 on 2010-01-03
[SIZE=2]Another LINUX NEWBIE, I have found several forums on how to install the IOMEGA PARALLEL PORT ZIP 100 drive. But none of them are for my version.  I have gotten the ZIP Drive to work but when I eject the disk and try another one it will not remount. I reboot and it is working again.  I have several disk that I want to view and edit but I dont want to have to reboot every time I switch disk.  Also the manual mount is not workng[/SIZE].

[SIZE=1][B][SIZE=2][COLOR=Red]Linux ubuntu-box 2.6.24-26-generic #1 SMP Tue Dec 1 18:37:31 UTC 2009 i686 GNU/Linu[/COLOR][/SIZE][COLOR=Red][SIZE=2]x

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 8.04.1
Release:    8.04
Codename:    hardy

_Attached devices:_
Host: scsi0 Channel: 00 Id: 00 Lun: 00
  Vendor: ATA      Model: SAMSUNG SP0411N  Rev: TW10
  Type:   Direct-Access                    ANSI  SCSI revision: 05
Host: scsi1 Channel: 00 Id: 00 Lun: 00
  Vendor: SONY     Model: CD-RW  CRX320E   Rev: NYK1
  Type:   CD-ROM                           ANSI  SCSI revision: 05
Host: scsi2 Channel: 00 Id: 06 Lun: 00
  Vendor: IOMEGA   Model: ZIP 100          Rev: K.05
  Type:   Direct-Access                    ANSI  SCSI revision: 02



[/SIZE][/COLOR][/B][/SIZE]

---

### Post by afrodeity on 2011-07-11
FAQ on mounting Zip Drive in 11.04 would be good.

---

### Post by mark bower on 2011-07-17
in both 9.10 and 10.10, my Iomega Zip 100s, internal IDE, are automatically detected on two computers, same M/B.

mark bower

---

### Post by stevemt on 2012-11-13
I have been able to mount my Iomega Zip 100 parallel drive, but I have one disc that is password protected that I cannot open  any suggestions

Many thanks in advance

STEVE

---

### Post by dwb814 on 2012-12-28
> **stevemt said:**
> I have been able to mount my Iomega Zip 100 parallel drive, but I have one disc that is password protected that I cannot open  any suggestions

Many thanks in advance

STEVE

If you have the password you can use mtools
[http://pkgs.org/ubuntu-12.04/ubuntu-main-i386/mtools_4.0.12-1_i386.deb.html](http://pkgs.org/ubuntu-12.04/ubuntu-main-i386/mtools_4.0.12-1_i386.deb.html)

to read about it put this in the terminal: ```
man mzip
```Hope that helps!

---

