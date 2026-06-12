---
title: "Grub Error 25 after new install"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by NooNoo on 2009-04-02
Hi after a recent upgrade of my machine i decided to do a fresh install of everything, here is my setup.

pentium 4 3ghz
2gb ram
ide1 master - 80gb windows xp media center (fresh install)
ide1 slave - dvd rw
ide2 master - 80gb (data disc no OS)
ide2 slave - 80gb (data disc no OS)
ide3 master - 80gb (S-ata Ubuntu 8.1)

after getting xp up and running i wanted to install Ubuntu on the sata drive this went ok upto the reboot and then grub gives the "error 25" at stage 1.5

when installing Ubuntu i told it to put grub on hd0 was this wrong?

i cant even get XP to boot by running live disk and telling to boot from first HD.

is this because ive put Ubuntu on the SATA drive?

All help will be greatly appreciated as i haven't had linux for a while and want to get back into using it again.

 /boot/grub/device.map reads
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd

i cannot find grub.conf

my menu.lst is as follows
title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		565ea241-2dac-4b20-8b21-92cdd55d2454
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=565ea241-2dac-4b20-8b21-92cdd55d2454 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		565ea241-2dac-4b20-8b21-92cdd55d2454
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=565ea241-2dac-4b20-8b21-92cdd55d2454 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		565ea241-2dac-4b20-8b21-92cdd55d2454
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by sahabcse on 2009-04-02
Hi

Try to reload the grub. Please follow below url

[http://sahabm.blogspot.com/2009/01/grub-fix-windows.html](http://sahabm.blogspot.com/2009/01/grub-fix-windows.html)
[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)

---

### Post by 73ckn797 on 2009-04-02
In Applications/Accessories/Terminal enter:
```
blkid
```

This will reveal the drive "uuid". Make certain where it has been installed. The grub lists the uuid of each drive. Does that match what menu.lst shows?

---

### Post by NooNoo on 2009-04-02
ok,
blkid reports
/dev/sda1: UUID="72947B9D947B6311" TYPE="ntfs" 
/dev/sdb1: UUID="4890495F9049549A" LABEL="Data" TYPE="ntfs" 
/dev/sdc1: UUID="EEC0E8E0C0E8AFCF" LABEL="Freecom" TYPE="ntfs" 
/dev/sdd1: UUID="565ea241-2dac-4b20-8b21-92cdd55d2454" TYPE="ext3" 
/dev/sdd5: TYPE="swap" UUID="ddaf12e9-05b2-4ade-b9a9-3b06d15616bb" 
/dev/loop0: TYPE="squashfs" 

and from the grub fix grub tells me its installed on hd3 but it cant mount hd0 to put it there (probably coz it ntfs)

---

### Post by ronparent on 2009-04-02
On first examination your menu.lst appears to be correct to boot (hd3) from (hd0). To address your questions direct:

Q. when installing Ubuntu i told it to put grub on hd0 was this wrong?

A. Correct for booting from your bios selected boot drive. This is what you want if you want to load from the grub menu.

Q. i cant even get XP to boot by running live disk and telling to boot from first HD.

A. This in because the grub boot loader has overwritten the boot sector on (hd0). Once the grub loader (on hd0) can find grub (on hd3) everything shoud work fine.

Q. is this because ive put Ubuntu on the SATA drive?

A. Your menu.lst should find your linux drive as id'd by uuid. The problem is the grub bootloader is not finding grub itself (or menu.lst)

From the ubuntu live cd try from the terminal commands as follows (leave out everything including and after ##):

from the terminal prompt: grub  ## to load grub

grub> find /boot/grub/stage1  ## to verify location of your linux installation
grub> root (hd3,1) ## or whaever the output of above command to find your linux
grub> setup (hd0) ## to rewrite your grub menu.lst and at least verify that stage1a is found

This should get you up and running - usless something more subtle is at work.

---

### Post by NooNoo on 2009-04-02
i tried this
> from the terminal prompt: grub ## to load grub

grub> find /boot/grub/stage1 ## to verify location of your linux installation
grub> root (hd3,1) ## or whaever the output of above command to find your linux
grub> setup (hd0) ## to rewrite your grub menu.lst and at least verify that stage1a is found

This should get you up and running - usless something more subtle is at work. 

it wrote grub back to the disk ok but on restarting i still get the same error.
is there any error logging for grub that might pinpoint this problem???

---

### Post by NooNoo on 2009-04-02
i have run the boot info script and attatched the results.txt to this post

---

### Post by ronparent on 2009-04-02
Your results.txt appears to contain conflicting infor???
Boot info summary says:
=> Grub.97 is installed in the MBR of /dev/sdd and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
This statement could work only if hdd is the bios selectred boot drive

Disk /dev/sdd: 80.0 GB, 80000000000 bytes says:
/dev/sdd1    *             63   149,790,059   149,789,997  83 Linux
/dev/sdd2         149,790,060   156,248,189     6,458,130   5 Extended
/dev/sdd5         149,790,123   156,248,189     6,458,067  82 Linux swap / Solaris

Your grub, from the first statement above appears to be looking at hd3,1 as root. Actully root is hd3,0 above. Is this what you entered for 'root (hd3,0)' under the grub prompt? That is where grub is. 
i.e. grub> root (hd3,0)
     grub> setup (hdo)

This is not material to your problem, but did you actually reinstall ubuntu? Your uuid is different from your initial post. It seems that your initial install was correct as is the current. The problem appears to be centered on the grub boot loader on hd0 finding the root on hd3,0 to load the grub menu. Once this works you should be in business - providing that you leave hd0 as the bios selected boot device.

---

### Post by NooNoo on 2009-04-03
Ok a little explanation of what i have been doing and current state of affairs.

the inconsistencies shown in the previous post are due to changes in the bios settings for sata and pata working together (more likely to work) this changed the uuid's for the drives (or maybe just the sata i cant remeber)
also i changed the boot order to be the sata drive first (the one containing Linux)

next i unplugged all disks but the sata

then when booting of live disk i did
grub> find /boot/grub/stage1
this reported hd0,0
grub> root (hd0,0)
grub> setup(hd0)

on restart this brought up the grub menu and allowed booting from Linux(which i'm currently using)

after this i plugged all drives back in, still able to boot linux and can mount all drives.

OK SO FAR
when trying to load windows on restart i get "cannont find NTLDR + NTDETECT" error message

if i unplug the other drive and i only boot the windows disk i get 
grub stage 1.5 error 21

If i was to do fixmbr + fixboot for this will i loose grub again? 
Or is this from the previous install of Linux when grub was told to install to hd0?

Here's the weird part in Linux
grub> find /boot/grub/stage1
shows
Error 15: File not found

attatched is the latest bootinfo results

in the menu.lst the edited (#out) entries are due to looking at the following post
[http://ubuntuforums.org/showthread.php?t=813628&highlight=boot+info+script]("http://ubuntuforums.org/showthread.php?t=813628&highlight=boot+info+script")

Sorry for the marathon post but everything has changed since the begining

---

### Post by meierfra. on 2009-04-03
Set you bios to boot from the Ubuntu drive.  The windows item on menu.lst depends on the exact position of your Windows drive in  the boot order in the bios. To determine the positions, press "c" at the grub menu to get to the grub command line.

Type

```
geometry (hd0)
geometry (hd1)
geometry (hd2)
geometry (hd3)
geometry (hd4)
```


This will display the partitions on each of  your hard drives. "(hd0)" will be the ubuntu drive. You can distinguish the three other drives by their size (given in sectors). Your XP drive is the smallest one (15630148 sectors). Say XP is on (hdX), where X is some number.

Press "esc" to get back to the grub menu. Select the Windows entry  and press "e".  Change all the 2's to X (that is to the number you got from  the geometry commands) (to change one  the 2's, select that line, press "e", change the 2's  to X" and press "enter".

Once you changed all the 2's, press "b" to boot into Window.

If this boots  you into "XP" just edit menu.lst accordingly.
If this did not work, report any error messages you got.

---

### Post by ronparent on 2009-04-03
This install is getting difficult to follow. 

But as I read it windows executables (NTLSR etc) are on sda1 - (hd0,0). 
The ubuntu install which includes grub is located on sdd1 - (hd3,0)

If grub is configured correctly then you are chailoading from root (hd3,0) to (hd0,0)

For the command to load windows in menu.lst try:

title       Windows XP Media Center Edition (hd0)
rootnoverify     (hd3,0)
#root		(hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1

My memory od how chainloading works could be imperfect, so anyone is welcome to correct me. Meanwhile i'll research.

---

### Post by NooNoo on 2009-04-03
SUCCESS!!!!!!!!!!!!!!!

root (hd1,0) was needed which makes sense really as this is the second disk in the bios.

my great thanks to you both, my wife will be happy now as well as she can use the computer again.

---

### Post by meierfra. on 2009-04-04
> SUCCESS!!!!!!!!!!!!!!!

Great. Have fun with XP and Ubuntu.

---

### Post by Doug Shaver on 2009-05-15
> **sahabcse said:**
> Hi

Try to reload the grub. Please follow below url

[http://sahabm.blogspot.com/2009/01/grub-fix-windows.html](http://sahabm.blogspot.com/2009/01/grub-fix-windows.html)
[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)

I tried installing Ubuntu in dual-boot configuration on a laptop with Vista. After the installation finished, I tried rebooting and got the error 25 message.

Your first link does not help me because I do not have the Vista installation CD. The second link seems inapplicable because I am not adding Windows to Ubuntu but vice versa.

Furthermore, my laptop now will not boot from the Ubuntu installation CD. I gets as far as the screen with the Ubuntu logo and the progress bar, and the progress bar just freezes.

---

