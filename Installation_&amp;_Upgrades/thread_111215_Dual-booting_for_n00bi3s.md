---
title: "Dual-booting for n00bi3s"
date: 2006-01-01
forum: Installation &amp; Upgrades
---

### Post by Flune on 2006-01-01
Greetings!

I need some help getting my system dual booted.  My machine is set up like this:
IDE 0:
-master: Windows XP (my primary system; 2 partitions, system is on the first)
-slave: disc drive
IDE 1:
-master: disc drive
-slave: Linux system

I can't boot to the Linux system without unplugging the Windows drive, after which, the only way to get back into Windows is to unplug the Linux drive and boot again.  So - what do I need to do to get my system dual-booted? I've heard a bit about GRUB, but I don't know how to use it.  Can someone tell me what I need to do to get this working? Can I set up GRUB from Windows or do I need to get back into Linux somehow? Help would be greatly appreciated; thank you.

- Flune

---

### Post by Flune on 2006-01-05
Here's another question: if GRUB is the solution, can I set it up from within Windows?

---

### Post by Burning Bronx on 2006-01-05
Why setting up from windows? Just do a 
```
sudo apt-get install grub
sudo update-grub
```
After that you'd need to set it up so it could boot your XP... so you open the grub config file
```
sudo gedit /boot/grub/menu.lst
```
There in the end you shoul add these lines 
```
title		Other operating systems:
root

title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

These should give your grub the entry line for loading Windows.

---

### Post by Flune on 2006-01-06
Ah, well, that does help set up the menu system part of it, but I've hit a snag - selecting the option doesn't work. I select the option, but it gives me the error:

Error 13: Invalid or unsupported executable format.

Additionally, when it displays the line:
root (hd0,0)
It gives the output:
Filesystem type is ex2fs partition type 0x83

My assumption is that this is a problem stemming from the fact that I think that I have 2 MBRs; I think this is why I have to unplug one drive to boot to the other and then continue booting to the second after plugging the first back in.

Any other thoughts?

---

### Post by benco on 2006-01-06
The error message is strange. It looks like your (hd0,0) partition is seen as a Linux (ext3) partition. You may have an incorrect device assignation either in menu.lst or in device.map.
Can you run the following commands :
> 
# cat /boot/grub/menu.lst
# cat /boot/grub/device.map
# fdisk -l

and post the results here ?

---

### Post by Flune on 2006-01-06
menu.lst:
> # menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdd1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdd1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

#title		Ubuntu, memtest86+
#root		(hd0,0)
#kernel		/boot/memtest86+.bin  
#boot

### END DEBIAN AUTOMAGIC KERNELS LIST
fs


I'm not sure that last fs should be there...might have been from a failed attempt to do an ALT, f, s or something.

device.map:
> (hd0)	/dev/hdd

fdisk -l (I'm assuming that's the letter 'L') doesn't do anything; specifying a /dev/hd* lists some of the info for me if I do hdb or hdc, giving me my CD and DVD info respectively, but hda and hdd give me the message "Cannot open hda" (or hdd).

---

### Post by lha on 2006-01-06
There's something strange going on in your device.map and menu.lst. How did you install Ubuntu? Did you have your hd with Windows as IDE0 master and hd with Linux as IDE1 slave? And did you install GRUB to MBR of your Linux drive? If you didn't, how did you install Ubuntu?

You need to put sudo in front of fdisk -l to get useful output.
```
sudo fdisk -l
```
Yes, l is a lower case L.

Could you also post the results of
```
cat /etc/fstab
```? Fstab might need to modified too, in addition to menu.lst and device.map.

---

### Post by Flune on 2006-01-07
Aha! Here's the actual fdisk output, then:
> 
Disk /dev/hdd: 30.7 GB, 30758289408 bytes
255 heads, 63 sectors/track, 3739 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        3583    28780416   83  Linux
/dev/hdd2            3584        3739     1253070    5  Extended
/dev/hdd5            3584        3739     1253038+  82  Linux swap / Solaris


Here's the fdisk info:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


As I said...
IDE 0:
-master: Windows XP (my primary system; 2 partitions, system is on the first)
-slave: disc drive
IDE 1:
-master: disc drive
-slave: Linux system

Originally, IDE 1 was a Windows ME drive; I reformatted it, put the Ubuntu disc in, and formatted to ext3 and installed it there.  GRUB seemed to be installed with Ubuntu when I looked.

---

### Post by lha on 2006-01-07
Fdisk doesn't see your hd with windows. I hope it wasn't plugged in when you ran fdisk.

Now I assume you have plugged in your hd with Windows. Hopefully sudo fdisk -l will show you partition info on /dev/hda, too. Now find

title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

in your menu.lst and change (hd0,0) to (hd1,0) on the line following "title Microsoft Windows XP Professional". Reboot, select Windows from GRUB menu and cross your fingers. ;)

---

### Post by benco on 2006-01-07
Before that, don't forget to add :
> 
(hd1) /dev/hda

to your device.map file.

---

### Post by mztriz on 2006-01-07
This may also help. video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu 
:cool:

---

### Post by Flune on 2006-01-07
> Fdisk doesn't see your hd with windows. I hope it wasn't plugged in when you ran fdisk.

Now I assume you have plugged in your hd with Windows. Hopefully sudo fdisk -l will show you partition info on /dev/hda, too.

Unfortunately, no.  I tried what was suggested in the this post and the one after, to no avail.  GRUB actually froze on me and went very slowly from one command to the next (root, makeactive, etc.).  It did note this:

> Filesystem type unknown, partition type 0x7

Well, something like that.

Here's a thought: right now, I have my Windows drive on IDE 0 Master and my Linux partition on IDE 1 Slave; since I'm using the Linux MBR with GRUB in the long run anyway, what if I switch the two drives?  Would this work? Furthermore, what would I need to reconfigure in my GRUB files to get this to work?

---

### Post by Kipper on 2006-01-07
Flune,

If your drives are still set up like this:

"I need some help getting my system dual booted. My machine is set up like this:
IDE 0:
-master: Windows XP (my primary system; 2 partitions, system is on the first)
-slave: disc drive
IDE 1:
-master: disc drive
-slave: Linux system"

and you still have GRUB installed on IDE 1 slave, then the following edit to  "menu.lst" might do the trick for you:

[B]"title Windows XP
rootnoverify (hd1,0)
hide (hd0,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1"[/B]

I'm assuming you have selected the slave drive on HDD controller IDE1 as your boot device in your system's BIOS (probably HDD-1) 

The naming schemes for drives in the BIOS, Linux and GRUB can be a bit confusing.

IDE0
Master = hda in Linux
Slave = hdb in Linux
IDE1
Master = hdc in Linux
Slave = hdd in Linux

You can see this in both part of GRUB's notation and in the etc/fstab file.

It looks like you set the first hard drive in the boot sequence in your BIOS to be the hard drive attached to IDE1 slave, hence the GRUB  entry for Ubuntu is:

[B]title Ubuntu, kernel 2.6.12-9-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hdd1 ro quiet splash
initrd /boot/initrd.img-2.6.12-9-386
boot[/B]

Your filesystem root is on the first partition of your IDE1 slave drive, hence you see "root=/dev/hdd1" - as IDE1 slave is hdd in Linux and it's the first partition, so its hdd1.

But to confuse matters GRUB names and numbers drives and partitions is a little differently. Firstly it counts partitions from zero not 1. Secondly, GRUB numbers hard drives by their boot sequence. 

So, as IDE1 slave (Linux hdd) is the first boot device, the GRUB root statement (which has a different meaning to root in Linux)  becomes 

**root (hd0,0)**

The important point here is that as far as GRUB is concerned your Windows XP install is on disk hd1 not hd0. This has been said before in this thread, but what has been missed is that Winodws will only boot if it thinks it is on the first boot device, which it isn't. But a little trick in GRUB will fool Windows into thinking it is. That's what the "map statments" do. It makes Windows think it is booting for the first hard drive.

Make the change to "menu.lst" and you should have a functioning dual-boot system with both hard drives plugged in the way you started out.

---

### Post by lha on 2006-01-07
[QUOTE=Flune]Here's a thought: right now, I have my Windows drive on IDE 0 Master and my Linux partition on IDE 1 Slave; since I'm using the Linux MBR with GRUB in the long run anyway, what if I switch the two drives?  Would this work? Furthermore, what would I need to reconfigure in my GRUB files to get this to work?[/QUOTE]

It is possible, you'd have to edit fstab and device.map, too, to make it work.

Here's a thing you might want to try before swapping those drives: 
Run sudo update-grub again. It might be necessary because you edited device.map. Change root (hd1,0) in menu.lst to rootnoverify (hd1,0) in the line below "title Microsoft Windows XP Professional". You might also need to add

map (hd0) (hd1)
map (hd1) (hd0)

under rootnoverify (hd1,0).

---

### Post by lha on 2006-01-07
Oh, Kipper had the time to answer before I did. :)

---

### Post by Flune on 2006-01-07
Ok, tried that, got an
Error 11 (I think): Unrecognizable device string

And now, to boot into Linux gives me and Error 17.  And then freezes.  So I'm stuck in Windows.

Thoughts? I don't really have anything on this drive, and I have no problems reformatting it, which seems to be the next step for me.  Is there a way to just start from scratch, install Ubuntu onto the second drive again, and then dual boot somehow by installing GRUB or some equivalency to Windows instead?

All of this is magnified by the problem that I can't access my (Pheonix) BIOS anymore.  I've ah...* cough * fogotten the password and don't know how to reset it. If anyone has recommendations on that as well, I'd appreciate it.

Here's the real issue: all I want is access to GCC or some sort of C and C++ compiler.  If someone can tell me what I need to know set up a _free_ Windows compiler, that's all I'd really need for a while.  I can wait to set the rest of Ubuntu up for a month until I have access to my Linux friends elsewhere, again, but the programming end of all of this is essential.

---

### Post by lha on 2006-01-08
[QUOTE=Flune]Ok, tried that, got an
Error 11 (I think): Unrecognizable device string

And now, to boot into Linux gives me and Error 17.  And then freezes.  So I'm stuck in Windows.

Thoughts? I don't really have anything on this drive, and I have no problems reformatting it, which seems to be the next step for me.  Is there a way to just start from scratch, install Ubuntu onto the second drive again, and then dual boot somehow by installing GRUB or some equivalency to Windows instead?

All of this is magnified by the problem that I can't access my (Pheonix) BIOS anymore.  I've ah...* cough * fogotten the password and don't know how to reset it. If anyone has recommendations on that as well, I'd appreciate it.[/QUOTE]

Ok, this ones really tough...

Let's find out what GRUB sees. Boot to GRUB with your both hard drive's plugged in. Do not select any of those items in menu, but press c to get into GRUB's 
command line. You will see some instructions and a prompt grub>. Type

cat (hd

and press <tab>. GRUB should show all possibilities how to complete this line, something like this:

```
grub> cat (hd
 Possible disks are:   hd0 hd1

grub> cat (hd
```

So here GRUB sees two hard drives. We want to know what kind of partitions GRUB thinks they have. Hit 0,, (a zero and a comma, 2 keypresses!) and then <tab>.

```
grub> cat (hd0,
 Possible partitions are:
   Partition num: 0, Filesystem type is fat, partition type 0xb
   Partition num: 1, Filesystem type unknown, partition type 0x82
   Partition num: 2, Filesystem type is ext2fs, partition type 0x83
   Partition num: 4, Filesystem type is ext2fs, partition type 0xfd

grub> cat (hd0,

```

Now, press backspace to erase the 0, from command line and type 1, (a number one and a comma) and press <tab>, again. That is, you should have
```
grub> cat (hd1,
``` on your command line and then press <tab>. If you have only one partition on this drive, GRUB completes line like this:

```
grub> cat (hd1,4)
```

Now you can press backspace to erase everything on command line and type halt and press enter to shut down.

It is possible to boot GRUB using Windows' own boot loader NTLDR. You'll have to copy a boot sector from Linux drive to a file in Windows' file system and edit BOOT.INI to make this new boot-sector-in-a-file visible in your NTLDR. There's a program called[BootPart]("http://www.winimage.com/bootpart.htm") for Windows which does this almoust automatically. You can find some insights on how this proggie does it's trick [here]("http://hacks.oreilly.com/pub/h/2337") and [there]("http://www.techspot.com/vb/all/windows/t-23581-Dual-Booting-Windows-and-Linux-2-different-drives.html").

[QUOTE=Flune]Here's the real issue: all I want is access to GCC or some sort of C and C++ compiler.  If someone can tell me what I need to know set up a _free_ Windows compiler, that's all I'd really need for a while.  I can wait to set the rest of Ubuntu up for a month until I have access to my Linux friends elsewhere, again, but the programming end of all of this is essential.[/QUOTE]

It's a long time since I programmed under Windows, but I remember using [MinGW]("http://www.mingw.org/").

---

### Post by Kipper on 2006-01-08
Flune,

I'm sorry you seem to have run into problems. Starting over with your Ubuntu install and installing GRUB on the MBR of the drive Ubuntu is on should get you going, but before you re-install maybe we can sort the problem out. Not being able to get into your BIOS is a problem, as you cannot check/change the boot  sequence. I cannot hlep you with that, I've never put a password on a BIOS as I don't use my machines in public spaces. I guess you'll have to Google for a forum about your m/board to see how this can be by-passed/reset. It could just be a case of clearing the CMOS which would return the BIOS to it's default(factory) settings. But you must check your m/board's documentation for that before doing anything else. 

Just to re-fresh can you confirm your current drive set up is as before:

IDE 0:
-master: Windows XP 
-slave: disc drive
IDE 1:
-master: disc drive
-slave: Linux system

Can you boot into Ubuntu on your slave drive at all?  Yes/no?
What actual changes did you make to your GRUB menu.lst file? 
Was it just the change to the "Windows" section before this went haywire?
Was it exactly as I typed?
Can you boot into Windows at all?

---

### Post by Kipper on 2006-01-08
Flune,

Ok, I see Lha has given you the instructions to use GRUB in "command-mode".

He is right that is it possible to use Window's own boot mechanism to boot a Linux system. My perferred way to do this is by using a program called "W32.grub". But this would only be necessary if you can no longer access the GRUB you installed on your IDE1 slave drive. In anycase, if need be, Unbuntu has a "rescue disc" mechanism that might yet save the day. 

Lha, seems to have the job in hand, good luck.

---

### Post by lha on 2006-01-08
I forgot to mention that I have never used BootPart or even NTLDR. I just ran into pages that mentioned using those to boot Linux. Messing around with NTLDR can be quite dangerous and I have no knowledge at all on recovering NTLDR to usable state if it gets screwed up. So maybe that should be used as a last resort after extensive backuping of your files.

---

### Post by Thirsteh on 2006-01-08
Not sure if someone has said this previously, but if you're going to dualboot, install Windows first, and DEFRAGMENT!!!! It's so insanely important it hurts. Then install Linux.

---

### Post by Kipper on 2006-01-08
[QUOTE=Thirsteh]Not sure if someone has said this previously, but if you're going to dualboot, install Windows first, and DEFRAGMENT!!!! It's so insanely important it hurts. Then install Linux.[/QUOTE]

Very true, but this ONLY applies if you are going to install Linux on the same disk as Windows. Install Linux on a second disk and it doesn't matter.

---

### Post by Thirsteh on 2006-01-08
[QUOTE=Kipper]Very true, but this ONLY applies if you are going to install Linux on the same disk as Windows. Install Linux on a second disk and it doesn't matter.[/QUOTE]

Ah, yes, of course. I've only ever done dual-booting on a single disk so didn't get that down with the other stuff. Thanks though :D

---

### Post by Kipper on 2006-01-10
FLune,

Are still out there? Winning or losing? Just wondering if we helped you to get anywhere with your dual-boot project.

---

