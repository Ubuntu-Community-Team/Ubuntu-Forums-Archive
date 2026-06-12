---
title: "DVD/CD Drive not recognising any discs"
date: 2007-09-19
forum: Hardware &amp; Laptops
---

### Post by The Pinny Parlour on 2007-09-19
Hi all,

I have a Samsung Writemaster optical drive that refuses to recognise anything inserted into it.  any ideas on why this maybe?

Thank You,

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=4663ccde-5607-4e84-91c4-63cb9066c3ac / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=240afb1d-9520-4448-8c1c-f7739f1e1f4d none swap sw 0 0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by TaintedTux on 2007-09-20
Same here on my sister's laptop. Im afraid to say Im very close to dumping Ubuntu due to this issue and going with Arch as my box is. This is a necessity for her,and I need it fixed asap. And I must admit ive become quite displeased with the lack of support im receiving on forums and whatnot for Ubuntu. I posted a thread on this weeks ago and have 0 replies...in all honesty on the Arch forum I could bet you Id have 15 replies by now. Overall Im just not satisfied with Ubuntu and the eagerness of the Ubuntu community to help with problems. Im sorry if I offended anyone but this is my honest opinion, and I feel if you want to keep many users there prolly better be a LOT of bug fixes for Fiesty soon.

---

### Post by dabl on 2007-09-20
I'd like to see the outputs of:

```
fdisk -l
``` and

```
hwinfo
``` for your system.

FYI, using an "hd_" number is not normal for CD/DVD devices, although I don't know that it is a fatal mistake.  "hd" and "sd" are normally hard disk drives.  Here is some information that may be relevant to your issues -- look at the example fstab file:

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

On my Ubuntu and Kubuntu systems, the CD/DVD drive was numbered "/dev/scd0" at the time of installation -- you might want to give that a try rather than the way you have it now. Mine is mounted at /media/cdrom0, same as yours, so I think that is fine.

---

### Post by The Pinny Parlour on 2007-09-21
Thank you.

39: IDE 02.0: 10602 CD-ROM (DVD)
  [Created at block.222]
  UDI: /org/freedesktop/Hal/devices/storage_model_TSSTcorpCD/DVDW_SH_W162Z
  Unique ID: 90A1.KBLwJqZR8I9
  Parent ID: JCE+.mF7SxcIkSvE
  SysFS ID: /block/hdc
  SysFS BusID: 1.0
  SysFS Device Link: /devices/pci0000:00/0000:00:02.5/ide1/1.0
  Hardware Class: cdrom
  Model: "TSSTcorpCD/DVDW SH-W162Z"
  Vendor: "TSSTcorpCD/DVDW"
  Device: "SH-W162Z"
  Driver: "SIS_IDE", "ide-cdrom"
  Driver Modules: "sis5513", "ide_cd"
  Device File: /dev/hdc
  Device Files: /dev/hdc, /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw, /dev/disk/by-path/pci-0000:00:02.5-ide-1:0
  Device Number: block 22:0
  Features: CD-R, CD-RW, DVD, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+DL
  Size: 0 sectors a 512 bytes
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #17 (IDE interface)
  Drive Speed: 48

---

### Post by The Pinny Parlour on 2007-09-21
Thanks dabl.

Your suggestions helped me to understand my fstab and edit it. Outcome, everything works successfully.

Many thanks for the link to TuxFiles.org.

Regards,

---

### Post by ilheu on 2007-09-30
This is the output of my hwinfo for my DVD/CD drive:

 [HTML] 59: SCSI 00.0: 10602 CD-ROM (DVD)
  [Created at block.222]
  UDI: /org/freedesktop/Hal/devices/storage_model_CD/DVDW_TS_H552U
  Unique ID: twPO.pl4JSMLximE
  Parent ID: 3p2J.Sv9GVhzxoc5
  SysFS ID: /block/sr0
  SysFS BusID: 0:0:0:0
  SysFS Device Link: /devices/pci0000:00/0000:00:1f.1/host0/target0:0:0/0:0:0:0
  Hardware Class: cdrom
  Model: "TSSTcorp CD/DVDW TS-H552U"
  Vendor: "TSSTcorp"
  Device: "CD/DVDW TS-H552U"
  Revision: "US03"
  Driver: "ata_piix", "sr"
  Driver Modules: "ata_piix"
  Device File: /dev/sr0 (/dev/sg0)
  Device Files: /dev/sr0, /dev/scd0, /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw, /dev/disk/by-path/pci-0000:00:1f.1-scsi-0:0:0:0
  Device Number: block 11:0 (char 21:0)
  Features: CD-R, CD-RW, DVD, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD+DL
  Drive status: no medium
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #25 (IDE interface)
  Drive Speed: 48[/HTML]

my /etc/fstab looks like this:

[HTML]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=dee3c220-2617-40ac-9599-0cc713bec927 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
UUID=d132c077-b1d2-44c7-8d76-015436453f87 /home           ext3    defaults        0       2
# /dev/sda1
UUID=6f8d1b8c-7ffe-4de6-a884-51f2b13b2360 none            swap    sw              0       0
/dev/sr0      /media/cdrom0   udf,iso9660 user,noauto     0       0
#
# sudo manually mounted disks
#
# /dev/hda1
UUID=e5567b55-d57b-45c0-94b1-c833d3afff09 /mnt/data1           ext3    defaults        0       0
# /dev/hdd1
UUID=935fd467-fafa-4740-9b8f-b9eac6420074 /mnt/data2           ext3    defaults        0       0
#

# Generated by Automatix
## End of Automatix mounted partitions[/HTML]


yet I can not browse the content of any CD or DVD does anyone have any more ideas? I am not able to manually mount and/or automount any media.

I should also add that I've also tried to mount as /dev/scd0 ; /dev/cdrom; /dev/sr0 and still no luck... this is the output of my maually mount command:

rui@atoll:~$ sudo mount /media/cdrom0
mount: No medium found

maybe it has to do with format? This is the output of  dmesg | grep CD

[HTML][    4.254046] scsi 0:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-H552U US03 PQ: 0 ANSI: 5
[    6.169039] Uniform CD-ROM driver Revision: 3.20
[    6.169093] sr 0:0:0:0: Attached scsi CD-ROM sr0
[  884.108136] Unable to identify CD-ROM format.
[/HTML]

No sure what else to try :confused:

---

### Post by posta_boy03 on 2007-09-30
Im having the same problem. Ive used mine for over a year to burn both CD's and DVD's just fine. And just within the last wk anytime i put any form of media(CD-R, CD-RW, DVD-R, DVD-RW) it doesnt recognize the disk whether its blank or not. It just tells me to insert blank disk. I would try what was suggested but i don't undestand what all of that means. Is there anyone that can walk me through how to fix my problem? Don't know if it matters but I'm using XP and i use Roxio for CD burning but for dvd's i use Clone DVD and Anydvd but primarily i use ConvertXtoDVD for movies that i have downloaded from diff. torrent sites. But like I said even when using Roxio to try to make a music CD i just get "insert blank disk" If anyone out there can help I would greatly appreciate it!

---

### Post by cameran on 2007-10-01
i am having this problem too.  there are lots of threads on this weird error but they all get abandoned.  spent all day on this and spent a lot of time in #ubuntu as well.  no help.  launchpad has several entries about this problem too but they are either abandoned or have a cryptic "fix released" thing or something but nowhere to get the fix.  

i'm a linux server admin and if i can't get simple DVDs to work, imagine a person all excited to leave windows who finds they can't do this? and all they find on the forums are dozens of abandoned threads on this problem.

it kicked in for me this week as well - wondering if there was an update that could be the problem?

---

### Post by dabl on 2007-10-02
@ilheu -- Somehow your drive was assigned /dev/sr0, as per the fstab line.  But the mount line looks fine, it's not obvious why it shouldn't work.

I'm going to ask this gently:  Did it used to work, before you used Automatix to do something else?  I don't like to trash-talk things, but sometimes things that used to be OK before you used Automatix aren't OK any more .....

Also, the transition from Edgy to Feisty featured quite a bumpy conversion to something called wodim drivers for optical drives, and I'm frankly no expert, but as a Feisty beta tester, I went a few weeks with off-and-on functionality in my CD/DVD drive.  But I see "ata_piix" showing as the relevant driver for yours.  Hmmmmmmmmmmm.  You might want to search this forum on that term, and see if there are fixable issues.  That's about as much as I can offer -- sorry I don't have a golden bullet for you.  :)

---

### Post by reckik on 2007-10-17
Same problem here and looking for a fix for a while now. The abandened post do really suck ;)

---

### Post by evil_cat on 2007-10-23
This works fine for me


"sudo modprobe ide_generic"
:guitar:
For some reason, ide_generic driver doesn't load automatically.. Possibly the kernel or what ever feels it's unnecessary as we already have main hard disk support

ide_generic will load ide_cd and cdrom modules automatically.

---

