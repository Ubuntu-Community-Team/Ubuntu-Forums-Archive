---
title: "Second Hard Drive: Unmountable!"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by brottmayer on 2009-01-23
Hello,

First off, I just started using Ubuntu 8.10 Intrepid Ibex about a week ago. During the initial booting, it recognized my three hard drives. Two internal hard drives and one external.

Everything was fine and I was able to work on it with no problem. But now, it is telling me that my second hard drive cannot be mounted.

I have no idea as to why or how! But if someone could help me in figuring this out it would be greatly appreciated. Since this contains all of my data.

Thanks,
Brandon.

---

### Post by utnubuuser on 2009-01-23
Does your harddisk show up if you type lspci in a terminal?

or rather,  dmesg | grep -i scsi

---

### Post by brottmayer on 2009-01-23
To tell you the truth i don't think so, but i could be mistaken. Here's a copy of what was brought up when I ran that code in the terminal window:

```

brottmayer@brottmayer-desktop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]
02:01.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
brottmayer@brottmayer-desktop:~$ 

```

---

### Post by utnubuuser on 2009-01-23
ok,  try the second comand  and maybe sudo dmesg | grep -i disk

---

### Post by brottmayer on 2009-01-23
Yes it does show the second hard drive, the one that says WDC WD3000JB-00K 08.0

```

brottmayer@brottmayer-desktop:~$ dmesg | grep -i scsi
[    2.390175] SCSI subsystem initialized
[    3.116808] scsi0 : pata_atiixp
[    3.116916] scsi1 : pata_atiixp
[    3.556623] scsi 0:0:0:0: Direct-Access     ATA      ST3200826A       3.03 PQ: 0 ANSI: 5
[    3.557190] scsi 0:0:1:0: Direct-Access     ATA      WDC WD3000JB-00K 08.0 PQ: 0 ANSI: 5
[    3.557852] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-H552B GA04 PQ: 0 ANSI: 5
[    3.558168] scsi 1:0:1:0: CD-ROM            LITE-ON  CD-ROM LTN-489S  8GS4 PQ: 0 ANSI: 5
[    3.633343] scsi2 : sata_sil
[    3.633431] scsi3 : sata_sil
[    3.703961] scsi4 : SCSI emulation for USB Mass Storage devices
[    3.704223] scsi5 : SCSI emulation for USB Mass Storage devices
[    3.722102] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    3.722146] scsi 0:0:1:0: Attached scsi generic sg1 type 0
[    3.722182] scsi 1:0:0:0: Attached scsi generic sg2 type 5
[    3.722214] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[    4.272193] scsi6 : sata_sil
[    4.272631] scsi7 : sata_sil
[    5.004862] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.084681] sd 0:0:1:0: [sdb] Attached SCSI disk
[    5.093697] sr0: scsi3-mmc drive: 1x/48x writer cd/rw xa/form2 cdda tray
[    5.093804] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    5.096520] sr1: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    5.096572] sr 1:0:1:0: Attached scsi CD-ROM sr1
[    8.711130] scsi 5:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    8.717112] scsi 5:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    8.723104] scsi 5:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    8.729110] scsi 5:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    8.739567] scsi 4:0:0:0: Direct-Access     SAMSUNG  SV0813H          RJ10 PQ: 0 ANSI: 0
[    8.744779] sd 4:0:0:0: [sdc] Attached SCSI disk
[    8.744918] sd 4:0:0:0: Attached scsi generic sg4 type 0
[    8.754161] sd 5:0:0:0: [sdd] Attached SCSI removable disk
[    8.754208] sd 5:0:0:0: Attached scsi generic sg5 type 0
[    8.764152] sd 5:0:0:1: [sde] Attached SCSI removable disk
[    8.764203] sd 5:0:0:1: Attached scsi generic sg6 type 0
[    8.774144] sd 5:0:0:2: [sdf] Attached SCSI removable disk
[    8.774199] sd 5:0:0:2: Attached scsi generic sg7 type 0
[    8.784143] sd 5:0:0:3: [sdg] Attached SCSI removable disk
[    8.784202] sd 5:0:0:3: Attached scsi generic sg8 type 0
brottmayer@brottmayer-desktop:~$ 

```

---

### Post by utnubuuser on 2009-01-24
ok, your harddisks are there,

how about  sudo fdisk -l

---

### Post by brottmayer on 2009-01-24
```

brottmayer@brottmayer-desktop:~$ sudo fdisk -l
[sudo] password for brottmayer: 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38ef9d17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23330   187398193+  83  Linux
/dev/sda2           23331       24321     7960207+   5  Extended
/dev/sda5           23331       24321     7960176   82  Linux swap / Solaris

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xde852189

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36481   293033601   42  SFS

Disk /dev/sdc: 80.0 GB, 80060423680 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeecc8afe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9732    78172258+   c  W95 FAT32 (LBA)
brottmayer@brottmayer-desktop:~$ 

```

---

### Post by utnubuuser on 2009-01-24
and your 200 and 300 gig drives are internal, and the 80 external.  Is that right?

And also,  this setup worked for a while, then suddenly stopped working?

And does the second hd show-up in your "Places"?

---

### Post by brottmayer on 2009-01-24
and your 200 and 300 gig drives are internal, and the 80 external. Is that right?

[COLOR="Blue"]Yes. The 200 and 300 are internal and the 80 is external.[/COLOR]

And also, this setup worked for a while, then suddenly stopped working?

[COLOR="Blue"]Yes. That is correct. I was able to use the second hard drive for viewing and saving onto. [/COLOR]

And does the second hd show-up in your "Places"? 

[COLOR="Blue"]Yes, it does show up in my Places under Computer.[/COLOR]

---

### Post by utnubuuser on 2009-01-24
I'm just trying to re-locate a posting on here with the exact same prob.  Found one about two weeks ago.

---

### Post by brottmayer on 2009-01-24
Thank you very much for helping me with this!

Brandon.

---

### Post by utnubuuser on 2009-01-24
try:  sudo mount -a

---

### Post by brottmayer on 2009-01-24
I entered the code as you mentioned and tried to mount the volume. While opening it I got this error message:

> 
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


And when I tried to manually mount it i get this error message:

> 
mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)


Thanks.

---

### Post by utnubuuser on 2009-01-24
Could I have a look at  sudo gedit /etc/fstab

---

### Post by brottmayer on 2009-01-24
Here you go:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2a5cf923-9046-42ca-9461-e576e793a6fb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=2e60f972-037f-4291-a701-e7716c4d32db none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


---

### Post by utnubuuser on 2009-01-24
and:  df

---

### Post by brottmayer on 2009-01-24
OK, The Vault is my external hard drive:

> 
brottmayer@brottmayer-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            184457332  13118332 161969092   8% /
tmpfs                  1490636         0   1490636   0% /lib/init/rw
varrun                 1490636       212   1490424   1% /var/run
varlock                1490636         0   1490636   0% /var/lock
udev                   1490636      2800   1487836   1% /dev
tmpfs                  1490636        24   1490612   1% /dev/shm
lrm                    1490636      2000   1488636   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdc1             78153152  45280672  32872480  58% /media/THE VAULT
brottmayer@brottmayer-desktop:~$ 



---

### Post by utnubuuser on 2009-01-24
Have you tried unmounting?

---

### Post by utnubuuser on 2009-01-24
try: sudo unmount /dev/sdb1

---

### Post by utnubuuser on 2009-01-24
and then try: sudo mount /dev/sdb1

---

### Post by brottmayer on 2009-01-24
OK, before doing this, I just want to be sure that i won't lose the data that is already on the hard drive, right?

---

### Post by utnubuuser on 2009-01-24
another quick question;  don't suppose there's an icon for the second hd on the desktop?

I wa reading another posting where they tried mounting/unmounting unsuccefully once, but managed to get it after several attempts

---

### Post by utnubuuser on 2009-01-24
should be safe,   your first harddisk is sda,  second sdb and external sdc

To be really safe,  restart the comp with a livecd, move the files, then continue

---

### Post by brottmayer on 2009-01-24
There's no icon, as I hadn't figured out how to make a copy of the drive onto the desktop until tonight. I've just been going through Places and Computer to open it. OK give me a bit and i will let you know about the attempt to unmount and remount.

Thanks,
Brandon.

---

### Post by brottmayer on 2009-01-24
Ok I put in the code to umount but got an error message saying:

> 
brottmayer@brottmayer-desktop:~$ sudo unmount /dev/sdb1
sudo: unmount: command not found
brottmayer@brottmayer-desktop:~$ 


---

### Post by utnubuuser on 2009-01-24
The only other time I've heard about this sort of issue is when a disk is gets an unclean shutdown.  -Like removing a USB stick without unmounting first.

You might have to make a directory for the disk and add an entry in your fsab file.

Try the unmounting first though.

---

### Post by utnubuuser on 2009-01-24
The other thing yu might try is alt+F2, then gksu, then nautilus,  this gets you into nautilus as root user.

---

### Post by brottmayer on 2009-01-24
Ok, I did that, but I do not see the second hard drive there. And when i tried to go to the Computer, it says that root cannot handle the computer?

:D So now what? LOL!

Brandon.

---

### Post by utnubuuser on 2009-01-24
LOL  -- I'm a little lost too.  Did you try shutting down the computer and accessing the files with a live CD?

---

### Post by utnubuuser on 2009-01-24
Is your /home partition on the second disk?

---

### Post by brottmayer on 2009-01-24
What do you mean accessing it with a live file? Do you mean with the iso file I burned onto a CD to boot up Ubuntu? And how do I access the files with a live CD?

No, the /home partition is on the first hard drive. The second disk is mostly used for data.

---

### Post by utnubuuser on 2009-01-24
I suppose the next thing to do would be to create a mount point and an entry in fstab

sudo mkdir /media/sdb
sudo chmod 777 /media/sdb

sudo gedit /etc/fstab
add:
/dev/sdb1  /media/sdb ext3 defaults 0 0

and I'm assuming the filesystem on the hd is ext3.  If it isn't, change that entry to whatever you set it up as.
save
restart computer

but I would definitely try to get the data off' the disk with a liveCD beforehand.

and you could also try just making the directory, /media/sdb, then try mounting with sudo mount /dev/sdb1 /media/sdb

---

### Post by brottmayer on 2009-01-24
OK if you do not mind, telling me how to get the data off the disk with a live CD, I will then do the command you mentioned. Thanks.

Brandon.

---

### Post by utnubuuser on 2009-01-24
ok  Hopefully this will work....

put the live cd in the drawer, restart the computer, and hopefully when it restarts it'll autodetect the hdds.  
you should then be able to move your data from one hd to the other, or to your external drive.
It's worth a shot.  I've heard of permissions problems like this before, though usually not on internal harddrives.
send me a private message to let me know when you're back.

---

### Post by brottmayer on 2009-01-24
Ubuntuuser,

I reinstalled the OS, and it worked fine. I am able to see and use my second hard drive. Thanks for all of your help.

Brandon.

---

### Post by utnubuuser on 2009-01-24
LOL.  That's my usual solution too.

---

### Post by herold on 2009-01-27
I think I see one of the problems from a few days ago.  It hink you typed unmount, but the command to unmount is umount.  (Note that the command does not have n for a second letter.)

---

