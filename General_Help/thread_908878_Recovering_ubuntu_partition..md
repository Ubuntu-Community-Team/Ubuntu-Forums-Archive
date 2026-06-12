---
title: "Recovering ubuntu partition."
date: 2008-09-02
forum: General Help
---

### Post by Kronie on 2008-09-02
So i was using ubuntu a wile back, and it had poor gaming support, so idecided to install vista to dualboot, but vista didnt want to install on the pc with installed linux, so i just moved the ubuntu partition from primary drive to external USB drive and turned it off when i was installing windows 
SO
now i want to give ubuntu another go.
How do i tell grub that i have ubuntu on external hard drive?

---

### Post by falcon61102 on 2008-09-03
You'd have to boot from the live CD and edit the menu.lst.  Make sure your USB drive is plugged in.  Try this:
```
sudo grub
find /boot/grub/stage1
root (hdX,Y)
setup (hdX)
quit
```

What this is going to do is first find where your boot files are and it will output a display that's going to be something like "(hd0,1)".  You're going to take what's output from the find command and use it in the root command.  Then for the setup command you only use (hdX) which is hd plus the first number that's output.  That will setup your GRUB to boot again from the USB drive.  

If you want to guarentee that you don't accidentally overwrite your Windows info, unplug the internal HD while you do all this since you won't need it anyway.  Otherwise, just be real careful with the commands.

Once you setup the GRUB, you are probably going to have to edit a couple other files since the setup was on a different HD a couple of the HD UUIDs might have to be changed.  To do this, first run:
```
sudo blkid
```
This will print out all the UUIDs for the HDs installed.

Now you want to change the fstab to reflect that information:
```
gksudo gedit /etc/fstab
```

You should see a number of lines there but you want to find the one that has the mount point of "/" and change its UUID to match that of the one that printed out above.  Make sure you save before you close.

Also, you are going to need a SWAP partition to be established if you don't already have one.  You can use gparted on the LiveCD to do this.  Once you create a SWAP partition, you are going to need to update that UUID in the fstab as well.  You can use the same procedure as above, but make sure you run the blkid command again to get the up to date UUID.

Those should be the only major things that you have to do manually.  You should be able to boot at that point and you may have to configure a few things once your running but that should get you going.  

Another note.  The GRUB update you are doing will install the GRUB to the USB drive.  That way the GRUB will only be present when you boot from the USB drive.  Then what you can do is set you boot order to have USB devices first and that way any time you boot with your USB HD plugged in, it will go to Ubuntu as a default.  Unplug the USB HD and it will go to visita default.

You could also just reinstall from the LiveCD and you wouldn't have to do all these edits.

---

### Post by Kronie on 2008-09-04
@falcon61102

thnx, will try it tomorow :)

---

### Post by falcon61102 on 2008-09-04
No problem.  Let me know how it goes.

---

### Post by Kronie on 2008-09-04
right so i done the first step
> You'd have to boot from the live CD and edit the menu.lst. Make sure your USB drive is plugged in. Try this:
Code:

sudo grub
find /boot/grub/stage1
root (hdX,Y)
setup (hdX)
quit

 but i see no signs of grub on boot. i think its because of vista OS chooser thingy... or grub would simply overwrite it?

---

### Post by falcon61102 on 2008-09-04
Originally the GRUB should have been installed onto your Ubuntu partition, but it may have gone to your MBR and been overwritten by Vista.  Try using the Super GRUB Disk to see if detects your Ubuntu installation.  You can get it at:
[www.supergrubdisk.org](www.supergrubdisk.org)

Just make sure that when you install, you don't install the GRUB on the internal HD otherwise anytime you unplug your USB drive, you'll get an error.  A surefire way to avoid this would be to unplug or remove your internal HD temporarily until you get the external GRUB working correctly.  Then you can't overwrite the internal.

If you want to only have the GRUB come up when you boot to the external I recommend removing the internal HD temporarily so that it's not even detected.  This way you'll have two seperate booting systems.  This would also allow to boot from the USB HD from any computer once it's setup.

---

### Post by Kronie on 2008-09-04
basically what i wanna do here is to have ubuntu and vista to boot from grub. thats it. Just like after ubuntu install. i dont want to keep oroginal vista booter.

---

### Post by falcon61102 on 2008-09-04
Oh ok, then you can install the GRUB to the internal HD.  Use the Super GRUB Disk, it should auto detect everything for you.

---

### Post by Kronie on 2008-09-04
ok so now i got grub workin, i used SGD. The reason it didnt show up is because in bios i turned off the feature"boot from USB". And it seems like grub was installed on internal hd.. I  can boot windows from it too. But i also when i choose to boot Ubuntu(even in safe mode) i get 

Error 22. No such partition.

---

### Post by falcon61102 on 2008-09-04
That's probably because of the changes you made to your system.  Boot up from your liveCD and run the commands that you quoted earlier, dealing with the GRUB.  They should work now. 

If that doesn't work for some reason, then we'll have to manually edit the menu.lst.  Run the following commands and post them here, I'll help you figure out what you need to edit.  It all depends on how the GRUB is currently installed now.
```
sudo fdisk -l
```
-l is a lower case L

Open the menu.lst with:
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Kronie on 2008-09-04
just a quick update. i just found a temprorary "cure" for error 22. 
when grub pops up, i select ubuntu, and then press 'e' to edit settings. and it appears taht ubuntu thinks taht its still installed on hd0,3(right now its on 1,1) so, i changed it to 1,1 and i got to my custom ubuntu splash. it was loading for around 5 minutes. it was just a suqare buncing around the sides. no actual OS loading. and after 5 minutes it gave me black screen and a command line

heres what it said

```
Busybox 1.13 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initrafms) _(blinking)
```

not anything like my ubuntu :))

Also i tried to use ubuntu in safe-mode(and changing the hdx,y before booting, ofcourse) and all i got was just lots of commands loading. then at some point it stopped, and no OS was loaded.

---

### Post by falcon61102 on 2008-09-04
Getting there. 

As for this error, there are a couple things that can be causing it.  Next time you get to the GRUB, besides changing to (hd1,1), add one of these commands to the end of the kernal string:
```
all_generic_ide 
floppy=off 
irqpoll
```
If one doesn't work, try the next.  Also, you may need all three so you're going to have to play with it a little bit.

Once you do find a setting that works, make sure you edit your menu.lst so you don't have to edit the GRUB every time you boot.

EDIT: Here is some more reading on that error you're getting:
[http://ubuntuforums.org/showthread.php?t=765195&highlight=apci](http://ubuntuforums.org/showthread.php?t=765195&highlight=apci)

---

### Post by Kronie on 2008-09-04
tried all possible combinations of theese 3 settings. no luck. BUT, i tried turning on RAID in bios(i have sata HD and sata DVDRW) and i got Error 17(with changing (HDx,x) values).

---

### Post by falcon61102 on 2008-09-05
Changing the RAID setting may have reassigned the drive paths on startup so your external may no longer be (hd1,1)  If you boot up from the LiveCD and run fdisk you can see if that changed any or you could try a couple different combos at the GRUB menu with the hd numbers.

---

### Post by Kronie on 2008-09-05
just tried find /boot/grub/stage1 
and it said that its still hd1,1

---

### Post by falcon61102 on 2008-09-05
Post the results of:
```
sudo fdisk -l
sudo blkid
cat /boot/grub/menu.lst
```

Something's not quite right.

---

### Post by Kronie on 2008-09-05
> **ubuntu@ubuntu:~$ sudo fdisk -l**

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4652    37365760    7  HPFS/NTFS
/dev/sda2   *        4653       30394   206772224    7  HPFS/NTFS

Disk /dev/sdf: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       25738   206740453+   7  HPFS/NTFS
/dev/sdf2   *       25739       30401    37455547+  83  Linux

**ubuntu@ubuntu:~$ sudo blkid**
/dev/sda1: UUID="780E7E5E0E7E14FA" LABEL="Vista OS" TYPE="ntfs" 
/dev/sda2: UUID="318B513EDD69F843" LABEL="Program Files" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
/dev/sdf1: UUID="CE00E87000E86147" LABEL="My Book" TYPE="ntfs" 
/dev/sdf2: UUID="103a9b9c-4ddb-7496-09ff-2ddbb0116b9f" TYPE="ext3" 

**ubuntu@ubuntu:~$ cat /boot/grub/menu.lst**
cat: /boot/grub/menu.lst: No such file or directory
s

---

### Post by falcon61102 on 2008-09-05
Oops.  I forgot your menu.lst is on the external.  Could you post a copy of that here.

---

### Post by Kronie on 2008-09-05
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
default         0

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=474b1db3-339d-40b5-ac6f-e64a1bcc04e8 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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
# defoptions=quiet splash vga=795

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
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=true

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=474b1db3-339d-40b5-ac6f-e64a1bcc04e8 ro quiet splash vga=795
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=474b1db3-339d-40b5-ac6f-e64a1bcc04e8 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

```

changed menu.lst a bit. instead of (hd0,3) made it 1,1 in all ubuntu entries

---

### Post by falcon61102 on 2008-09-05
Ok, I found your problem.  Besides having to change to root (hd1,1) you need to change the UUID for your kernal line.  Currently the line reads:
```
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=474b1db3-339d-40b5-ac6f-e64a1bcc04e8 ro quiet splash vga=795
```

Change that to:
```
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=103a9b9c-4ddb-7496-09ff-2ddbb0116b9f ro quiet splash vga=795
```

Save and reboot.

---

### Post by Kronie on 2008-09-05
aw man, i just quit livecd like 10 mins ago D: ill try it out tomorow(or maybe later today)


but how the hell did u figure that out?! i mean... cmon! are u a robot or sumtin? 0_o

---

### Post by falcon61102 on 2008-09-05
Lol... lots of trial and error... lots of error.

---

### Post by Kronie on 2008-09-05
it worked! Dude i dont know how to thank you! ^_^

---

### Post by falcon61102 on 2008-09-05
No problem.  Glad I could help.  

Make sure change it for your recovery mode in the menu.lst as well just in case you ever need to boot to that.

---

### Post by Kronie on 2008-09-05
did :)

but seriously, how did u found out what was causing the error?
what are those bunch of numbers\letters?

---

### Post by falcon61102 on 2008-09-05
Each partition in your hard drive has a unique identifier called a UUID.  The GRUB uses that to show the path to the kernal file during boot.  When you get an Error 17 in the GRUB it means that it can't find a file or partition that the kernal is in so once you said that the stage 1 was still (hd1,1), I knew that the GRUB was still finding the right partition.  That means it was still looking for the kernal file.  Process of elimination.  Start with the easiest thing and work your way closer.

---

### Post by Kronie on 2008-09-05
oh, so this is where the numbers came form :)

> ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="780E7E5E0E7E14FA" LABEL="Vista OS" TYPE="ntfs"
/dev/sda2: UUID="318B513EDD69F843" LABEL="Program Files" TYPE="ntfs"
/dev/loop0: TYPE="squashfs"
/dev/sdf1: UUID="CE00E87000E86147" LABEL="My Book" TYPE="ntfs"
**_/dev/sdf2: UUID="103a9b9c-4ddb-7496-09ff-2ddbb0116b9f" TYPE="ext3"_**


now i get it :)

again, thanx a lot for help!

---

### Post by falcon61102 on 2008-09-05
Exactly.  No prob.

---

### Post by Kronie on 2008-09-05
one quick question tho. i just got an updates, and it includes the kernel update. in the new update the HD code, and (hdx,y) are the original ones(the ones that we had to change). is there any way to tell booter that OS is on another drive?

---

### Post by falcon61102 on 2008-09-05
You can try:
```
sudo grub update
```

There's more information about that at:
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

