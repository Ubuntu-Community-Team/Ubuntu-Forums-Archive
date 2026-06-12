---
title: "How to restore grub?"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by LittleKoy on 2009-07-07
This is the same old story. I installed WinXP after Ubuntu, and that idiot os overwrote the bootloader. Now I want grub back.

I searched and found several guides, but they all tell me to (in a LiveCD):
```
grub> find /boot/grub/stage1
```

but I get Error 15 (file not found)

I even tried
```
grub> find /media/disk/boot/grub/stage1
```

but it still doesn't find it (which is strange, sine the file IS there).

And about root (?,?), I don't know what to put inside it. My Ubuntu / is on sda1, but if I do root (sda,0) or (sd0,0) it says error while parsing number.
If I do (hdX,0), it says that hdX is not a drive, for X=0,1,2,3,..

I'm stuck, what can I do?

---

### Post by dstew on 2009-07-07
You might have to mount the hard disk to the Live CD file system before the grub shell program can find it. Once you have the output of the grub **find** command, use that as the root to install grub.

If you know Ubuntu's root is /dev/sda1, a safe bet for grub's root argument is (hd0,0). Then, install the boot loader into the Master Boot Record of /dev/sda with setup (hd0):```
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```Then, shut down the Live CD system, remove the CD from the drive, and reboot.

---

### Post by LittleKoy on 2009-07-07
I mounted it as /media/disk.

find /boot/grub/stage1 and /media/disk/boot/grub/stage1 both give error 15.
root (hd0,0) tells me "Error 21: selected disk does not exist"

---

### Post by dstew on 2009-07-07
From a Live CD system, do```
sudo fdisk -l
```and post the output to the forum.

---

### Post by LittleKoy on 2009-07-07
```
Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000810f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2576    20691688+  83  Linux
/dev/sda2            2577       46922   356209245   83  Linux
/dev/sda3   *       46923       48137     9759487+   7  HPFS/NTFS
/dev/sda4           48138       48641     4048380    5  Extended
/dev/sda5           48139       48641     4040347+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf079e959

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    c  W95 FAT32 (LBA)

```

The second is an USB hd, I only plug it occasionally for backup..

---

### Post by dstew on 2009-07-08
Strange, it all seems very straightforward. Did you happen to format your Linux file system as ext4? Perhaps that is causing some trouble with the grub shell program on the Live CD.

---

### Post by LittleKoy on 2009-07-08
> **dstew said:**
> Strange, it all seems very straightforward. Did you happen to format your Linux file system as ext4? Perhaps that is causing some trouble with the grub shell program on the Live CD.

Yes, your guess is correct..

---

### Post by presence1960 on 2009-07-08
let's get an exact shot of your setup & boot info. Boot the Live Cd and download to the desktop the Boot Info Script 0.32 from here: [http://sourceforge.net/projects/bootinfoscript/files/](http://sourceforge.net/projects/bootinfoscript/files/) 
Once DL'd open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. paste the entire contents of the file back here, then when pasted highlight all text and click # on the toolbar to place code tags around the text. This info will shed light on a lot of things- like if and where GRUB is installed on your machine.

---

### Post by presence1960 on 2009-07-08
> **dstew said:**
> Strange, it all seems very straightforward. Did you happen to format your Linux file system as ext4? Perhaps that is causing some trouble with the grub shell program on the Live CD.

I have ext 4 for both 9.04 Ubuntu and Sabayon 4.2 and have not had those problems. That does not mean it can not happen. Let's see what the boot info script returns when it is run.

---

### Post by presence1960 on 2009-07-08
> **LittleKoy said:**
> This is the same old story. I installed WinXP after Ubuntu, and that idiot os overwrote the bootloader. Now I want grub back.

I searched and found several guides, but they all tell me to (in a LiveCD):
```
grub> find /boot/grub/stage1
```

but I get Error 15 (file not found)

I even tried
```
grub> find /media/disk/boot/grub/stage1
```

but it still doesn't find it (which is strange, sine the file IS there).

And about root (?,?), I don't know what to put inside it. My Ubuntu / is on sda1, but if I do root (sda,0) or (sd0,0) it says error while parsing number.
If I do (hdX,0), it says that hdX is not a drive, for X=0,1,2,3,..

I'm stuck, what can I do?
I know this is probably a no brainer, but based on your command you posted did you preface grub with sudo? I ran it with just grub, and when i ran the find /boot/grub/stage1 I got an error 15 like you did.

---

### Post by presence1960 on 2009-07-08
```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

if what you say about your partitions is accurate in #5 use root (hd0,0). In #6 use setup (hd0).

when you boot GRUB will be in the MBR and point to your menu.lst in sda1

---

### Post by brookie on 2009-07-08
I'm not a guru or anything, just a noob, but I followed this tutorial and added a dual boot winxp partition with no problems. [http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=6]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=6")

it got my grub back in order and all worked well afterward. 
good luck,
brook

---

### Post by presence1960 on 2009-07-08
> **brookie said:**
> I'm not a guru or anything, just a noob, but I followed this tutorial and added a dual boot winxp partition with no problems. [http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=6]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=6")

it got my grub back in order and all worked well afterward. 
good luck,
brook

Right on Brookie, same thing I posted except I didn't tell how to edit menu.lst for the windows entry. One step at a time. But your post was right on the money. The OP's problem is he isn't using sudo to run the grub command, that's why he is getting error 15. Need administrative priviledge to run that grub command.

---

### Post by LittleKoy on 2009-07-08
OPS :D

Ah ah, so that was the problem... Thank you, I'm back in Ubuntu :D

---

### Post by presence1960 on 2009-07-08
> **LittleKoy said:**
> OPS :D

Ah ah, so that was the problem... Thank you, I'm back in Ubuntu :D

Glad to hear that! Enjoy Ubuntu. BTW reboot & check to see if you can boot into windows. if not edit your windows entry in menu.lst to this:

```
title          Windows <your version>
rootnoverify   (hd0,2)
chainloader    +1
```

---

