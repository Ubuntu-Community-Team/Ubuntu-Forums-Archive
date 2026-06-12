---
title: "[SOLVED] Grub Error 17. Boot from external HDD. Need Help"
date: 2008-11-04
forum: General Help
---

### Post by CMR_98823 on 2008-11-04
Hi, I have recently installed Ubuntu 8.10 to my external HDD.

However when it goes through my normal bootup process, I get this screen that says something along the lines of, Grub Loading....Error 17.

I'm not really sure what to do, I kind of read some of the topics around concerning Error 17 but I'm not sure how to execute those solutions.

Thanks for any help.

---

### Post by caljohnsmith on 2008-11-04
Are you getting the Grub error 17 before seeing a Grub menu, or before seeing something like "Press ESC to see menu", or do you get the error after getting the Grub menu and selecting Ubuntu? 

How about booting your Live CD, open a terminal (Applications > Accessories > Terminal), and post the output of:
```
sudo fdisk -lu
```
From the above output, determine which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
sudo blkid
cat /mnt/boot/grub/menu.lst
```
And please post the output of the above commands. We can work from there. :)

---

### Post by CMR_98823 on 2008-11-04
Hi, I'm currently at school, when I get home I will see about this.


I must say though, when the Error 17 appears I get no option of selecting Ubuntu or selecting a terminal. The only thing there is after the error is a blank black screen with a blinking cursor that allows no function...

---

### Post by CMR_98823 on 2008-11-05
Okay, I got the results, though I have no idea what it means or what to look for.

_**The first command you asked for is as follows:**_

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c73af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   314456309   157228123+   7  HPFS/NTFS
/dev/sda2       314456310   625137344   155340517+   5  Extended
/dev/sda5       314456373   619096904   152320266   83  Linux
/dev/sda6       619096968   625137344     3020188+  82  Linux swap / Solaris


**_Second string of commands is as follows:_**


ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="DE74A76A74A743DD" LABEL="Movies" TYPE="ntfs" 
/dev/sda5: UUID="4d746fec-9f24-455d-ac6d-fc75759d1a83" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="08c67ccd-09b5-496b-90eb-a41aada675a1" 
/dev/loop0: TYPE="squashfs" 
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=4d746fec-9f24-455d-ac6d-fc75759d1a83 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4d746fec-9f24-455d-ac6d-fc75759d1a83

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		4d746fec-9f24-455d-ac6d-fc75759d1a83
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4d746fec-9f24-455d-ac6d-fc75759d1a83 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		4d746fec-9f24-455d-ac6d-fc75759d1a83
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4d746fec-9f24-455d-ac6d-fc75759d1a83 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		4d746fec-9f24-455d-ac6d-fc75759d1a83
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
ubuntu@ubuntu:~$





[EDIT 9:57PM]

I should add that I have partitioned a spot on my external HDD. Windows is installed on a separate HDD.

I installed from LIVE CD without going into "try ubuntu without any changes" option.

---

### Post by panda726 on 2008-11-05
It looks like the output here only covers your external drive.  If I am reading correctly that you do not get ANY grub menu before getting Error 17 (please confirm), then, while I don't know enough about these errors to be certain, I suspect that the initial configfile (or something similar) load may be for ```
(hdX,Z)
```  However, you probably need it to read ```
(hdY,Z)
```  How this is changed, I do not know myself, but caljohnsmith is good at dealing with grub:)

Tor

---

### Post by caljohnsmith on 2008-11-05
You mentioned originally that you had installed Ubuntu to an external HDD, and yet your fdisk output only shows one 320 GB HDD, sda; is that your external drive? If so, what happened to your internal drive? Did you disconnect it? And you said you have Windows installed to a separate drive, so is sda1 just a data NTFS partition?

I would begin by reinstalling Grub to the MBR (Master Boot Record) of your external drive, and also changing your menu.lst slightly. If sda is indeed the external drive, then please post the output of:
```
sudo grub
grub> root (hd0,4)
grub> setup (hd0)
grub> quit
```
Next modify your menu.lst:
```
sudo mount /dev/sda5 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And change the line near the beginning that has "hiddenmenu" to:
```
# hiddenmenu
```
Save, reboot, and let me know what happens on start up.

---

### Post by CMR_98823 on 2008-11-05
Hi, the only thing I noticed on start up after inputing those commands, was that there was a small bar under the loading bar during the loading process. Other than that, I noticed nothing else.  :confused:


By the way, I did have my internal unplugged. I left it unplugged because it looks like you based these commands on the assumption of that. When I plugged my internal back in, I ran the previous string of commands mentioned earlier in this thread and the external actually read as sdb.

Should I continue this with my internal plugged in, or does it really matter right now?


[EDIT]

Also, my external has a partition in it, close to 150gb is partitioned for Ubuntu, and the remaining partition for data.



## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu   **_<-----------This is the line I edited from just "hiddenmenu" to "# hiddenmenu"_**




To Panda:  > If I am reading correctly that you do not get ANY grub menu before getting Error 17 (please confirm

You are correct, in that I do not get ANY grub menu.

---

### Post by CMR_98823 on 2008-11-06
These results are posted with internal HDD connected.


**_First string of commands:_**

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x99ee99ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   268414019   134206978+   7  HPFS/NTFS
/dev/sda2       268414020   312576704    22081342+   f  W95 Ext'd (LBA)
/dev/sda5       268414083   312576704    22081311    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c73af

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   314456309   157228123+   7  HPFS/NTFS
/dev/sdb2       314456310   625137344   155340517+   5  Extended
/dev/sdb5       314456373   619096904   152320266   83  Linux
/dev/sdb6       619096968   625137344     3020188+  82  Linux swap / Solaris

```

**_Next string of commands:_**

```
ubuntu@ubuntu:~$ sudo mount /dev/sdb5 /mnt
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="98383E91383E6DFE" TYPE="ntfs" 
/dev/sda5: UUID="CC94AF2D94AF18CA" LABEL="Extra" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: UUID="DE74A76A74A743DD" LABEL="Movies" TYPE="ntfs" 
/dev/sdb5: UUID="4d746fec-9f24-455d-ac6d-fc75759d1a83" TYPE="ext3" 
/dev/sdb6: TYPE="swap" UUID="08c67ccd-09b5-496b-90eb-a41aada675a1" 
ubuntu@ubuntu:~$ cat /mnt/boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=4d746fec-9f24-455d-ac6d-fc75759d1a83 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=4d746fec-9f24-455d-ac6d-fc75759d1a83

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		4d746fec-9f24-455d-ac6d-fc75759d1a83
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4d746fec-9f24-455d-ac6d-fc75759d1a83 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		4d746fec-9f24-455d-ac6d-fc75759d1a83
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4d746fec-9f24-455d-ac6d-fc75759d1a83 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		4d746fec-9f24-455d-ac6d-fc75759d1a83
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



```


I've tried 3 or 4 different "solutions" for Grub Error 17, and still cannot figure out how to get it to boot from my external hdd, doesn't say much, I'm not much of a linux wiz.

Any help much appreciated thanks! :)

---

### Post by caljohnsmith on 2008-11-06
Let's make one more check to see that you have Grub installed correctly to the external sdb drive (I'm assuming you still have your internal drive plugged in):
```
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
If the first command returns "GRUB", and the second command returns "ff04", then it appears you have Grub properly installed to the MBR of sdb. If that is the case, then getting a Grub error 17 before seeing a Grub menu can sometimes be caused by your [BIOS settings]("http://ubuntuforums.org/showthread.php?t=442945") for the HDD, or even [cable issues]("http://ubuntuforums.org/showthread.php?t=768101") with your HDD. You could go into your BIOS and change settings related to your HDD like "auto-detect", LBA, CHS, RAID, AHCI vs. IDE, IDE-emulation, ACPI, DMA, etc. and see if it helps. I would recommend writing down any settings you change so you can always revert back to the original setting if necessary. Good luck and let me know how it goes. :)

---

### Post by CMR_98823 on 2008-11-06
Ugh....you won't believe this, but my external HDD got wiped clean of everything including the MBR....I'll look into doing this as soon as I can figure out how to recover my boot sector...lol this sucks one problem after another. :roll:


In fact, I'm not really sure how to go about doing this....anyone know how to reinstall a MBR to an external HDD? :)

---

### Post by meierfra. on 2008-11-06
If you are lucky  only your partition table got wiped. In this case testdisk might be able to recover your partition table. Follow the instruction in this link:

[http://georgia.ubuntuforums.org/showpost.php?p=6107798&postcount=3]("http://georgia.ubuntuforums.org/showpost.php?p=6107798&postcount=3")

---

### Post by CMR_98823 on 2008-11-06
Thank you, I will give that a shot.

---

### Post by CMR_98823 on 2008-11-08
Well, I'm not sure exactly what I did, besides going through about a dozen different diagnostic tools to get my HDD at least functional again...but I got Ubuntu to load properly without any errors.


Thanks to all for your help!

---

### Post by CMR_98823 on 2008-11-08
So, Ubuntu is loaded properly now. However I installed it with my Windows HDD unplugged. The way I currently have to load Ubuntu is by selecting my external as the boot drive in my BIOS, and if I want to load Windows, I have to select that drive as the boot.

What should I do in order to get the OS selection screen?

---

### Post by meierfra. on 2008-11-08
Edit menu.lst:

Change "hiddenmenu" to "#hiddenmenu" and add the following to the very end of the file:

title Windows
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


Now when you boot from the external drive, you should get a grub menu with Ubuntu and Windows.



If this does not work, post your current menu.lst and the output of "sudo fdisk -lu"

---

### Post by CMR_98823 on 2008-11-09
It gave me the selection this time...but I don't know if I accidentally did something wrong, but I'm getting these errors now...it'll boot, but it's saying that there's errors in all kinds of sectors.


```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x99ee99ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   268414019   134206978+   7  HPFS/NTFS
/dev/sda2       268414020   312576704    22081342+   f  W95 Ext'd (LBA)
/dev/sda5       268414083   312576704    22081311    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c92fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   619096904   309548421   83  Linux
/dev/sdb2       619096905   625137344     3020220    5  Extended
/dev/sdb5       619096968   625137344     3020188+  82  Linux swap / Solaris

Disk /dev/sdc: 4016 MB, 4016045568 bytes
255 heads, 63 sectors/track, 488 cylinders, total 7843839 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4ca44ca3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              38     7839719     3919841    b  W95 FAT32

```

---

### Post by meierfra. on 2008-11-09
> .it'll boot, but it's saying that there's errors in all kinds of sectors.

Are you getting this errors trying to boot Windows? Or trying to boot Ubuntu?

Can you post a picture of the error mesages?

---

### Post by CMR_98823 on 2008-11-09
It's only getting errors when I boot into Ubuntu...I think it's a problem I created, I tried installing a new splash screen...the thumb print one...and I don't know if I messed something up in the menu.lst.

Anyways, I don't know how to get a screenshot of my loading screen, but I did note the error somewhat...and it reads somewhere along the lines of:

..."End Request Dev SR3 .......Sector (190000)" 190000 is different input values, ranging in the 190000's.


Is there a way I could restore that file?

---

### Post by zero777zero on 2008-11-09
i had this problem the other day, ended up having to reinstall completely from 8.04 (my new 8.10 disc wouldnt do it, dont know if it suffers from a tiny scratch or what). grub seems so sketchy that i dont keep any important info on my internal in case i need to do a reinstall.

---

### Post by meierfra. on 2008-11-09
[QUOTE=CMR_98823].."End Request Dev SR3 .......Sector (190000)" 190000 is different input values, ranging in the 190000's.[/QUOTE]

[QUOTE=zero777zero]grub seems so sketchy[/QUOTE]

I doubt this has anything to do with grub. But you might post your menu.lst (place it inside the code tags. To get the code tags click on the # symbol)

Sound more like a problem with your hard drive (But that's outside my area of expertise. You might post the output of "dmesg") 


Are you able to boot into Windows from the Grub menu by now?

---

### Post by CMR_98823 on 2008-11-09
Well, at first it worked fine after the install, worked flawlessly besides some graphic driver errors which are hopefully resolved...but after messing around with the splash screen, and after rebooting thats when things started getting ugly.

I'm no coding or scripting expert so it's very likely I entered something wrong in my terminal or menu.lst.

Any help much appreciated!:)

---

### Post by CMR_98823 on 2008-11-09
> Are you able to boot into Windows from the Grub menu by now?

I am able to boot into windows from grub...it doesn't really allow much time though to choose....lol 


I'll post outputs in a min...

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=9c92c744-ba23-42b4-8ab2-8e672f8aaf6c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=9c92c744-ba23-42b4-8ab2-8e672f8aaf6c

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		9c92c744-ba23-42b4-8ab2-8e672f8aaf6c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9c92c744-ba23-42b4-8ab2-8e672f8aaf6c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		9c92c744-ba23-42b4-8ab2-8e672f8aaf6c
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=9c92c744-ba23-42b4-8ab2-8e672f8aaf6c ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		9c92c744-ba23-42b4-8ab2-8e672f8aaf6c
kernel		/boot/memtest86+.bin
quiet

title Windows
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


### END DEBIAN AUTOMAGIC KERNELS LIST
```


```
d.0/usb1/1-2/1-2:1.0/input/input2
[    5.648160] input,hidraw0: USB HID v1.11 Mouse [Logitech USB Gaming Mouse] on usb-0000:00:1d.0-2
[    5.651700] hiddev96hidraw1: USB HID v1.11 Device [Logitech USB Gaming Mouse] on usb-0000:00:1d.0-2
[    5.651724] usbcore: registered new interface driver usbhid
[    5.651728] usbhid: v2.6:USB HID core driver
[    6.848093] ata5: SATA link down (SStatus 0 SControl 0)
[    8.928070] ata6: SATA link down (SStatus 0 SControl 0)
[    8.928135] ohci1394 0000:01:03.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    9.025972] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[dfcfb800-dfcfbfff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    9.079443] Driver 'sd' needs updating - please use bus_type methods
[    9.079594] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    9.079621] sd 2:0:0:0: [sda] Write Protect is off
[    9.079624] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    9.079668] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.079759] sd 2:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
[    9.079783] sd 2:0:0:0: [sda] Write Protect is off
[    9.079786] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    9.079831] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.079835]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    9.086642] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
[    9.086647] Uniform CD-ROM driver Revision: 3.20
[    9.086744] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    9.094504]  sda1 sda2 <sr1: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    9.099730] sr 0:0:1:0: Attached scsi CD-ROM sr1
[    9.117641]  sda5 >
[    9.117806] sd 2:0:0:0: [sda] Attached SCSI disk
[    9.122154] sr2: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    9.122306] sr 3:0:0:0: Attached scsi CD-ROM sr2
[   10.132196] usb-storage: device scan complete
[   10.132681] scsi 9:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  8.01 PQ: 0 ANSI: 0 CCS
[   10.133050] scsi 9:0:0:1: CD-ROM            SanDisk  U3 Cruzer Micro  8.01 PQ: 0 ANSI: 0
[   10.133875] usb-storage: device scan complete
[   10.135314] scsi 8:0:0:0: Direct-Access     Seagate  FreeAgentDesktop 100D PQ: 0 ANSI: 4
[   10.138052] sd 9:0:0:0: [sdb] 7843839 512-byte hardware sectors (4016 MB)
[   10.138552] sd 9:0:0:0: [sdb] Write Protect is off
[   10.138558] sd 9:0:0:0: [sdb] Mode Sense: 45 00 00 08
[   10.138564] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[   10.139795] sd 9:0:0:0: [sdb] 7843839 512-byte hardware sectors (4016 MB)
[   10.140293] sd 9:0:0:0: [sdb] Write Protect is off
[   10.140298] sd 9:0:0:0: [sdb] Mode Sense: 45 00 00 08
[   10.140300] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[   10.140340]  sdb: sdb1
[   10.141270] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[   10.141456] sd 9:0:0:0: Attached scsi generic sg4 type 0
[   10.145057] sr3: scsi3-mmc drive: 48x/48x tray
[   10.145213] sr 9:0:0:1: Attached scsi CD-ROM sr3
[   10.145365] sr 9:0:0:1: Attached scsi generic sg5 type 5
[   10.147546] sd 8:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
[   10.149166] sd 8:0:0:0: [sdc] Write Protect is off
[   10.149172] sd 8:0:0:0: [sdc] Mode Sense: 1c 00 00 00
[   10.149177] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[   10.151674] sd 8:0:0:0: [sdc] 625142448 512-byte hardware sectors (320073 MB)
[   10.153173] sd 8:0:0:0: [sdc] Write Protect is off
[   10.153179] sd 8:0:0:0: [sdc] Mode Sense: 1c 00 00 00
[   10.153184] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[   10.153231]  sdc: sdc1 sdc2 <<6>sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   10.214560] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   10.214567] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   10.214572] end_request: I/O error, dev sr3, sector 196352
[   10.214614] Buffer I/O error on device sr3, logical block 49088
[   10.216179] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   10.216184] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   10.216189] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   10.216194] end_request: I/O error, dev sr3, sector 196356
[   10.216233] Buffer I/O error on device sr3, logical block 49089
[   10.217804] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   10.217809] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   10.217814] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   10.217819] end_request: I/O error, dev sr3, sector 196352
[   10.217857] Buffer I/O error on device sr3, logical block 49088
[   10.218696]  sdc5 >
[   10.218920] sd 8:0:0:0: [sdc] Attached SCSI disk
[   10.219122] sd 8:0:0:0: Attached scsi generic sg6 type 0
[   10.220065] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   10.220074] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   10.220082] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   10.220090] end_request: I/O error, dev sr3, sector 196356
[   10.220133] Buffer I/O error on device sr3, logical block 49089
[   10.221572] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   10.221582] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   10.221590] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   10.221599] end_request: I/O error, dev sr3, sector 196584
[   10.221646] Buffer I/O error on device sr3, logical block 49146
[   10.223432] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   10.223438] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   10.223443] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   10.223448] end_request: I/O error, dev sr3, sector 196588
[   10.223488] Buffer I/O error on device sr3, logical block 49147
[   10.224939] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   10.224946] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   10.224953] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   10.224961] end_request: I/O error, dev sr3, sector 196584
[   10.225004] Buffer I/O error on device sr3, logical block 49146
[   10.226562] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   10.226570] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   10.226577] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   10.226585] end_request: I/O error, dev sr3, sector 196588
[   10.226628] Buffer I/O error on device sr3, logical block 49147
[   10.232556] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   10.232562] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   10.232567] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   10.232573] end_request: I/O error, dev sr3, sector 196600
[   10.232613] Buffer I/O error on device sr3, logical block 49150
[   10.236055] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   10.236059] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   10.236064] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   10.236069] end_request: I/O error, dev sr3, sector 196600
[   10.236114] Buffer I/O error on device sr3, logical block 49150
[   10.238304] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   10.238309] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   10.238313] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   10.238319] end_request: I/O error, dev sr3, sector 196600
[   10.240678] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   10.240683] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   10.240687] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   10.240693] end_request: I/O error, dev sr3, sector 196600
[   10.242180] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   10.242185] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   10.242189] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   10.242195] end_request: I/O error, dev sr3, sector 196600
[   10.243315] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   10.243323] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   10.243331] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   10.243339] end_request: I/O error, dev sr3, sector 196600
[   10.245075] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   10.245083] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   10.245091] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   10.245100] end_request: I/O error, dev sr3, sector 196600
[   10.246055] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   10.246060] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   10.246065] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   10.246071] end_request: I/O error, dev sr3, sector 196536
[   10.247181] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   10.247186] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   10.247190] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   10.247196] end_request: I/O error, dev sr3, sector 196540
[   10.248335] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   10.248340] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   10.248345] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   10.248350] end_request: I/O error, dev sr3, sector 196592
[   10.250314] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   10.250319] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   10.250323] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   10.250328] end_request: I/O error, dev sr3, sector 196596
[   10.251807] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   10.251812] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   10.251816] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   10.251822] end_request: I/O error, dev sr3, sector 196600
[   10.253432] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   10.253437] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   10.253442] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   10.253447] end_request: I/O error, dev sr3, sector 196600
[   10.297274] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d800008429de]
[   10.502195] PM: Starting manual resume from disk
[   10.502200] PM: Resume from partition 8:37
[   10.502202] PM: Checking hibernation image.
[   10.502824] PM: Resume from disk failed.
[   10.625387] kjournald starting.  Commit interval 5 seconds
[   10.625397] EXT3-fs: mounted filesystem with ordered data mode.
[   16.646382] udevd version 124 started
[   17.013774] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.038905] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.979029] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   18.008543] ACPI: Power Button (FF) [PWRF]
[   18.008747] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
[   18.040536] ACPI: Power Button (CM) [PWRB]
[   18.857464] parport_pc 00:07: reported by Plug and Play ACPI
[   18.857586] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   18.977065] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   18.977091] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.001994] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[   19.437084] intel_rng: FWH not detected
[   19.495022] iTCO_vendor_support: vendor-support=0
[   19.498759] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   19.498924] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
[   19.499098] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   20.063313] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   20.371695] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   20.371704] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   20.371712] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   20.371720] end_request: I/O error, dev sr3, sector 196352
[   20.371783] __ratelimit: 11 callbacks suppressed
[   20.371788] Buffer I/O error on device sr3, logical block 49088
[   20.372736] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   20.372743] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   20.372749] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   20.372757] end_request: I/O error, dev sr3, sector 196356
[   20.372806] Buffer I/O error on device sr3, logical block 49089
[   20.373782] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   20.373790] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   20.373797] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   20.373805] end_request: I/O error, dev sr3, sector 196352
[   20.373854] Buffer I/O error on device sr3, logical block 49088
[   20.374828] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   20.374836] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   20.374843] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   20.374851] end_request: I/O error, dev sr3, sector 196356
[   20.374899] Buffer I/O error on device sr3, logical block 49089
[   20.375874] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   20.375880] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   20.375887] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   20.375894] end_request: I/O error, dev sr3, sector 196584
[   20.375942] Buffer I/O error on device sr3, logical block 49146
[   20.376933] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   20.376942] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   20.376951] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   20.376960] end_request: I/O error, dev sr3, sector 196588
[   20.377018] Buffer I/O error on device sr3, logical block 49147
[   20.378102] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   20.378110] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   20.378117] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   20.378125] end_request: I/O error, dev sr3, sector 196584
[   20.378174] Buffer I/O error on device sr3, logical block 49146
[   20.379148] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   20.379155] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   20.379163] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   20.379170] end_request: I/O error, dev sr3, sector 196588
[   20.379219] Buffer I/O error on device sr3, logical block 49147
[   20.381771] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   20.381778] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   20.381786] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   20.381794] end_request: I/O error, dev sr3, sector 196600
[   20.381844] Buffer I/O error on device sr3, logical block 49150
[   20.382815] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   20.382822] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   20.382830] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   20.382838] end_request: I/O error, dev sr3, sector 196600
[   20.382887] Buffer I/O error on device sr3, logical block 49150
[   20.383861] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   20.383868] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   20.383876] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   20.383884] end_request: I/O error, dev sr3, sector 196600
[   20.384909] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   20.384916] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   20.384925] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   20.384933] end_request: I/O error, dev sr3, sector 196600
[   20.385955] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   20.385963] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   20.385970] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   20.385978] end_request: I/O error, dev sr3, sector 196600
[   20.387009] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   20.387018] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   20.387027] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   20.387036] end_request: I/O error, dev sr3, sector 196600
[   20.388054] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   20.388062] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   20.388069] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   20.388078] end_request: I/O error, dev sr3, sector 196600
[   20.389099] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   20.389107] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   20.389114] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   20.389122] end_request: I/O error, dev sr3, sector 196536
[   20.390149] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   20.390158] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   20.390165] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   20.390173] end_request: I/O error, dev sr3, sector 196540
[   20.391190] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   20.391198] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   20.391205] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   20.391213] end_request: I/O error, dev sr3, sector 196592
[   20.392239] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   20.392247] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   20.392254] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   20.392262] end_request: I/O error, dev sr3, sector 196596
[   20.393285] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   20.393293] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   20.393301] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   20.393309] end_request: I/O error, dev sr3, sector 196600
[   20.394338] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   20.394346] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   20.394354] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   20.394362] end_request: I/O error, dev sr3, sector 196600
[   21.840724] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   21.840735] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   21.840743] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   21.840754] end_request: I/O error, dev sr3, sector 196352
[   21.841765] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   21.841773] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   21.841780] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   21.841788] end_request: I/O error, dev sr3, sector 196356
[   21.842810] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   21.842817] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   21.842825] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   21.842833] end_request: I/O error, dev sr3, sector 196352
[   21.843725] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   21.843731] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   21.843738] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   21.843746] end_request: I/O error, dev sr3, sector 196356
[   21.844773] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   21.844780] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   21.844787] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   21.844794] end_request: I/O error, dev sr3, sector 196584
[   21.845688] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   21.845695] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   21.845701] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   21.845709] end_request: I/O error, dev sr3, sector 196588
[   21.846736] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   21.846743] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   21.846750] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   21.846758] end_request: I/O error, dev sr3, sector 196584
[   21.847651] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   21.847658] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   21.847665] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   21.847673] end_request: I/O error, dev sr3, sector 196588
[   21.850155] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   21.850164] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   21.850174] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   21.850183] end_request: I/O error, dev sr3, sector 196600
[   21.851197] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   21.851207] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   21.851218] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   21.851227] end_request: I/O error, dev sr3, sector 196600
[   21.852251] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   21.852259] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   21.852267] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   21.852276] end_request: I/O error, dev sr3, sector 196600
[   21.853286] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   21.853294] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   21.853301] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   21.853309] end_request: I/O error, dev sr3, sector 196600
[   21.854337] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   21.854346] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   21.854354] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   21.854362] end_request: I/O error, dev sr3, sector 196600
[   21.855381] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   21.855389] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   21.855396] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   21.855405] end_request: I/O error, dev sr3, sector 196600
[   21.856422] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   21.856428] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   21.856433] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   21.856438] end_request: I/O error, dev sr3, sector 196600
[   21.857469] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   21.857474] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   21.857479] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   21.857484] end_request: I/O error, dev sr3, sector 196536
[   21.858383] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   21.858388] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   21.858392] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   21.858397] end_request: I/O error, dev sr3, sector 196540
[   21.859431] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   21.859436] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   21.859440] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   21.859445] end_request: I/O error, dev sr3, sector 196592
[   21.860347] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   21.860351] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   21.860355] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   21.860361] end_request: I/O error, dev sr3, sector 196596
[   21.861394] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   21.861399] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   21.861404] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   21.861409] end_request: I/O error, dev sr3, sector 196600
[   21.862442] sr 9:0:0:1: [sr3] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   21.862446] sr 9:0:0:1: [sr3] Sense Key : No Sense [current] 
[   21.862451] sr 9:0:0:1: [sr3] Add. Sense: No additional sense information
[   21.862456] end_request: I/O error, dev sr3, sector 196600
[   22.865245] lp0: using parport0 (interrupt-driven).
[   23.026757] Adding 3020180k swap on /dev/sdc5.  Priority:-1 extents:1 across:3020180k
[   23.494357] EXT3 FS on sdc1, internal journal
[   24.302997] ip_tables: (C) 2000-2006 Netfilter Core Team
[   24.969911] ACPI: WMI: Mapper loaded
[   26.122854] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   26.216581] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   26.216588] apm: disabled - APM is not SMP safe.
[   26.391060] ppdev: user-space parallel port driver
[   28.075472] Bluetooth: Core ver 2.13
[   28.076176] NET: Registered protocol family 31
[   28.076186] Bluetooth: HCI device and connection manager initialized
[   28.076193] Bluetooth: HCI socket layer initialized
[   28.094682] Bluetooth: L2CAP ver 2.11
[   28.094690] Bluetooth: L2CAP socket layer initialized
[   28.110344] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.110353] Bluetooth: BNEP filters: protocol multicast
[   28.138943] Bridge firewalling registered
[   28.139196] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   28.161520] Bluetooth: SCO (Voice Link) ver 0.6
[   28.161535] Bluetooth: SCO socket layer initialized
[   28.183792] Bluetooth: RFCOMM socket layer initialized
[   28.183817] Bluetooth: RFCOMM TTY layer initialized
[   28.183822] Bluetooth: RFCOMM ver 1.10
[   29.478271] pci 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   29.722901] Linux agpgart interface v0.103
[   29.747739] [drm] Initialized drm 1.1.0 20060810
[   29.770836] pci 0000:05:00.0: setting latency timer to 64
[   29.771076] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   30.279570] [drm] Setting GART location based on new memory map
[   30.281094] [drm] Loading R400 Microcode
[   30.281152] [drm] Num pipes: 2
[   30.281162] [drm] writeback test succeeded in 1 usecs
[   32.320401] skge eth1: enabling interface
[   33.990496] 0000:03:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   33.990517] 0000:03:00.0: eth0: 10/100 speed: disabling TSO
[   34.092748] NET: Registered protocol family 17
[   35.715897] 0000:03:00.0: eth0: changing MTU from 1500 to 576
[   37.358465] 0000:03:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[   37.358474] 0000:03:00.0: eth0: 10/100 speed: disabling TSO
[  168.948473] ppdev0: registered pardevice
[  168.996184] ppdev0: unregistered pardevice
[  170.175148] ppdev0: registered pardevice
[  170.224267] ppdev0: unregistered pardevice
[  170.289672] __ratelimit: 41 callbacks suppressed
[  170.289690] type=1503 audit(1226218826.707:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6030/net/" pid=6030 profile="/usr/sbin/cupsd"
[  171.337695] type=1503 audit(1226218827.755:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6034/net/" pid=6034 profile="/usr/sbin/cupsd"
[  171.416851] NET: Registered protocol family 10
[  171.418130] lo: Disabled Privacy Extensions
[  171.420725] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  171.422518] type=1503 audit(1226218827.839:7): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6034 profile="/usr/sbin/cupsd"
[  171.422547] type=1503 audit(1226218827.839:8): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6034 profile="/usr/sbin/cupsd"
[  171.422564] type=1503 audit(1226218827.839:9): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6034 profile="/usr/sbin/cupsd"
[  171.422581] type=1503 audit(1226218827.839:10): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6034 profile="/usr/sbin/cupsd"
[  171.422599] type=1503 audit(1226218827.839:11): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6034 profile="/usr/sbin/cupsd"
[  171.422618] type=1503 audit(1226218827.839:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6034 profile="/usr/sbin/cupsd"
[  171.422636] type=1503 audit(1226218827.839:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6034 profile="/usr/sbin/cupsd"
[  171.422655] type=1503 audit(1226218827.839:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6034 profile="/usr/sbin/cupsd"
[  171.516106] ppdev0: registered pardevice
[  171.564040] ppdev0: unregistered pardevice

```

---

### Post by ericesque on 2008-11-09
if you can boot up a live cd, you should try running fsck to clear up the sector issues.

fsck -y /dev/sdb1

that -y option will tell fsck to fix any errors on the file system that it encounters without user input-- which is what I would recommend, but wanted to let you know.

Just got by a GRUB 17 error myself.

---

### Post by meierfra. on 2008-11-09
> doesn't really allow much time though to choose.

Just change "timeout 3" in menu.lst to "timeout 10". That will give you 10 seconds to choose Windows.


> you should try running fsck to clear up the sector issues.

fsck -y /dev/sdb1

I agree.

---

### Post by CMR_98823 on 2008-11-09
> **meierfra. said:**
> Just change "timeout 3" in menu.lst to "timeout 10". That will give you 10 seconds to choose Windows.




I agree.

Would I be running fsck -y /dev/sdb1? Or that would depend on my fdisk -lu readout?

```
Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c92fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   619096904   309548421   83  Linux
/dev/sdc2       619096905   625137344     3020220    5  Extended
/dev/sdc5       619096968   625137344     3020188+  82  Linux swap / Solaris

```

So mine would be fsck -y /dev/sdc1?

---

### Post by meierfra. on 2008-11-09
> So mine would be fsck -y /dev/sdc1?

Yes.

---

### Post by meierfra. on 2008-11-09
Actually I would guess that "fsck" will come out clean.  The errors are produced by "dev sr3" :
> 
Buffer I/O error on device sr3, logical block 49089

and sr3 seems to be your cd rom drive:

> sr3: scsi3-mmc drive: 48x/48x tray 

So if you have a CD in the CD drive, remove it and see whether you still get the errors.

---

### Post by CMR_98823 on 2008-11-09
```
/dev/sdc1:recovering journal
/dev/sdc1 : clean, 111761/19349504 files, 1826028/77387105 blocks
```

Turned out clean.

No cd in tray.

However, this is the first line in that whole sequence of following errors:

Along the lines of, "Unable to enumerate USB device on PORT 2".

Reading around it seems it's a fairly common "bug" with nothing to worry about. Is it perhaps a driver error on a USB port?

---

### Post by meierfra. on 2008-11-09
> Reading around it seems it's a fairly common "bug" with nothing to worry about.

I had come to the same conclusion.

> Is it perhaps a driver error on a USB port? 

No idea.

---

### Post by CMR_98823 on 2008-11-09
Appreciate the help, I'll probably be around often and I'll try and keep myself and questions to my own threads from now on. :oops: 

I'm just very new to Linux OS and not sure how to approach the whole CLI thing, used to GUI's and not the whole scripting aspect of OS.

---

### Post by meierfra. on 2008-11-09
> I'm just very new to Linux OS and not sure how to approach the whole CLI thing, used to GUI's and not the whole scripting aspect of OS.

We all started out the same way. Almost all things in Ubuntu can be done via GUI, but soon you will noticed that lots of things can be done faster via the CLI. 
 Have fun with Ubuntu.

---

