---
title: "how to open files from ext. hard drive?"
date: 2011-10-28
forum: Hardware
---

### Post by Matrix01 on 2011-10-28
ext. hard drive is connected in usb port,
and Natty is on monitor,

how do u open files?

---

### Post by jmate24 on 2011-10-28
go to a terminal and type: (this is to enable read/write on your ext usb drive)

```
sudo nautilus /media
```

if using pcmanfm then type:

```
sudo pcmanfm /media
```

then click on the long 'uuid' folder (the one that looks like a big code with letters and numbers (it's called hexidecimal) and open it then right click and go to the permissions tab and change the scroll box labeled 'root' in the file and folder permissions to your username and then go to the Group permissions and select the 'root' scroll box and change it to your username.

---

### Post by blackbird34 on 2011-10-28
You could just open nautilus, see your HD in the side bar, and click on it to mount it and view, open, read, write the files...

---

### Post by Matrix01 on 2011-10-30
deleted.

---

### Post by Script Warlock on 2011-10-30
> **Matrix01 said:**
> what is nautilus?


nautilus - the GNOME File Manager or ubuntu's default file manager

---

### Post by Matrix01 on 2011-10-30
how do u find out whether nautilus or pcmanfm? 


> **jmate24 said:**
> go to a terminal and type: (this is to enable read/write on your ext usb drive)

```
sudo nautilus /media
```if using pcmanfm then type:

```
sudo pcmanfm /media
```then click on the long 'uuid' folder (the one that looks like a big code with letters and numbers (it's called hexidecimal) and open it then right click and go to the permissions tab and change the scroll box labeled 'root' in the file and folder permissions to your username and then go to the Group permissions and select the 'root' scroll box and change it to your username.

---

### Post by Script Warlock on 2011-10-30
click any folder you find in your desktop or home and press HELP>ABOUT

---

### Post by Matrix01 on 2011-10-30
neither sudo nautilus /media nor sudo nautilus /media does not work.

[ATTACH]205861[/ATTACH]

---

### Post by Script Warlock on 2011-10-30
usually ubuntu will automount any drives you plugged. what do you mean ext hard drive.. external?

---

### Post by Matrix01 on 2011-10-30
i opened document,
where do u see 'HELP'?

[ATTACH]205862[/ATTACH]

> **Script Warlock said:**
> click any folder you find in your desktop or home and press HELP>ABOUT

---

### Post by WasMeHere on 2011-10-30
Hi Matrix01,

Please post what flavour ('vanilla' Ubuntu, Kubuntu, Xubuntu, Lubuntu ...) of Natty (11.04) that you have! By the way, is Natty installed on the computer where the external disk is mounted? Or is Natty on another computer, from which you are logging in remotely?

Knowing this would make it easier for us to suggest what to do.

Have fun finding out :-)
Olle

---

### Post by Matrix01 on 2011-10-30
this 11.04 is booting from USB flash drive, not from external hard drive.


> **Olle Wiklund said:**
> Hi Matrix01,

Please post what flavour ('vanilla' Ubuntu, Kubuntu, Xubuntu, Lubuntu ...) of Natty (11.04) that you have! By the way, is Natty installed on the computer where the external disk is mounted? Or is Natty on another computer, from which you are logging in remotely?

Knowing this would make it easier for us to suggest what to do.

Have fun finding out :-)
Olle

---

### Post by Script Warlock on 2011-10-30
> **Matrix01 said:**
> i opened document,
where do u see 'HELP'?

[ATTACH]205862[/ATTACH]

we have a global menu in ubuntu just point your mouse on the top panel and see all options displayed.

---

### Post by WasMeHere on 2011-10-30
So you are running a live session. Is it 'vanilla' Ubuntu with Unity?

---

### Post by Matrix01 on 2011-10-30
when mouse is pointed on top panel,
file, edit, view, places, help showed up.
is this what you are talking about?

> **Script Warlock said:**
> we have a global menu in ubuntu just point your mouse on the top panel and see all options displayed.

---

### Post by WasMeHere on 2011-10-30
Hello again Matrix01,

> **Matrix01 said:**
> neither sudo nautilus /media nor sudo nautilus /media does not work.

[ATTACH]205861[/ATTACH]

From what you have posted I think that you run 'vanilla' Ubuntu Natty live. It is very strange that neither of those commands work. The screen output indicates that something is wrong with the superuser implementation, because it complains about the ***/etc/sudoers*** file. This file should be present in an installed environment. I am not sure about 11.04 live, but in 'vanilla' ubuntu 11.10 live, it is possible to run ***sudo nautilus /media*** and get a file browser window at the ***/media*** directory although ***/etc/sudoers*** is absent (and as usual *live*, you need no password to run *sudo*).

1. Have you been changing something in your live environment? For example installed something, tweaked something and made it resident with a casper-rw file?

2. Could your iso file be bad? Have you checked it with md5sum?

Have fun finding out :-)
Olle

---

### Post by Matrix01 on 2011-10-30
i downloaded unetbootin, and iso file, they are still saved in win7.,
and installed persistent Natty a week ago or so.
how do u check if this is vanilla natty?

i have not installed any other softwares yet,
this Natty has been troubling with launching Firefox.
so someone from forum told me to disable addons, but did not work after shut PC down.

how do u check iso file with md5sum?

> **Olle Wiklund said:**
> Hello again Matrix01,



From what you have posted I think that you run 'vanilla' Ubuntu Natty live. It is very strange that neither of those commands work. The screen output indicates that something is wrong with the superuser implementation, because it complains about the ***/etc/sudoers*** file. This file should be present in an installed environment. I am not sure about 11.04 live, but in 'vanilla' ubuntu 11.10 live, it is possible to run ***sudo nautilus /media*** and get a file browser window at the ***/media*** directory although ***/etc/sudoers*** is absent (and as usual *live*, you need no password to run *sudo*).

1. Have you been changing something in your live environment? For example installed something, tweaked something and made it resident with a casper-rw file?

2. Could your iso file be bad? Have you checked it with md5sum?

Have fun finding out :-)
Olle

---

### Post by WasMeHere on 2011-10-31
> **Matrix01 said:**
> i downloaded unetbootin, and iso file, they are still saved in win7.,
and installed persistent Natty a week ago or so.
how do u check if this is vanilla natty?

i have not installed any other softwares yet,
this Natty has been troubling with launching Firefox.
so someone from forum told me to disable addons, but did not work after shut PC down.

how do u check iso file with md5sum?
'Vanilla' means Ubuntu without prefix [KLX], if 11.04 using Unity desktop manager. The System Manager will give some basic information too.

Persistent live is still 'only' for testing. I think that it is not as stable as an installed system regarding updates and upgrades.

The md5sum can be downloaded from 
[[COLOR="RoyalBlue"]_https://help.ubuntu.com/community/UbuntuHashes_[/COLOR]]("https://help.ubuntu.com/community/UbuntuHashes")
and should be compared to the output of the following command
```
md5sum ubuntu-11.04-desktop-i386.iso   # or
md5sum ubuntu-11.04-desktop-amd64.iso
```

---

### Post by Matrix01 on 2011-11-02
where is system manager?

> **Olle Wiklund said:**
> 'Vanilla' means Ubuntu without prefix [KLX], if 11.04 using Unity desktop manager. The System Manager will give some basic information too.

Persistent live is still 'only' for testing. I think that it is not as stable as an installed system regarding updates and upgrades.

The md5sum can be downloaded from 
[[COLOR=RoyalBlue]_https://help.ubuntu.com/community/UbuntuHashes_[/COLOR]]("https://help.ubuntu.com/community/UbuntuHashes")
and should be compared to the output of the following command
```
md5sum ubuntu-11.04-desktop-i386.iso   # or
md5sum ubuntu-11.04-desktop-amd64.iso
```

---

### Post by WasMeHere on 2011-11-02
The System Manager can be found somewhere in your menus but at different places depending on your system, try at

*System -- Administration*

The program's name (command) is also different. In 'vanilla' Ubuntu, it can be called from a terminal window with the command
```
gnome-system-monitor
```

---

### Post by Matrix01 on 2011-11-04
[ATTACH]206275[/ATTACH]
opened update manager, and it looks like this.

need i click check?

> **Olle Wiklund said:**
> 'Vanilla' means Ubuntu without prefix [KLX], if 11.04 using Unity desktop manager. The System Manager will give some basic information too.

Persistent live is still 'only' for testing. I think that it is not as stable as an installed system regarding updates and upgrades.

The md5sum can be downloaded from 
[[COLOR=RoyalBlue]_https://help.ubuntu.com/community/UbuntuHashes_[/COLOR]]("https://help.ubuntu.com/community/UbuntuHashes")
and should be compared to the output of the following command
```
md5sum ubuntu-11.04-desktop-i386.iso   # or
md5sum ubuntu-11.04-desktop-amd64.iso
```

---

### Post by WasMeHere on 2011-11-04
> **Matrix01 said:**
> [ATTACH]206275[/ATTACH]
opened update manager, and it looks like this.

need i click check?

Yes, click 'check'!. You might be prompted to enter your password too. This way your present version of Ubuntu will be updated with security updates, bug-fixes and other improvements of the software. If updates are found, the 'install updates' button can be selected. Click that the receive and install the updates!

But stay away from the 'upgrade' button at the top, unless you have a recent backup!

---

### Post by Matrix01 on 2011-11-05
In a few days ago,
I clicked update, 
and while 11.04 was getting updated,  closed lid of this netbook, and opened lid again, monitor was blank,
and power button did not work,
so unplugged ac adapter, and plugged it again, turned netbook on,
this message was on monitor; "low graphic mode, you have to configure"

i could not figured this out, so
reinstalled 11.04.

> **Olle Wiklund said:**
> Yes, click 'check'!. You might be prompted to enter your password too. This way your present version of Ubuntu will be updated with security updates, bug-fixes and other improvements of the software. If updates are found, the 'install updates' button can be selected. Click that the receive and install the updates!

But stay away from the 'upgrade' button at the top, unless you have a recent backup!

---

### Post by WasMeHere on 2011-11-05
That is too bad! My experience is that updating within a version is safe.

What happens when you close the lid of your netbook? It can be set to different actions (lock screen, sleep, hibernate, poweroff ...)?
Could closing the lid interfere with the updating process?

Of course it *could be* something that your update installed, that created problems. It is important that you run at least the security updates, so I hope that you dare use the updating utility.

---

### Post by Matrix01 on 2011-11-05
deleted.

---

### Post by Matrix01 on 2011-11-06
I typed your code, and found files in usb flash drive but
no files from external hard drive

for your infos., this 11.04 is booted form usb flash drive.
 

> **jmate24 said:**
> go to a terminal and type: (this is to enable read/write on your ext usb drive)

```
sudo nautilus /media
```if using pcmanfm then type:

```
sudo pcmanfm /media
```then click on the long 'uuid' folder (the one that looks like a big code with letters and numbers (it's called hexidecimal) and open it then right click and go to the permissions tab and change the scroll box labeled 'root' in the file and folder permissions to your username and then go to the Group permissions and select the 'root' scroll box and change it to your username.

---

### Post by Matrix01 on 2011-11-06
how do u open nautilus?

> **blackbird34 said:**
> You could just open nautilus, see your HD in the side bar, and click on it to mount it and view, open, read, write the files...

---

### Post by haqking on 2011-11-06
> **Matrix01 said:**
> how do u open nautilus?

nautilius is the file manager by default in 11.04 or 11.10 ubuntu.

if you go to the go menu in 11.10 and choose the go menu and home it will bring up nautilus

or from terminal you type

```
nautilus
```

---

### Post by Matrix01 on 2011-11-06
opened home folder,
external hard drive is not there.

[ATTACH]206502[/ATTACH]

---

### Post by haqking on 2011-11-06
> **Matrix01 said:**
> opened home folder,
external hard drive is not there.

[ATTACH]206502[/ATTACH]

so what are those on the left, are none of those your drive ?

---

### Post by WasMeHere on 2011-11-06
These entries on the left panel of Nautilus are partitions.

SYSTEM
144 GB Filesyst...
HP_TOOLS
4.3 GB Filesystem

I think one of them is your external disk. Click on it to open!

---

### Post by Matrix01 on 2011-11-06
system;
HP tools; 
they are partitions from hard disk drive (from factory, HP.)
 
144 GB; that must be internal hard disk drive.

4.3GB; that must be 8G usb flash drive,
i guess part of memory space is occupied with 11.04 ubuntu bootloader. 

this external hard drive has 931 GB, larger memory size.
it's not in file manager.
i opened each of them except 4.3GB which did not open.

> **Olle Wiklund said:**
> These entries on the left panel of Nautilus are partitions.

SYSTEM
144 GB Filesyst...
HP_TOOLS
4.3 GB Filesystem

I think one of them is your external disk. Click on it to open!

---

### Post by Matrix01 on 2011-11-06
does external hard disk drive have to be formatted to Linux?

---

### Post by WasMeHere on 2011-11-06
No, for example Fat32 and NTFS partitions should be possible to mount out of the box. But you need some kind of partition(s).

While your external disk is attached and powered up, can you post the output of the command
```
sudo fdisk -lu
```

---

### Post by Matrix01 on 2011-11-06
11.04 was booting forever after update had failed.

---

### Post by Matrix01 on 2011-11-06
I guess this 4.3 GB is formatted in FAT 32,
and when i clicked open, 'mount' was on tab.
do i need to click 'mount'?
 
> **Olle Wiklund said:**
> No, for example Fat32 and NTFS partitions should be possible to mount out of the box. But you need some kind of partition(s).

While your external disk is attached and powered up, can you post the output of the command
```
sudo fdisk -lu
```

---

### Post by WasMeHere on 2011-11-06
Click on the text to open (and if necessary, mount), click on the symbol to the right to unmount.

But what about ```
sudo fdisk -lu
```

---

### Post by Matrix01 on 2011-11-08
what does clicking mount or unmount do to USB flash drive?

> **Olle Wiklund said:**
> Click on the text to open (and if necessary, mount), click on the symbol to the right to unmount.

But what about ```
sudo fdisk -lu
```

---

### Post by WasMeHere on 2011-11-08
I am referring to clicking in the file browser Nautilus. It mounts the partition (as user) unless it is already mounted, and changes directory to it. Then you can continue to browse in the main window of Nautilus, if there are subdirectories, change directory to those, and watch the files. You can open the files with the default program by double (left-)clicking or select program from a meny by right-clicking.

Unmounting is done by clicking on the 'eject' symbol at the right side of the entry for the partition shown on the left panel of Nautilus.

---

### Post by Matrix01 on 2011-11-13
well,
11.04 is not booting from USB flash drive anymore.
i tried to reinstall it, but it did not work.

---

### Post by WasMeHere on 2011-11-13
Do you have any idea of what happened? Could it be connected to your problem of this thread (how to open files from ext. hard drive)? Or something else? Software or hardware problem?

The better you describe what is happening and what is not happening (or where you get stuck), the better we can help.

---

### Post by Matrix01 on 2011-11-15
this message showed up after;
reformartted usb stick and reinstalled unetbootin563 and iso file; ubuntu-11.04-desktop-i386.iso.

(initramfs)mount:mounting/dev/loop0on//filesystem.squashfs failed:invalid argument can not mount/dev/loop0(/cdrom/casper/filesystem.squashfs)on//filesystem.squashfs

---

### Post by WasMeHere on 2011-11-15
This is how I repartition and format my USB drives to make them easily bootable:

0. Backup private files (if you have on the USB drive).

1. Use ***gparted***, which can be run either from a live environment or from the installed Ubuntu. Run ```
sudo apt-get install gparted
``` if necessary.

2. Delete existing partition(s) and create at least one new partition

3. Make a FAT32 file system in the first partition

4. Add the BOOT flag and the LBA flag

5. Add a descriptive label if you want (it helps identify the partition, but is not necessary) for example USB-1104
_____

Try if you find something useful for you in the following post!
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=11451221&postcount=4_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11451221&postcount=4")

and in the following internet links
[[COLOR="RoyalBlue"]_https://help.ubuntu.com/community/Installation/FromUSBStick_[/COLOR]]("https://help.ubuntu.com/community/Installation/FromUSBStick")
[[COLOR="RoyalBlue"]_http://www.bootdisk.com/pendrive.htm_[/COLOR]]("http://www.bootdisk.com/pendrive.htm")
[[COLOR="RoyalBlue"]_http://www.pendrivelinux.com/_[/COLOR]]("http://www.pendrivelinux.com/")
[[COLOR="RoyalBlue"]_http://unetbootin.sourceforge.net/_[/COLOR]]("http://unetbootin.sourceforge.net/")
[[COLOR="RoyalBlue"]_MultiSystem_[/COLOR]]("http://liveusb.info/dotclear/")

---

### Post by Matrix01 on 2011-11-15
well,
do u mean to open terminal and type command?
Ubuntu is not booting from USB drive anymore.

> **Olle Wiklund said:**
> This is how I repartition and format my USB drives to make them easily bootable:

0. Backup private files (if you have on the USB drive).

1. Use ***gparted***, which can be run either from a live environment or from the installed Ubuntu. Run ```
sudo apt-get install gparted
``` if necessary.

2. Delete existing partition(s) and create at least one new partition

3. Make a FAT32 file system in the first partition

4. Add the BOOT flag and the LBA flag

5. Add a descriptive label if you want (it helps identify the partition, but is not necessary) for example USB-1104
_____

Try if you find something useful for you in the following post!
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=11451221&postcount=4_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11451221&postcount=4")

and in the following internet links
[[COLOR="RoyalBlue"]_https://help.ubuntu.com/community/Installation/FromUSBStick_[/COLOR]]("https://help.ubuntu.com/community/Installation/FromUSBStick")
[[COLOR="RoyalBlue"]_http://www.bootdisk.com/pendrive.htm_[/COLOR]]("http://www.bootdisk.com/pendrive.htm")
[[COLOR="RoyalBlue"]_http://www.pendrivelinux.com/_[/COLOR]]("http://www.pendrivelinux.com/")
[[COLOR="RoyalBlue"]_http://unetbootin.sourceforge.net/_[/COLOR]]("http://unetbootin.sourceforge.net/")
[[COLOR="RoyalBlue"]_MultiSystem_[/COLOR]]("http://liveusb.info/dotclear/")

---

### Post by WasMeHere on 2011-11-15
***What system can you run?*** On any computer, live or installed, linux or windows? That decides how to help.

---

### Post by Matrix01 on 2011-11-17
this HP Mini netbook has window 7 starter.

---

### Post by WasMeHere on 2011-11-17
> **Matrix01 said:**
> ext. hard drive is connected in usb port,
and Natty is on monitor,

how do u open files?

When you wrote this first post, did you run Ubuntu from a USB drive or from an installed system (installed onto a partition or Wubi install within Windows)?

I think that some time ago you could run Ubuntu from a USB drive, but now you cannot do it any more. Then there should be a path back to a working USB drive. Just do what you did the first time, if you can remember what you did ;-)

Maybe the following links will help you get there
[[COLOR="RoyalBlue"]_https://help.ubuntu.com/community/Installation/FromUSBStick_[/COLOR]]("https://help.ubuntu.com/community/Installation/FromUSBStick")
[[COLOR="RoyalBlue"]_http://unetbootin.sourceforge.net/_[/COLOR]]("http://unetbootin.sourceforge.net/")

Good luck
Olle

---

### Post by Matrix01 on 2011-11-17
in the first,
11.04 was booting from USB falsh drive...
not sure what...
buntu does not boot from USB stick anymore....
tried the way i did in the first...


> **Olle Wiklund said:**
> When you wrote this first post, did you run Ubuntu from a USB drive or from an installed system (installed onto a partition or Wubi install within Windows)?

I think that some time ago you could run Ubuntu from a USB drive, but now you cannot do it any more. Then there should be a path back to a working USB drive. Just do what you did the first time, if you can remember what you did ;-)

Maybe the following links will help you get there
[[COLOR=RoyalBlue]_https://help.ubuntu.com/community/Installation/FromUSBStick_[/COLOR]]("https://help.ubuntu.com/community/Installation/FromUSBStick")
[[COLOR=RoyalBlue]_http://unetbootin.sourceforge.net/_[/COLOR]]("http://unetbootin.sourceforge.net/")

Good luck
Olle

---

### Post by Matrix01 on 2011-11-17
this' the exact error message on monitor.
but
their Fix: 1) does not work....i used Unetbootin from the beginning.
so
may try Fix 2), use another application, usb creator?

 [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

"The error "Can not mount /dev/loop1 on /cow" is because usb-creator.exe  is not creating a valid casper-rw file holding ext2/ext3 filesystem.  Fix: 1) Use Unetbootin or 2) After running usb-creator.exe, recreate  casper-rw using cygwin tools or [http://www.pendrivelinux.com/casper-rw-creator-make-a-persistent-file-from-windows/](http://www.pendrivelinux.com/casper-rw-creator-make-a-persistent-file-from-windows/). (As of April 2010)"

---

### Post by WasMeHere on 2011-11-17
> **Matrix01 said:**
> ...
"The error "Can not mount /dev/loop1 on /cow" is because usb-creator.exe  is not creating a valid casper-rw file holding ext2/ext3 filesystem.  Fix: 1) Use Unetbootin or 2) After running usb-creator.exe, recreate  casper-rw using cygwin tools or [http://www.pendrivelinux.com/casper-rw-creator-make-a-persistent-file-from-windows/](http://www.pendrivelinux.com/casper-rw-creator-make-a-persistent-file-from-windows/). (As of April 2010)"
1. The casper-rw file could not be created. But do you need it? I think that file is for saving personal data and system updates and added software after installation. If you 'only' want to run a live session and then want to install your system to your hard drive, then you do not need the casper-rw file. So you should try to select ***not*** to make a persistent USB drive (or whatever words are used, but the meaning should be to make a simple live USB drive without any casper-rw file).

2. Writing is necessary anyway. Was something written to your USB drive? ***Could it be changed at all*** during the procedure to make a boot USB drive? Is there any way to make your USB device read-only (for example a small switch)? Is there any chance that you can reformat your USB flash drive? Can you borrow a computer from someone else, maybe a computer with a CD/DVD drive? Just to be able to get a working USB drive.

---

### Post by Matrix01 on 2011-11-18
[ATTACH]207470[/ATTACH]
this netbook has four partitions,
i was told that new partition will not be created...
so
there's no room for buntu.
so
i was thinking to create persistent USB flash drive, and run buntu from USB.
Is this good idea? 

> **Olle Wiklund said:**
> 1. The casper-rw file could not be created. But do you need it? I think that file is for saving personal data and system updates and added software after installation. If you 'only' want to run a live session and then want to install your system to your hard drive, then you do not need the casper-rw file. So you should try to select ***not*** to make a persistent USB drive (or whatever words are used, but the meaning should be to make a simple live USB drive without any casper-rw file).

2. Writing is necessary anyway. Was something written to your USB drive? ***Could it be changed at all*** during the procedure to make a boot USB drive? Is there any way to make your USB device read-only (for example a small switch)? Is there any chance that you can reformat your USB flash drive? Can you borrow a computer from someone else, maybe a computer with a CD/DVD drive? Just to be able to get a working USB drive.

---

### Post by WasMeHere on 2011-11-18
Yes I see. It is very stupid to deliver a computer filled with primary partitions, and it would be a big job to fix it. So it is an option to run Ubuntu from a USB drive instead. One option, is the one you are trying. Another is a regular installation to a USB drive or flash card. You would run a live system on one USB drive and install to the other one (or the flash card). It would be enough with 8 GB, but quite nice with a 16 GB USB stick or flash card.

But first you should try from windows to make a boot stick again
[[COLOR="RoyalBlue"]_https://help.ubuntu.com/community/Installation/FromUSBStick_[/COLOR]]("https://help.ubuntu.com/community/Installation/FromUSBStick")
Try not only with the newest version but also with 10.04 and 11.04 or the corresponding Linux Mint versions 9 and 11 (based on Ubuntu).

---

### Post by WasMeHere on 2011-11-18
I want to add that USB flash sticks and flash memory cards have a shorter life-time (number of writes) than magnetic hard drives. (The SSD drives have better life-time, but are also more expensive.) If you get problems after running Ubuntu from a USB stick, it might be 'worn out'.

So it is worth checking your USB stick (from Windows) with ***chkdsk***. Run from a DOS-prompt window (command line)

```
help chkdsk
``` or ```
chkdsk /?
``` to find out which option to select to make it check not only the file system but also that all sectors are good for reading and writing.

---

### Post by Matrix01 on 2011-11-19
i bought this PNY 8G USB flash drive in 4 weeks ago, 
and guess it was in a good shape when 11.04 was running.

typed code in DOS, and output looks like this;
[ATTACH]207541[/ATTACH]

[ATTACH]207545[/ATTACH]

how do u check USB pen drive?

> **Olle Wiklund said:**
> I want to add that USB flash sticks and flash memory cards have a shorter life-time (number of writes) than magnetic hard drives. (The SSD drives have better life-time, but are also more expensive.) If you get problems after running Ubuntu from a USB stick, it might be 'worn out'.

So it is worth checking your USB stick (from Windows) with ***chkdsk***. Run from a DOS-prompt window (command line)

```
help chkdsk
``` or ```
chkdsk /?
``` to find out which option to select to make it check not only the file system but also that all sectors are good for reading and writing.

---

### Post by Matrix01 on 2011-11-19
i may try to run ubuntu from external hard drive, and install buntu in USB flash drive.
what do u think?

also,
i have another laptop has CD drive and USB 3.0 port

---

### Post by WasMeHere on 2011-11-19
Hi Matrix01,

What do you mean by
> i bought this PNY 8G USB flash drive in 4 weeks ago,
and guess it was in a good shape when 11.04 was running,
but i can not find it anywhere.
Have you lost it or is the problem that your computer cannot see it, neither from Ubuntu nor from Windows?

It is possible to run Ubuntu either from a USB hard drive or a USB flash drive. It makes no difference except for size and lifetime. So go ahead and try!

The final alternative, of course, is to migrate to Ubuntu as the main operating system, and if necessary run Windows in a virtual machine. It took me two years of dual booting until I wiped my Windows (from my main computer). Since you have problems with the four primary partitions on your netbook, a good alternative might be to get a ***cheap second-hand computer that you dedicate to learning linux ***(Ubuntu, Linux Mint and whatever looks interesting). This might be as cheap as buying new periferal devices in order to run linux in your netbook.

Have fun finding out about linux :-)
Olle

---

### Post by WasMeHere on 2011-11-19
We were editing posts at the same time, so the first question is answered now: You can see your USB drive in Windows :-) Then the following command should check for bad sectors
```
chkdsk G: /r
```
By the way, do you know which key to press in order to get a menu where you can select boot from the USB stick? On EeePC I think it is the ESC key, on many computers it is the F9 or F10 key, sometimes the Del key or Enter key. It is usually shown quickly shortly after rebooting. Otherwise you should find it in your manual or browsing the internet.

---

### Post by WasMeHere on 2011-11-19
> **Matrix01 said:**
> i may try to run ubuntu from external hard drive, and install buntu in USB flash drive.
what do u think?

also,
i have another laptop has CD drive and USB 3.0 port
What about this other laptop: Would it be possible with dual boot? [s]If you post the output of
[FONT="Courier New"][SIZE="3"]sudo fdisk -lu[/SIZE][/FONT]
mount all partitions and post the output of
[FONT="Courier New"][SIZE="3"]df[/SIZE][/FONT][/s]
*Edit: Sorry for that, I forgot that it is windows, so instead you should post a view of your drive with its partitions from within Windows like the following *[ATTACH]207470[/ATTACH]

and we can discuss what would be possible.

---

### Post by Matrix01 on 2011-11-19
funny,
i could not find this 8G USB flash drive,,,,
and
found it in seam of couch,
and edited my post,
i did not know you can get my original post, you must be a part of administor of ubuntu forum.

i have an old Apple desk top with zip drive, that's how old, you know zip drive was popular a long time ago,  and Compaque desk top in storage.
i do not know if they work, i do not have ac adapter, and monitor, so did not have time to test them.

i thought about getting second hand computer, who knows anythings may not work.

how do u get Windows in virtual machine?


> **Olle Wiklund said:**
> Hi Matrix01,

What do you mean by

Have you lost it or is the problem that your computer cannot see it, neither from Ubuntu nor from Windows?

It is possible to run Ubuntu either from a USB hard drive or a USB flash drive. It makes no difference except for size and lifetime. So go ahead and try!

The final alternative, of course, is to migrate to Ubuntu as the main operating system, and if necessary run Windows in a virtual machine. It took me two years of dual booting until I wiped my Windows (from my main computer). Since you have problems with the four primary partitions on your netbook, a good alternative might be to get a ***cheap second-hand computer that you dedicate to learning linux ***(Ubuntu, Linux Mint and whatever looks interesting). This might be as cheap as buying new periferal devices in order to run linux in your netbook.

Have fun finding out about linux :-)
Olle

---

### Post by Matrix01 on 2011-11-19
that did not work.

[ATTACH]207601[/ATTACH]

do u mean which key to get to BIOS options?
i have changed boot order, 
let me check.


> **Olle Wiklund said:**
> We were editing posts at the same time, so the first question is answered now: You can see your USB drive in Windows :-) Then the following command should check for bad sectors
```
chkdsk G: /r
```
By the way, do you know which key to press in order to get a menu where you can select boot from the USB stick? On EeePC I think it is the ESC key, on many computers it is the F9 or F10 key, sometimes the Del key or Enter key. It is usually shown quickly shortly after rebooting. Otherwise you should find it in your manual or browsing the internet.

---

### Post by Matrix01 on 2011-11-19
press F10, and change boot order on this HP Mini netbook.

boot order is set;
USB diskette on key/ usb hard disk.
usb cd/dvd rom.
! network adapter.
usb floppy.

do u know what network adapter is?
and what does ! mean?

---

### Post by Matrix01 on 2011-11-20
typed command, but did not work,
so
posted Seven forum...
and they told me to run command prompt as administrator....

here's output....
USB flash drive seems to have no problems..
[ATTACH]207605[/ATTACH]

---

### Post by WasMeHere on 2011-11-20
Hello again Matrix01,

I have seen that you have written several posts and I will try to answer them one by one.

Have fun finding out
Olle

---

### Post by WasMeHere on 2011-11-20
> **Matrix01 said:**
> i may try to run ubuntu from external hard drive, and install buntu in USB flash drive.
what do u think?

also,
i have another laptop has CD drive and USB 3.0 port

Maybe it would be easier to try Ubuntu on this one. You can to boot from CD as well as from USB. As long as you only run a live sesssion, it should be pretty safe :-)

---

### Post by WasMeHere on 2011-11-20
> **Matrix01 said:**
> funny,
i could not find this 8G USB flash drive,,,,
and
found it in seam of couch,
and edited my post,
i did not know you can get my original post, you must be a part of administor of ubuntu forum.

i have an old Apple desk top with zip drive, that's how old, you know zip drive was popular a long time ago,  and Compaque desk top in storage.
i do not know if they work, i do not have ac adapter, and monitor, so did not have time to test them.

i thought about getting second hand computer, who knows anythings may not work.

how do u get Windows in virtual machine?
I mean the first post of this thread, and it is easy to see. (I am a regular user, that has learned a lot from these forums. Now I want to help others learn about Ubuntu.)

The Zip drive makes me think maybe 12 years old. What about the Compaq? If you find suitable ac adapters it is worth trying those old computers, but if they are very old, you cannot run any fancy graphics. Maybe Lubuntu or Knoppix or Ubuntu 10.04 Lucid might work. (But you have to check what architecture it is in the Apple: Power PC? There is a PowerPC version of Ubuntu, I have run Ubuntu Lucid
in an old PowerPC Desktop Mac.)

A second-hand computer, maybe 3-5 years old would more powerful.

*Edit:* You install software that emulates the hardware, for example VirtualBox. Then you create a file-system for it and install (or run live from an iso-file) any operating system. So if you have an installation disk for Windows, you can install it into the virtual machine. Browse the internet for details. There are also recent threads here in the Ubuntu Forums about virtual machines (how to install them).

---

### Post by WasMeHere on 2011-11-20
> **Matrix01 said:**
> press F10, and change boot order on this HP Mini netbook.

boot order is set;
USB diskette on key/ usb hard disk.
usb cd/dvd rom.
! network adapter.
usb floppy.

do u know what network adapter is?
and what does ! mean?

Network adapter is booting via the local network. It is often done in big companies in order to make the maintenance of computers simpler.

---

### Post by WasMeHere on 2011-11-20
> **Matrix01 said:**
> typed command, but did not work,
so
posted Seven forum...
and they told me to run command prompt as administrator....

here's output....
USB flash drive seems to have no problems..
[ATTACH]207605[/ATTACH]

Yes it passed the [FONT="Courier New"]chkdsk /r[/FONT] test, so it is a good USB stick with a good file system :-)

Now to the next task: Can you boot from it, or make it a USB boot drive? Or make a boot CD for the other PC? So that you get a chance to run Ubuntu.

---

### Post by Matrix01 on 2011-11-20
i do not have Window's installation disk.
this Win7 starter was installed in this HP Mini from factory.
Will u tell me which one is your favorite distro?

> **Olle Wiklund said:**
> I mean the first post of this thread, and it is easy to see. (I am a regular user, that has learned a lot from these forums. Now I want to help others learn about Ubuntu.)

The Zip drive makes me think maybe 12 years old. What about the Compaq? If you find suitable ac adapters it is worth trying those old computers, but if they are very old, you cannot run any fancy graphics. Maybe Lubuntu or Knoppix or Ubuntu 10.04 Lucid might work. (But you have to check what architecture it is in the Apple: Power PC? There is a PowerPC version of Ubuntu, I have run Ubuntu Lucid
in an old PowerPC Desktop Mac.)

A second-hand computer, maybe 3-5 years old would more powerful.

*Edit:* You install software that emulates the hardware, for example VirtualBox. Then you create a file-system for it and install (or run live from an iso-file) any operating system. So if you have an installation disk for Windows, you can install it into the virtual machine. Browse the internet for details. There are also recent threads here in the Ubuntu Forums about virtual machines (how to install them).

---

### Post by Matrix01 on 2011-11-20
same error message showed up on monitor when i tried to boot 11.04 from this usb falsh drive.
will u tell me what i can do?

> **Olle Wiklund said:**
> Yes it passed the [FONT="Courier New"]chkdsk /r[/FONT] test, so it is a good USB stick with a good file system :-)

Now to the next task: Can you boot from it, or make it a USB boot drive? Or make a boot CD for the other PC? So that you get a chance to run Ubuntu.

---

### Post by Matrix01 on 2011-11-20
so
assuming create live cd from this laptop,
and install ubuntu in usb flash drive..

can buntu run from this usb flahs drive, if this usb stick is connected to any other PC has usb port?

> **Olle Wiklund said:**
> Maybe it would be easier to try Ubuntu on this one. You can to boot from CD as well as from USB. As long as you only run a live sesssion, it should be pretty safe :-)

---

### Post by WasMeHere on 2011-11-21
> **Matrix01 said:**
> i do not have Window's installation disk.
this Win7 starter was installed in this HP Mini from factory.
Will u tell me which one is your favorite distro?
I run 'vanilla' Ubuntu 10.04 LTS on my main computer and I run Ubuntu Studio 11.04 on another computer. Sometimes I recommend Linux Mint for people who are new to linux, because it makes it easier to convert from Windows. Linux Mint is based on Ubuntu. But it also depends on the computer: a desktop environment with a small footprint for an old computer, more eye-candy for a computer with powerful graphics.

---

### Post by WasMeHere on 2011-11-21
> **Matrix01 said:**
> so
assuming create live cd from this laptop,
and install ubuntu in usb flash drive..

can buntu run from this usb flahs drive, if this usb stick is connected to any other PC has usb port?
You can always try :-)

It depends: If the reason is that the boot stick is bad, of course not, but if the problem is that the computer has problems booting from USB, then it might work on another computer. It is also a good idea to make a boot CD and try to boot from that, because it is easier (when you have a CD/DVD drive).

Have you tried to make a boot USB drive according to the Ubuntu instructions on the web? Have you tried with Unetbootin?

---

### Post by Matrix01 on 2011-11-21
I tried Unetbootin, and got that error message "can not mount....."

> **Olle Wiklund said:**
> You can always try :-)

It depends: It the reason is that the boot stick is bad, of course not, but if the problem is that the computer has problems booting from USB, then it might work on another computer. It is also a good idea to make a boot CD and try to boot from that, because it is easier (when you have a CD/DVD drive).

Have you tried to make a boot USB drive according to the Ubuntu instructions on the web? Have you tried with Unetbootin?

---

### Post by WasMeHere on 2011-11-21
> **Matrix01 said:**
> this message showed up after;
reformartted usb stick and reinstalled unetbootin563 and iso file; ubuntu-11.04-desktop-i386.iso.

(initramfs)mount:mounting/dev/loop0on//filesystem.squashfs failed:invalid argument can not mount/dev/loop0(/cdrom/casper/filesystem.squashfs)on//filesystem.squashfs

Is this the output you get also now? How did you install the iso file? Did you run Unetbootin and in the menu of Unetbootin select the iso file and the USB drive? And then OK?

If that is the case, try reformatting the USB drive according to my post [[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=11458343&postcount=43_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11458343&postcount=43") and then try the various links in that post according to

help.ubuntu.com...
unetbootin (again)
multisystem

These methods are slightly different and will work on different computers. But try also to make a CD and try booting from your CD/DVD drive on the other computer!

***Edit: See the screendump of Unetbootin***

---

### Post by Matrix01 on 2011-11-22
yep,
unfortunately, this' the output, same error message still shows up.
and
nope,
i did not use iso file from menu in unetbootin.
one of member from this forum posted link to iso file of 11.04,
and i used that with unetbootin.  he said that installation is faster this way.
so 
unetbootin looks like this except drive G does not show up in this screen shot.
and
what is this for?
"space used to preserve files across reboots (ubuntu only)"

[ATTACH]207753[/ATTACH]

i reformatted this 8G usb flash drive with Win7.
11.04 is not booting anymore, error message shows up, so I am not able to open Gparted.

> **Olle Wiklund said:**
> Is this the output you get also now? How did you install the iso file? Did you run Unetbootin and in the menu of Unetbootin select the iso file and the USB drive? And then OK?

If that is the case, try reformatting the USB drive according to my post [[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=11458343&postcount=43_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11458343&postcount=43") and then try the various links in that post according to

help.ubuntu.com...
unetbootin (again)
multisystem

These methods are slightly different and will work on different computers. But try also to make a CD and try booting from your CD/DVD drive on the other computer!

***Edit: See the screendump of Unetbootin***

---

### Post by WasMeHere on 2011-11-22
> **Matrix01 said:**
> yep,
unfortunately, this' the output, same error message still shows up.
and
nope,
i did not use iso file from menu in unetbootin.
one of member from this forum posted link to iso file of 11.04,
and i used that with unetbootin.  he said that installation is faster this way.
so 
unetbootin looks like this except drive G does not show up in this screen shot.
and
what is this for?
"space used to preserve files across reboots (ubuntu only)"

[ATTACH]207753[/ATTACH]

i reformatted this 8G usb flash drive with Win7.
11.04 is not booting anymore, error message shows up, so I am not able to open Gparted.
"space used to preserve files across reboots (ubuntu only)" is where to store personal data, programs and configurations, ***persistent USB boot drive***. I would expect that a casper-rw-file will be created with the specified size.

Can you specify the volume ID G: in the Unetbootin window, and then press OK to go?
What happens?
If this is what you do and none of your computers boots off that USB drive, try one of the other methods that I described!

---

### Post by Matrix01 on 2011-11-22
so..
how much memory size do i need in box, "space used to......"?

yep,
when i actually, created persistent USB flash drive,
G drive showed up, and press OK, and installation started.

do u mean try another application, usb installer in ubuntu website,
or
create live CD with another PC?

> **Olle Wiklund said:**
> "space used to preserve files across reboots (ubuntu only)" is where to store personal data, programs and configurations, ***persistent USB boot drive***. I would expect that a casper-rw-file will be created with the specified size.

Can you specify the volume ID G: in the Unetbootin window, and then press OK to go?
What happens?
If this is what you do and none of your computers boots off that USB drive, try one of the other methods that I described!

---

### Post by WasMeHere on 2011-11-22
> **Matrix01 said:**
> so..
how much memory size do i need in box, "space used to......"?

yep,
when i actually, created persistent USB flash drive,
G drive showed up, and press OK, and installation started.

do u mean try another application, usb installer in ubuntu website,
or
create live CD with another PC?
how much memory size do you need in box: You could use all that is allowed (if it works) or you could use for example 4 GB. You need no such space to boot, but you need it to preserve data.

Yes I mean try another application, usb installer in ubuntu website,
or create live CD with another PC!

---

### Post by Matrix01 on 2011-11-23
i will try Mint;
do u know where to get ISO file?

> **Olle Wiklund said:**
> how much memory size do you need in box: You could use all that is allowed (if it works) or you could use for example 4 GB. You need no such space to boot, but you need it to preserve data.

Yes I mean try another application, usb installer in ubuntu website,
or create live CD with another PC!

---

### Post by WasMeHere on 2011-11-23
> **Matrix01 said:**
> i will try Mint;
do u know where to get ISO file?
Here:
[[COLOR="RoyalBlue"]_http://www.linuxmint.com/download.php_[/COLOR]]("http://www.linuxmint.com/download.php")
Good luck :-)

---

### Post by Matrix01 on 2011-11-25
how's 10.04?

> **Olle Wiklund said:**
> I run 'vanilla' Ubuntu 10.04 LTS on my main computer and I run Ubuntu Studio 11.04 on another computer. Sometimes I recommend Linux Mint for people who are new to linux, because it makes it easier to convert from Windows. Linux Mint is based on Ubuntu. But it also depends on the computer: a desktop environment with a small footprint for an old computer, more eye-candy for a computer with powerful graphics.

---

### Post by WasMeHere on 2011-11-25
Well, I'm used to Ubuntu 10.04, gnome desktop environment, quite easy to learn. But you have to install multimedia support (proprietary libraries and codecs in order to view videos, dvd movies, listen to mp3 music). This is described in the 'Comprehensive Multimedia & Video Howto'
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=766683_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683") 
It will be supported until April 2013.

---

### Post by Matrix01 on 2011-11-25
[ATTACH]207946[/ATTACH]

tried another bootloader, universal usb installer, which was on ubuntu website.
formatted 8G usb in NTFS this time
did not work.
error message showed up, not bootable.

---

### Post by WasMeHere on 2011-11-25
It seems to be really difficult for you to boot from USB, so ***please make a boot CD and try booting from your CD/DVD drive on the other computer***!

Then you will have a live Ubuntu system, and that means that you will have linux tools that might help you to make a bootable USB drive for the netbook. Then you will be able to use ***gparted*** and do the partitioning and formatting work suggested in post #43
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=11458343&postcount=43_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11458343&postcount=43")

Good luck :-)
Olle

---

### Post by WasMeHere on 2011-11-26
Hi Matrix01,

[This post is somewhat different from the other ones in your thread.] 
If you know or find other people interested in linux where you live, you might get hands-on help to install linux into your computer(s). Your task is really not that difficult, but there seems to be some threshold, than holds you back. It has not been possible [yet ;-)] to make any of us at the Ubuntu Forums understand what it is, hence we don't give you what you need.

So now I suggest that you ask someone to help you at your computer. Ask a friend, colleague, or maybe someone at a local computer store or repair shop. Maybe there is a computer club in your neighbourhood, where the guys would be happy to help.

I will be here at the Ubuntu Forums and continue to help, but please consider also this possibility to get hands-on help!

Best regards
Olle

---

### Post by Matrix01 on 2011-11-26
[ATTACH]208037[/ATTACH] 

well, i did this.
xubuntu is booting from usb flash drive, but this does not store changes.

next,
connect ext hard disk drive and open.
[ATTACH]208041[/ATTACH]

do i need to back up and format ext. HDD?

disks on gparted;
[ATTACH]208039[/ATTACH]

---

### Post by WasMeHere on 2011-11-26
> **Matrix01 said:**
> [ATTACH]208037[/ATTACH] 

well, i did this.
xubuntu is booting from usb flash drive, but this does not store changes.

next,
connect ext hard disk drive and open.
[ATTACH]208041[/ATTACH]

do i need to back up and format ext. HDD?

disks on gparted;
[ATTACH]208039[/ATTACH]
Congratulation, Matrix01, you run a live system again :KS

I recognize the four primary partitions on /dev/sda, so I assume you are running it on your netbook. Now that you have Xubuntu running you can use the linux tools, and it is possible to do a lot of things. I think we will find out a good solution for your netbook, either booting from your hard drive, from a USB drive (hard or flash) or from a flash card (if there is a card reader slot in your netbook).

Gparted can see one partition on /dev/sdd, size 1TB, but cannot recognize its file system. ***Is it an external USB hard drive of that size, or is it your pendrive with 8 GB that is 'misunderstood'?***

The second picture shows how you fail to mount "pendrive". It also states that it has 'unknown filesystem type exfat'.

Well, exfat is not unknown, but a proprietory filesystem owned by Microsoft, and it cannot be mounted by Ubuntu (or any linux system). In order to get this "pendrive" work with Ubuntu, I suggest that you

1. Backup any personal files from it

2a. *If it is a small pendrive with less than or equal to 32 GB*
Reformat it to FAT32 according to my previos post
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=11458343&postcount=43_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11458343&postcount=43")

2b. *If it is a big external hard drive*, Decide how you want to use it!
- with Ubuntu and Windows, format to ***NTFS***
- with only Ubuntu, format to ***ext3***
- with only Windows, leave it as it is [I guess Windows can manage it ;-)]

Have fun finding out about Ubuntu :-)
Olle

---

### Post by Matrix01 on 2011-11-26
yep,
i'm on HP Mini Netbook, with Atom 1.67 G processor, 1 G RAM, samsung 134 G HDD, again...
i asked which one runs faster in forum, and someone told me 'xubuntu.'

i used universal usb installer this time, instead of unetbootin.
xubuntu is booting from 8G USB flash drive that is formatted in FAT 32, 
and
allocation size is set to default.
Is allocation size where to be formatted?

i figured out what live CD is.

this netbook has card reader slot 'SD-MMC", and three 2.0 USB port.

I connected USB HDD which has 1 TB,
and 
unknown file system is this USB HDD,
i guess i did not format this usb hdd.

now,
i like to change this;
run live session from 1 TB ext. HDD, and install xubuntu in 8G USB flash drive,
pen drive and netbook are portable.

Is usb hdd need to be backed up, and formatted in NTFS?




> **Olle Wiklund said:**
> Congratulation, Matrix01, you run a live system again :KS

I recognize the four primary partitions on /dev/sda, so I assume you are running it on your netbook. Now that you have Xubuntu running you can use the linux tools, and it is possible to do a lot of things. I think we will find out a good solution for your netbook, either booting from your hard drive, from a USB drive (hard or flash) or from a flash card (if there is a card reader slot in your netbook).

Gparted can see one partition on /dev/sdd, size 1TB, but cannot recognize its file system. ***Is it an external USB hard drive of that size, or is it your pendrive with 8 GB that is 'misunderstood'?***

The second picture shows how you fail to mount "pendrive". It also states that it has 'unknown filesystem type exfat'.

Well, exfat is not unknown, but a proprietory filesystem owned by Microsoft, and it cannot be mounted by Ubuntu (or any linux system). In order to get this "pendrive" work with Ubuntu, I suggest that you

1. Backup any personal files from it

2a. *If it is a small pendrive with less than or equal to 32 GB*
Reformat it to FAT32 according to my previos post
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=11458343&postcount=43_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11458343&postcount=43")

2b. *If it is a big external hard drive*, Decide how you want to use it!
- with Ubuntu and Windows, format to ***NTFS***
- with only Ubuntu, format to ***ext3***
- with only Windows, leave it as it is [I guess Windows can manage it ;-)]

Have fun finding out about Ubuntu :-)
Olle

---

### Post by WasMeHere on 2011-11-27
> **Matrix01 said:**
> yep,
i'm on HP Mini Netbook, with Atom 1.67 G processor, 1 G RAM, samsung 134 G HDD, again...
i asked which one runs faster in forum, and someone told me 'xubuntu.'

i used ***universal usb installer*** this time, instead of unetbootin.
xubuntu is booting from 8G USB flash drive that is formatted in FAT 32, 
and
allocation size is set to default.
Is allocation size where to be formatted?
No, leave the allocation size at its default value! At least now. Keep this pendrive in a working condition!
> i figured out what live CD is.

this netbook has card reader slot 'SD-MMC", and three 2.0 USB port.

I connected USB HDD which has 1 TB,
and 
unknown file system is this USB HDD,
i guess i did not format this usb hdd.
So it is the USB hard drive that has the exfat file system. It was probably formatted when you bought it. 
> now,
i like to change this;
run live session from 1 TB ext. HDD, and install xubuntu in 8G USB flash drive,
pen drive and netbook are portable.

Is usb hdd need to be backed up, and formatted in NTFS?
You want to run Ubuntu from the "1 TB ext. HDD", so ***yes, you need to back it up*** first and then use gparted to make new partitions. But why do you want to run it live? Is it because you want it as a temporary solution to install from there to the '8G USB flash drive'?

Anyway, format it with NTFS ***only*** if you want it as a data disk for Ubuntu and Windows. ***If you want to use it as a live disk, you should make several partitions***.

0. After backup, make sure your USB HDD is ***not*** mounted! Start editing the partition table with gparted from the live USB stick session!

1. Primary partition with FAT32 and flags: BOOT and LBA and label: USB_HDD_OS.
I recommend size 12 GB (good if you want to reuse it later with persistence or a small fully installed Ubuntu system). If you are sure that you will only run standard live systems, 2 GB would be enough.

2. Extended partition, size 'all remaining space'
3. Logical swap partition, size 4 GB
4. Logical partition with NTFS, size 'all remaining space' with label: *data*

---

### Post by Matrix01 on 2011-11-27
yep,
run live session from usb hdd, and like to install ubuntu in usb pen drive which is portable,

can i use usb hdd as data storage for ubuntu and windows as well as a live disk?


> **Olle Wiklund said:**
> No, leave the allocation size at its default value! At least now. Keep this pendrive in a working condition!

So it is the USB hard drive that has the exfat file system. It was probably formatted when you bought it. 

You want to run Ubuntu from the "1 TB ext. HDD", so ***yes, you need to back it up*** first and then use gparted to make new partitions. But why do you want to run it live? Is it because you want it as a temporary solution to install from there to the '8G USB flash drive'?

Anyway, format it with NTFS ***only*** if you want it as a data disk for Ubuntu and Windows. ***If you want to use it as a live disk, you should make several partitions***.

0. After backup, make sure your USB HDD is ***not*** mounted! Start editing the partition table with gparted from the live USB stick session!

1. Primary partition with FAT32 and flags: BOOT and LBA and label: USB_HDD_OS.
I recommend size 12 GB (good if you want to reuse it later with persistence or a small fully installed Ubuntu system). If you are sure that you will only run standard live systems, 2 GB would be enough.

2. Extended partition, size 'all remaining space'
3. Logical swap partition, size 4 GB
4. Logical partition with NTFS, size 'all remaining space' with label: *data*

---

### Post by WasMeHere on 2011-11-27
> **Matrix01 said:**
> yep,
run live session from usb hdd, and like to install ubuntu in usb pen drive which is portable,

can i use usb hdd as data storage for ubuntu and windows as well as a live disk?
Yes, most of the disk space will be available for data storage:

1000-12-4 GB = 984 GB. A very small amount of disk space will be needed for administration of the partitions and FAT32. But there will be more space allocated for administration of the NTFS so the available size for file storage might be approximately 950 GB in the NTFS partition.

Byt the way, after you have created the NTFS (NT file system), you should boot into windows and plug in the external drive. Then either Windows will automatically check and fix the file system, or you can do it manually from dospromt (the command line in windows) with the command ```
chkdsk [COLOR="Red"]G:[/COLOR] /f 
``` if it is recognized as volume [COLOR="Red"]G:[/COLOR]

---

### Post by Matrix01 on 2011-11-27
how do u select sentenses from post, and make your post with quote?

> **Olle Wiklund said:**
> No, leave the allocation size at its default value! At least now. Keep this pendrive in a working condition!

So it is the USB hard drive that has the exfat file system. It was probably formatted when you bought it. 

You want to run Ubuntu from the "1 TB ext. HDD", so ***yes, you need to back it up*** first and then use gparted to make new partitions. But why do you want to run it live? Is it because you want it as a temporary solution to install from there to the '8G USB flash drive'?

Anyway, format it with NTFS ***only*** if you want it as a data disk for Ubuntu and Windows. ***If you want to use it as a live disk, you should make several partitions***.

0. After backup, make sure your USB HDD is ***not*** mounted! Start editing the partition table with gparted from the live USB stick session!

1. Primary partition with FAT32 and flags: BOOT and LBA and label: USB_HDD_OS.
I recommend size 12 GB (good if you want to reuse it later with persistence or a small fully installed Ubuntu system). If you are sure that you will only run standard live systems, 2 GB would be enough.

2. Extended partition, size 'all remaining space'
3. Logical swap partition, size 4 GB
4. Logical partition with NTFS, size 'all remaining space' with label: *data*

---

### Post by Matrix01 on 2011-11-27
so,
when i make live disk in this usb hdd, and use this usb hdd as data storage,

1. back up files and pictures first,

2. make four partitions.




> **Olle Wiklund said:**
> No, leave the allocation size at its default value! At least now. Keep this pendrive in a working condition!

So it is the USB hard drive that has the exfat file system. It was probably formatted when you bought it. 

You want to run Ubuntu from the "1 TB ext. HDD", so ***yes, you need to back it up*** first and then use gparted to make new partitions. But why do you want to run it live? Is it because you want it as a temporary solution to install from there to the '8G USB flash drive'?

Anyway, format it with NTFS ***only*** if you want it as a data disk for Ubuntu and Windows. ***If you want to use it as a live disk, you should make several partitions***.

0. After backup, make sure your USB HDD is ***not*** mounted! Start editing the partition table with gparted from the live USB stick session!

1. Primary partition with FAT32 and flags: BOOT and LBA and label: USB_HDD_OS.
I recommend size 12 GB (good if you want to reuse it later with persistence or a small fully installed Ubuntu system). If you are sure that you will only run standard live systems, 2 GB would be enough.

2. Extended partition, size 'all remaining space'
3. Logical swap partition, size 4 GB
4. Logical partition with NTFS, size 'all remaining space' with label: *data*

---

### Post by WasMeHere on 2011-11-27
> **Matrix01 said:**
> how do u select sentenses from post, and make your post with quote?
I use the edit option according to the attached picture, so it is possible to edit tags manually for example the > tags

---

### Post by WasMeHere on 2011-11-27
> **Matrix01 said:**
> so,
when i make live disk in this usb hdd, and use this usb hdd as data storage,

1. back up files and pictures first,

2. make four partitions.

Yes, one primary partition, one extended partition and two logical partitions inside the extended partition according to my description :-)

---

### Post by Matrix01 on 2011-11-27
so
ubuntu will be in primary partition,
and
which one will be data storage?

> **Olle Wiklund said:**
> Yes, one primary partition, one extended partition and two logical partitions inside the extended partition according to my description :-)

---

### Post by Matrix01 on 2011-11-27
meanwhile,
installed wubi, that was easy,
thought wubi ran live session,
saves changes..

by the way, 
update failed?
[ATTACH]208102[/ATTACH]

---

### Post by WasMeHere on 2011-11-27
> **Matrix01 said:**
> so
ubuntu will be in primary partition,
and
which one will be data storage?

The NTFS partition, available from Ubuntu and Windows

---

### Post by WasMeHere on 2011-11-27
> **Matrix01 said:**
> meanwhile,
installed wubi, that was easy,
thought wubi ran live session,
saves changes..

by the way, 
update failed?
[ATTACH]208102[/ATTACH]
No internet connection? I have no experience of wubi, so I can't help you with that.

---

### Post by Matrix01 on 2011-11-27
BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
 Enter 'help' for a list of built-in commands.

 (initramfs)

i tried to run live session from this usb pen drive,
this message showed up.

---

### Post by WasMeHere on 2011-11-28
> **Matrix01 said:**
> BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
 Enter 'help' for a list of built-in commands.

 (initramfs)

i tried to run live session from this usb pen drive,
this message showed up.
Busybox is a simple shell, that can be run to rescue a system.

Is this the USB pen drive with Xubuntu that worked a couple of days ago?

If it is, what happened?

If is it another pen drive, how is it configured? What if you try to make it bootable the same way as the one booting with Xubuntu?! Maybe it needs repartitioning, and as long as you can boot linux from the other USB pendrive with Xubuntu, it should be possible. (But there are pendrives that are harder to make bootable.)

---

### Post by Matrix01 on 2011-11-28
Ran update again,
update completed.

by the way,
in screen shot in post #97
can u see the Network Icon on top panel on the right,
and 
fire fox icon on top panel,
Firefox was running when i ran update


> **Olle Wiklund said:**
> No internet connection? I have no experience of wubi, so I can't help you with that.

---

### Post by Matrix01 on 2011-11-28
yep,
this is the same usb pen drive which xubuntu was running live session days ago.
not sure what happened?

> **Olle Wiklund said:**
> Busybox is a simple shell, that can be run to rescue a system.

Is this the USB pen drive with Xubuntu that worked a couple of days ago?

If it is, what happened?

If is it another pen drive, how is it configured? What if you try to make it bootable the same way as the one booting with Xubuntu?! Maybe it needs repartitioning, and as long as you can boot linux from the other USB pendrive with Xubuntu, it should be possible. (But there are pendrives that are harder to make bootable.)

---

### Post by WasMeHere on 2011-11-28
> **Matrix01 said:**
> Ran update again,
update completed.

by the way,
in screen shot in post #97
can u see the Network Icon on top panel on the right,
and 
fire fox icon on top panel,
Firefox was running when i ran update
I guess you need to configure the internet connection from the host system to the wubi sub-system.

---

### Post by WasMeHere on 2011-11-28
> **Matrix01 said:**
> yep,
this is the same usb pen drive which xubuntu was running live session days ago.
not sure what happened?

Try to make it bootable again exactly the same way as you did last time, when it worked. Don't download anything to it or install anything to it, at least not until you have some other linux system working! Just run it and use gparted etc ...

---

### Post by Matrix01 on 2011-11-28
how to configure internet?

> **Olle Wiklund said:**
> I guess you need to configure the internet connection from the host system to the wubi sub-system.

---

### Post by Matrix01 on 2011-11-28
i reformated usb pen drive in FAT 32, and dwonloaded bootloader,
and
in usb hdd after copied and moved files.
when i ran live session from either of them,  same message showed up.

> **Olle Wiklund said:**
> Try to make it bootable again exactly the same way as you did last time, when it worked. Don't download anything to it or install anything to it, at least not until you have some other linux system working! Just run it and use gparted etc ...

---

### Post by WasMeHere on 2011-11-28
> **Matrix01 said:**
> how to configure internet?

I have no experience of wubi, so I can't help you with that.

---

### Post by WasMeHere on 2011-11-28
> **Matrix01 said:**
> i reformated usb pen drive in FAT 32, and dwonloaded bootloader,
and
in usb hdd after copied and moved files.
when i ran live session from either of them,  same message showed up.
***You have done something in a different way, otherwise it would have worked.*** (Unless the USB pendrive broke, but it is very unlikely.)

Have you changed anything else on your computer for example in the BIOS menus? Can you boot into your other computer with the USB pendrive or USB HDD?

*Edit: Try to remember exactly how you did to make the pendrive bootable with Xubuntu, and repeat that!*

---

### Post by Matrix01 on 2011-11-28
i have changed BIOS menu after USB pen drive did not run live session.
will try to boot into other PC which is stored in another place.  i have to go to get that laptop.
and will check BIOS menu again.


> **Olle Wiklund said:**
> ***You have done something in a different way, otherwise it would have worked.*** (Unless the USB pendrive broke, but it is very unlikely.)

Have you changed anything else on your computer for example in the BIOS menus? Can you boot into your other computer with the USB pendrive or USB HDD?

*Edit: Try to remember exactly how you did to make the pendrive bootable with Xubuntu, and repeat that!*

---

### Post by Matrix01 on 2011-11-28
how to set them?
floppy boot,
internal network adapter boot,
enabled or disabled?

and boot order is set;
usb cd /dvd rom
usb diskette on key/usb hard disk
usb floppy
notebook HD
network adapter.

which one is usb flash drive?

---

### Post by WasMeHere on 2011-11-28
> **Matrix01 said:**
> how to set them?
floppy boot,
internal network adapter boot,
enabled or disabled?

and boot order is set;
usb cd /dvd rom
usb diskette on key/usb hard disk
usb floppy
notebook HD
network adapter.

which one is usb flash drive?
The BIOS alternatives vary between computers. Sometimes it works out of the box selecting boot from USB. Sometimes a USB drive is interpreted as a hard drive, so you should change the boot order between the hard drives.

It is definitely not network boot. I don't think it is floppy boot, but sometimes a CD or USB boot drive is emulating floppy (this was used for old boot systems).

I'm not sure what happens when you have two bootable USB drives attached at the same time. Probably one of them will be booted, but you should check that too!

---

### Post by Matrix01 on 2011-11-28
by the way,
do u know how to bypass log in,
and go to home screen when xubuntu boots?

---

### Post by WasMeHere on 2011-11-28
> **Matrix01 said:**
> by the way,
do u know how to bypass log in,
and go to home screen when xubuntu boots?
When you manage to boot from the USB pendrive again, please don't tweak it until you have at least one more Ubuntu system running. By the way, it usually does not ask for a password during a live session.

---

### Post by Matrix01 on 2011-11-29
will u tell me why USB HDD is not mounted when u edit partitions?

> **Olle Wiklund said:**
> No, leave the allocation size at its default value! At least now. Keep this pendrive in a working condition!

So it is the USB hard drive that has the exfat file system. It was probably formatted when you bought it. 

You want to run Ubuntu from the "1 TB ext. HDD", so ***yes, you need to back it up*** first and then use gparted to make new partitions. But why do you want to run it live? Is it because you want it as a temporary solution to install from there to the '8G USB flash drive'?

Anyway, format it with NTFS ***only*** if you want it as a data disk for Ubuntu and Windows. ***If you want to use it as a live disk, you should make several partitions***.

0. After backup, make sure your USB HDD is ***not*** mounted! Start editing the partition table with gparted from the live USB stick session!

1. Primary partition with FAT32 and flags: BOOT and LBA and label: USB_HDD_OS.
I recommend size 12 GB (good if you want to reuse it later with persistence or a small fully installed Ubuntu system). If you are sure that you will only run standard live systems, 2 GB would be enough.

2. Extended partition, size 'all remaining space'
3. Logical swap partition, size 4 GB
4. Logical partition with NTFS, size 'all remaining space' with label: *data*

---

### Post by Matrix01 on 2011-11-29
where's misc. options?

> **Olle Wiklund said:**
> I use the edit option according to the attached picture, so it is possible to edit tags manually for example the

---

### Post by Matrix01 on 2011-11-29
do u mean Network configuration depends on how to install ubuntu?

> **Olle Wiklund said:**
> I have no experience of wubi, so I can't help you with that.

---

### Post by WasMeHere on 2011-11-29
> **Matrix01 said:**
> will u tell me why USB HDD is not mounted when u edit partitions?
The disk should be connected (to the power and to the motherboard) but ***not mounted***. This is because when mounted some process might access it (read/write) which would destroy the editing of partitions and file systems and vice versa.

---

### Post by WasMeHere on 2011-11-29
> **Matrix01 said:**
> where's misc. options?
Look at the http address of Firefox in the attached screenshot!
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=11493441&postcount=94_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11493441&postcount=94")
It is near the bottom of that page. You can get to it via the ***User CP*** link at the top of your page when browsing the Ubuntu Forums

---

### Post by WasMeHere on 2011-11-29
> **Matrix01 said:**
> do u mean Network configuration depends on how to install ubuntu?

Wubi install is running Ubuntu as an application program within Windows, so Ubuntu must get to the internet via Windows. I don't know the details, I have never done it. Maybe it should be running out of the box. Maybe someone else reading this thread can help you. Otherwise you need to start a new thread about Wubi install and internet.

---

### Post by Matrix01 on 2011-11-30
update completed for a while ago.
need i configure network?

> **Olle Wiklund said:**
> Wubi install is running Ubuntu as an application program within Windows, so Ubuntu must get to the internet via Windows. I don't know the details, I have never done it. Maybe it should be running out of the box. Maybe someone else reading this thread can help you. Otherwise you need to start a new thread about Wubi install and internet.

---

### Post by WasMeHere on 2011-11-30
> **Matrix01 said:**
> update completed for a while ago.
need i configure network?
Wubi-installed Ubuntu update completed? In that case I guess your Ubuntu has access to the internet :-)

Is this way to run Ubuntu better for you than to run from a USB drive?

---

### Post by Matrix01 on 2011-11-30
same thing happened when 11.04, Natty was booting from USB flash drive,
After Natty was working fine for a day or so, 

error message showed up when booting up.
reformatted usb pendrive, and downloaded unetbootin and Natty ISO,
did not work.

my another laptop, Toshiba, is in storage.
when i get a chance, connect this usb pen drive to Toshiba.
by the way,
Xubuntu is working from Wubi.


> **Olle Wiklund said:**
> ***You have done something in a different way, otherwise it would have worked.*** (Unless the USB pendrive broke, but it is very unlikely.)

Have you changed anything else on your computer for example in the BIOS menus? Can you boot into your other computer with the USB pendrive or USB HDD?

*Edit: Try to remember exactly how you did to make the pendrive bootable with Xubuntu, and repeat that!*

---

### Post by Matrix01 on 2011-11-30
yep, internet is working,
and
Xubuntu is working from Wubi.
Wubi took a long time to install, i fell in sleep.

> **Olle Wiklund said:**
> Wubi-installed Ubuntu update completed? In that case I guess your Ubuntu has access to the internet :-)

Is this way to run Ubuntu better for you than to run from a USB drive?

---

### Post by Matrix01 on 2011-11-30
what is security update in package?

---

### Post by WasMeHere on 2011-11-30
> **Matrix01 said:**
> same thing happened when 11.04, Natty was booting from USB flash drive,
After Natty was working fine for a day or so, 

error message showed up when booting up.
reformatted usb pendrive, and downloaded unetbootin and Natty ISO,
did not work.

my another laptop, Toshiba, is in storage.
when i get a chance, connect this usb pen drive to Toshiba.
by the way,
Xubuntu is working from Wubi.
Good the Xubuntu is working from Wubi and gives you access to the linux tools :-)

Maybe there is some tweaking of your USB pen drive, that destroys booting. If you have not done it, maybe it happens automatically. One way to avoid that is to create it without the casper-iso file, so that it is not persistent. Then, whatever downloads or tweaks only lasts until the next shutdown or reboot.

So what do you want to do next with your netbook? Running Xubuntu to get used to it for some week(s) or continue to try making the external hard drive bootable, or trying to make a 'regular' install to the USB pen drive (for example via amjjawad's method)?

---

### Post by WasMeHere on 2011-11-30
> **Matrix01 said:**
> what is security update in package?
An installed system needs regular security updates. Along with that also software improvements are offered via an automatic system with icons or widgets to make you aware of it.

But you can also start these updates manually from the command line terminal or from an Update Manager. It is good to learn about the apt-get program, that you use for updates as well as installation/removal of program packages.

```
sudo apt-get update
sudo apt-get upgrade
```
will give you the security updates plus software improvements.

Learn more reading the manual
```
man apt-get
```

---

### Post by WasMeHere on 2011-11-30
By the way, now that you have installed Xubuntu into Windows, I suggest that you make a full backup of your hard drive, so that it can be easily restored, it something happens to it. There are many ways to perform the backup operation. You can search the Ubuntu Forums or the entire internet to find many suggestions and tutorials.

I suggest that you learn to use Clonezilla. Download the iso file from the internet and make a live Clonezilla USB drive! You can backup up a whole drive or one or more partitions. It would be a good idea to make an ***image of your internal drive*** and write it to file(s) on your NTFS partition on the external USB HDD.

---

### Post by Matrix01 on 2011-12-02
does casper iso file make persitent usb pen drive?

i like to find someone whom has Window 7 Starter installation disk, and install ubuntu in this HDD, and save Windows in VM ( do not know how to do that.)

meanwhile,
install ubuntu in usb pen drive,
will u tell me about amijawad's method?

> **Olle Wiklund said:**
> Good the Xubuntu is working from Wubi and gives you access to the linux tools :-)

Maybe there is some tweaking of your USB pen drive, that destroys booting. If you have not done it, maybe it happens automatically. One way to avoid that is to create it without the casper-iso file, so that it is not persistent. Then, whatever downloads or tweaks only lasts until the next shutdown or reboot.

So what do you want to do next with your netbook? Running Xubuntu to get used to it for some week(s) or continue to try making the external hard drive bootable, or trying to make a 'regular' install to the USB pen drive (for example via amjjawad's method)?

---

### Post by navaleshubham10 on 2011-12-02
are u using ubuntu as a software in windows
:confused:

---

### Post by Matrix01 on 2011-12-02
when i made persistent usb pen drive, and tried to boot Natty,
log in tab showed up, 
although i have not even set up password or user name.

---

### Post by WasMeHere on 2011-12-02
> **Matrix01 said:**
> does casper iso file make persitent usb pen drive?

i like to find someone whom has Window 7 Starter installation disk, and install ubuntu in this HDD, and save Windows in VM ( do not know how to do that.)

meanwhile,
install ubuntu in usb pen drive,
will u tell me about amijawad's method?
Not the iso file, it is the casper-**rw** file, "space used to preserve files", see also your old attachment:
> **Matrix01 said:**
> what is this for?
"space used to preserve files across reboots (ubuntu only)"

[ATTACH]207753[/ATTACH]

Here is amjjawad's method: [[COLOR="RoyalBlue"]_HOW TO Install Lubuntu on USB Drive_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1872303")

If you have a USB drive, from which you can boot Ubuntu, is easy to install ubuntu on the hard drive. ***But*** as far as I know, you need a Windows install CD (or iso file made from that CD) to install Windows into a VM. [COLOR="Red"]Let us hope that someone else reading this thread will know another method[/COLOR]

But if you do not really need all four partitions (for example the hp-tools partition), you can make that one into an extended partition and shrink the windows partition and use that space for Ubuntu in one linux partition and one swap partition inside the extended partition. But such things are not easy, so it is ***absolutely necessary to have a full backup of your internal hard drive*** before you start doing it.

---

### Post by Matrix01 on 2011-12-02
i removed CD burner from software center
because obviously netbook has no CD drive,
can get external CD drive though.

> **Olle Wiklund said:**
> An installed system needs regular security updates. Along with that also software improvements are offered via an automatic system with icons or widgets to make you aware of it.

But you can also start these updates manually from the command line terminal or from an Update Manager. It is good to learn about the apt-get program, that you use for updates as well as installation/removal of program packages.

```
sudo apt-get update
sudo apt-get upgrade
```
will give you the security updates plus software improvements.

Learn more reading the manual
```
man apt-get
```

---

### Post by Matrix01 on 2011-12-02
here's screen shot of HP Tools;

[ATTACH]208360[/ATTACH]

[ATTACH]208361[/ATTACH]

i think they need to be saved?

> **Olle Wiklund said:**
> Not the iso file, it is the casper-**rw** file, "space used to preserve files", see also your old attachment:

Here is amjjawad's method: [[COLOR="RoyalBlue"]_HOW TO Install Lubuntu on USB Drive_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1872303")

If you have a USB drive, from which you can boot Ubuntu, is easy to install ubuntu on the hard drive. ***But*** as far as I know, you need a Windows install CD (or iso file made from that CD) to install Windows into a VM. [COLOR="Red"]Let us hope that someone else reading this thread will know another method[/COLOR]

But if you do not really need all four partitions (for example the hp-tools partition), you can make that one into an extended partition and shrink the windows partition and use that space for Ubuntu in one linux partition and one swap partition inside the extended partition. But such things are not easy, so it is ***absolutely necessary to have a full backup of your internal hard drive*** before you start doing it.

---

### Post by Matrix01 on 2011-12-02
found some articles about HP Mini netbook and ubuntu installation.
do these articles help to install ubuntu on this netbook?

this netbook is HP Mini 110-3098NR.

[http://ubuntuforums.org/showthread.php?t=1109131](http://ubuntuforums.org/showthread.php?t=1109131) boot order may be key?

[http://ubuntuforums.org/showthread.php?t=1031619](http://ubuntuforums.org/showthread.php?t=1031619)

[http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and/HP-mini-110-Cant-use-recovery-disks-BIOS-insists-hard-disk-check/td-p/648861](http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and/HP-mini-110-Cant-use-recovery-disks-BIOS-insists-hard-disk-check/td-p/648861)

[http://ubuntuforums.org/showthread.php?t=1337358](http://ubuntuforums.org/showthread.php?t=1337358)

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#HP_Mini_110_.2BAC8_Compaq_Mini_100c.2BAC8-110c](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#HP_Mini_110_.2BAC8_Compaq_Mini_100c.2BAC8-110c)

---

### Post by WasMeHere on 2011-12-02
> **Matrix01 said:**
> when i made persistent usb pen drive, and tried to boot Natty,
log in tab showed up, 
although i have not even set up password or user name.

I see. Usually, when I set up USB pen drives, I don't make them persistent, so I did not remember that. Anyway, if you want to keep your pen drive bootable, there might be two ways to go.

1. A regular bootable pen drive without casper-rw file for persistence. This works better if there is a swap partition in the computer. I guess it would work with a boot partition on the external USB HDD. Did you reformat the external USB HDD according to our previous correspondence? In that case there is a swap partition.

2. An installed system according to amjjawad on the USB pen drive.

---

### Post by WasMeHere on 2011-12-02
> **matrix01 said:**
> i removed cd burner from software center
because obviously netbook has no cd drive,
can get external cd drive though.
ok

---

### Post by WasMeHere on 2011-12-02
> **Matrix01 said:**
> here's screen shot of HP Tools;

[ATTACH]208360[/ATTACH]

[ATTACH]208361[/ATTACH]

i think they need to be saved?

If you save (copy) them to the external USB HDD, you will have peace of mind. But it is more important to have a full backup of the internal hard drive, because if something goes wrong during to re-partitioning of the internal hard drive or installation of Ubuntu, you will wipe windows.

---

### Post by WasMeHere on 2011-12-02
> **Matrix01 said:**
> found some articles about HP Mini netbook and ubuntu installation.
do these articles help to install ubuntu on this netbook?

this netbook is HP Mini 110-3098NR.

[http://ubuntuforums.org/showthread.php?t=1031619](http://ubuntuforums.org/showthread.php?t=1031619)

[http://ubuntuforums.org/showthread.php?t=1109131](http://ubuntuforums.org/showthread.php?t=1109131)

[http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and/HP-mini-110-Cant-use-recovery-disks-BIOS-insists-hard-disk-check/td-p/648861](http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and/HP-mini-110-Cant-use-recovery-disks-BIOS-insists-hard-disk-check/td-p/648861)

[http://ubuntuforums.org/showthread.php?t=1337358](http://ubuntuforums.org/showthread.php?t=1337358)

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#HP_Mini_110_.2BAC8_Compaq_Mini_100c.2BAC8-110c](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#HP_Mini_110_.2BAC8_Compaq_Mini_100c.2BAC8-110c)

This last post of the second thread above has valuable information [[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=7010555&postcount=60_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=7010555&postcount=60")

And this one indicates success, but not may details [[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=1337358_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1337358")

And certainly, the final link, the Wiki page is valuable to read :-)

Summarizing, I would say that if you make your computer run from a USB drive, it will also run from an installed system on the internal hard disk drive. It might need some tweaking of the boot options, but it will run.

---

### Post by Matrix01 on 2011-12-02
[ATTACH]208368[/ATTACH]
does hp tools have enough room for ubuntu?

> **Olle Wiklund said:**
> If you save (copy) them to the external USB HDD, you will have peace of mind. But it is more important to have a full backup of the internal hard drive, because if something goes wrong during to re-partitioning of the internal hard drive or installation of Ubuntu, you will wipe windows.

---

### Post by Matrix01 on 2011-12-02
5:turned acpi off ( I keep reading to turn it off at the installation screen so I thought I would in the bios, I didn't turn it off at the install screen)

what is acpi?

> **Olle Wiklund said:**
> This last post of the second thread above has valuable information [[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=7010555&postcount=60_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=7010555&postcount=60")

And this one indicates success, but not may details [[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=1337358_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1337358")

And certainly, the final link, the Wiki page is valuable to read :-)

Summarizing, I would say that if you make your computer run from a USB drive, it will also run from an installed system on the internal hard disk drive. It might need some tweaking of the boot options, but it will run.

---

### Post by Matrix01 on 2011-12-02
And this one indicates success, but not may details [http://ubuntuforums.org/showthread.php?t=1337358](http://ubuntuforums.org/showthread.php?t=1337358)

Do desktop iso and netbook remix iso have same kernel but different interface?

---

### Post by WasMeHere on 2011-12-02
> **Matrix01 said:**
> [ATTACH]208368[/ATTACH]
does hp tools have enough room for ubuntu?
No, you would have to shrink the big windows partition and then move the boundary between the partition(s) such that there will be enough space for ubuntu and swap inside an extended partition (instead of the hp partition). I tried to explain that in [[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=11505765&postcount=132_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11505765&postcount=132")

It is possible but risky, hence the need for backup.

---

### Post by WasMeHere on 2011-12-02
> **Matrix01 said:**
> 5:turned acpi off ( I keep reading to turn it off at the installation screen so I thought I would in the bios, I didn't turn it off at the install screen)

what is acpi?

Browse the internet to find out the technical details! It is possible to turn it off during boot of a live CD or USB drive using a function key (I think it is F6) at the first screen, when you can select a live session or installation. Later on after installation, it is also possible to select in the grub menu (or to tweak grub) to make the change persistent. There are several things that can be turned on or off in the same way.
[[COLOR="RoyalBlue"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

---

### Post by WasMeHere on 2011-12-02
> **Matrix01 said:**
> And this one indicates success, but not may details [http://ubuntuforums.org/showthread.php?t=1337358](http://ubuntuforums.org/showthread.php?t=1337358)

Do desktop iso and netbook remix iso have same kernel but different interface?
I think the netbook remix is old and it's kernel is old too (there is no netbook flavour of the recent version 11.10). And I think it was necessary in the beginning of netbooks in order to recognize the hardware, but today the standard kernel recognizes the hardware of netbooks.

---

### Post by Matrix01 on 2011-12-05
is desk top version of iso file better? 

> **Olle Wiklund said:**
> I think the netbook remix is old and it's kernel is old too (there is no netbook flavour of the recent version 11.10). And I think it was necessary in the beginning of netbooks in order to recognize the hardware, but today the standard kernel recognizes the hardware of netbooks.

---

### Post by Matrix01 on 2011-12-05
does advanced configurtion and power interface, need to be turned off?


> **Olle Wiklund said:**
> Browse the internet to find out the technical details! It is possible to turn it off during boot of a live CD or USB drive using a function key (I think it is F6) at the first screen, when you can select a live session or installation. Later on after installation, it is also possible to select in the grub menu (or to tweak grub) to make the change persistent. There are several things that can be turned on or off in the same way.
[[COLOR="RoyalBlue"]_https://help.ubuntu.com/community/BootOptions_[/COLOR]]("https://help.ubuntu.com/community/BootOptions")

---

### Post by Matrix01 on 2011-12-05
i recall that you have wiped windows from your HDD, and saved windows in VM,
does windows in VM installed on your ubuntu?

---

### Post by WasMeHere on 2011-12-05
> **Matrix01 said:**
> is desk top version of iso file better?
It depends on your hardware and how you want to use it, *and* how long you want to use it (the netbook remix is old). In order to know what is best for you, try them and decide!

---

### Post by WasMeHere on 2011-12-05
> **Matrix01 said:**
> does advanced configurtion and power interface, need to be turned off?
I don't know with your computer, but it is one of the possibilities (choices) at F6 to get Ubuntu running from a CD/USB drive. ACPI is a good feature and should definitely be used if it works with the computer, particularly with a laptop or netbook to manage the battery.

Use these F6 boot options as trial and error tweaks!

---

### Post by WasMeHere on 2011-12-05
> **Matrix01 said:**
> i recall that you have wiped windows from your HDD, and saved windows in VM,
does windows in VM installed on your ubuntu?
I have a windows installation CD, so I installed the VM and then installed Windows from the CD into the VM. In this computer I run Ubuntu 10.04 LTS, VirtualBox and Windows XP. (It is also multibooting other linux versions, but only for testing, Ubuntu 10.04 LTS is my 'work horse'.)

We also have other computers at home, and they are multibooting linux (Ubuntu or Linux Mint) and Windows. If you want to play games in Windows, you should run it on the real machine, because it will be slower in a VM.

---

### Post by Matrix01 on 2011-12-06
do u mean to go to boot order?
on my Netbook, F10.

> **Olle Wiklund said:**
> I don't know with your computer, but it is one of the possibilities (choices) at F6 to get Ubuntu running from a CD/USB drive. ACPI is a good feature and should definitely be used if it works with the computer, particularly with a laptop or netbook to manage the battery.

Use these F6 boot options as trial and error tweaks!

---

### Post by Matrix01 on 2011-12-06
i went to computer store, and
told you can dwonload iso file of Window from website.
have u tried this?

> **Olle Wiklund said:**
> I have a windows installation CD, so I installed the VM and then installed Windows from the CD into the VM. In this computer I run Ubuntu 10.04 LTS, VirtualBox and Windows XP. (It is also multibooting other linux versions, but only for testing, Ubuntu 10.04 LTS is my 'work horse'.)

We also have other computers at home, and they are multibooting linux (Ubuntu or Linux Mint) and Windows. If you want to play games in Windows, you should run it on the real machine, because it will be slower in a VM.

---

### Post by WasMeHere on 2011-12-06
> **Matrix01 said:**
> do u mean to go to boot order?
on my Netbook, F10.

Not the bios boot order, but the ***first menu of the ubuntu live disk***, where you select to test (running a live session) and other options, ***or*** if/when installed ***the grub menu***, where you can select different kernels and if dual boot select between different systems (linux, windows ...).

---

### Post by WasMeHere on 2011-12-06
> **Matrix01 said:**
> i went to computer store, and
told you can dwonload iso file of Window from website.
have u tried this?
I'm satisfied with my CD, so I have not tried that, but it sounds like a good option. I guess you need a version, that recognizes your license key (on the sticker somewhere on your computer).

*Edit: Beware that Microsoft considers a virtual machine to be another computer even when it is on a computer, which has a Windows license. So you may get problems to get the license accepted.*

---

### Post by Matrix01 on 2011-12-08
do u mean;

try ubuntu without installing,
install ubuntu,
.......
.......

these options?

> **Olle Wiklund said:**
> Not the bios boot order, but the ***first menu of the ubuntu live disk***, where you select to test (running a live session) and other options, ***or*** if/when installed ***the grub menu***, where you can select different kernels and if dual boot select between different systems (linux, windows ...).

---

### Post by WasMeHere on 2011-12-08
> **Matrix01 said:**
> do u mean;

try ubuntu without installing,
install ubuntu,
.......
.......

these options?
Yes, the screen with those options. You can press F6 to get boot options when you are at that screen.

---

### Post by Matrix01 on 2011-12-08
pressed esc,
and 
boot: (boot prompt) shoes up
i typed in

i; install,
c; check disk,
h; help,
t; try w/o installing,

output is; kernel not found.

> **Olle Wiklund said:**
> Yes, the screen with those options. You can press F6 to get boot options when you are at that screen.

---

### Post by WasMeHere on 2011-12-08
> **Matrix01 said:**
> pressed esc,
and 
boot: (boot prompt) shoes up
i typed in

i; install,
c; check disk,
h; help,
t; try w/o installing,

output is; kernel not found.
why press ***escape***, when you should press ***F6*** (the function key number 6 above the 'regular keys 6 and 7')? After selecting F6, you can go back and select via the menu (the arrow keys). At least, it was like that in several previous versions. But I suggest that, at your text menu, you should try without installing, that is use ***t***.

[I]Edit: I have a Kubuntu 11.10 boot CD, and tested it now. There is a menu where to select for example to run Kubuntu. I could select F6 and escape. Then I returned to the previous menu (graphical, not a text menu) and could select for example language and escape again, and finally select to run Kubuntu. Then I came to a menu to select 'run live' or 'install' and finally I could start the live session.

**Are you trying to run Xubuntu 11.10 now? Or another flavour or version of Ubuntu?**[/I]

---

### Post by Matrix01 on 2011-12-09
trying to run xubuntu.
i was told xubuntu is light weight and runs faster.

find out this,
pressed F6 while menu is on screen,
reset count down, but does not do anythings else.


> **Olle Wiklund said:**
> why press ***escape***, when you should press ***F6*** (the function key number 6 above the 'regular keys 6 and 7')? After selecting F6, you can go back and select via the menu (the arrow keys). At least, it was like that in several previous versions. But I suggest that, at your text menu, you should try without installing, that is use ***t***.

[I]Edit: I have a Kubuntu 11.10 boot CD, and tested it now. There is a menu where to select for example to run Kubuntu. I could select F6 and escape. Then I returned to the previous menu (graphical, not a text menu) and could select for example language and escape again, and finally select to run Kubuntu. Then I came to a menu to select 'run live' or 'install' and finally I could start the live session.

**Are you trying to run Xubuntu 11.10 now? Or another flavour or version of Ubuntu?**[/I]

---

### Post by Matrix01 on 2011-12-09
so restarted netbook again;
menu shows up like this; 

default
help
try xubuntu w/0 inst'
inst' x
check disk
test memory
boot from isr HD
press tab to edit option,

pressed tab key,
this shows up,
>/ubnkern initrd=/ubninit

---

### Post by WasMeHere on 2011-12-09
> **Matrix01 said:**
> trying to run xubuntu.
i was told xubuntu is light weight and runs faster.

find out this,
pressed F6 while menu is on screen,
reset count down, but does not do anythings else.
1. select language while count-down by pressing the Enter key
2. then at the menu press F6 ...

---

### Post by WasMeHere on 2011-12-09
> **Matrix01 said:**
> so restarted netbook again;
menu shows up like this; 

default
help
try xubuntu w/0 inst'
inst' x
check disk
test memory
boot from isr HD
press tab to edit option,

pressed tab key,
this shows up,
>/ubnkern initrd=/ubninit
I have tried booting xubuntu 11.10 (see the attached files).

1. Select language 'while count-down' by pressing the Enter key.

2. Then at the menu press F6 and select whatever boot options you want or need (one or more) with the Space-bar or Enter key and leave the sub-menu with the Escape key.

3. Select 'Try Xubuntu without installing' with arrow keys and press the Enter key to go on to the live session.

4. In the live session, you have a hidden panel at the bottom. Show it by moving the cursor to the bottom edge of the screen.

You need not make it complicated by pressing tab to enter text mode and edit options manually.

---

### Post by Matrix01 on 2011-12-09
default
 help
 try xubuntu w/0 inst'
 inst' x
 check disk
 test memory
 boot from isr HD
 press tab to edit option,

 pressed tab key,
that's all on menu on screen.

F1....F6 are not on menu.
how did u run xubuntu 11.10?







> **Olle Wiklund said:**
> I have tried booting xubuntu 11.10 (see the attached files).

1. Select language 'while count-down' by pressing the Enter key.

2. Then at the menu press F6 and select whatever boot options you want or need (one or more) with the Space-bar or Enter key and leave the sub-menu with the Escape key.

3. Select 'Try Xubuntu without installing' with arrow keys and press the Enter key to go on to the live session.

4. In the live session, you have a hidden panel at the bottom. Show it by moving the cursor to the bottom edge of the screen.

You need not make it complicated by pressing tab to enter text mode and edit options manually.

---

### Post by WasMeHere on 2011-12-09
> **Matrix01 said:**
> default
 help
 try xubuntu w/0 inst'
 inst' x
 check disk
 test memory
 boot from isr HD
 press tab to edit option,

 pressed tab key,
that's all on menu on screen.

F1....F6 are not on menu.
how did u run xubuntu 11.10?

I ran it from the boot CD. I guess you did not use the Ubuntu way to make the USB boot drive, because then it should have looked the same. 

1. Did you use Unetbootin or some other method?
2. What happens if you 'try xubuntu w/0 inst' ... and wait ...?

---

### Post by Matrix01 on 2011-12-10
yep,

1. unetbootin.
2. same error message i had for a while ago;

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
 Enter 'help' for a list of built-in commands.

 (initramfs)

> **Olle Wiklund said:**
> I ran it from the boot CD. I guess you did not use the Ubuntu way to make the USB boot drive, because then it should have looked the same. 

1. Did you use Unetbootin or some other method?
2. What happens if you 'try xubuntu w/0 inst' ... and wait ...?

---

### Post by WasMeHere on 2011-12-10
> **Matrix01 said:**
> so restarted netbook again;
menu shows up like this; 

default
help
try xubuntu w/0 inst'
inst' x
check disk
test memory
boot from isr HD
press tab to edit option,

pressed tab key,
this shows up,
>/ubnkern initrd=/ubninit
Substitute that 'ubnkern line' with parts of this from the ***syslinux.cfg*** file:

```
label ubnentry0
menu label Start Linux Mint
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/mint.seed boot=casper  quiet splash --

label ubnentry1
menu label Start Linux Mint (compatibility mode)
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/mint.seed boot=casper xforcevesa  ramdisk_size=1048576 root=/dev/ram rw noapic noapci nosplash irqpoll --
```

and I am thinking of entering one or several of the ***boot options*** into the first part:
***[COLOR="Red"]xforcevesa noapic noapci nosplash irqpoll [/COLOR]***... and maybe ***[COLOR="Red"]nomodeset[/COLOR]***

```
label ubnentry0
menu label Start Linux Mint
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/mint.seed boot=casper  quiet splash***[COLOR="Red"] here [/COLOR]***--
```
or manually at the boot menu, simply add the boot options before **'--'** (leaving spaces around) and maybe remove 'quiet splash'

---

### Post by Matrix01 on 2011-12-10
pressed tab key when menu is on screen,
this shows up,

>/ubnkern initrd=/ubninit file= /cdrom/xubuntu.seal boot=casper quiet splash --
 
and erased 'quiet splash',and this shows up;


busybox.............(ash)
initramfs
mount:mounting/dev/loop0 on //file system.squashfs failed:invalid argument can not mount/dev/loop0 (/cdrom/casper/filesystem.squashfs) on // file system squashfs


i have seen this message, can not remember where.









> **Olle Wiklund said:**
> Substitute that 'ubnkern line' with parts of this from the ***syslinux.cfg*** file:

```
label ubnentry0
menu label Start Linux Mint
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/mint.seed boot=casper  quiet splash --

label ubnentry1
menu label Start Linux Mint (compatibility mode)
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/mint.seed boot=casper xforcevesa  ramdisk_size=1048576 root=/dev/ram rw noapic noapci nosplash irqpoll --
```and I am thinking of entering one or several of the ***boot options*** into the first part:
***[COLOR=Red]xforcevesa noapic noapci nosplash irqpoll [/COLOR]***... and maybe ***[COLOR=Red]nomodeset[/COLOR]***

```
label ubnentry0
menu label Start Linux Mint
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/mint.seed boot=casper  quiet splash***[COLOR=Red] here [/COLOR]***--
```or manually at the boot menu, simply add the boot options before **'--'** (leaving spaces around) and maybe remove 'quiet splash'

---

### Post by WasMeHere on 2011-12-10
> **Matrix01 said:**
> pressed tab key when menu is on screen,
this shows up,

>/ubnkern initrd=/ubninit file= /cdrom/xubuntu.seal boot=casper quiet splash --
 
and erased 'quiet splash',and this shows up;


busybox.............(ash)
initramfs
mount:mounting/dev/loop0 on //file system.squashfs failed:invalid argument can not mount/dev/loop0 (/cdrom/casper/filesystem.squashfs) on // file system squashfs


i have seen this message, can not remember where.

I don't really know how the different things interact during boot, but anyway, please try the boot options one by one , then two by two ... and let us hope that you find a setting that will work.

If you have persistence, the basic file system is mounted via /dev/loop0 on **[COLOR="Red"]/rofs[/COLOR]** and the casper-rw-file mounted via aufs on **[COLOR="Red"]/[/COLOR]** (at least on my installation).

Maybe it would work well also for you to make the boot USB from
[FONT="Courier New"]linuxmint-11-gnome-dvd-i386.iso[/FONT],  Linux Mint gnome 11 i386 (32-bit system).
It uses only 269 MB when idle as you can see in the attached picture. I also attach the output of
```
sudo fdisk -lu
df
ls -g /cdrom
ls -g /rofs
ls -g /
cat /cdrom/syslinux.cfg
```
when running the pesistent system. Have an extra look at the **[COLOR="Red"]red[/COLOR]** text!
```

olle@mint ~ $ sudo fdisk -lu
...
/dev/sda6       172056213   197230004    12586896   82  Linux växling / Solaris

Disk /dev/sdb: 15,8 GB, 15812526080 bytes

   Device StartFlg  Begin         End     Size kB   Id  System
/dev/sdb1   *          63    10490444     5245191    c  W95 FAT32 (LBA)
/dev/sdb2        10490445    30876929    10193242+   5  Extended
/dev/sdb5        10490508    13639184     1574338+  82  Linux Swap / Solaris
/dev/sdb6        13639248    30876929     8618841    b  W95 FAT32

olle@mint ~ $ df
File system           1K-block    Used     Free   Used% Mounted on
[COLOR="Red"]aufs                   4127424    382560   3535200  10% /[/COLOR]
none                   1796988       708   1796280   1% /dev
[COLOR="Red"]/dev/sdb1              5234948   5098336    136612  98% /cdrom
/dev/loop0              864512    864512         0 100% /rofs[/COLOR]
none                   1806384       276   1806108   1% /dev/shm
tmpfs                  1806384        28   1806356   1% /tmp
none                   1806384       348   1806036   1% /var/run
none                   1806384         0   1806384   0% /var/lock
/home/olle/.Private    4127424    382560   3535200  10% /home/olle
/dev/sdb6              8610416         8   8610408   1% /media/usb-data

olle@mint ~ $ ls -g /cdrom
totalt 4215912
drwxr-xr-x 3 root       4096 2011-12-09 22:17 boot
drwxr-xr-x 2 root       4096 2011-12-10 00:15 casper
-rwxr-xr-x 1 root 4293918720 2011-12-10 12:49 casper-rw
drwxr-xr-x 2 root       4096 2011-12-09 22:18 isolinux
-r-xr-xr-x 1 root      32768 2011-12-09 22:18 ldlinux.sys
-rwxr-xr-x 1 root       1134 2011-05-22 15:59 md5sum.txt
-rwxr-xr-x 1 root      56832 2011-12-09 22:18 menu.c32
drwxr-xr-x 2 root       4096 2011-12-09 22:18 preseed
-rwxr-xr-x 1 root        990 2011-12-10 00:08 syslinux.cfg
-rwxr-xr-x 1 root        465 2011-12-09 23:18 ubnfilel.txt
-rwxr-xr-x 1 root   18526711 2011-05-22 14:54 ubninit
-rwxr-xr-x 1 root    4521296 2011-05-22 14:54 ubnkern
-rwxr-xr-x 1 root         45 2011-12-09 23:17 ubnpathl.txt
olle@mint ~ $ ls -g /rofs
totalt 0
drwxr-xr-x   2 root 2451 2011-05-01 15:03 bin
drwxr-xr-x   4 root  289 2011-05-03 21:50 boot
drwxr-xr-x   5 root 1198 2011-04-26 01:07 dev
drwxr-xr-x 143 root 4154 2011-05-22 13:53 etc
drwxr-xr-x   2 root    3 2011-04-21 18:50 home
lrwxrwxrwx   1 root   32 2011-04-26 01:01 initrd.img -> boot/initrd.img-2.6.38-8-generic
drwxr-xr-x  20 root 2584 2011-05-01 15:03 lib
drwxr-xr-x   2 root    3 2011-04-26 00:50 media
drwxr-xr-x   2 root    3 2011-04-21 18:50 mnt
drwxr-xr-x   4 root   59 2011-05-22 13:26 opt
drwxr-xr-x   2 root    3 2011-04-21 18:50 proc
drwx------   4 root   83 2011-05-21 12:37 root
drwxr-xr-x   2 root 3607 2011-05-01 15:03 sbin
drwxr-xr-x   2 root    3 2011-03-21 09:26 selinux
drwxr-xr-x   2 root    3 2011-04-26 00:50 srv
drwxr-xr-x   2 root    3 2011-03-28 22:10 sys
drwxrwxrwt   4 root   60 2011-05-22 13:50 tmp
drwxr-xr-x  11 root  187 2011-04-26 00:56 usr
drwxr-xr-x  14 root  185 2011-04-28 13:42 var
lrwxrwxrwx   1 root   29 2011-04-26 01:01 vmlinuz -> boot/vmlinuz-2.6.38-8-generic
olle@mint ~ $ ls -g /
totalt 48
drwxr-xr-x   2 root  2451 2011-05-01 15:03 bin
drwxr-xr-x   5 root  4096 2011-12-10 00:14 boot
drwxr-xr-x   7 root  4096 1970-01-01 01:00 cdrom
drwxr-xr-x  18 root  4420 2011-12-10 13:24 dev
drwxr-xr-x 156 root  4096 2011-12-10 12:24 etc
drwxr-xr-x   5 root  4096 2011-12-10 00:57 home
lrwxrwxrwx   1 root    32 2011-04-26 01:01 initrd.img -> boot/initrd.img-2.6.38-8-generic
drwxr-xr-x  20 root  2584 2011-05-01 15:03 lib
drwx------   2 root 16384 2011-12-09 21:28 lost+found
drwxr-xr-x   3 root  4096 2011-12-10 12:24 media
drwxr-xr-x   2 root     3 2011-04-21 18:50 mnt
drwxr-xr-x   4 root    59 2011-05-22 13:26 opt
dr-xr-xr-x 165 root     0 2011-12-10 13:23 proc
drwxr-xr-x  20 root   341 2011-05-05 17:10 rofs
drwx------   9 root  4096 2011-12-10 00:08 root
drwxr-xr-x   2 root  3607 2011-05-01 15:03 sbin
drwxr-xr-x   2 root     3 2011-03-21 09:26 selinux
drwxr-xr-x   2 root     3 2011-04-26 00:50 srv
drwxr-xr-x  12 root     0 2011-12-10 13:23 sys
drwxrwxrwt  14 root   320 2011-12-10 12:47 tmp
drwxr-xr-x  15 root  4096 2011-04-26 00:56 usr
drwxr-xr-x  17 root  4096 2011-04-28 13:42 var
lrwxrwxrwx   1 root    29 2011-04-26 01:01 vmlinuz -> boot/vmlinuz-2.6.38-8-generic

olle@mint ~ $ cat /cdrom/syslinux.cfg
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default [COLOR="Red"]Linux Mint 11 Gnome *persistent*[/COLOR]
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/mint.seed boot=casper quiet splash[COLOR="Red"] persistent [/COLOR]--

label ubnentry0
menu label Start Linux Mint
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/mint.seed boot=casper  quiet splash --

label ubnentry1
menu label Start Linux Mint (compatibility mode)
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/mint.seed boot=casper xforcevesa  ramdisk_size=1048576 root=/dev/ram rw noapic noapci nosplash irqpoll --

label ubnentry2
menu label Check the integrity of the DVD
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry3
menu label Memory Test
kernel /isolinux/memtest
append initrd=/ubninit 

label ubnentry4
menu label Boot from local drive
kernel /ubnkern
append initrd=/ubninit

```
*Edit: Attachment included*

---

### Post by Matrix01 on 2011-12-12
what does this red text mean?

> **Olle Wiklund said:**
> I don't really know how the different things interact during boot, but anyway, please try the boot options one by one , then two by two ... and let us hope that you find a setting that will work.

If you have persistence, the basic file system is mounted via /dev/loop0 on **[COLOR="Red"]/rofs[/COLOR]** and the casper-rw-file mounted via aufs on **[COLOR="Red"]/[/COLOR]** (at least on my installation).

Maybe it would work well also for you to make the boot USB from
[FONT="Courier New"]linuxmint-11-gnome-dvd-i386.iso[/FONT],  Linux Mint gnome 11 i386 (32-bit system).
It uses only 269 MB when idle as you can see in the attached picture. I also attach the output of
```
sudo fdisk -lu
df
ls -g /cdrom
ls -g /rofs
ls -g /
cat /cdrom/syslinux.cfg
```
when running the pesistent system. Have an extra look at the **[COLOR="Red"]red[/COLOR]** text!
```

olle@mint ~ $ sudo fdisk -lu
...
/dev/sda6       172056213   197230004    12586896   82  Linux växling / Solaris

Disk /dev/sdb: 15,8 GB, 15812526080 bytes

   Device StartFlg  Begin         End     Size kB   Id  System
/dev/sdb1   *          63    10490444     5245191    c  W95 FAT32 (LBA)
/dev/sdb2        10490445    30876929    10193242+   5  Extended
/dev/sdb5        10490508    13639184     1574338+  82  Linux Swap / Solaris
/dev/sdb6        13639248    30876929     8618841    b  W95 FAT32

olle@mint ~ $ df
File system           1K-block    Used     Free   Used% Mounted on
[COLOR="Red"]aufs                   4127424    382560   3535200  10% /[/COLOR]
none                   1796988       708   1796280   1% /dev
[COLOR="Red"]/dev/sdb1              5234948   5098336    136612  98% /cdrom
/dev/loop0              864512    864512         0 100% /rofs[/COLOR]
none                   1806384       276   1806108   1% /dev/shm
tmpfs                  1806384        28   1806356   1% /tmp
none                   1806384       348   1806036   1% /var/run
none                   1806384         0   1806384   0% /var/lock
/home/olle/.Private    4127424    382560   3535200  10% /home/olle
/dev/sdb6              8610416         8   8610408   1% /media/usb-data

olle@mint ~ $ ls -g /cdrom
totalt 4215912
drwxr-xr-x 3 root       4096 2011-12-09 22:17 boot
drwxr-xr-x 2 root       4096 2011-12-10 00:15 casper
-rwxr-xr-x 1 root 4293918720 2011-12-10 12:49 casper-rw
drwxr-xr-x 2 root       4096 2011-12-09 22:18 isolinux
-r-xr-xr-x 1 root      32768 2011-12-09 22:18 ldlinux.sys
-rwxr-xr-x 1 root       1134 2011-05-22 15:59 md5sum.txt
-rwxr-xr-x 1 root      56832 2011-12-09 22:18 menu.c32
drwxr-xr-x 2 root       4096 2011-12-09 22:18 preseed
-rwxr-xr-x 1 root        990 2011-12-10 00:08 syslinux.cfg
-rwxr-xr-x 1 root        465 2011-12-09 23:18 ubnfilel.txt
-rwxr-xr-x 1 root   18526711 2011-05-22 14:54 ubninit
-rwxr-xr-x 1 root    4521296 2011-05-22 14:54 ubnkern
-rwxr-xr-x 1 root         45 2011-12-09 23:17 ubnpathl.txt
olle@mint ~ $ ls -g /rofs
totalt 0
drwxr-xr-x   2 root 2451 2011-05-01 15:03 bin
drwxr-xr-x   4 root  289 2011-05-03 21:50 boot
drwxr-xr-x   5 root 1198 2011-04-26 01:07 dev
drwxr-xr-x 143 root 4154 2011-05-22 13:53 etc
drwxr-xr-x   2 root    3 2011-04-21 18:50 home
lrwxrwxrwx   1 root   32 2011-04-26 01:01 initrd.img -> boot/initrd.img-2.6.38-8-generic
drwxr-xr-x  20 root 2584 2011-05-01 15:03 lib
drwxr-xr-x   2 root    3 2011-04-26 00:50 media
drwxr-xr-x   2 root    3 2011-04-21 18:50 mnt
drwxr-xr-x   4 root   59 2011-05-22 13:26 opt
drwxr-xr-x   2 root    3 2011-04-21 18:50 proc
drwx------   4 root   83 2011-05-21 12:37 root
drwxr-xr-x   2 root 3607 2011-05-01 15:03 sbin
drwxr-xr-x   2 root    3 2011-03-21 09:26 selinux
drwxr-xr-x   2 root    3 2011-04-26 00:50 srv
drwxr-xr-x   2 root    3 2011-03-28 22:10 sys
drwxrwxrwt   4 root   60 2011-05-22 13:50 tmp
drwxr-xr-x  11 root  187 2011-04-26 00:56 usr
drwxr-xr-x  14 root  185 2011-04-28 13:42 var
lrwxrwxrwx   1 root   29 2011-04-26 01:01 vmlinuz -> boot/vmlinuz-2.6.38-8-generic
olle@mint ~ $ ls -g /
totalt 48
drwxr-xr-x   2 root  2451 2011-05-01 15:03 bin
drwxr-xr-x   5 root  4096 2011-12-10 00:14 boot
drwxr-xr-x   7 root  4096 1970-01-01 01:00 cdrom
drwxr-xr-x  18 root  4420 2011-12-10 13:24 dev
drwxr-xr-x 156 root  4096 2011-12-10 12:24 etc
drwxr-xr-x   5 root  4096 2011-12-10 00:57 home
lrwxrwxrwx   1 root    32 2011-04-26 01:01 initrd.img -> boot/initrd.img-2.6.38-8-generic
drwxr-xr-x  20 root  2584 2011-05-01 15:03 lib
drwx------   2 root 16384 2011-12-09 21:28 lost+found
drwxr-xr-x   3 root  4096 2011-12-10 12:24 media
drwxr-xr-x   2 root     3 2011-04-21 18:50 mnt
drwxr-xr-x   4 root    59 2011-05-22 13:26 opt
dr-xr-xr-x 165 root     0 2011-12-10 13:23 proc
drwxr-xr-x  20 root   341 2011-05-05 17:10 rofs
drwx------   9 root  4096 2011-12-10 00:08 root
drwxr-xr-x   2 root  3607 2011-05-01 15:03 sbin
drwxr-xr-x   2 root     3 2011-03-21 09:26 selinux
drwxr-xr-x   2 root     3 2011-04-26 00:50 srv
drwxr-xr-x  12 root     0 2011-12-10 13:23 sys
drwxrwxrwt  14 root   320 2011-12-10 12:47 tmp
drwxr-xr-x  15 root  4096 2011-04-26 00:56 usr
drwxr-xr-x  17 root  4096 2011-04-28 13:42 var
lrwxrwxrwx   1 root    29 2011-04-26 01:01 vmlinuz -> boot/vmlinuz-2.6.38-8-generic

olle@mint ~ $ cat /cdrom/syslinux.cfg
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default [COLOR="Red"]Linux Mint 11 Gnome *persistent*[/COLOR]
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/mint.seed boot=casper quiet splash[COLOR="Red"] persistent [/COLOR]--

label ubnentry0
menu label Start Linux Mint
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/mint.seed boot=casper  quiet splash --

label ubnentry1
menu label Start Linux Mint (compatibility mode)
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/mint.seed boot=casper xforcevesa  ramdisk_size=1048576 root=/dev/ram rw noapic noapci nosplash irqpoll --

label ubnentry2
menu label Check the integrity of the DVD
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash --

label ubnentry3
menu label Memory Test
kernel /isolinux/memtest
append initrd=/ubninit 

label ubnentry4
menu label Boot from local drive
kernel /ubnkern
append initrd=/ubninit

```
*Edit: Attachment included*

---

### Post by WasMeHere on 2011-12-12
> what does this red text mean?

**[COLOR="Red"]/rofs[/COLOR]** ReadOnlyFileSystem

```
File system           1K-block    Used     Free   Used% Mounted on
[COLOR="Red"]aufs                   4127424    382560   3535200  10% /
/dev/sdb1              5234948   5098336    136612  98% /cdrom
/dev/loop0              864512    864512         0 100% /rofs[/COLOR]

```
/ is the file system root (equivalent to C: of Windows)
/cdrom is the live partition on the USB drive (the name shows the origin, the CD drive)

```
label unetbootindefault
menu label Default [COLOR="Red"]Linux Mint 11 Gnome *persistent*[/COLOR]
```
This is only a descriptive text
```
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/mint.seed boot=casper quiet splash[COLOR="Red"] persistent [/COLOR]--
```
This is how the unetbootin boot drive is told that it is persistent, and should use a casper-rw file on its root (/dev/sdb1 mounted on /cdrom)

I think all these instructions and descriptions are clear enough so that you can compare with what it looks like in your computer and make corrections if necessary, and succeed with your live USB session :-) Otherwise I strongly advice you to seek help at your place from someone that can sit at your computer and do it 'hands on'.

---

### Post by Matrix01 on 2011-12-13
hard to find someone is familiar with ubunutu in person...
when i got this netbook, i went to computer store.
one of tech service told me to get help from this Forum,
and 
i wen to another store, tech service told me that they will install ubuntu if u pay $200.
most people i know have Apple or Windows.



> **Olle Wiklund said:**
> **[COLOR=Red]/rofs[/COLOR]** ReadOnlyFileSystem

```
File system           1K-block    Used     Free   Used% Mounted on
[COLOR=Red]aufs                   4127424    382560   3535200  10% /
/dev/sdb1              5234948   5098336    136612  98% /cdrom
/dev/loop0              864512    864512         0 100% /rofs[/COLOR]

```/ is the file system root (equivalent to C: of Windows)
/cdrom is the live partition on the USB drive (the name shows the origin, the CD drive)

```
label unetbootindefault
menu label Default [COLOR=Red]Linux Mint 11 Gnome *persistent*[/COLOR]
```This is only a descriptive text
```
kernel /ubnkern
append initrd=/ubninit file=/cdrom/preseed/mint.seed boot=casper quiet splash[COLOR=Red] persistent [/COLOR]--
```This is how the unetbootin boot drive is told that it is persistent, and should use a casper-rw file on its root (/dev/sdb1 mounted on /cdrom)

I think all these instructions and descriptions are clear enough so that you can compare with what it looks like in your computer and make corrections if necessary, and succeed with your live USB session :-) Otherwise I strongly advice you to seek help at your place from someone that can sit at your computer and do it 'hands on'.

---

### Post by WasMeHere on 2011-12-13
> **Matrix01 said:**
> hard to find someone is familiar with ubunutu in person...
when i got this netbook, i went to computer store.
one of tech service told me to get help from this Forum,
and 
i wen to another store, tech service told me that they will install ubuntu if u pay $200.
most people i know have Apple or Windows.
You might find a computer club or something like that, where at least some of the members are interested and experienced in linux in general or Ubuntu in particular. It is worth trying :-)


But, OK, let continue this way.

So, what is the status now with persistent boot? Have you tried any of the boot options yet? I think you can find out how to enter them into the Unetbootin configuration file. Just look back some posts in this thread!

Do some trial and error with the boot options first one-at-a-time, then two-at-a-time to find out what is needed!

Good luck :-)

---

### Post by Matrix01 on 2011-12-14
tried each of boot options;

default,
try xubuntu w/o inst'.
inst'.
boot from 1st HD.

each outputs are exactly same;
busybox.........(ash).

what is 1st hard disk?


> **Olle Wiklund said:**
> You might find a computer club or something like that, where at least some of the members are interested and experienced in linux in general or Ubuntu in particular. It is worth trying :-)


But, OK, let continue this way.

So, what is the status now with persistent boot? Have you tried any of the boot options yet? I think you can find out how to enter them into the Unetbootin configuration file. Just look back some posts in this thread!

Do some trial and error with the boot options first one-at-a-time, then two-at-a-time to find out what is needed!

Good luck :-)

---

### Post by WasMeHere on 2011-12-14
> **Matrix01 said:**
> tried each of boot options;

default,
try xubuntu w/o inst'.
inst'.
boot from 1st HD.

each outputs are exactly same;
busybox.........(ash).

what is 1st hard disk?

1st hard disk is meant to boot your internal hard drive, but I know that is does not always work that way.

But I do not mean those alternatives when I wrote boot options. I mean that in the command line of the first alternative 'default', you edit the options at the end of the line:

```
....... -- # to be changed to (and remove 'quiet splash')
....... nomodeset --
....... noapic --
....... xforcevesa --
....... noapci --
....... irqpoll --
```
etc.

---

### Post by Matrix01 on 2011-12-14
error message; ----------------------- casper quiet splash...........
does not show up anymore...
always, busy box.................(ash.)



> **Olle Wiklund said:**
> 1st hard disk is meant to boot your internal hard drive, but I know that is does not always work that way.

But I do not mean those alternatives when I wrote boot options. I mean that in the command line of the first alternative 'default', you edit the options at the end of the line:

```
....... -- # to be changed to (and remove 'quiet splash')
....... nomodeset --
....... noapic --
....... xforcevesa --
....... noapci --
....... irqpoll --
```etc.

---

### Post by Matrix01 on 2011-12-14
Is persistent usb drive going to work if buntu is installed from this wubi?

---

### Post by WasMeHere on 2011-12-15
> **Matrix01 said:**
> Is persistent usb drive going to work if buntu is installed from this wubi?
Short answer: Yes!

Long answer: There are many ways to install a persistent usb drive. A common way is to use an iso-file of the version and flavour you like (in your case Xubuntu, I guess), and then use a tool to create the booting stuff. One of these tools is Unetbootin, which is in the repositories of Ubuntu. So yes, 'Wubibuntu' can make it as well as Windows. Maybe it is more convenient from Windows, because it is easier to get a bleeding edge version of Unetbootin with automatic installation of a persistent file.

The USB drive should be the same independent of Ubuntu, Wubibuntu or Windows, but I cannot guarantee that it works in every computer. It certainly works out of the box in most modern computers. It works with some tweaking (with those boot options we have discussed) in several other computers. But you have to use trial and error to find out how to tweak it.

Next step if it won't work would be to try other tools to make live USB drives. If you have a 'regular' read-only live system, it is easy to add the persistence (a casper-rw file and a call of it).

Third step might be to try another version (Xubuntu 10.04 LTS or 11.04 or Linux Mint 9 or 11 if Xubuntu 11.10 won't work). Or some other linux OS, for example Knoppix, which is made to run live (persistent if you like, but there is no regular installation).

---

### Post by Matrix01 on 2011-12-16
since xubuntu is running from wubi,
i like to install lubuntu in usb flash drive from wubi.
do i need to download Gparted?

> **Olle Wiklund said:**
> Short answer: Yes!

Long answer: There are many ways to install a persistent usb drive. A common way is to use an iso-file of the version and flavour you like (in your case Xubuntu, I guess), and then use a tool to create the booting stuff. One of these tools is Unetbootin, which is in the repositories of Ubuntu. So yes, 'Wubibuntu' can make it as well as Windows. Maybe it is more convenient from Windows, because it is easier to get a bleeding edge version of Unetbootin with automatic installation of a persistent file.

The USB drive should be the same independent of Ubuntu, Wubibuntu or Windows, but I cannot guarantee that it works in every computer. It certainly works out of the box in most modern computers. It works with some tweaking (with those boot options we have discussed) in several other computers. But you have to use trial and error to find out how to tweak it.

Next step if it won't work would be to try other tools to make live USB drives. If you have a 'regular' read-only live system, it is easy to add the persistence (a casper-rw file and a call of it).

Third step might be to try another version (Xubuntu 10.04 LTS or 11.04 or Linux Mint 9 or 11 if Xubuntu 11.10 won't work). Or some other linux OS, for example Knoppix, which is made to run live (persistent if you like, but there is no regular installation).

---

### Post by WasMeHere on 2011-12-16
> **Matrix01 said:**
> since xubuntu is running from wubi,
i like to install lubuntu in usb flash drive from wubi.
do i need to download Gparted?
Gparted is the tool to make partitions and file systems. It is a good idea to prepare the drive so that it is good before you install Lubuntu. And you install it from the repositories with
```
sudo apt-get install gparted
```
The easiest way is to use Gparted to

- make one primary partition of the whole flash drive
- format it to FAT32
- add flags boot, lba
- make a label (for example USB-OS)

and then use Unetbootin to install Lubuntu from its iso file to the flash drive.
```
sudo apt-get install unetbootin
```
Start without persistence. If it does not work, first try to tweak the live boot, then try some other tool or method. When it works, you can add persistence (the casper-rw file and the call to it).

Or maybe you would like to try Amjjawad's method first.

Good luck :-)

---

### Post by Matrix01 on 2011-12-17
is amjjawad's method same way i downloaded unetbootin and iso file?

> **Olle Wiklund said:**
> Gparted is the tool to make partitions and file systems. It is a good idea to prepare the drive so that it is good before you install Lubuntu. And you install it from the repositories with
```
sudo apt-get install gparted
```The easiest way is to use Gparted to

- make one primary partition of the whole flash drive
- format it to FAT32
- add flags boot, lba
- make a label (for example USB-OS)

and then use Unetbootin to install Lubuntu from its iso file to the flash drive.
```
sudo apt-get install unetbootin
```Start without persistence. If it does not work, first try to tweak the live boot, then try some other tool or method. When it works, you can add persistence (the casper-rw file and the call to it).

Or maybe you would like to try Amjjawad's method first.

Good luck :-)

---

### Post by WasMeHere on 2011-12-17
> **Matrix01 said:**
> is amjjawad's method same way i downloaded unetbootin and iso file?
Read the following thread.
[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=1872303[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1872303")

---

### Post by Matrix01 on 2011-12-18
how do u install gparted in xubuntu?
usb flash drive need to be formatted as FAT 32.

---

### Post by Matrix01 on 2011-12-18
hello,
i installed Lubuntu with unetbootin in usb flash drive.
it runs.

well,
this may break....
from my past experience...
with Natty and Xubuntu, 
they were running one time or so,
and 
error message.
they were installed form Win7 Starter.
this time,
from wubi...
and different distro,

see how this goes?

---

### Post by WasMeHere on 2011-12-18
> **Matrix01 said:**
> hello,
i installed Lubuntu with unetbootin in usb flash drive.
it runs.

well,
this may break....
from my past experience...
with Natty and Xubuntu, 
they were running one time or so,
and 
error message.
they were installed form Win7 Starter.
this time,
from wubi...
and different distro,

see how this goes?

I'm happy that your Lubuntu system is up and running :KS

It is easy to backup a persistent live system: Copy the casper-rw file to an external drive once a week!

If it breaks, and the flash drive itself is not damaged, *I'm almost sure that any error would be in the casper-rw file.* So you can overwrite it with a backed-up casper-rw file. It is very easy to restore the system.

But all the time you can start the live system without persistence, by selecting a start option without 'persistent' in the command line. So your live system should last much longer than one day.

Good luck :-)

[I]Edit: Compare your system to the one described in the following thread
[URL="http://ubuntuforums.org/showpost.php?p=11546560&postcount=5"][COLOR="RoyalBlue"][U]
http://ubuntuforums.org/showpost.php?p=11546560&postcount=5[/U][/COLOR][/URL][/I]

---

### Post by Matrix01 on 2011-12-18
thank you,

how do u find  casper-rw file, and copy it in an usb hdd?


and,
i opened thread in your link.
how do i open my lubuntu in terminal like that?



> **Olle Wiklund said:**
> I'm happy that your Lubuntu system is up and running :KS

It is easy to backup a persistent live system: Copy the casper-rw file to an external drive once a week!

If it breaks, and the flash drive itself is not damaged, *I'm almost sure that any error would be in the casper-rw file.* So you can overwrite it with a backed-up casper-rw file. It is very easy to restore the system.

But all the time you can start the live system without persistence, by selecting a start option without 'persistent' in the command line. So your live system should last much longer than one day.

Good luck :-)

[I]Edit: Compare your system to the one described in the following thread
[URL="http://ubuntuforums.org/showpost.php?p=11546560&postcount=5"][COLOR=RoyalBlue][U]
http://ubuntuforums.org/showpost.php?p=11546560&postcount=5[/U][/COLOR][/URL][/I]

---

### Post by Matrix01 on 2011-12-19
i am thinking to wipe win7 starter from internal hdd, and install win7 starter in an usb pen drive with iso file,
and YUMI or any kind of bootloader, 

and install ubuntu in internal disk.
i do not know if this works?

---

### Post by Matrix01 on 2011-12-19
recalled that we talked about checking iso file when xubuntu 11.10 stopped running from unetbootin.

i checked iso file of xubuntu 11.10 in win7 starter with winMD5sum.

iso file of xubuntu 11.10 is ok,
but
ubuntu 11.04 natty has problem.

how do u find if this was server error?

[ATTACH]209349[/ATTACH]

[ATTACH]209350[/ATTACH]

---

### Post by WasMeHere on 2011-12-19
> **Matrix01 said:**
> thank you,

how do u find  casper-rw file, and copy it in an usb hdd?


and,
i opened thread in your link.
how do i open my lubuntu in terminal like that?

The casper-rw file is in the root directory of the boot partition, mounted on /cdrom. So the full path/name is [FONT="Courier New"][SIZE="3"]/cdrom/casper-rw[/SIZE][/FONT]

At least it should be there if you have made the persistence according to the method described by me (similar to that of sudodus).

You open a terminal with ***ctrl + alt + t***

---

### Post by WasMeHere on 2011-12-19
> **Matrix01 said:**
> i am thinking to wipe win7 starter from internal hdd, and install win7 starter in an usb pen drive with iso file,
and YUMI or any kind of bootloader, 

and install ubuntu in internal disk.
i do not know if this works?

I have not done this kind of installation with Windows (only into hard disk drives except Bart PE). It probably works, but I suggest that you look for help from some place with experienced people.

It certainly works to install [lkx]ubuntu into the hard drive, and you can get help here to do that. By the way, I think you can do it yourself now with no or only a little help ;-)

---

### Post by WasMeHere on 2011-12-19
> **Matrix01 said:**
> recalled that we talked about checking iso file when xubuntu 11.10 stopped running from unetbootin.

i checked iso file of xubuntu 11.10 in win7 starter with winMD5sum.

iso file of xubuntu 11.10 is ok,
but
ubuntu 11.04 natty has problem.

how do u find if this was server error?

[ATTACH]209349[/ATTACH]

[ATTACH]209350[/ATTACH]
If the md5sum is OK, the download was OK. Otherwise, please download again, because it was probably a file transfer error! If you get the error again, select another source (mirror site)!

---

### Post by Matrix01 on 2011-12-19
> **Olle Wiklund said:**
> The casper-rw file is in the root directory of the boot partition, mounted on /cdrom. So the full path/name is [FONT="Courier New"][SIZE="3"]/cdrom/casper-rw[/SIZE][/FONT]

At least it should be there if you have made the persistence according to the method described by me (similar to that of sudodus).

You open a terminal with ***ctrl + alt + t***

is this the code which typed in terminal?

---

### Post by WasMeHere on 2011-12-19
> The casper-rw file is in the root directory of the boot partition, mounted on /cdrom. So the full path/name is /cdrom/casper-rw

At least it should be there if you have made the persistence according to the method described by me (similar to that of sudodus).

You open a terminal with [FONT="Courier New"][SIZE="3"]ctrl + alt + t[/SIZE][/FONT]

> **Matrix01 said:**
> is this the code which typed in terminal?
1. I forgot to tell that you should not use the casper-rw file when you are backing it up. That is do not run a persistent session, but start Lubuntu with another start alternative from the start menu, for example
"Try Lubuntu without installing"

2. You open the terminal with the key code on the background. If you are inside a program, it ***may*** have another interpretation that overrides starting a terminal. But maybe that was not what you wanted to know, maybe you wanted to know how to make it transparent, so I attach a screenshot showing that.

*. You can also see in the screenshot, that /cow mounted on / is smaller than 4 GB (smaller than the size of the casper-rw file), which indicates that it is not used; it is actually a volatile session using ram-drive.

---

### Post by Matrix01 on 2011-12-19
well..
how do u back up lubuntu?
confusing here.

> **Olle Wiklund said:**
> 1. I forgot to tell that you should not use the casper-rw file when you are backing it up. That is do not run a persistent session, but start Lubuntu with another start alternative from the start menu, for example
"Try Lubuntu without installing"

2. You open the terminal with the key code on the background. If you are inside a program, it ***may*** have another interpretation that overrides starting a terminal. But maybe that was not what you wanted to know, maybe you wanted to know how to make it transparent, so I attach a screenshot showing that.

*. You can also see in the screenshot, that /cow mounted on / is smaller than 4 GB (smaller than the size of the casper-rw file), which indicates that it is not used; it is actually a volatile session using ram-drive.

---

### Post by WasMeHere on 2011-12-20
> **Matrix01 said:**
> well..
how do u back up lubuntu?
confusing here.
*If you write down and then post the different lines in the Unetbootin menu, I can tell you which one to select for a persistent session and which one to select for a volative session. *

When you want to backup your personal files and settings (in the casper-rw file), you should run the volatile session (or run from another operating system, for example Windows or Wubi-Xubuntu). The important thing is that you are not using casper-rw at the same time as you back it up.

---

### Post by Matrix01 on 2011-12-20
ctrl+alt+t does not open terminal from xubuntu with wubi
terminal can be opened by clicking icon in tool bar...

> **Olle Wiklund said:**
> The casper-rw file is in the root directory of the boot partition, mounted on /cdrom. So the full path/name is [FONT=Courier New][SIZE=3]/cdrom/casper-rw[/SIZE][/FONT]

At least it should be there if you have made the persistence according to the method described by me (similar to that of sudodus).

You open a terminal with ***ctrl + alt + t***

---

### Post by Matrix01 on 2011-12-20
by the way,
Chrome stopped launching from Lubuntu,
and it was working after lubuntu was installed.
do u know code to type in terminal, and launch Chrome?

---

### Post by Matrix01 on 2011-12-20
this unetbootin is starnge...
i clicked touch pad,
but none of choice can not be selected from menu.

> **Olle Wiklund said:**
> *If you write down and then post the different lines in the Unetbootin menu, I can tell you which one to select for a persistent session and which one to select for a volative session. *

When you want to backup your personal files and settings (in the casper-rw file), you should run the volatile session (or run from another operating system, for example Windows or Wubi-Xubuntu). The important thing is that you are not using casper-rw at the same time as you back it up.

---

### Post by WasMeHere on 2011-12-20
> **Matrix01 said:**
> ctrl+alt+t does not open terminal from xubuntu with wubi
terminal can be opened by clicking icon in tool bar...

OK, the keyboard shortcuts are different between different flavours of Ubuntu.

---

### Post by WasMeHere on 2011-12-20
> **Matrix01 said:**
> by the way,
Chrome stopped launching from Lubuntu,
and it was working after lubuntu was installed.
do u know code to type in terminal, and launch Chrome?
Then you were too late to back it up :-(

By default ```
chromium-browser
``` is installed. Have you installed Chrome?

It is important to let the system write everything from RAM into the casper-rw file before you shut off the current or make some kind of hard reboot. Otherwise the custom settings and personal files stored in the casper-rw file might be lost or corrupted.

Usually there is a light emitting diode that shows the activity of the USB flash drive. Wait until it has reached 'idle', and the text on the screen indicates that the system is ready. For example, first logout, then shutdown. Press Enter when prompted, and continue waiting ...

If your settings are too damaged now, I suggest that you start with a new (empty) casper-rw file. But in the future, make frequent backup copies of it and simply overwrite a damaged version with the most recent backup :-)

---

### Post by WasMeHere on 2011-12-20
> **Matrix01 said:**
> this unetbootin is starnge...
i clicked touch pad,
but none of choice can not be selected from menu.
You select using the arrow keys (up) or (down). Maybe you have to set the keyboard in ***NumLock*** mode, to get the arrow key functionality.

*Edit: Or use an external keyboard (easy if you have a USB keyboard)*

---

### Post by linuxcraze on 2011-12-20
I think you don't need to go "sudo" while typing commands.
sudo is used perform superuser (or administrator as may be considered).

just go to Places>Computer(or any place you like). Then from the side pane you can mount your external drive. It'll ask for password.
Now for the help issue, you can search net very well, or on the command line type any command with "--help" option.

---

### Post by Matrix01 on 2011-12-20
i ran update from update manager last night, and it failed.

---

### Post by Matrix01 on 2011-12-20
nope,
I did not.
Chrome was installed on Lubuntu by default.


> **Olle Wiklund said:**
> Then you were too late to back it up :-(

By default ```
chromium-browser
``` is installed. Have you installed Chrome?

It is important to let the system write everything from RAM into the casper-rw file before you shut off the current or make some kind of hard reboot. Otherwise the custom settings and personal files stored in the casper-rw file might be lost or corrupted.

Usually there is a light emitting diode that shows the activity of the USB flash drive. Wait until it has reached 'idle', and the text on the screen indicates that the system is ready. For example, first logout, then shutdown. Press Enter when prompted, and continue waiting ...

If your settings are too damaged now, I suggest that you start with a new (empty) casper-rw file. But in the future, make frequent backup copies of it and simply overwrite a damaged version with the most recent backup :-)

---

### Post by WasMeHere on 2011-12-20
> **Matrix01 said:**
> i ran update from update manager last night, and it failed.
I found advice from An Sanct in the following thread
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=1885392_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1885392")
that it may be problem with updating. I did it anyway, and it worked for me, but maybe I was lucky.

---

### Post by Matrix01 on 2011-12-20
this PNY usb flash drive does not emit light.
i have another one, Sundisk usb pen drive, emitts light,
but this has only 1G.

how do i start new casper file?
i do not know where casper file is.



> **Olle Wiklund said:**
> Then you were too late to back it up :-(

By default ```
chromium-browser
``` is installed. Have you installed Chrome?

It is important to let the system write everything from RAM into the casper-rw file before you shut off the current or make some kind of hard reboot. Otherwise the custom settings and personal files stored in the casper-rw file might be lost or corrupted.

Usually there is a light emitting diode that shows the activity of the USB flash drive. Wait until it has reached 'idle', and the text on the screen indicates that the system is ready. For example, first logout, then shutdown. Press Enter when prompted, and continue waiting ...

If your settings are too damaged now, I suggest that you start with a new (empty) casper-rw file. But in the future, make frequent backup copies of it and simply overwrite a damaged version with the most recent backup :-)

---

### Post by WasMeHere on 2011-12-20
> **Matrix01 said:**
> nope,
I did not.
Chrome was installed on Lubuntu by default.
Try ```
chromium-browser
``` anyway. I think that is how to call it from a terminal window :-)

---

### Post by WasMeHere on 2011-12-20
Are you able to use activate arrow keys to move the high-light to different lines in the Unetbootin menu?

I think you should make a new casper-rw file and tweak your system very carefully, and make frequent backup copies. You can easily compress it using ```
gzip -c casper-rw > /some-path-on-external-HDD/casper-rw.gz
``` to save space.

---

### Post by WasMeHere on 2011-12-20
> **Matrix01 said:**
> this PNY usb flash drive does not emit light.
i have another one, Sundisk usb pen drive, emitts light,
but this has only 1G.

how do i start new casper-rw file?
i do not know where casper-rw file is.
Here are instructions how to make it.
[[COLOR="RoyalBlue"]_http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/_[/COLOR]]("http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/")

Copy it to the root directory (of your boot partition) on the USB flash drive. This is also described in the thread by *Sudodus* where An Sanct gave advice.

---

### Post by WasMeHere on 2011-12-20
I just found out that you can use
***ctrl + n*** to select the **n**ext line and
***ctrl + p*** to select the **p**revious line
in the Unetbootin menu, so you need no arrow keys.

---

### Post by Matrix01 on 2011-12-21
[ATTACH]209467[/ATTACH]
space used to preserve files across reboots.........................
will u tell me what this's for?


> **Olle Wiklund said:**
> Here are instructions how to make it.
[[COLOR=RoyalBlue]_http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/_[/COLOR]]("http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/")

Copy it to the root directory (of your boot partition) on the USB flash drive. This is also described in the thread by *Sudodus* where An Sanct gave advice.

---

### Post by Matrix01 on 2011-12-21
ctrl+alt+t works on Lubuntu 11.10 with unetbootin, 
but
they do not work on Xubuntu 11.10 with wubi...

> **Olle Wiklund said:**
> OK, the keyboard shortcuts are different between different flavours of Ubuntu.

---

### Post by Matrix01 on 2011-12-21
i always click shutdown first,
and
message shows up 'please remove installation device......then press enter'
do i need to log out before clicking shut down,
or
can i turn off the switch on netbook?

> **Olle Wiklund said:**
> Then you were too late to back it up :-(

By default ```
chromium-browser
``` is installed. Have you installed Chrome?

It is important to let the system write everything from RAM into the casper-rw file before you shut off the current or make some kind of hard reboot. Otherwise the custom settings and personal files stored in the casper-rw file might be lost or corrupted.

Usually there is a light emitting diode that shows the activity of the USB flash drive. Wait until it has reached 'idle', and the text on the screen indicates that the system is ready. For example, first logout, then shutdown. Press Enter when prompted, and continue waiting ...

If your settings are too damaged now, I suggest that you start with a new (empty) casper-rw file. But in the future, make frequent backup copies of it and simply overwrite a damaged version with the most recent backup :-)

---

### Post by WasMeHere on 2011-12-21
> **Matrix01 said:**
> [ATTACH]209467[/ATTACH]
space used to preserve files across reboots.........................
will u tell me what this's for?

It is an automatic way to create the persistent file (I guess file, it might be a partition, I'm using an older version of Unetbootin, where I have to make the casper-rw file manually). Use it if you like, but afterwards, try to identify what it is and where it is, so that you can easily back it up!

Otherwise use the method described by me.

---

### Post by WasMeHere on 2011-12-21
> **Matrix01 said:**
> ctrl+alt+t works on Lubuntu 11.10 with unetbootin, 
but
they do not work on Xubuntu 11.10 with wubi...
Yes, it's different. It depends on those responsible for each distribution what key bindings they make. But you can tweak it and add your own key bindings. I'm not very familiar with Xubuntu, so I don't know which menu to use for it. But you have a menu entry or start icon for the terminal.

---

### Post by WasMeHere on 2011-12-21
> **Matrix01 said:**
> i always click shutdown first,
and
message shows up 'please remove installation device......then press enter'
do i need to log out before clicking shut down,
or
can i turn off the switch on netbook?
Such things vary between computers. It depends on how the operating system co-operates with the computer hardware. You have to find out for yourself which is most convenient and safe. For me (***with live Lubuntu***) it is best to log out first and then shutdown (clicking on the screen) and wait ... , press Enter and wait (it will finally shut down and poweroff after the ram is copied to the casper-rw file).

With my installed systems it is always OK to shutdown directly (clicking on the screen).

---

### Post by Matrix01 on 2011-12-21
i am using unetbootin 565.
how much space do i need to put in box?

> **Olle Wiklund said:**
> It is an automatic way to create the persistent file (I guess file, it might be a partition, I'm using an older version of Unetbootin, where I have to make the casper-rw file manually). Use it if you like, but afterwards, try to identify what it is and where it is, so that you can easily back it up!

Otherwise use the method described by me.

---

### Post by Matrix01 on 2011-12-21
how do u make own key bindings?

> **Olle Wiklund said:**
> Yes, it's different. It depends on those responsible for each distribution what key bindings they make. But you can tweak it and add your own key bindings. I'm not very familiar with Xubuntu, so I don't know which menu to use for it. But you have a menu entry or start icon for the terminal.

---

### Post by WasMeHere on 2011-12-21
> **Matrix01 said:**
> i am using unetbootin 565.
how much space do i need to put in box?

The more you put there, the more space for applications programs, updates, configuration files. I think it is a good idea to keep personal files (documents, pictures, videos, music files etc) somewhere else (on your internal or external hard drive). I am not sure if this method can override the 4GB file size limit of FAT32. It costs very little to try, only your valuable time ;-)

---

### Post by Matrix01 on 2011-12-21
arrow keys work, and select menu.

default
help
try lubuntu w/o inst'
inst' 
check disk
boot from first hd.


> **Olle Wiklund said:**
> Are you able to use activate arrow keys to move the high-light to different lines in the Unetbootin menu?

I think you should make a new casper-rw file and tweak your system very carefully, and make frequent backup copies. You can easily compress it using ```
gzip -c casper-rw > /some-path-on-external-HDD/casper-rw.gz
``` to save space.

---

### Post by WasMeHere on 2011-12-21
> **Matrix01 said:**
> how do u make own key bindings?

Ask in a new thread for Xubuntu or Lubuntu (I know how to do it Ubuntu with gnome). But you might find a menu for it in 'Preferences' or 'Settings', so look around in the menu system for a while before posting a new thread.

---

### Post by Matrix01 on 2011-12-21
this error message popped up;
sorry the program "menu-cached" closed unexpectedly.

---

### Post by Matrix01 on 2011-12-21
i connected usb pen drive which has Lubuntu with unetbootin, 
and opened files,
found casper file folder.

---

### Post by WasMeHere on 2011-12-21
> **Matrix01 said:**
> arrow keys work, and select menu.

[COLOR="RoyalBlue"]default[/COLOR]
help
[COLOR="Red"]try lubuntu w/o inst'[/COLOR]
inst' 
check disk
boot from first hd.

In my version, I have added persistent to the [COLOR="RoyalBlue"]default[/COLOR] alternative, but not to any other alternative, so if you want to run Lubuntu without persistence (in order to backup the casper-rw file), you can start
[COLOR="Red"]try lubuntu w/o inst'[/COLOR]

I don't know how your system is set up, but to compare it to mine, refer to the thread by *sududus*
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=11546560&postcount=5_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11546560&postcount=5")
Look at the file [FONT="Courier New"][SIZE="3"]syslinux.cfg[/SIZE][/FONT]

---

### Post by WasMeHere on 2011-12-21
> **Matrix01 said:**
> this error message popped up;
sorry the program "menu-cached" closed unexpectedly.
???

---

### Post by WasMeHere on 2011-12-21
> **Matrix01 said:**
> i connected usb pen drive which has Lubuntu with unetbootin, 
and opened files,
found casper file folder.
You should look for a big file (the size you decided when running Unetbootin) and the name is not casper (because that name is already used by the directory), it is casper-rw or something else.

---

### Post by Matrix01 on 2011-12-21
this lubuntu is already running persistent,
even though default is selected.

> **Olle Wiklund said:**
> In my version, I have added persistent to the [COLOR=RoyalBlue]default[/COLOR] alternative, but not to any other alternative, so if you want to run Lubuntu without persistence (in order to backup the casper-rw file), you can start
[COLOR=Red]try lubuntu w/o inst'[/COLOR]

I don't know how your system is set up, but to compare it to mine, refer to the thread by *sududus*
[[COLOR=RoyalBlue]_http://ubuntuforums.org/showpost.php?p=11546560&postcount=5_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11546560&postcount=5")
Look at the file [FONT=Courier New][SIZE=3]syslinux.cfg[/SIZE][/FONT]

---

### Post by Matrix01 on 2011-12-21
typed 'chromium-browser' in terminal,
that does not work.

> **Olle Wiklund said:**
> Then you were too late to back it up :-(

By default ```
chromiumped-browser
``` is installed. Have you installed Chrome?

It is important to let the system write everything from RAM into the casper-rw file before you shut off the current or make some kind of hard reboot. Otherwise the custom settings and personal files stored in the casper-rw file might be lost or corrupted.

Usually there is a light emitting diode that shows the activity of the USB flash drive. Wait until it has reached 'idle', and the text on the screen indicates that the system is ready. For example, first logout, then shutdown. Press Enter when prompted, and continue waiting ...

If your settings are too damaged now, I suggest that you start with a new (empty) casper-rw file. But in the future, make frequent backup copies of it and simply overwrite a damaged version with the most recent backup :-)

---

### Post by Matrix01 on 2011-12-21
by the way,
i connected sun disk 1G usb pen drive, 
and error message tab showed up:
"error mounting, mount exited with exit code 16: mount can't open/ etc/mtab for writing: input/ output error.

how do i write in an usb pen drive or an usb HDD?

---

### Post by WasMeHere on 2011-12-21
> **Matrix01 said:**
> this lubuntu is already running persistent,
even though default is selected.
Yes, because you selected it when you created the USB boot drive with Unetbootin.

I suggest that you 'look behind the curtain', in order to understand how it is built. So look at the files! That way you can understand how to make a start-up alternative without persistance, in order to backup your casper-rw file. But you can also use your wubi-installed Xubuntu, mount the USB flash drive and then backup your casper-rw file.

The important thing is to make frequent backups, since it is easily corrupted. A standard installation is much more robust (and still it should be backed up at least once every month, but every time you have made something important or time-consuming).

---

### Post by WasMeHere on 2011-12-21
> **Matrix01 said:**
> typed 'chromium-browser' in terminal,
that does not work.

> 
Originally Posted by Olle Wiklund:
Then you were too late to back it up

By default
```
chromium[s]ped[/s]-browser
```
is installed. Have you installed Chrome?
 Did you try
```
chromium-browser
``` and it failed? Then you need to reinstall it.
```
sudo apt-get purge chromium-browser
sudo apt-get install chromium-browser
```
Or as I suggested earlier: Start from the beginning with a clean casper-rw file. Either by the method of *sududos* or wipe the USB drive and use Unetbootin to make it once more.

---

### Post by WasMeHere on 2011-12-21
> **Matrix01 said:**
> by the way,
i connected sun disk 1G usb pen drive, 
and error message tab showed up:
"error mounting, mount exited with exit code 16: mount can't open/ etc/mtab for writing: input/ output error.

how do i write in an usb pen drive or an usb HDD?
This should usually work. What system was running when you connected the 1G usb pen drive? Is it seen by fdisk? Please post the output of
```
sudo fdisk -lu
``` when the 1G usb pen drive is connected! Use whatever system can see it (Lubuntu or Xubuntu)!

If it was Lubuntu that could not see it, that is another sign that the persistence is damaged. In my Lubuntu 11.10 live system a second USB flash drive is automatically mounted (I tested it now to be sure).

---

### Post by Matrix01 on 2011-12-22
[ATTACH]209562[/ATTACH]
there pendrive is in xubuntu with wubi.
and,
here's output,

[ATTACH]209563[/ATTACH]

is fdisk flash drive?


> **Olle Wiklund said:**
> This should usually work. What system was running when you connected the 1G usb pen drive? Is it seen by fdisk? Please post the output of
```
sudo fdisk -lu
``` when the 1G usb pen drive is connected! Use whatever system can see it (Lubuntu or Xubuntu)!

If it was Lubuntu that could not see it, that is another sign that the persistence is damaged. In my Lubuntu 11.10 live system a second USB flash drive is automatically mounted (I tested it now to be sure).

---

### Post by Matrix01 on 2011-12-22
how do u install Opera browser?
there's no internet borwser is working on lubuntu,
so
i have to shut down, and go back and forth between xubuntu (wubi) and lubuntu (unetbootin.)

> **Olle Wiklund said:**
> Did you try
```
chromium-browser
``` and it failed? Then you need to reinstall it.
```
sudo apt-get purge chromium-browser
sudo apt-get install chromium-browser
```Or as I suggested earlier: Start from the beginning with a clean casper-rw file. Either by the method of *sududos* or wipe the USB drive and use Unetbootin to make it once more.

---

### Post by Matrix01 on 2011-12-22
back up?
you mean back up data which is stored
or
back up entire OS, Lubuntu

> **Olle Wiklund said:**
> Yes, because you selected it when you created the USB boot drive with Unetbootin.

I suggest that you 'look behind the curtain', in order to understand how it is built. So look at the files! That way you can understand how to make a start-up alternative without persistance, in order to backup your casper-rw file. But you can also use your wubi-installed Xubuntu, mount the USB flash drive and then backup your casper-rw file.

The important thing is to make frequent backups, since it is easily corrupted. A standard installation is much more robust (and still it should be backed up at least once every month, but every time you have made something important or time-consuming).

---

### Post by WasMeHere on 2011-12-22
see next post

---

### Post by WasMeHere on 2011-12-22
> **Matrix01 said:**
> [ATTACH]209562[/ATTACH]
there pendrive is in xubuntu with wubi.
and,
here's output,

[ATTACH]209563[/ATTACH]

Fdisk is the name of an old standard program, that can view and edit partitions. Read ```
man fdisk
``` for details.

Yes, you refer to the 1 GB pendrive. It is [FONT="Courier New"][SIZE="3"]/dev/sdc[/SIZE][/FONT] with the FAT32 partition [FONT="Courier New"][SIZE="3"]/dev/sdc1[/SIZE][/FONT]

Good, it is mounted and readable. I hope it is also writable, so that you can also save and delete files on the pendrive. In that case the pendrive and Xubuntu co-operate OK.

[FONT="Courier New"][SIZE="3"]/dev/sda[/SIZE][/FONT] is 160 GB and has four partitions (3 [COLOR="Red"]NTFS[/COLOR] and a very small FAT32 file systems). Is this your internal hard drive?

The device [FONT="Courier New"][SIZE="3"]/dev/sdb[/SIZE][/FONT] is skipped by fdisk. How come? Do you have a card reader, so that a flash card would get that device name? Or something else? What happens if you insert your USB HDD and run ```
sudo fdisk -lu
``` again?

---

### Post by WasMeHere on 2011-12-22
> **Matrix01 said:**
> how do u install Opera browser?
there's no internet borwser is working on lubuntu,
so
i have to shut down, and go back and forth between xubuntu (wubi) and lubuntu (unetbootin.)
I am afraid that your persistent Lubuntu USB system is broken, and suggest that you reinstall it with Unetbootin. That should be fairly easy. Then identify the file for persistence and make a backup of it (before it gets damaged). After that you can install Opera. I think it is easy to follow the instructions on the Opera web site. (I did it some years ago without problems, but I don't use it now, I use Firefox. Actually I installed Firefox into my persistent live Lubuntu.)

---

### Post by Matrix01 on 2011-12-22
after chromium was removed,
firefox was installed during this operation,
and
firefox works....


> **Olle Wiklund said:**
> I am afraid that your persistent Lubuntu USB system is broken, and suggest that you reinstall it with Unetbootin. That should be fairly easy. Then identify the file for persistence and make a backup of it (before it gets damaged). After that you can install Opera. I think it is easy to follow the instructions on the Opera web site. (I did it some years ago without problems, but I don't use it now, I use Firefox. Actually I installed Firefox into my persistent live Lubuntu.)

---

### Post by Matrix01 on 2011-12-22
[ATTACH]209565[/ATTACH]


QUOTE=Olle Wiklund;11557450]Fdisk is the name of an old standard program, that can view and edit partitions. Read ```
man fdisk
``` for details.

Yes, you refer to the 1 GB pendrive. It is [FONT=Courier New][SIZE=3]/dev/sdc[/SIZE][/FONT] with the FAT32 partition [FONT=Courier New][SIZE=3]/dev/sdc1[/SIZE][/FONT]

Good, it is mounted and readable. I hope it is also writable, so that you can also save and delete files on the pendrive. In that case the pendrive and Xubuntu co-operate OK.

[FONT=Courier New][SIZE=3]/dev/sda[/SIZE][/FONT] is 160 GB and has four partitions (3 exFAT and a very small FAT32 file systems). Is this your internal hard drive?

The device [FONT=Courier New][SIZE=3]/dev/sdb[/SIZE][/FONT] is skipped by fdisk. How come? Do you have a card reader, so that a flash card would get that device name? Or something else? What happens if you insert your USB HDD and run ```
sudo fdisk -lu
``` again?[/QUOTE]

---

### Post by WasMeHere on 2011-12-22
> **Matrix01 said:**
> back up?
you mean back up data which is stored
or
back up entire OS, Lubuntu
One advantage with a persistent live system is that everything is standard and read only except what is stored in the ***casper-rw*** file. So it is enough to make a copy of that file in order to backup the system :-) Or a compressed copy to save space.

---

### Post by Matrix01 on 2011-12-22
i tried to look up my thread in a long time ago.
they seem to be cut off.

---

### Post by WasMeHere on 2011-12-22
> **matrix01 said:**
> after chromium was removed,
firefox was installed during this operation,
and
firefox works....
:-)

---

### Post by WasMeHere on 2011-12-22
> **Matrix01 said:**
> i tried to look up my thread in a long time ago.
they seem to be cut off.
What is the problem? Can't you look back into your own thread:
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=1870877_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1870877")

---

### Post by Matrix01 on 2011-12-22
> **Olle Wiklund said:**
> :-)

do u still think this lubuntu  is broken?

---

### Post by WasMeHere on 2011-12-22
> **Matrix01 said:**
> [ATTACH]209565[/ATTACH]


[QUOTE=Olle Wiklund;11557450]Fdisk is the name of an old standard program, that can view and edit partitions. Read ```
man fdisk
``` for details.

Yes, you refer to the 1 GB pendrive. It is [FONT=Courier New][SIZE=3]/dev/sdc[/SIZE][/FONT] with the FAT32 partition [FONT=Courier New][SIZE=3]/dev/sdc1[/SIZE][/FONT]

Good, it is mounted and readable. I hope it is also writable, so that you can also save and delete files on the pendrive. In that case the pendrive and Xubuntu co-operate OK.

[FONT=Courier New][SIZE=3]/dev/sda[/SIZE][/FONT] is 160 GB and has four partitions (3 exFAT and a very small FAT32 file systems). Is this your internal hard drive?

The device [FONT=Courier New][SIZE=3]/dev/sdb[/SIZE][/FONT] is skipped by fdisk. How come? Do you have a card reader, so that a flash card would get that device name? Or something else? What happens if you insert your USB HDD and run ```
sudo fdisk -lu
``` again?[/QUOTE]

Yes, don't worry about the difficult text in the manual. It's good to know what is behind the curtains. Use ```
sudo fdisk -lu
``` to list partitions, but use ***gparted*** to edit partitions!

---

### Post by Matrix01 on 2011-12-22
[ATTACH]209567[/ATTACH]

is this what u talking about?

> **Olle Wiklund said:**
> You should look for a big file (the size you decided when running Unetbootin) and the name is not casper (because that name is already used by the directory), it is casper-rw or something else.

---

### Post by Matrix01 on 2011-12-22
i started posting thread in this forum in april,
clicked 'last' page,
and
there are no thread after october? 

> **Olle Wiklund said:**
> What is the problem? Can't you look back into your own thread:
[[COLOR=RoyalBlue]_http://ubuntuforums.org/showthread.php?t=1870877_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1870877")

---

### Post by WasMeHere on 2011-12-22
> **Matrix01 said:**
> do u still think this lubuntu  is broken?
Let us hop it is OK, the problem may be that we were confused. But it should be able to automount the 1GB pen drive in read-write mode (when you click on it in the file browser). Of course it should also be able to mount it using the ***mount*** (terminal command). Try again!

But the important thing is that ***it is easy to make it again*** with Unetbootin. And when you have found the file, ***it is easy to make a backup copy*** :-)

---

### Post by Matrix01 on 2011-12-22
is this the file?
[ATTACH]209568[/ATTACH]

> **Olle Wiklund said:**
> Let us hop it is OK, the problem may be that we were confused. But it should be able to automount the 1GB pen drive in read-write mode (when you click on it in the file browser). Of course it should also be able to mount it using the ***mount*** (terminal command). Try again!

But the important thing is that ***it is easy to make it again*** with Unetbootin. And when you have found the file, ***it is easy to make a backup copy*** :-)

---

### Post by Matrix01 on 2011-12-22
[ATTACH]209570[/ATTACH]
usb hdd is connected,
and
typed command,
output is like that,
Is this an internal hdd? 

> **Olle Wiklund said:**
> Yes, don't worry about the difficult text in the manual. It's good to know what is behind the curtains. Use ```
sudo fdisk -lu
``` to list partitions, but use ***gparted*** to edit partitions!

---

### Post by Matrix01 on 2011-12-22
this netbook has sd-mmc port.
is this a card reader?

> **Olle Wiklund said:**
> Yes, don't worry about the difficult text in the manual. It's good to know what is behind the curtains. Use ```
sudo fdisk -lu
``` to list partitions, but use ***gparted*** to edit partitions!

---

### Post by WasMeHere on 2011-12-22
> **Matrix01 said:**
> [ATTACH]209567[/ATTACH]

is this what u talking about?

Yes that's it :-) Now where is it located? In my case it is located in the root of the boot partition on the USB live Lubuntu drive (mounted on /cdrom). Run the command ```
df
``` when running the live session and post the result!

By the way, the SecureDigital drive in the same picture is probably /dev/sdb.

---

### Post by WasMeHere on 2011-12-22
> **Matrix01 said:**
> i started posting thread in this forum in april,
clicked 'last' page,
and
there are no thread after october?
I can read ***this*** thread without problems. Do you mean another thread?

---

### Post by Matrix01 on 2011-12-22
[attach]209571[/attach]




> **olle wiklund said:**
> yes that's it :-) now where is it located? In my case it is located in the root of the boot partition on the usb live lubuntu drive (mounted on /cdrom). Run the command ```
df
``` when running the live session and post the result!

By the way, the securedigital drive in the same picture is probably /dev/sdb.

---

### Post by Matrix01 on 2011-12-22
where are my other older threads from april?

> **Olle Wiklund said:**
> I can read ***this*** thread without problems. Do you mean another thread?

---

### Post by WasMeHere on 2011-12-22
> **Matrix01 said:**
> [ATTACH]209570[/ATTACH]
usb hdd is connected,
and
typed command,
output is like that,
Is this an internal hdd?
Good :KS

/dev/sda is the internal hard drive, almost certainly NTFS file system on 3 partitions (not exFAT, as I wrote the last time)

/dev/sdb in this case is a 1 TB drive, I assume the external drive, this one cannot be read by fdisk. Is it exFAT file system or some strange partition table (strange to linux, maybe something new by Microsoft)? (I have a faint memory of discussing exfat and re-formatting to ntfs long ago, and leaving space for persistent boot on it)

/dev/sdc in this case is the 8 GB USB boot drive with Lubuntu. Please show also the end of the output (scroll down) so that the partitions are shown. And add to that the output of ```
df
```

---

### Post by WasMeHere on 2011-12-22
> **Matrix01 said:**
> this netbook has sd-mmc port.
is this a card reader?
Yes, I think there should be a slot somewhere (usually in the front) to put in a flash card.

---

### Post by WasMeHere on 2011-12-22
> **Matrix01 said:**
> where are my other older threads from april?
Does it work to search with the tool at the top of the page like in the attached picture?

---

### Post by WasMeHere on 2011-12-22
> **Matrix01 said:**
> [attach]209571[/attach]

Something is wrong. ***df*** should definitely show something. Try ```
sudo df
```

---

### Post by Matrix01 on 2011-12-22
thank u,
i found them.

> **Olle Wiklund said:**
> Does it work to search with the tool at the top of the page like in the attached picture?

---

### Post by Matrix01 on 2011-12-22
here's end of output;

[ATTACH]209574[/ATTACH]

and out put of df;

[ATTACH]209575[/ATTACH]



> **Olle Wiklund said:**
> Good :KS

/dev/sda is the internal hard drive, almost certainly NTFS file system on 3 partitions (not exFAT, as I wrote the last time)

/dev/sdb in this case is a 1 TB drive, I assume the external drive, this one cannot be read by fdisk. Is it exFAT file system or some strange partition table (strange to linux, maybe something new by Microsoft)? (I have a faint memory of discussing exfat and re-formatting to ntfs long ago, and leaving space for persistent boot on it)

/dev/sdc in this case is the 8 GB USB boot drive with Lubuntu. Please show also the end of the output (scroll down) so that the partitions are shown. And add to that the output of ```
df
```

---

### Post by WasMeHere on 2011-12-22
> **Matrix01 said:**
> here's end of output;

[ATTACH]209574[/ATTACH]

and out put of df;

[ATTACH]209575[/ATTACH]
Well, there is only one partition on the 8 GB USB drive, in this case
/dev/sdc1. So the casper-rw file must be there. I think it is damaged, since you don't get any output from ***df***

Anyway, in order to find the file, if you mount the 'Lubuntu USB drive' from xubuntu, and browse it you should file the file soon. You can also look for it from the terminal window with the command to find the biggest file size in kB (biggest last in the list) in and below the current directory (dot)
```
sudo find . -type f -exec du -a {} \; |sort -n
```
If mounted like in my Lubuntu live USB drive:
```
sudo find /cdrom -type f -exec du -a {} \; |sort -n
```
or from Xubuntu
```
sudo find /media -type f -exec du -a {} \; |sort -n
```

---

### Post by Matrix01 on 2011-12-22
how do u make desktop short cut of home folder?

---

### Post by Matrix01 on 2011-12-22
typed the first command, and output goes very long.....i think this is xubuntu withj wubi,
[ATTACH]209585[/ATTACH]

and
next,
typed 3rd command,
there's pendrive, casper-rw,

[attach]209584[/attach]
and typed 2nd one,

[ATTACH]209586[/ATTACH]



> **olle wiklund said:**
> well, there is only one partition on the 8 gb usb drive, in this case
/dev/sdc1. So the casper-rw file must be there. I think it is damaged, since you don't get any output from ***df***

anyway, in order to find the file, if you mount the 'lubuntu usb drive' from xubuntu, and browse it you should file the file soon. You can also look for it from the terminal window with the command to find the biggest file size in kb (biggest last in the list) in and below the current directory (dot)
```
sudo find . -type f -exec du -a {} \; |sort -n
```if mounted like in my lubuntu live usb drive:
```
sudo find /cdrom -type f -exec du -a {} \; |sort -n
```or from xubuntu
```
sudo find /media -type f -exec du -a {} \; |sort -n
```

---

### Post by WasMeHere on 2011-12-23
> **Matrix01 said:**
> how do u make desktop short cut of home folder?
Often you right-click on the desktop background and select 'program launcher' or something of that meaning, and fill in the forms that pop up. It differs between different flavours of Ubuntu. You can also do it via some configuration menu.

Normally the file browser starts in the home folder, so you need no short-cut, only start it from its icon on the desktop or panel. Also, normally the terminal window starts in the home folder.

In terminal, [FONT="Courier New"][SIZE="3"]cd[/SIZE][/FONT] (without any path specified) will bring you to your home folder, and **~** (tilde) is short for your home folder, meaning the same as /home/$USER.
example: ```
cd ~/Desktop
```

---

### Post by WasMeHere on 2011-12-23
> **Matrix01 said:**
> typed the first command, and output goes very long.....i think this is xubuntu withj wubi,
[ATTACH]209585[/ATTACH]

and
next,
typed 3rd command,
there's pendrive, casper-rw,

[attach]209584[/attach]
and typed 2nd one,

[ATTACH]209586[/ATTACH]
OK, that was enough to find it. And it is like in my USB flash drive Lubuntu. The persistent file's name is casper-rw. It is located in the root directory of the boot partition of that drive. In your case the only partition. When mounted by Xubuntu the full path is
```
/media/PENDRIVE/casper-rw
```
I think that if you boot Lubuntu from the USB pen drive, it will be
```
/cdrom/casper-rw
``` because it is like that in my Lubuntu system. But I am not sure, because it is made by another version of Unetbootin.

Now you know where your casper-rw file is, and you can make a backup copy of it to the internal hard disk drive :-) Use Xubuntu to back it up!

But I still think that there is something wrong with your persistent live system, so I recommend that you start all over with Unetbootin.

---

### Post by Matrix01 on 2011-12-23
output is like this;
[ATTACH]209610[/ATTACH]

> **Olle Wiklund said:**
> OK, that was enough to find it. And it is like in my USB flash drive Lubuntu. The persistent file's name is casper-rw. It is located in the root directory of the boot partition of that drive. In your case the only partition. When mounted by Xubuntu the full path is
```
/media/PENDRIVE/casper-rw
```I think that if you boot Lubuntu from the USB pen drive, it will be
```
/cdrom/casper-rw
``` because it is like that in my Lubuntu system. But I am not sure, because it is made by another version of Unetbootin.

Now you know where your casper-rw file is, and you can make a backup copy of it to the internal hard disk drive :-) Use Xubuntu to back it up!

But I still think that there is something wrong with your persistent live system, so I recommend that you start all over with Unetbootin.

---

### Post by Matrix01 on 2011-12-23
[ATTACH]209611[/ATTACH]
how do u use this?

> **Olle Wiklund said:**
> Often you right-click on the desktop background and select 'program launcher' or something of that meaning, and fill in the forms that pop up. It differs between different flavours of Ubuntu. You can also do it via some configuration menu.

Normally the file browser starts in the home folder, so you need no short-cut, only start it from its icon on the desktop or panel. Also, normally the terminal window starts in the home folder.

In terminal, [FONT=Courier New][SIZE=3]cd[/SIZE][/FONT] (without any path specified) will bring you to your home folder, and **~** (tilde) is short for your home folder, meaning the same as /home/$USER.
example: ```
cd ~/Desktop
```

---

### Post by WasMeHere on 2011-12-23
> **Matrix01 said:**
> output is like this;
[ATTACH]209610[/ATTACH]

It is not an executable file. But maybe it works better to list it with
```
ls -l /media/PENDRIVE/casper-rw
```

---

### Post by WasMeHere on 2011-12-23
> **Matrix01 said:**
> [ATTACH]209611[/ATTACH]
how do u use this?
You 'move' = 'change directory' to your Desktop directory, where you have the files and links that are visible on the desktop as icons.
```
ls -l
``` lists the files. You can navigate the terminal to any directory with the [FONT="Courier New"][SIZE="3"]cd[/SIZE][/FONT] command.

---

### Post by Matrix01 on 2011-12-24
[attach]209665[/attach]

---

