---
title: "GRUB error 17 when plugging in a ide drive"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by mangoHead84 on 2007-05-11
I have two SATA hard drives. I recently found an old IDE drive and thought i'd plug it in. When i plug it in however, grub gives me error 17 at stage 1.5. 

The boot order of the drives does not change after attaching the IDE drive. I think the problem might be something to do with how grub is set up. In the file which specifies the mapping for grub /dev/sd1 (first SATA hdd) is mapped to hd0 and /dev/sd2 (second SATA hdd) is mapped to hd1.

 I don't know what happens with the mappings when the IDE drive is plugged in. i.e. what is the mapping for the new IDE drive? e.g. hd0, hd1, hd2?? 

Does anyone know how to fix this problem? Please reply.

---

### Post by EXCiD3 on 2007-05-11
I started receiving Error 17 when I had my usb hd turned on before i booted.

---

### Post by dannyboy79 on 2007-05-11
you should be able to edit the boot line so that you can get into your ubuntu install. when you machine is booting, hit esc, this should bring up grub menu, then hit "e" to edit the first boot option line.

this will bring up a few lines, we need to edit the first line so hit "e" again. and simply edit the first line, it'll be something like
(hd0,1) or whatever, now just change the very fiurst number until your system boots and then we can fix it from there. so try out things like (hd1,1) or (hd2,1). this has happened because you added a drive and your device.map needs to be updated. once you're in your system, rename your old device.map file just in case.

```
sudo mv /boot/grub/device.map /boot/grub/device.map-b4newdrive
```

go to the grub cli by entering

```
sudo grub
```

then enter this

```
grub --device-map=device.map
```

```
quit
```
it may be "end" which is what exits you from the grub command line.

Now make sure that grub actually created a new device.map file and see what it looks like now.

```
gksudo gedit /boot/grub/device.map
```

if it's blank than that means that the commmand we entered in grub cli didn't work. post back if that happens. If it's not empty and you see the added drive which was m,isssing from your old device.map, than that's good. we're getting somewhere. now we just need to make sure that we don't need to update menu.lst and or fstab as well. so please post the results of these commands:

```
sudo fdisk -l
```

```
cat /etc/fstab
```

good luck! if and when you post back and you need further assistance, please make sure you answer all my questions and have posted the output from the desired commands. i won't ask for the info twice cause I can'ty help  if I don't have the info I need.

---

### Post by mangoHead84 on 2007-05-11
Ok, first of all. When GRUB loads it throws error 17 and does not go to the menu. I tried pressing 'esc' after getting the error and also pressing 'c' to launch the command line, as well as 'e' to edit the menu, but it won't let me do anything except restart.

Then i had a look at my device.map file, which had the following contents:

```
(hd0)   /dev/sda
(hd1)   /dev/sdb

```
So then I tried changing it to this:

```
(hd8)   /dev/sda
(hd9)   /dev/sdb
```

and then updating the menu.lst file so that the menu items which previously said root(hd0,0) now said (hd8,0) etc..

Then I tried running the command grub --device-map=device.map in order to reload device.map

however it replied with the error 27: Command not recognised. In fact 'grub> help'  gives you the following set of commands:
```

help
blocklist FILE                         boot                                   
cat FILE                               chainloader [--force] FILE             
clear                                  color NORMAL [HIGHLIGHT]               
configfile FILE                        device DRIVE DEVICE                    
displayapm                             displaymem                             
find FILENAME                          geometry DRIVE [CYLINDER HEAD SECTOR [ 
halt [--no-apm]                        help [--all] [PATTERN ...]             
hide PARTITION                         initrd FILE [ARG ...]                  
kernel [--no-mem-option] [--type=TYPE] makeactive                             
map TO_DRIVE FROM_DRIVE                md5crypt                               
module FILE [ARG ...]                  modulenounzip FILE [ARG ...]           
pager [FLAG]                           partnew PART TYPE START LEN            
parttype PART TYPE                     quit                                   
reboot                                 root [DEVICE [HDBIAS]]                 
rootnoverify [DEVICE [HDBIAS]]         serial [--unit=UNIT] [--port=PORT] [-- 
setkey [TO_KEY FROM_KEY]               setup [--prefix=DIR] [--stage2=STAGE2_ 
terminal [--dumb] [--no-echo] [--no-ed terminfo [--name=NAME --cursor-address 
testvbe MODE                           unhide PARTITION                       
uppermem KBYTES                        vbeprobe [MODE]  
```       

There is no command called device-map. I tried restarting anyway with the IDE drive, got error 17 again. Then without the IDE drive, this time selecting the menu items caused an 'invalid device name' (or something along those line) error. However by editing the menu items from root(hd8,0) to root(hd0,0) loaded normally. Meaning that the changes made to the device.map file had not taken hold.

Also the output of fdisk (without the IDE drive attached) is:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19083   153284166   83  Linux
/dev/sdb2           19084       19457     3004155    f  W95 Ext'd (LBA)
/dev/sdb5           19084       19457     3004123+  82  Linux swap / Solaris
```

The output of fstab (without the IDE drive attached) is:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=48ae3d3a-93ce-42e7-89bd-26a97c3749f0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=c1858350-540c-4b1f-9462-07feb0b9afc6 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /media/windows  ntfs    nls=utf8,umask=0222     0    0
/dev/sda2       /media/winswap  vfat    iocharset=utf8,umask=000  0    0
```

The contents of menu.lst (relevant section only):

```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=48ae3d3a-93ce-42e7-89bd-26a97c3749f0 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=48ae3d3a-93ce-42e7-89bd-26a97c3749f0 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

I am using GRUB version 0.97-20ubuntu6, a lot of the stuff on the forums seems to be for a different version of GRUB. This problem's got me stumped.

---

### Post by dannyboy79 on 2007-05-11
im sorry, i got my error's mixed up for grub (thinking of 15). you're saying that when you install the ide drive that you get the error 17 right? well it's because the grub can't read the partition you're telling it to find the stage2 and the rest of it's files, at least that's what error 17 states.

try this (i found it in gogle):
make sure in your bios, that its not set on auto, that it has your harddrive listed instead of auto, my problem was i have a 200 gig HD, but my pentium only sees it as a 136 gig hd, once xp boots, it sees the other part of the hard drive, i was trying to format that part, finally i realized its a windows only thing, and to go by my bios, so now all is well

also, when you install the new hard drive, are you still leaving the hard drives withjin the bios the same? are you still chosing to boot the same drive? and also, is the ide's boot flag set? you can change that within a live cd (obviously you need it attached before you boot the live cd.) Just run gnome partition editor, select the ide drive and click on the drive options, then uncheck boot flag.

are you hooking this ide externally (using usb box/adapter) or are you attaching it to an internal ide channel? it's possible that you have boot to usb before internal ide set in your bios? if you're hooking it to a internal ide channel than I am going to bet that your ide drive is showing up as (hd0) and then pushing sata drives to hd1 and hd2 respectively. so it wouldn't hurt to insert a line within your device.map file like this

(hd0) /dev/hda1 (or whatever the ide drive and partition show up as within fdisk -l. you didn't show me it so how can i help.)

I know that I asked many questions and asked for ouput from many commands but I can't help you when you don't ansqwer my q's or post command results.  I am not being rude but I won't ask for the info agin, please read my previous post along with this one and provide me the info. i of course need the commands entered when the ide drive is hooked up. live cd if you can't boot into your normal ubuntu

---

### Post by mangoHead84 on 2007-05-16
I'm sorry if i appeared rude or uncooperative in my last post, i wasn't being rude on purpose. I genuinely appreciate your help and I'm more than happy to give any information that helps to solve this problem. The reason I didn't post the output of the fdisk and fstab commands with the IDE drive plugged in was because I couldn't boot my computer while the drive was plugged in and I hadn't thought of booting from CD until you mentioned it. So here are the latest results:

I checked my bios and my hard drive was listed, there was no setting for 'auto'.

the hard drive boot order remains the same when the IDE drive is plugged in. That is, the IDE drive is added to the end of the list i.e. 
1. 1st SATA disk (the one with GRUB on it)
2. 2nd SATA disk
3. IDE drive (freshly plugged in)

I managed to boot from the CD, which was a brilliant idea by the way, and the boot flag on the IDE drive was not set.

I am hooking up the IDE drive internally and in the bios it shows up under the 'hard disk' section, not the 'removable devices' section. I also suspected that by plugging in the IDE drive it was showing up as (hd0) and bumping the SATA drives to (hd1) and (hd2), which is why i previously tried to alter the devices.map file. 

The output from fdisk after booting from the cd:

ubuntu@ubuntu:~$ sudo fdisk -l
```

Disk /dev/hdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        7476    60049408    7  HPFS/NTFS

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19083   153284166   83  Linux
/dev/sdb2           19084       19457     3004155    f  W95 Ext'd (LBA)
/dev/sdb5           19084       19457     3004123+  82  Linux swap / Solaris
```

the output from fstab after booting from the cd:
```
ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb5 swap swap defaults 0 0
```

The IDE drive shows up as /dev/hdb. I tried adding an entry in device.map file
(hd2)	/dev/hdb
 and then restrating with the drive plugged in but still no success.

---

### Post by dannyboy79 on 2007-05-16
well, i am not entirely sure what's occuring here? When you put in the ata drive, did you have to change a bios setting so that hard drives would be sata and ide or is there like a setting for sata sa ide NOT raid? it's possible that your motherboard can't boot to sata if ide is connected? you can try this, I gave you the wrong instructions before. we really need to chroot into your system from the live cd and instead of entering the grub command line, we need to try that device.map command from the normal command line. so in order to chroot into your ubuntu install this is what you should do. make sure the ide drive is attached before you put the live cd in. (found how to chroot into system here: [http://www.ubuntugeek.com/how-to-fix-broken-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-fix-broken-ubuntu-feisty-fawn.html))

```
sudo mkdir /media/ubuntu
```
```
sudo mount /dev/sdb1 /media/ubuntu 
```
```
sudo chroot /media/ubuntu su
```
now you should be at a command line just like you're in your normal ubuntu install. then try this:

```
grub --device-map=device.map
```

then open the device.map file to see if it added the hdb1 drive?

also, how are you attaching it? do you haev the jumper set to master or slave, is it on ide0 or ide1. what are the bios settings regarding the drives? is there a way to change the hard drive bios setting from auto to LBA? I know you answered this once but I am merely double checking. I also want you to tell me what the live cd states that the partitions are as far as filesystems.

so to find out what filesystems grub is seeing them as enter the grub command line using

```
sudo grub
```

then do this

```
geometry (hd0)
```

```
geometry (hd1)
```

```
geometry (hd2)
```

this is just to see if grub is recognizing your hard drives and partitions as what they are, Type 83 is ext3 and type 82 is linux swap. Because the real meaning of Grub Error 17 is this:
Cannot mount selected partition 
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB. AS an FYI, this has been helping me help you a little bit, it's for Gentoo and also it;s when grub had a grub.conf but it's still usefull info: [http://forums.gentoo.org/viewtopic.php?t=120802](http://forums.gentoo.org/viewtopic.php?t=120802)
good luck and let me know if I can try to help more.

---

### Post by mangoHead84 on 2007-05-21
I have given up trying to connect the drive. After connecting the IDE drive, and checking the BIOS settings i restarted. When the computer restarted, the IDE drive (Slave) and the DVDRW (Master) were not recognised by the bios. This had occurred before once when i was mount the IDE drive and had restarted the computer a few times. However, this time it would not load either of the IDE drives 5 times out of 10. I tried using a different cable (one i know works) with the same result. When the DVD drive is plugged in by itself, it is always recognised. 

In the end I went and bought an external case with a USB adapter plugged the drive into that and into the computer and now it works fine. Thank you for all your help dannyboy79, too bad we couldn't find a fix.

---

### Post by dannyboy79 on 2007-05-21
yeah, it's too bad. I hate problems I can't resolve. How were you hooking up the ide drive with the dvdrom, as in the jumper settings for each device? were you using cable select? using master/slave? I have had more problems using cable select so I have since always used master and slave jumper settings. oh well, the usb external drive is most likely the easiest and now you have a drive you can carry around that's larger than just a little flash drive.

---

