---
title: "Optical drive not detected - Panasonic Toughbook CF-48"
date: 2010-09-11
forum: Hardware
---

### Post by mightybrick on 2010-09-11
I've been searching for hours, but can't seem to find anything to help fix my problem. I installed 10.04, and have been very impressed. I was a PCLinuxOS user prior, but I may be converted if I am able to resolve this problem (this problem even crept up in the last few weeks in PCLinuxOS). Everything but my optical drive works flawlessly. I have a CD-RW/DVD-ROM drive in my laptop, but Ubuntu is unable to detect the presence of the drive. Any disc, burned, original, or blank, fails to be detected by the drive. The drive appears as if it is not installed when viewed in the disk utility. The drive works fine, as I used it for the installation of 10.04.
In terminal, for lshw -C drive I get:
```
brock@brock-laptop:~$ sudo lshw -C disk
  *-disk                  
       description: ATA Disk
       product: WDC WD1200BEVE-0
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WXC308963841
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000a8916

```In terminal, for wodim --devices I get:
```
brock@brock-laptop:~$ wodim --devices
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.

```It appears that the drive is not even recognized as being present in the machine.
I'm not sure what to try, or where to go from here. Would someone be able to point me in the right direction?
If it would help at all, here is the output for sudo lshw --short:
```
brock@brock-laptop:~$ sudo lshw -short
H/W path               Device     Class          Description
============================================================
                                  system         CF-48E4KFUKM
/0                                bus            CF48-5
/0/0                              memory         121KiB BIOS
/0/4                              processor      Intel(R) Pentium(R) M processor 1400MHz
/0/4/8                            memory         64KiB L1 cache
/0/4/9                            memory         1MiB L2 cache
/0/1d                             memory         System Memory
/0/1d/0                           memory         256MiB TSOP SDRAM Synchronous
/0/1d/1                           memory         512MiB DIMM SDRAM Synchronous
/0/1e                             memory         Flash Memory
/0/1e/0                           memory         512KiB TSOP FLASH Non-volatile
/0/1                              memory         
/0/2                              memory         
/0/100                            bridge         82855PM Processor to I/O Controller
/0/100/1                          bridge         82855PM Processor to AGP Controller
/0/100/1/0                        display        Radeon RV250 [Mobility FireGL 9000]
/0/100/1d                         bus            82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
/0/100/1d.1                       bus            82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
/0/100/1d.7                       bus            82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
/0/100/1e                         bridge         82801 Mobile PCI Bridge
/0/100/1e/0                       bridge         RL5c476 II
/0/100/1e/0.1                     bridge         RL5c476 II
/0/100/1e/2            eth0       network        RTL-8139/8139C/8139C+
/0/100/1e/3            eth1       network        PRO/Wireless LAN 2100 3B Mini PCI Adapter
/0/100/1f                         bridge         82801DBM (ICH4-M) LPC Interface Bridge
/0/100/1f.1            scsi0      storage        82801DBM (ICH4-M) IDE Controller
/0/100/1f.1/0.0.0      /dev/sda   disk           120GB WDC WD1200BEVE-0
/0/100/1f.1/0.0.0/1    /dev/sda1  volume         7946MiB Linux filesystem partition
/0/100/1f.1/0.0.0/2    /dev/sda2  volume         104GiB Extended partition
/0/100/1f.1/0.0.0/2/5  /dev/sda5  volume         4086MiB Linux swap / Solaris partition
/0/100/1f.1/0.0.0/2/6  /dev/sda6  volume         100GiB Linux filesystem partition
/0/100/1f.3                       bus            82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
/0/100/1f.5                       multimedia     82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
/0/100/1f.6                       communication  82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
/1                                power          CF-VZSU18A

```Thanks.

---

### Post by mightybrick on 2010-09-11
Here is a bump, in hopes that someone may spot this post and be able to pass along some helpful suggestions.

---

### Post by schily on 2010-09-12
wodim is defective do not expect it to be usable.

you need to remove wodim and anything from "cdrkit" and replace it by the working original software cdrtools.

cdrtools-3.00 is at: [ftp://ftp.berlios.de/pub/schily/](ftp://ftp.berlios.de/pub/schily/)

if you don't like to compile it yourself, get one of the various binary packages.

---

### Post by mightybrick on 2010-09-12
Thanks, Schily.
I've been a linux user for the last 3 years, but I'm very new to compiling and such. What would the recommended method of installation of cdrtools-3.00 be? Would you be willing to offer a basic walk-through? Thanks.

EDIT: I got it installed through this PPA: brandonsnider/cdrtools. The drive will now work once or twice, then quits working randomly until I reboot the machine. Also, DVDs won't work at all. Any further suggestions?

---

### Post by schily on 2010-09-13
> **mightybrick said:**
> Thanks, Schily.
EDIT: I got it installed through this PPA: brandonsnider/cdrtools. The drive will now work once or twice, then quits working randomly until I reboot the machine. Also, DVDs won't work at all. Any further suggestions?

This is not a problem caused by cdrecord but most likely by something like hald or similar or a problem in the kernel.

Without a specific error message, I cannot comment.

---

### Post by mightybrick on 2010-09-13
> **schily said:**
> This is not a problem caused by cdrecord but most likely by something like hald or similar or a problem in the kernel.

Without a specific error message, I cannot comment.
Thanks for your reply. Hmmm. Funny thing is I don't get any error messages, the drive just stops responding. Is there a log file anywhere I could check for any clues?

---

