---
title: "Wubi/GRUB on a USB Key and loop files on disk ?"
date: 2008-10-13
forum: General Help
---

### Post by Zakhafr on 2008-10-13
Hello guys,

here is a puzzle!

**What I want to do:** run a Linux Box (preferably Ubuntu) on a Windows XP PC where I have no administrator rights.

**Some possibilities:** although I have no administrator rights, it is still allowed to boot the PC from either a CD or a USB key.
Of course I have write access to the local hard drive, provided that I write only "user files" (eg, writes are prohibited only in "system" places such as c:\, c:\windows, etc...)

**What I could do (but won't):** of course, I already have a USB key (Mandriva inside) and could boot on it, repartition the hard drive and install whatever, but I don't want to do so because I would have trespassed (a lot!) my non-administrator rights on Windows.
I am also running Linux (Mandriva) on the PC, booted from the USB key, I have no question about that and it works fine, but what I would like is to have _the loop files on hard disk_, because the USB Key is a bit slow and has more space limitations.


So all that naturally points to **Wubi**.


My idea was then to have a USB key (it could be a very small one) just to start up the PC, the boot loop files located on the PC.


**What I did so far:** I tested I was able to run a Wubi from this PC. Making a C:\ubuntu directory and copying files on it is OK, it is allowed on my user rights.
What was not allowed was:
-1) modifying _C:\BOOT.INI_ to add the line to boot Ubuntu
-2) copy the files _wubildr_ & _wubildr.mbr_ to _C:\_
So I did these two operations with my Mandriva Key, and the Ubuntu Wubi works fine.
Now what I'd like to do is reverse these operations so that the PC stays *clean*, except C:\Ubuntu and its content which is "user files" I'm allowed to have. Of course to have a way to boot Ubuntu, I imagine the equivalent of wubildr could be on the USB key.
What I also did at home, is modify the Wubi GRUB menu.lst so that I have the choice booting several Wubi installs. It works fine, and allows me to test Intrepid while not disrupting my Hardy/Wubi install, and without the hassle of juggling with partitions.
So Wubildr is capable of booting **ANY** (eg not only c:\ubuntu) valid loop file, as long as you give it the full path. For example, I gave it *(hd0,2)/Intrepid/disks/root.disk* for my Intrepid beta install and all is fine!


**So the question is:** how do I "move" my wubildr & wubildr.mbr (or equivalent) to my USB key to be able to startup my Wubi Box on C:\ubuntu?


**What won't work:** my Mandriva Key is VERY good work from Mandriva community. It boots both live & persistent. I could take model on that because the Linux file system is on a compressed loop file on the key. But obviously that won't work because the GRUB residing on the key does not have NTFS support. So I won't be able to address C:\ (or the Linux equivalent) because it is obviously formated in NTFS!

**What is out of scope:** I could also try having a Windows bootloader on the USB key, and do the Wubi trick on it! But Windows being not open, it'll be hard to find documentation about that, not counting the copyright problem... and obviously, I don't want to pay for a whole Windows XP just to run the bootloader!

**What is guess/understand:** I guess _wubildr.mbr_ might be equivalent to an MBR record. This MBR record (stage 1?) do most likely chain on _wubildr_ (stage 2?) from the same drive.
To my understanding, wubildr is just another stage 2 Grub loader, the **big **difference is that it has been given NTFS support. So from this bootloader, you can then access data on any NTFS formatted partition on your system.

So if I am correct, the operations would be:
- make wubildr.mbr my USB Key MBR *(how do I do that, either on Windows on Linux?)*
- copy to the USB key: wubildr and the parts of \ubuntu\winboot wubi seems to need (this file looks like places to search for the GRUB menu.lst, and must probably reside on the same drive wubildr was booted from).


*Any Wubi specialist would like to help with this issue?*

I'm pretty sure such a possibility would be appreciated by most people wanting to run their favorite Linux apps from a place where they don't have admin rights (work :) !)

---

### Post by ago on 2008-10-13
Ubuntu 8.10 comes with a LiveUSB creator. You might look into that first.

---

### Post by Zakhafr on 2008-10-13
Ok, I'll look at it :)

Do you mean the LiveUSB creator produces a USB key with **bootloader having NTFS support** like wubi has ?

If so, it is obviously a working solution.
If not, it is the same as I have with my Mandriva 2007.1

_I already have_ an USB LiveRemaster tool with that Mandriva, but at boot/GRUB time it _does not have NTFS support_, just ext2/3 or FAT :(
So Mandriva's bootloader can mount a loop file on the FAT partition (what is does) but could not work with a loop file stored on NTFS.

*Edit: I love Wubi, you did a really very good job with that!*

---

### Post by Zakhafr on 2008-10-13
> **ago said:**
> Ubuntu 8.10 comes with a LiveUSB creator. You might look into that first.

It does not "come" (would mean pre-installed on the Live CD as it is on Mandriva)... or I failed to find it :)
But it seems to exist a synaptic package called **USB-creator** on the intrepid repository.

Is it the good one ?

I downloaded it, launched it, it saw my USB key, used it, seems to have copied the same files as thoses on the CD... but I cannot boot on this USB key :(
System accesses the key and stops.
Nothing on the screen.
The partition is FAT32 with boot flag on.
Looks like the key doesn't have a proper MBR set.

And by the way, there is no menu.lst on this system. It seems that the options of the menu are in multiple .cfg files.
I'll try to address that once I've found a way to make the USB key bootable!

But, correct me if I'm wrong, as the key is using what is on the CD I might just boot from the CD if I give the right options such as:
(hd0,2)/ubuntu/disks/root.disk ....

It's quite cumbersome but as a test it would avoid fighting with non-booting USB keys!


-----------------------------------------------------------

**[Edit]**
____________
I managed to make the boot on the key work using tutorial here
[http://www.pendrivelinux.com/2008/10/06/usb-ubuntu-810-install-from-windows-non-persistent/]("http://www.pendrivelinux.com/2008/10/06/usb-ubuntu-810-install-from-windows-non-persistent/")

It is a tutorial from Windows. The ubuntu810.bat is badly broken because it does not change to the proper directory at the end, but I repaired it.
So now I have a key booting Intrepid Beta and that's fine, but as the first post says, that's **NOT **what I want.
I want the USB key to contain only files for the boot sequence, and boot on loop files on the harddrive with NTFS filesystem.

So I then tried to do as you suggested.
From here I have to *guess*!

So here is what I did, I edited the text.cfg file under directory syslinux that appears to contain booting commands.

And I made it that:
```
default live
label live
  menu label ^Try Ubuntu without any change to your computer
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
label Ondisk
  menu label ^Start Intrepid on your computer
  kernel (hd0,2)/ubuntu/disks/boot/vmlinuz-2.6.27-6-generic
  append root=UUID=CAD0969BD0968D77 loop=(hd0,2)/ubuntu/disks/root.disk initrd=(hd0,2)/ubuntu/disks/boot/initrd.img-2.6.27-6-generic ro quiet splash --
```

First label "live" and its command are the standard ones.
Second, my "Ondisk" is my boot entry, it should be booting the kernel that is on my NTFS disk (being hd0,2 on my GRUB). I put the exact same parameters GRUB uses when booting from Wubi on my disk. I just cut/paste them from the C:\Ubuntu\winboot\menu.lst.


I can see a line labeled "Start Intrepid on your computer" when I boot from the key, but it does nothing when I select this line and try to boot!

So either I entered bad parameters, or bootloader on the CD/USB does not support NTFS systems (which I suspect strongly)... and I still need some Wubi thingies to bootstrap that.


Anymore ideas or clues to what is wrong ?

---

### Post by Zakhafr on 2008-10-14
I did a little more research.

Booting on a USB key uses a little piece of software known as Syslinux. Documentation here: [http://syslinux.zytor.com/wiki/index.php/SYSLINUX]("http://syslinux.zytor.com/wiki/index.php/SYSLINUX")

There is a hidden file on the FAT32 USB key root named ldlinux.sys
It is launched at boot time and reads its menu configuration from text files situated in /syslinux (also other possible locations).

At this point, there is **NO** NTFS support.

I tried to add a line to load wubildr.mbr

It loads saying:
Loading \wubildr.mbr ... loaded

But then nothing else happens, although I had also copied wubildr and relevant files to the USB Key root.

For now I think the best option would be to find an old Windows 98, format the key, run SYS on the key to make it bootable and install Wubi on it :)
More reasonably, I'll try to build a PE Windows Key so that I have a chance to run wubi from that :)

---

### Post by Zakhafr on 2008-10-14
Here is what I'd like to do: [http://ubuntuforums.org/showthread.php?t=740950]("http://ubuntuforums.org/showthread.php?t=740950")

Unfortunately I think the user didn't make a "How To" as suggested by Ago.

I'll try a private message ;)

---

### Post by Zakhafr on 2008-10-14
So here is the **how-to**

- Start you Ubuntu machine.
- Download the source of grubinst from SourceForge [http://downloads.sourceforge.net/grub4dos/grubinst_1.0.1_src.zip?modtime=1167501947&big_mirror=0]("http://downloads.sourceforge.net/grub4dos/grubinst_1.0.1_src.zip?modtime=1167501947&big_mirror=0")
- Uncompress the zip file to some directory (in your home partition for example)
- Open a terminal
- Go to that directory
- Compile grubinst using
 ```
make -f Makefile.lnx
```
- Get the proper device name of you USB key. It is **IMPORTANT** you do not do mistakes here otherwise you will destroy you hard disk regular MBR. So for example, type
```
sudo fdisk -l
```
and try to see how is your USB key named. For example, mine is /dev/sdc
- In case we got wrong (2 precautions), we are going to save the MBR we will overwrite, so that we should be able to put it back if there was a problem. So type:
```
sudo ./grubinst --save-mbr=USB.mbr /dev/sdX
```
(replace X by the proper letter of your USB)
- Now the MBR of you key has been saved next to grusint program.
- We can now, for good, write Grub4DOS to the key (always replace X by relevant letter):
```
sudo ./grubinst /dev/sdX
```
- Now we copy necessary files for wubi
- Copy **wubildr** to the root of your key, and rename it **grldr**
- Make a **ubuntu** directory to the root of your key
- From your harddrive, copy **/ubuntu/winboot** to the **/ubuntu** on the key


That's all you need to boot!
You can use the rest of your key to store you data. 

It could work directly (depending on your system)

On mine, it does as described in the post I linked: hd0 is now the USB key (you can see for a short moment a message from Grub4DOS saying it boots from hd0, so definitely, the USB key is hd0), the primary disk on which wubi disks are stored became hd1.

I managed to boot changing hd0 to hd1, but I got to busybox (possibly something in /etc/fstab).

So the next step would be to correct that issue: maybe the trick Ago gave for the boot, and if I manage to remap the drives in Ubuntu to their original names it would be fine!

---

### Post by ago on 2008-10-15
That's cool but you need to realize that wubi works like a normal installation, that means that the hardware is setup for your current rig, so if you take the USB key to a different machine you will have issues. This is why I was suggesting using the Live USB creator approach, because that will get you a Live CD + persistance (rw) environment which is not pre-configured for specific hardware (knoppix style).

You also probably need to edit root and groot in /ubuntu/disks/boot/grub/menu.lst so that they point to the UUID of the partition on the USB key.

---

