---
title: "installing and using multiple linux distros on usb stick"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by v1nsai on 2009-05-02
I've been going through guides and whatnot trying to get my 8gb usb stick set up how I want it, here's what I've got so far:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         305     2449881    b  W95 FAT32 
/dev/sdb2             306         342      297202+   6  FAT16
/dev/sdb3             343         586     1959930    5  Extended
/dev/sdb4             587         974     3116610    b  W95 FAT32
/dev/sdb5             343         465      987966    b  W95 FAT32
/dev/sdb6             466         586      971901    b  W95 FAT32
```

Here's how I want to use them:

sdb1 - has windows programs and extra space.  It's in the first position so Windows can see it.

sdb2 - Damn Small Linux, for working with old crappy systems

sdb3 - Extended partition
   sdb5 - Ultimate Boot Disk (Windows)
   sdb6 - Fedora 10

sdb4 - Ubuntu 9.04 ;)

I've gotten it partitioned properly and have been installing the distros using unetbootin in windows (anyone know of another one that actually works??) so my question is about setting up grub.  I've been looking around and everything I find requires access to the /boot/grub/menu.lst but since I've essentially installed a livecd I don't have access to the filesystem until I have actually booted into it.  I've been at this for quite some time, but I'm pretty stumped.  Help appreciated :\

---

### Post by v1nsai on 2009-05-02
Got ubuntu to boot from one of my partitions (taking the time to make a boot cd and using the liveusb creator is the only utility I have used that just f*cking WORKED.  Excuse my enthusiasm.)  It didn't help as much as I thought it might though, the /boot folder only contains some files I'm not familiar with, no grub/menu.lst or anything similar, so I'm still pretty lost on how to set up menu.lst (can someone confirm that once I get menu.lst set up I just grub> setup (drive,partition) to install it to mbr of flash drive right?)

**edit: I found 'info grub'! For anyone who would like to learn grub themselves, 'sudo apt-get install grub-doc(s?)' will install the real grub man pages. Armed with this I have learned grub pretty quickly. I found initrd and vmlinuz files on /Casper of my ubuntu partition, and gotten it installed to my mbr. I'm still not able to get it to boot but wanted to provide help for anyone else who might have a similar problem, since no one is going to help me /shrug. I'd still appreciate some help with menu.lst but not too worried about it, I'll figure it out with a little guesswork ;)

---

### Post by v1nsai on 2009-05-03
Sorry for another bump, but nothing I have tried has worked.  I'm trying to get this running for work tomorrow, I'm a mobile computer tech and it'd be amazing to have all my tools with me on one flash drive :guitar:

Can anyone suggest anything?  Is it even possible to boot what is essentially a live cd like this?  Ubuntu 9.04 can install itself to a flash drive but its a 4.4 gb install, my live cd is only taking ~700 mb.  Where can I find the files that I need since the filesystem is only accessible from inside the livecd?

---

### Post by v1nsai on 2009-05-03
Well, I found a great boot menu called sbm, it installs through windows or linux to the mbr then boots and allows you to select from any of the partitions on your disk that it automatically detects :guitar:

Buuuuuuutttt when I try to boot ubuntu with it, I get to the live cd menu, I select try ubuntu blah blah blah and after the splash screen I get sent to busybox, it says that IO APIC resources could not be allocated.  Been researching it but everything I have found suggest that the BIOS or motherboard are at fault, but it boots properly without the sbm booter so I know it isn't that.  Bah.

---

### Post by travelinrob on 2010-03-12
Did you get any further with this? I would like to do the same type of configuration. I've been searching and haven't found any definitive instructions.

Rob

---

### Post by Diego Garcia Mendoza on 2010-03-29
Yeah i'm tying to do the same, i'll start some test and tell you about any advance... I don't wanna buy/carry 10 USB for my distros and utils :(

---

### Post by C.S.Cameron on 2010-03-29
Well Nimblex is a small, (200mb), distro that comes with Vbox.
You should be able to run just about any iso file you choose.
Only I'm not sure if you can use virtual tools to fix something on another drive.

---

### Post by oldfred on 2010-03-30
I have seen several ways. Grub will boot some ISO directly if they are set up for it. I have several ISO directly booting on my USB. 
Also there is nothing preventing your USB from being another multiboot drive. This will be my next test.

How to install ubuntu on USB drive and carry entire computing system in pocket? 
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)
With details on some of the ccaveats, std install.
[http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

MultiBoot USB with Grub2 (boot directly from iso files)
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604)
-----------------
[http://forums.fedoraforum.org/showthread.php?t=217113](http://forums.fedoraforum.org/showthread.php?t=217113)

---

