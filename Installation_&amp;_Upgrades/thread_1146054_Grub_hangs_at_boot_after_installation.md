---
title: "Grub hangs at boot after installation"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by retry111 on 2009-05-02
Hi,

I've installed ubuntu 9.04 using the alternate install CD and partition encryption. I've created an unencrypted /boot partition to boot from. My MBR is used by somthing else so I've tried to install grub onto a USB drive during the install.

When grub boots from the USB drive on my system it displays "GRUB", and nothing else. The system hangs at this point. Does anyone know what can cause this?

I've tried numerous grub installs on usb drive - but I only get the above, it doesn't get to the boot menu.

The /boot partition I created when installing (ubuntu 9.04 alternate install CD) resides inside a DOS extended partition as a logical partition (formatted with ext3). It is not marked as bootable. Is the problem with this setup? 

I'm installing grub using the grub shell:
root (hd0,4)
setup (hd1)
... where (hd0,4) is the boot partion on my drive (where the /grub directory with stage1 etc. is located as placed by the ubuntu installer) and (hd1) is an external USB disk I'm trying to boot from. I'm not sure what to do next.

Thanks for any help!

---

### Post by retry111 on 2009-05-02
I've been working on this. I've moved and resized partitions on my drive to get a better setup.

I now have a normal primary partition marked as bootable for /boot. There are two other partitions created in the DOS extended for swap and root, which I setup as encrypted volumes. 

I've installed grub on the USB drive as before and on the boot parition, but still no joy - still hanging with the "GRUB" message.

So its not the boot partition being in the extended partition, or the bootable flag not being set on the partition. Any ideas?

---

### Post by caljohnsmith on 2009-05-02
How about trying this:
```
sudo grub
grub> device (hd0) /dev/sdb
grub> device (hd1) /dev/sda
grub> root (hd1,4)
grub> setup (hd0)
grub> quit
```
In other words, to correctly install Grub to the MBR of the sdb drive (your USB drive) and have it point to the sda drive for its boot files, you have to switch the drives around with Grub's "device" command. Let me know if that works or if you still run into problems.

John

---

### Post by retry111 on 2009-05-04
Hi John,

Thanks for the help - it works perfectly following your steps! Though I don't understand why swapping the drives round makes it work though - when grub boots, is the disk it is booting from referenced as hd0, where it is initially detected as hd1 in the grub shell? 

Anyway thanks again,
Terry.

---

### Post by sahabcse on 2009-05-04
For fixing the grub follow below 

[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)

---

### Post by caljohnsmith on 2009-05-04
> **retry111 said:**
> Hi John,

Thanks for the help - it works perfectly following your steps! Though I don't understand why swapping the drives round makes it work though - when grub boots, is the disk it is booting from referenced as hd0, where it is initially detected as hd1 in the grub shell? 

Anyway thanks again,
Terry.
Yes, you are exactly right, on start up Grub "sees" (hd0) as the first boot drive, not necessarily sda; thus when you set the USB drive to boot first, it is (hd0) to Grub on start up. Yet when you are in linux running Grub commands, only then is it generally true that (hd0) is sda, (hd1) is sdb, (hd2) is sdc, etc. Anyway, glad that you can now boot with your USB drive. :)

Cheers,
John

---

