---
title: "VFS error"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by indiekid97 on 2009-01-24
Thanks in advance to all who reply,

Yesterday, I pulled my new Asus laptop out of the box and proceeded to install Ubuntu 8.10 Desktop Edition. The laptop came pre loaded with Vista64 which  intend to keep on there for the sole purpose of gaming.
The laptop's specs are as follows:
2.23Ghz Core 2 Duo
4GB of RAM
1GB Nvidia Geforce 9600M GS
300GB HDD

 On my first attempt at using the Live CD, the desktop froze before I could get to the install screen. After waiting 30 minutes, I did a hard reset.

Upon rebooting, I chose the "Install Ubuntu" option instead of loading up the Live session. Everything went fine, it ran a little more slowly than I had remembered on my old, outdated Pentium M machine. This spiked my curiosity, but I dismissed it as a matter of perception. After setting up the partitioner as follows:
sda1 (10GB-NTFS): Windows pagefile (partitioned as such out of the box)
sda2(70GB-NTFS): Vista
sda3(80GB-ext3):Ubuntu
sda4(150GB): Data

I continued the installation, upon reaching the progress bar, I went to make no coffee, foreseeing no problems. When I returned I was greeted by a black background running a loop of the following text:
```
VFS: busy inodes on changed media
VFS: busy inodes on changed media
VFS: busy inodes on changed media
VFS: busy inodes on changed media
VFS: busy inodes on changed media
VFS: busy inodes on changed media
VFS: busy inodes on changed media
VFS: busy inodes on changed media
wlan0: associated
wlan0L disassociated by local choice
```

Baffled, I let the loop run overnight. Upon waking up, I killed it to find that no OS would boot. I have installed Ubuntu at least 20 times before, and have never had such trouble. Any and all help will be greatly appreciated.

~indie

---

### Post by indiekid97 on 2009-01-24
Bump

---

### Post by albinootje on 2009-01-24
> **indiekid97 said:**
>  Yesterday, I pulled my new Asus laptop out of the box and proceeded to install Ubuntu 8.10 Desktop Edition.

Can you :
1) Provide us with the type of Asus laptop ?
2) Boot with the various boot options as described here :
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by indiekid97 on 2009-01-24
1. Of course, I didn't include the model number because I assumed it would just lead you to the specs:
Asus Model X83VM-X1

2. I'll give the boot options a try and let you know the results

EDIT: After scrolling though the boot options, nothing jumps out at me as obviously useful, I have looked around the web but have failed to find a solution.

---

### Post by albinootje on 2009-01-25
> **indiekid97 said:**
> 
Asus Model X83VM-X1

2. I'll give the boot options a try and let you know the results

EDIT: After scrolling though the boot options, nothing jumps out at me as obviously useful, I have looked around the web but have failed to find a solution.

Thanks for the model type!

I'm pointing you to the boot options page because that can help in case of a BIOS bug, some irq conflict, or a kernel bug or a combination of those. Not trying any of them is certainly not going to get us any further.

And some bad news if you really want Linux on this laptop :
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1028090](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1028090)
[http://www.phoronix.com/forums/showthread.php?p=57378](http://www.phoronix.com/forums/showthread.php?p=57378)

Both posters in those two threads returned the laptop.

---

### Post by albinootje on 2009-01-25
You can try this and see how it goes :
[https://bugs.launchpad.net/fedora/+source/linux/+bug/172937/comments/27](https://bugs.launchpad.net/fedora/+source/linux/+bug/172937/comments/27)

> 
I went into BIOS and changed the IDE settings to COMPATIBILITY MODE. Viola! It worked. Hope this helps someone else out.


---

### Post by indiekid97 on 2009-01-25
I'm determine to make it work, so I'll just hae to keep trying. Thank you for the links, I never thought to cross check the model with Linux errors
*faceplam*
I'll repost in a few hours when I can test out that BIOS setting

---

### Post by indiekid97 on 2009-01-25
After trying the IDE compatibility mode, I can assure you that it only causes more problems.  Ubuntu refuses to even boot int a live session with this setting enabled.
I'm still searching the web, but returning the laptop really isn't an option unfortunately...

EDIT: I have found that the error is caused by a firmware issue which causes the DVD drive to unmount after spin down, which would obviously impead the boot process. I have spoken with an openSUSE user who used a USB drive to get around this problem, however, he claims that the IDE BIOS compatibility mode allowed him to use the DVD burner after install. I'll edit this post with the results when I am finished attempting this method.


EDIT: After using a USB key to install,  can confirm that the OS runs fine :] If you're having trouble booting from USB, you must enter the BIOS (mash F2 on this model) and change the HDD boot order. NOT the boot priority, this will only boot from CD, as AMI BIOS considers a USB key another HDD. The setting can be found under Boot>Boot Hard Drive Setting (or some such)
I emailed Asus about the issue, bu I just received a reply in broken English stating that they only support Windows Vista.

---

### Post by dreamingdarkness on 2009-01-29
I have the same ASUS laptop, and same issue when I tried to install Ubuntu on its own partition/swap/etc.
I have everything installed and working great from a Wubi install except for Ubuntu insisting on running fsck every other boot-up or so. 

But I so very much wanted to have actual options for when I eventually break Vista. I hate relying on it to load my Linux!
I will have to give the USB install a try tomorrow.

indiekid97, what USB disk loader setup did you use? And is your dvd/cd-rom working after the install? I wasn't able to get it to work even on the Wubi install, as it decided it had no disk in it at all times and I had to reboot back into Vista to even get the disk out. The only major point of frustration for me with it so far, but it looks more and more like a doozy.

Unfortunately, return isn't an option for me either.
Cheap Vista-only firemware makes Homer something something...
Echoes of *facepalm* here.

---

### Post by albinootje on 2009-01-29
> **dreamingdarkness said:**
> I have the same ASUS laptop, and same issue when I tried to install Ubuntu on its own partition/swap/etc.
I have everything installed and working great from a Wubi install except for Ubuntu insisting on running fsck every other boot-up or so. 


Perhaps you used ext2 instead of ext3 ?
Can you post your :
```

cat /etc/fstab
sudo fdisk -l

```

---

### Post by dreamingdarkness on 2009-01-29
albinootje - since its a Wubi install, I think its actually still formatted as NTFS. The fdisk -l will show a Linux and Linux swap partition, but those are where I failed trying to install from CD for a native 64bit install (whereas the Wubi is a 32bit). 
The current Ubuntu install is on sda6:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd50fcf61

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10240000   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        1275       15428   113683452    7  HPFS/NTFS
/dev/sda3           15428       20732    42600448    6  FAT16
/dev/sda4           20732       38914   146043904+   f  W95 Ext'd (LBA)
/dev/sda5           20732       26166    43643900    7  HPFS/NTFS
/dev/sda6           26166       29480    26623992    7  HPFS/NTFS
/dev/sda7           29480       37766    66558976   83  Linux
/dev/sda8           37767       38914     9214976   82  Linux swap / Solaris
```

I am currently split on the idea of trying to move the current install to sda7, running sda8 as it's swap, I've got the lvpm tool installed that should be able to strip a Wubi install over to a real on-disk install. If I can't get the DVD/CD drive working, I'll have to do any further installs from USB. Silly buggy DVD firmware.

---

