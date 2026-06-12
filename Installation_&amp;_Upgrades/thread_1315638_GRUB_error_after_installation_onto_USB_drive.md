---
title: "GRUB error after installation onto USB drive"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by bscott433 on 2009-11-05
I had a working installation of 9.10. Decided to install 9.10 onto an external USB hard drive for booting my company laptop and running from USB.
I booted 9.10 from CDROM, did install to USB drive.
That worked fine, USB drive boots and runs from every machine I tried it on.

The problem is that my 9.10 installation on main machine now gives a GRUB error that Drive not found when the USB drive is not connected. 

How do I recover my main machine hard drive and get it to boot again???


I

---

### Post by ajgreeny on 2009-11-05
Easiest way is to attach the USB drive, then boot to your hard disk install and if using grub2 run ```
sudo update-grub /dev/sda
```This assumes that the hard disk in your laptop is sda, which in normal circumstances it should be.

That will put grub from your hard disk back onto the MBR of your laptop, so if the BIOS is set to boot from usb first but does not find a usb disk, it will default back to the hard disk and boot to your instaled ubuntu. You don't need to change the current BIOS boot order

---

### Post by bscott433 on 2009-11-05
Thanks for the reply, but still no joy...

I did connect the usb drive and booted to the GRUB menu on the USB drive. I chose the grub entry:
Ubuntu, Linux 2.6.31-14-generic (on /dev/sda1)

From Terminal ran sudo update-grub /dev/sda

I then shutdown, disconnected usb drive the booted machine..
i get:

GRUB loading.
error: no such disk
grub rescue>

Any other ideas??

---

### Post by bscott433 on 2009-11-05
I tried:
grub rescue>ls
(hd0) (hd0,5) (hd0,1)

I then tried:
grub rescue> set
prefix-(UUID=c82e2715-24b9-410d-9d36-ee00d503979f)/boot/grub
root=UUID=c82e2715-24b9-410d-9d36-ee00d503979f
grub rescue>


To me it appears that something other than hd0 is set as the boot device.
How to change it???

---

### Post by drs305 on 2009-11-06
> **bscott433 said:**
> 
To me it appears that something other than hd0 is set as the boot device.
How to change it???

Go to the Ubuntu community doc and follow the guide for booting from the rescue prompt:
[https://help.ubuntu.com/community/Grub2#Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Rescue%20Mode")

---

### Post by bscott433 on 2009-11-06
I was able to get it working fine this morning. 

After much searching and reading last night I booted to the original hard disk from the Grub menu on the external USB drive.
I then unmounted the USB drive, then issued:

sudo grub-install /dev/sda


Then rebooted and system is working fine.


Thanks for the replies!!!

---

### Post by ajgreeny on 2009-11-06
Ah! So your hard disk install must still be using legacy grub, am I correct?

EDIT:
Sorry, but it appears I spoke too soon and that **grub-install** is still a valid command even with grub2.  I had missed that and thought that **update-grub** had taken its place.

---

