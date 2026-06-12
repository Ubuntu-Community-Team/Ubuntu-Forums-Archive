---
title: "need help with grub"
date: 2005-12-05
forum: General Help
---

### Post by axel_2078 on 2005-12-05
Here's the deal. I'm running Mepis on hdc. Yesterday I installed Kubuntu 5.10 on hda. Once it rebooted, it would only allow me to boot Kubuntu. In order to access Mepis again (my primary OS) I had to reinstall grub.  I tried installing it to hda first, but that removed everything from the boot menu. I had to put it back in hdc in order to boot Mepis again.  How can I fix this so I can dual boot between them?

---

### Post by manicka on 2005-12-05
Manually add an entry to the grub menu when in mempis to boot the ubuntu install.

---

### Post by axel_2078 on 2005-12-05
Somehow I have to get the information to add it though.  I mounted hda while in mepis and went to /boot/grub/menu.lst, but there was no hard drive information listed in the file.

---

### Post by manicka on 2005-12-05
This is a copy of my grub menu entry. It may give some you some options to try out

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdb7 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

I'd try

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

 or variants thereof depending of your setup

---

### Post by limit223 on 2005-12-05
And this is my copy of menu.lst...hope that helps you somehow:

```
title		Ubuntu, kernel 2.6.15-rc1-ck1 
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.15-rc1-ck1 root=/dev/hdb10 ro quiet
initrd		/boot/initrd.img-2.6.15-rc1-ck1
savedefault
boot

title		Ubuntu, kernel 2.6.15-rc1-ck1 (recovery mode)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.15-rc1-ck1 root=/dev/hdb10 ro single
initrd		/boot/initrd.img-2.6.15-rc1-ck1
boot

title		Ubuntu, kernel 2.6.12-9-686-smp 
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.12-9-686-smp root=/dev/hdb10 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-686-smp
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-686-smp (recovery mode)
root		(hd0,9)
kernel		/boot/vmlinuz-2.6.12-9-686-smp root=/dev/hdb10 ro single
initrd		/boot/initrd.img-2.6.12-9-686-smp
boot

title		Ubuntu, memtest86+
root		(hd0,9)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb9.
title		Slackware (on /dev/hdb9)
root		(hd0,8)
kernel		/boot/vmlinuz root=/dev/hdb9 ro 
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb8.
title		SUSE LINUX 10.0 (on /dev/hdb8)
root		(hd0,7)
kernel		/boot/vmlinuz root=/dev/hdb8 vga=0x31a selinux=0 resume=/dev/hdb7 splash=silent showopts 
initrd		/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb8.
title		Failsafe -- SUSE LINUX 10.0 (on /dev/hdb8)
root		(hd0,7)
kernel		/boot/vmlinuz root=/dev/hdb8 vga=normal showopts ide=nodma apm=off acpi=off noresume selinux=0 nosmp noapic maxcpus=0 edd=off 3 
initrd		/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

