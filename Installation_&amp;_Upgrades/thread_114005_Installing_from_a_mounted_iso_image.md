---
title: "Installing from a mounted iso image?"
date: 2006-01-07
forum: Installation &amp; Upgrades
---

### Post by elemental666 on 2006-01-07
So for some reason my cd drive just quit working.  I am partitioned for dual boot and running default ubuntu on the 2nd set, I want setup a minimal on the 1 set of partitions, but my cd drive nixed on me...

Anyhow, I figured out how to mount the iso image for 5.10 install cd.  Can I start the install from within the working default ubuntu install, and install the minimal system with out using the cdrom?

---

### Post by elemental666 on 2006-01-07
Ok, so I extracted the iso to my /boot/ dir
 the cd lives in /boot/ubuntu/
I copied /boot/ubuntu/install/{vmlinz,initrd.gz} to /boot/ubuntu/


I then edited my /boot/grub/menu.lst and added: 
```
title		Install Ubuntu
root		(hd0,6)
kernel		/boot/ubuntu/vmlinz
initrd		/boot/ubuntu/initrd.gz
boot
```

reboot and I see the new option but it says file not found for the kernel image...

---

### Post by elemental666 on 2006-01-07
ok found the typo and now trying this:

```
title		Install Ubuntu
root		(hd0,6)
kernel		/boot/ubuntu/install/vmlinuz root=/dev/hda7 ro quiet splash 
initrd		/boot/ubuntu/install/initrd.gz
boot
```

---

### Post by elemental666 on 2006-01-07
to recap: I'm trying to boot to the install cd from my hd, I extracted the iso to:
 /boot/ubuntu/ 

everyting on the install cd lives there now.  this is on /dev/hda7

I then put a new option in /boot/grub/menu.lst that looks like this:
```
title		Install Ubuntu
root		(hd0,6)
kernel		/boot/ubuntu/install/vmlinuz root=/dev/ram0 devfs=mount,dall ramdisk_size=17000
initrd		/boot/ubuntu/install/initrd.gz

```

at this point it will boot and ask me for my language/keyboard options then it errors out saying it can't load the cdrom.
Here's what I need help with:

starting a server install, not the standard intsall
getting it to look on the HDD instead of the CDD.

---

### Post by kaptainlange on 2006-01-07
I'm doing the exact same thing at the moment, and running into the same problem.

I was thinking that maybe if you could mount the iso image in the cdrom directory on the installation filesystem, that might work.  Only problem is, I don't see the hard drives in the dev section when in the installation.  As such, I can't get to the iso image.  Any ideas on how that might work?

---

### Post by elemental666 on 2006-01-07
well, I just escaped to a shell from the installer and was able to mount /dev/hda7 which is were stuff lives, I'm gonna try to mount my partition and see if I can then mount the iso, my only other guess is to make a partition on the hard drive with iso9660 file system, if that's possible, then copy the extracted iso to this partion, and mount that...

I mounted the iso with:
```
mount -o loop -t iso9660 /boot/ubuntu/ubuntu-5.10-install-i386.iso /media/cdrom
```

ok off to try this

---

### Post by elemental666 on 2006-01-07
the mount command fails in the ramdrive environement, says it can't find anymore loop devices

---

