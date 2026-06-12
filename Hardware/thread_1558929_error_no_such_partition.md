---
title: "error: no such partition"
date: 2010-08-22
forum: Hardware
---

### Post by mikewbma on 2010-08-22
Hello Ubuntu buds:

I have a major problem.

I recently updated my ubuntu to the newest version. The update require me to reboot. But after reboot the screen shows

error: no such partition
grub rescue>

My laptop is  Acer aspire and it also has window 7 installed and I have no window 7 installation disk. 

I Tried many method:

1. I tried to from other post to insert the Ubuntu installation disk. The the screen shows

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

2. I tried to from other post

grub> rootnoverify (hd0,0)
grub> makeactive
grub> chainloader +1
grub> boot

I get Unknown command for each
plus i got grub rescue not grub.
and I don't know how to get grub and I don't know what version of
grub I have.

3. reinstall ubuntu
well i tried from other post to press exit at the beginning and select install ubuntu

the screen shows a brief: Critical Temperature and then it shows
method 1.

4: Erecovery disk for window 7.
Stopped half way because of an error.


I also tried other method involve sudo
all I get is
/bin/sh: sudo: not found

Can some expert please help me.

---

### Post by IcarusR on 2010-08-23
Did the UUIDs get changed.

Compare UUIDs in /etc/fstab & /boot/grub/grub.cfg

The following command will show you your drive UUIDs

```
sudo blkid
```

---

### Post by phoenix6669 on 2010-08-23
i'm having the same problem except i'm running vista and i have no vista disk and my wubi iso isn't reading...i've tried the sudo commands but i get the unknown command msg...i've tried boot...but i get unknown command...it doesn't matter what command i put in it still says unknown command...i'm using my netbook rightnow but it doesn't have a diskdrive and my flashdrive is only 256mb...so i think i8 have a real big problem...

---

### Post by phoenix6669 on 2010-08-23
actually mine isn't saying error: no such partition...mine is saying error: no such device and lists the uuid...and i can't boot into vista because of the grub rescue prompt

---

### Post by phoenix6669 on 2010-08-23
i can't even open a terminal to check the uuids or do anything

---

### Post by bcbc on 2010-08-23
> **phoenix6669 said:**
> i can't even open a terminal to check the uuids or do anything

You might be affected by this: [https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)

If that is the case, you just need to reinstall the windows bootloader: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by phoenix6669 on 2010-08-23
see the thing is...is that at the grub rescue prompt it's saying that the sudo command is unknown so i can't reinstall the grub bootloader and i don't have a vista dvd to access 
bootrec.exe /fixboot to fix the vista bootloader if i have to...i type any of this...and it says unknown command sudo...unknown command find...unknown command root...everything i type in is an unknown command
sudo grub 

find /boot/grub/stage1

root (hd<a>,<b>)

---

### Post by bcbc on 2010-08-23
> **phoenix6669 said:**
> see the thing is...is that at the grub rescue prompt it's saying that the sudo command is unknown so i can't reinstall the grub bootloader and i don't have a vista dvd to access 
bootrec.exe /fixboot to fix the vista bootloader if i have to...i type any of this...and it says unknown command sudo...unknown command find...unknown command root...everything i type in is an unknown command
sudo grub 

find /boot/grub/stage1

root (hd<a>,<b>)

You can't do any of this at the grub prompt. You need to download a windows repair cd and burn it and boot from it. Or boot from an ubuntu cd/usb and use lilo (sudo apt-get install lilo; sudo lilo -M /dev/sda mbr). that's the only way to fix your issue.

---

### Post by mikewbma on 2010-08-23
Their is no console
and sudo command is unknown

---

### Post by mikewbma on 2010-08-23
Their is some command that work for me

grub rescue>ls
(hd0)(hd0,5)(hd0,3)(hd0,2)(hd0,1)

grub rescue>set
prefix=(hd0,6)/boot/grub
root=hd0,6

---

### Post by mikewbma on 2010-08-23
Come to think of it
the root listed in set does not appear in the ls command
is that the problem.

If it is how do you change it?

---

### Post by drs305 on 2010-08-23
> **mikewbma said:**
> Come to think of it
the root listed in set does not appear in the ls command
is that the problem.

If it is how do you change it?

At the grub2 prompt (substitute the correct X,Y values):
```
set prefix=(hdX,Y)/boot/grub
set root=(hdX,Y)
```

Confirm you have the correct partition by running:
```
ls (hdX,Y)/boot
```
to make sure it lists the linux and initrd files.

---

### Post by phoenix6669 on 2010-08-24
is there any way i can put the windows re on a 256mb usb stick???...cause thats all i have right now...my net book doesn't have a cd/dvd drive

---

### Post by mikewbma on 2010-08-24
> **drs305 said:**
> At the grub2 prompt (substitute the correct X,Y values):
```
set prefix=(hdX,Y)/boot/grub
set root=(hdX,Y)
```

Confirm you have the correct partition by running:
```
ls (hdX,Y)/boot
```
to make sure it lists the linux and initrd files.


But Their is 5 different combinations of (X,Y) which one is the correct one from the result of ls?

---

### Post by drs305 on 2010-08-24
> **mikewbma said:**
> But Their is 5 different combinations of (X,Y) which one is the correct one from the result of ls?

You can run the second command I mentioned, substituting X,Y values from the "ls" command:
```
ls (hd[COLOR="DarkRed"]X,Y[/COLOR])/boot
```
The one with your Ubuntu installation will provide a result which includes your kernel (vmlinuz) and initrd  files. Experiment with the results the "ls" command produced. Most likely your install is (hd0,5) if you have Windows installed or (hd0,1) if Ubuntu is your only OS.

If you still are having problems, run the boot info script from this link:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")
Please place the results within "code" tags (press the # icon to generate the tags).

---

### Post by drs305 on 2010-08-24
> **phoenix6669 said:**
> is there any way i can put the windows re on a 256mb usb stick???...cause thats all i have right now...my net book doesn't have a cd/dvd drive

If you are just trying to restore Windows after messing up the Windows boot, boot to the LiveCD and run the following:
```
sudo apt-get install lilo
sudo lilo -M /dev/sd[COLOR="Red"]a[/COLOR] mbr
```
If "sda" is not your Windows drive, change the letter. Disregard any warning messages about missing parts of lilo - you aren't really doing a full installation of lilo.

This should allow Windows to boot if only the MBR was corrupted. If you are having further problems, please start your own thread and describe the problems you are having. Running the boot info script as linked in the previous post would be helpful in the new thread.

---

### Post by mikewbma on 2010-08-24
When I type

grub rescue>ls (hd0,5)/boot
grub rescue>ls (hd0,1)/boot

For both I get
error:unknown filesystem

---

### Post by drs305 on 2010-08-24
> **mikewbma said:**
> When I type

grub rescue>ls (hd0,5)/boot
grub rescue>ls (hd0,1)/boot

For both I get
error:unknown filesystem

Did you also try (hd0,2) and (hd0,3), which is the other partition found?

But really, all we can do is guess. If you can't find your partition in one of the "ls" results we need the boot info script results to help you.

---

### Post by mikewbma on 2010-08-24
grub rescue> ls (hd0)/boot
grub rescue> ls (hd0,3)/boot
grub rescue> ls (hd0,2)/boot

all

error: unknown filesystem

Maybe is the the boot script we need how do we fetch it

---

### Post by drs305 on 2010-08-24
> **mikewbma said:**
> 

Maybe is the the boot script we need how do we fetch it

Boot the LiveCD then go to the link in post #15. Download and run the script in accordance with the instructions on the linked page, then copy the results of the RESULTS.txt here.

---

### Post by mikewbma on 2010-08-24
Hmm The LiveCD your refering to the Ubuntu installation cd?

---

### Post by drs305 on 2010-08-24
> **mikewbma said:**
> Hmm The LiveCD your refering to the Ubuntu installation cd?

Yes. Just any linux cd that can get you to a point where you can access the internet, run a bash script/linux commands and post the results.

---

### Post by mikewbma on 2010-08-24
Well I Tried the Ubuntu CD the newest version downloaded moments ago.

Once I plug in the CD and reboot the computer. The screen show the purple Ubunut logo. Then it shows the error that I posted at the beginning with the 


Can not mount /dev/loop0 ...

from the beginning of the thread

Do you think i should try some linux that is not Ubuntu

---

### Post by phoenix6669 on 2010-08-25
my ubuntu live cd won't boot and i don't have a vista dvd cause my notebook didn't come with one when i bought it...and all i have right now is a flash drive 256Mb Centrios 80x but i don't know if i can make it bootable and i am using an Acer Aspire One right now so i can't even make an image disk

---

### Post by bcbc on 2010-08-25
You can download a vista and 7 recovery cd from here [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by mikewbma on 2010-08-25
If you just have terminal running with out the GUI

Where is the USB located from root. Cuz I can save the shell script in the USB and load it in because the System doesn't have internet.

---

### Post by bcbc on 2010-08-25
> **mikewbma said:**
> If you just have terminal running with out the GUI

Where is the USB located from root. Cuz I can save the shell script in the USB and load it in because the System doesn't have internet.

```
sudo blkid 
```

will tell you all partitions and devices. I expect the USB partition will be /dev/sdb1 but you should be able to tell. 

if it is, you can mount it:
```
sudo mount /dev/sdb1 /mnt
```

Then 
```
sudo bash /mnt/pathtoscript/boot_info (press TAB and it will autocomplete)
```

---

