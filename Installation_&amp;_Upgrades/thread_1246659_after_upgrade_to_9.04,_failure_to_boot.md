---
title: "after upgrade to 9.04, failure to boot"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by jvtroll on 2009-08-22
Hi,
I recently decided to upgrade from 8.10 to 9.04 (using the upgrade button in the update manager).  Now my computer hangs on the ubuntu splace screen then I get the following error (more or less):
"gave up waiting for root device. . . . Alert! /dev/disk/by-uuid/c881ed--4fbo-9c3b-731ec6749ell does not exist.  Dropping to a shell"

I had to write this down and then hand type it in because I don't know how to do a screen capture in this shell - so I may have gotten a character or two wrong in that file name.

I have tried starting in various 'safe' modes but have been unsuccessful.  I have now booted from a liveCD and was able to determine that most (if not all) personal files are intact and I have backed up everything I could find - except all my MythTV recordings which I don't have enough space for on my other drives.  I was all set to do a clean install, but the 9.04 installer stated that 9.04 was already installed.  Which got me thinking I could maybe save the orignal installation and my MythTV recordings while I am at it.  

Anyone have any idea how to fix this or should I just do a clean install? I am still quite a linux newb, so please go easy on me.
Thanks in advance for any help.

---

### Post by nhanquy on 2009-08-22
> **jvtroll said:**
>  . Alert! /dev/disk/by-uuid/c881ed--4fbo-9c3b-731ec6749ell does not exist.  Dropping to a shell"


Most likely the UUID has been changed. Use Gparted (Partition Editor) from the live CD to find out the correct UUID(by clicking on the partition).
Replace the above UUID with the new UUID in the file /boot/grub/menu.lst

Good luck!

---

### Post by jvtroll on 2009-08-22
So Gparted shows the following UUID:

35c881ed-5182-4fb0-9c3b-731ec6749e11

This is the same as the one that the boot error states does not exist.

Any other ideas?

---

### Post by jvtroll on 2009-08-22
anyone?

---

### Post by stlsaint on 2009-08-22
are you able to roll back to 8.04 kernel?

---

### Post by jvtroll on 2009-08-22
I don't know.  How does one roll back to an older kernel?  I never used 8.04 - started out with 8.10.

---

### Post by stlsaint on 2009-08-22
system>adin?start-up manager...then look at boot options and see if you have another kernel to choose from in there!! please post results of /boot/grub/menu.lst cmd


sudo gedit /boot/grub/menu.lst

---

### Post by nhanquy on 2009-08-22
> **jvtroll said:**
> So Gparted shows the following UUID:

35c881ed-5182-4fb0-9c3b-731ec6749e11

This is the same as the one that the boot error states does not exist.

Any other ideas?

Mine menu.lst  has:

<CODE>
title           Ubuntu 9.04, kernel 2.6.28-15-generic
uuid           ABCD
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=ABCD ro quiet splash
initrd          /boot/initrd.img-2.6.28-15-generic
quiet
</CODE>

so you have to look as your menu.lst to see if it has something similliar to that or not (You can mount the partittion with the liveCD)
 
make sure you have /boot/vmlinuz-.....  /boot/initrd.img....in there too!

---

### Post by jvtroll on 2009-08-22
HI Guys,
I think you are both asking for the same thing.  I tried starting from other kernels from the grub start up menu (including the various recovery modes).  Below is the contents of my my boot/grub/menu.1st file.  What I notice is that despite it saying Ubuntu 9.04, the kernel is different from the one posted by nhanquy.  stlsaint: Running here on the liveCD I was not able to find a program called 'start-up manager' either in the system/admin or system/preferences menus. 

<code>
title        Ubuntu 9.04, kernel 2.6.27-14-generic
uuid        35c881ed-5182-4fb0-9c3b-731ec6749e11
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=35c881ed-5182-4fb0-9c3b-731ec6749e11 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
uuid        35c881ed-5182-4fb0-9c3b-731ec6749e11
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=35c881ed-5182-4fb0-9c3b-731ec6749e11 ro  single
initrd        /boot/initrd.img-2.6.27-14-generic

title        Ubuntu 9.04, kernel 2.6.27-13-generic
uuid        35c881ed-5182-4fb0-9c3b-731ec6749e11
kernel        /boot/vmlinuz-2.6.27-13-generic root=UUID=35c881ed-5182-4fb0-9c3b-731ec6749e11 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-13-generic (recovery mode)
uuid        35c881ed-5182-4fb0-9c3b-731ec6749e11
kernel        /boot/vmlinuz-2.6.27-13-generic root=UUID=35c881ed-5182-4fb0-9c3b-731ec6749e11 ro  single
initrd        /boot/initrd.img-2.6.27-13-generic

title        Ubuntu 9.04, kernel 2.6.27-12-generic
uuid        35c881ed-5182-4fb0-9c3b-731ec6749e11
kernel        /boot/vmlinuz-2.6.27-12-generic root=UUID=35c881ed-5182-4fb0-9c3b-731ec6749e11 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-12-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-12-generic (recovery mode)
uuid        35c881ed-5182-4fb0-9c3b-731ec6749e11
kernel        /boot/vmlinuz-2.6.27-12-generic root=UUID=35c881ed-5182-4fb0-9c3b-731ec6749e11 ro  single
initrd        /boot/initrd.img-2.6.27-12-generic

title        Ubuntu 9.04, kernel 2.6.27-11-generic
uuid        35c881ed-5182-4fb0-9c3b-731ec6749e11
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=35c881ed-5182-4fb0-9c3b-731ec6749e11 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
uuid        35c881ed-5182-4fb0-9c3b-731ec6749e11
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=35c881ed-5182-4fb0-9c3b-731ec6749e11 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 9.04, kernel 2.6.27-7-generic
uuid        35c881ed-5182-4fb0-9c3b-731ec6749e11
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=35c881ed-5182-4fb0-9c3b-731ec6749e11 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
uuid        35c881ed-5182-4fb0-9c3b-731ec6749e11
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=35c881ed-5182-4fb0-9c3b-731ec6749e11 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 9.04, memtest86+
uuid        35c881ed-5182-4fb0-9c3b-731ec6749e11
kernel        /boot/memtest86+.bin
quiet <code>

---

### Post by jvtroll on 2009-08-23
OK, so I have tried booting from each of the kernels.  At best I get through the splash screen and end up with an endless spinning wheel.  I also tried going to a shell with networking from the recovery modes, but the DHCPDISCOVER program is unable to set up a connection with my dsl modem (despite Ubuntu doing so easily in the liveCD mode).  When I run ifconfig it says my ip address is 127.0.0.1 and the mask is 255.0.0.0
I am stuck here though, because I don't know how to edit these parameters in the shell.  
My hope is that if I could run apt-get update it would install the missing kernels.  Am I barking up the wrong tree?  If not, could anyone tell me how to configure the network connection in the shell?

Thanks.

---

### Post by nhanquy on 2009-08-23
You have too many kernels in the hard drive and that would waste space. Maybe you should remove some of them ( just keep the last kernel which worked for you) by using the liveCD.
It looks like you can not get the network connection ( so you can't do apt-get ).
If nothing works; you should consider backup your data (after booting from liveCD) and re-install.

---

### Post by jvtroll on 2009-08-23
So how do I remove the extra kernels?  Do I go onto my hard drive and delete the files, and if so, what are the files I need to remove?  Or can I use the synaptic package manager in the liveCD to manage files on the installed OS?

---

### Post by nhanquy on 2009-08-23
All kernels are under /boot/ 
You should only remove files you haven't used for a while now.
If it fails to connect with the wifi then try to connect with wired network.

---

