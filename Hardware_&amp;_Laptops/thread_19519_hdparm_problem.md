---
title: "hdparm problem"
date: 2005-03-12
forum: Hardware &amp; Laptops
---

### Post by davidswe on 2005-03-12
I am trying to set dma to 'on' for my dvd burner. (I am trying to fix a choopy dvd playback problem) When I run the command 'sudo hdparm -d 1 /dev/hdc' I get the following message: /dev/hdc
                               setting using_dma to 1 (on)
                               HDIO_SET_DMA failed: operation not permitted
                               using_dma        = 0 (off)

How can I turn dma on for this dvd drive?


Thanks!

Dave

---

### Post by jeremy on 2005-03-13
I have exaclty the same problem, can anyone help?

---

### Post by kleeman on 2005-03-13
You need to change the order of some modules in /etc/modules. This has been discussed several times in this forum already: Search for dma.....

---

### Post by jeremy on 2005-03-13
thanks for your answer, I have searched already, but have not found a solution. Here is the content of my /etc/modules, can you see what needs changing?

sd_mod
psmouse
mousedev
ide-cd
ide-disk
ide-generic
lp

---

### Post by kleeman on 2005-03-13
Do you have amd or intel hardware? If you have intel try the following:

>I just got this to work by putting

>piix
>ide-core

>ABOVE

>ide-cd
>ide-disk
>ide-generic

>in /etc/modules

If you have amd try this:

Thanks for your reply. It didn't help directly but when searching for the previous post you quoted I found the solution. Adding amd74xx to /etc/modules before ide-cd helped!

Summary from posts I read:

VIA Chipset:
Add via82cxxx to your /etc/modules file before ide-cd.
Rboot and set dma with hdparm -d1 /dev/hdx (change x to your drive)

nForce Chipset (and amd):
Add amd74xx to your /etc/modules file before ide-cd.
Rboot and set dma with hdparm -d1 /dev/hdx (change x to your drive)


If you don't have any of the above chipset, do a lsmod to see which modules are loaded. Look at the ide related modules, the module you need to add might be listed there.

---

### Post by kleeman on 2005-03-13
BTW you need to reboot to get this to take effect

---

### Post by jeremy on 2005-03-13
many thanks for your trouble, I have intel and will try what you suggest in the morning. Time to get the kids to bed!

---

### Post by jeremy on 2005-03-14
kleeman, I did what you said, altered my /etc/modules to read;

sd_mod
psmouse
mousedev
piix
ide-core
ide-cd
ide-disk
ide-generic
lp

rebooted, and all is well, thank you very much.

---

### Post by JaF on 2005-05-24
[QUOTE=kleeman]Do you have amd or intel hardware? If you have intel try the following:

>I just got this to work by putting

>piix
>ide-core

>ABOVE

>ide-cd
>ide-disk
>ide-generic

>in /etc/modules

If you have amd try this:

Thanks for your reply. It didn't help directly but when searching for the previous post you quoted I found the solution. Adding amd74xx to /etc/modules before ide-cd helped!

Summary from posts I read:

VIA Chipset:
Add via82cxxx to your /etc/modules file before ide-cd.
Rboot and set dma with hdparm -d1 /dev/hdx (change x to your drive)

nForce Chipset (and amd):
Add amd74xx to your /etc/modules file before ide-cd.
Rboot and set dma with hdparm -d1 /dev/hdx (change x to your drive)


If you don't have any of the above chipset, do a lsmod to see which modules are loaded. Look at the ide related modules, the module you need to add might be listed there.[/QUOTE]
You absolute legend. I was very close to giving up on Ubuntu and Linux in general. But now I can watch my DVDs :D

---

### Post by brady on 2005-06-02
I had the same problem described and the fix suggested here worked like a charm for enabling DMA.  Many thanks for the tip.

---

### Post by mohaham on 2005-06-02
Alternatively you can also do the following:
[http://ubuntuguide.org/#speedupcddvdrom](http://ubuntuguide.org/#speedupcddvdrom)

---

### Post by krusbjorn on 2005-06-09
[QUOTE=kleeman]Do you have amd or intel hardware? If you have intel try the following:

>I just got this to work by putting

>piix
>ide-core

>ABOVE

>ide-cd
>ide-disk
>ide-generic

>in /etc/modules

If you have amd try this:

Thanks for your reply. It didn't help directly but when searching for the previous post you quoted I found the solution. Adding amd74xx to /etc/modules before ide-cd helped!

Summary from posts I read:

VIA Chipset:
Add via82cxxx to your /etc/modules file before ide-cd.
Rboot and set dma with hdparm -d1 /dev/hdx (change x to your drive)

nForce Chipset (and amd):
Add amd74xx to your /etc/modules file before ide-cd.
Rboot and set dma with hdparm -d1 /dev/hdx (change x to your drive)


If you don't have any of the above chipset, do a lsmod to see which modules are loaded. Look at the ide related modules, the module you need to add might be listed there.[/QUOTE]


thanks a million! finally this problem is solved :)

---

### Post by leperisland on 2005-07-07
Hello,

I have tried all the /etc/module stuff - it's running much better but the video is stilla  bit out of syc with the audio, I can't seem to set this DMA for my hard drive. i get:

root@leperisland:/home/localgirl # sudo hdparm -d 1 /dev/sda6

/dev/sda6:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device


I have an AMD system with an Asus 87N8X-E motherboard.

many thanks in advance,

Caroline

---

### Post by crouton on 2005-07-10
Do you have the indicated modules?  You might have complied them directly into the kernel.

---

### Post by leperisland on 2005-07-10
[QUOTE=crouton]Do you have the indicated modules?  You might have complied them directly into the kernel.[/QUOTE]

I'm sorry I'm not sure what you mean - I'm really new to all this.

---

### Post by GTvulse on 2005-07-10
[QUOTE=leperisland]
root@leperisland:/home/localgirl # sudo hdparm -d 1 /dev/sda6
[/QUOTE]

You don't apply hardware controller parameters to a disk partition! Use this instead:

```

sudo hdparm -d 1 /dev/sda

```

On another venue, if you are working as root you don't need to use sudo (but activating the root account ---by giving it a password---defeats the purpose of forcing the administrator to use sudo).

---

### Post by leperisland on 2005-07-11
[QUOTE=dradul]You don't apply hardware controller parameters to a disk partition! Use this instead:

```

sudo hdparm -d 1 /dev/sda

```
[/QUOTE]

Hello - thanks for the help but I'm afraid i get he same error:
```

 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

```

...and 'mount' gives me

```

root@leperisland:/home/localgirl # mount
/dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/hdc on /media/cdrom0 type udf (ro,noexec,nosuid,nodev,user=localgirl)
/dev/sdb1 on /media/LOCAL GIRL' type vfat (rw,nosuid,nodev,sync,noatime,quiet,uid=1000,gid=1000,umask=077,iocharset=utf8)

```

Thanks again,

Caroline

---

### Post by kleeman on 2005-07-11
Caroline,
You are using a scsi harddrive since your device is sda6. Scsi drives DO NOT use dma!
I know because I have one!

---

### Post by GTvulse on 2005-07-11
[QUOTE=kleeman]Caroline,
You are using a scsi harddrive since your device is sda6. Scsi drives DO NOT use dma!
I know because I have one![/QUOTE]
 Yes. I suspected as much as that, but I have the doubt of SATA drives being able to use DMA, and perhaps that's what Caroline has. I don't have a SATA drive to be able to say anything about it (probably will in the next rig... :-)) but I do know they show up as SCSI drives to the kernel (although they really are not, only the command set is SCSI compatible).

---

### Post by kleeman on 2005-07-11
OK fair point it may be sata but for sure scsi drives don't use dma  ;-)

---

### Post by leperisland on 2005-07-11
[QUOTE=kleeman]Caroline,
You are using a scsi harddrive since your device is sda6. Scsi drives DO NOT use dma!
I know because I have one![/QUOTE]

Thanks everyone so far. kleeman - do you have any trouble with DVD playback seeing as you have a SATA drive and can't set the DMA? Mine is slightly out of sync - very annoying especially as my Windows using friends now have even more excuse to laugh at me :D This must be solved! They must not win!

---

### Post by kleeman on 2005-07-11
DVD looks fine on my system no lags or whatever. From the gentoo hdparm guide:

[http://gentoo-wiki.com/HOWTO_Use_hdparm_to_improve_IDE_device_performance](http://gentoo-wiki.com/HOWTO_Use_hdparm_to_improve_IDE_device_performance)

I get "Operation not supported" errors on even basic commands such as 'hdparm -i'

You are probaly attempting to use hdparm on a SATA or some other bizarre drive. hdparm currently has very limited support for SATA drives however these drives are generally setup automagicly to use most of the more decent settings. You should be able to get the basic information (without the -i) and benchmarking to work. Try benchmarking the drive to check if you are getting good speeds (generally above 1000MB for cached reads and above 50MB for buffered reads). 




My benchmark result for "sudo hdparm -Tt /dev/sda"

/dev/sda:
 Timing cached reads:   4276 MB in  2.00 seconds = 2137.26 MB/sec
 Timing buffered disk reads:  198 MB in  3.02 seconds =  65.59 MB/sec

BTW I enabled dma on my DVD drive not my hard disk to get the performance improvement. Maybe you should look into improving the dvd drive not the hard disk (just a thought)

---

### Post by cosmolee on 2005-07-29
Worked for me too!  

But I must say that the amount of work required to find this fix just shows how far Linux is from being Desktop-ready for non-geeky users....  Windows users would have never gotten this far to get their DVD playback going.  They would have quit when they were told they had to get libdvdcss and edit their sources.list file to download it.

---

### Post by kleeman on 2005-07-29
Yeah I would say that the devs should ensure that dma is autoimatically enabled on a dvd drive afterall playing dvds adequately (no jumps) on such a drive would seem a good default setting to me  :)

---

### Post by gmatt on 2005-10-08
I cant set the DMA off:

I get:

useri@ubuntu:~$ sudo hdparm -d0 /dev/sda
Password:

/dev/sda:
 setting using_dma to 0 (off)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

lsmod:
...
ieee1394              101880  2 ohci1394,sbp2
rtc                    13448  0
psmouse                27908  0
mousedev               12260  1
parport_pc             36328  0
lp                     13576  0
parport                38540  2 parport_pc,lp
ide_disk               17152  0
md                     43904  0
ext3                  127632  1
jbd                    54960  1 ext3
thermal                15120  0
processor              25684  2 powernow_k8,thermal
fan                     5384  0
sd_mod                 18456  3
usbhid                 32416  0
ehci_hcd               31752  0
uhci_hcd               30368  0
sata_via               10244  0
skge                   37008  0
sata_promise           12548  4
libata                 52744  2 sata_via,sata_promise
scsi_mod              143984  5 sr_mod,sbp2,sd_mod,sata_promise,libata
ide_cd                 40608  0
cdrom                  36520  2 sr_mod,ide_cd
ide_generic             1920  0
via82cxxx              13488  1
ide_core              148932  4 ide_disk,ide_cd,ide_generic,via82cxxx
...

useri@ubuntu:~$ ls /dev/ | grep sda
sda
sda1
sda2
sda5


useri@ubuntu:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ide-core
via82cxxx
ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
rtc
sbp2
sr_mod
powernowd


useri@ubuntu:~$ lspci | grep -i ide
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)



any comments? please :'(

---

### Post by jimmah6786 on 2008-01-24
Question regarding the ide-core, piix?

Do I need to download deb packages for them, compile source?

How do I get those modules?

Thanks All

---

### Post by kleeman on 2008-01-25
No they should be there in a standard install just not loaded. Follow the howto above....

---

### Post by jimmah6786 on 2008-02-03
I really don't think I have those modules installed. I can't get DMA enable for the life of me. 

Heres my /etc/modules:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ide-cd
ide-disk
ide-generic
fuse
lp

Heres my lsmod:
 lsmod |grep ide
video                  18060  0 
ide_generic             2176  0 [permanent]
ide_disk               18560  0 
ide_cd                 32672  0 
ide_core              116804  4 ide_generic,ide_disk,ide_cd,usb_storage
cdrom                  37536  2 ide_cd,sr_mod

And here is were I try to enable DMA:
sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

.


I also tried using in the beginning of my /etc/modules
piix
ide-core

Machine is a Intel Xeon.

Thanks

Jim

---

### Post by Green_Star on 2008-04-16
Hi , I too have same problem, I donno how to fix this. I searched forum but didnt find useful help. I feel like my hdb is too slow (main disk for all my media and files). and sda freezes when ever i make some copy paste files (100-200mb files). hdb is too slow like if it is recording tv, then it is almost unusable, when ever it is recording i can not play any video, video play will keep freeze like when a online video buffering. same thing happens when i download some thing from internet and watch some video same time. 

Motherboard : GIGABYTE GA-K8N Pro-SLI 939 NVIDIA nForce4 SLI ATX AMD Motherboard with 1394b
Processor: AMD Athlon 64 3700+ San Diego 2.2GHz Socket 939 Single-Core Processor Model ADA3700BNBOX
OS: Ubuntu 710, 2.6.22-14-generic(not 64bit)

> sudo fdisk -l


Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2cc92cc8

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            4623        4865     1951897+  82  Linux swap / Solaris
/dev/hda3            2551        4622    16643340   83  Linux

Partition table entries are not in disk order

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x160baef7

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       30401   244196001   83  Linux

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14ffede8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8534    68545480+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            8535       34667   209913322+  83  Linux
/dev/sda3           34668       60801   209921355   83  Linux




>  sudo hdparm -Tt /dev/hdb1

/dev/hdb1:
 Timing cached reads:   1268 MB in  2.00 seconds = 633.88 MB/sec
 Timing buffered disk reads:   12 MB in  3.52 seconds =   3.41 MB/sec


>  sudo hdparm -d 1 /dev/hdb1

/dev/hdb1:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Invalid argument
 using_dma     =  0 (off)


>  cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2


---

