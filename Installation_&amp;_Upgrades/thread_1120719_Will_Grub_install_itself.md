---
title: "Will Grub install itself?"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by ETW Grumpy on 2009-04-09
I tried to install Ubuntu on an external hard drive but the install didn't work.  I started having error 18 problems with grub after that. I want to use that external drive with a different computer. If I plug that drive into my laptop, will it try to install Grub on my laptop?

---

### Post by ronparent on 2009-04-09
No. Grub should configure itself when ubuntu is intially installed. After that it won't install to a another computer unless you do it. Be cautioned that it won't boot to this other computer unless it was configure to boot on the external hard drive and the other computer's bios is configured to seek the external drive first!

---

### Post by ETW Grumpy on 2009-04-09
OK, this is on a Windows external drive it should work just fine if I use it right? I don't want to mess up the new computer with this.

---

### Post by ronparent on 2009-04-09
Does windows boot ok with external drive unplugged?

---

### Post by ETW Grumpy on 2009-04-10
No, it kept getting an error 18 message until I changed one of the BIOS settings I wasn't supposed to change. Now it won't boot at all. I bought a laptop to replace it (Win Vista Home Premium)64 bit, I just want make sure that when I plug the external drive into the laptop it's not going to do something crazy and screw this computer up.

---

### Post by ronparent on 2009-04-10
It appears that the mbr on the boot drive was written by grub when you installed ubuntu on the external drive. Grub isn't working because the location to which grub itself is installed is unreachable by the boot loader! The error 18 usually indicates this on older computers with a bios limitation of something like 9 Gb. The common solution is to create a small dedicated grub partition at the start of the "boot" drive. 

You should first use the windows install disk to restore the windows mbr on the drive to which windows is installed. That should make windows bootable again. 

If you can set an external drive to boot first Then we can pursue the easiest solution to permit booting from that drive - when plugged in.  If not, we must find another boot solution to meet your requirement (to be able to boot ubuntu from the xternal dirve on any computer to which it is plugged into?). Look at your bios and see if an external hard drive can be selected as your boot device.

In any case be assured that under no circumstance can simply plugging the external drive into your computer cause harm - certainly not if it can't be booted. The only harm  has already happened in that your windows mbr has apparently been overwrittem and that is fixable.

---

