---
title: "Install Ubuntu from USB Stick but only 512mb?"
date: 2005-12-09
forum: Installation &amp; Upgrades
---

### Post by ShiftyPowers on 2005-12-09
Hey all, I have a laptop with a broken cd rom and need to try and install an operating system on the thing.  I have seen the instructions on how to install from here:

[https://wiki.ubuntu.com/Installation/FromUSBStick]("https://wiki.ubuntu.com/Installation/FromUSBStick")

However, I unfortunately only have a 512mb USB Stick so can't fit the entire installation disk on the drive.  Does anyone know what files I can safely not copy over and still be able to do a normal installation?  I imagine I can try and cut out some packages but I don't want to do so if it's going to damage the default install.

Any ideas would be greatly appreciated.  

Ubuntu Forever.

---

### Post by ShiftyPowers on 2005-12-10
a friendly bump from my side

---

### Post by UbuWu on 2005-12-10
Following that guide, use the contents of the server install cd instead of the normal install cd, it is much smaller ( [http://releases.ubuntu.com/ubuntu-server/breezy/](http://releases.ubuntu.com/ubuntu-server/breezy/) ) Afterwards, do an 'apt-get install ubuntu-desktop'

Edit: just saw it is also over 500 mb. It has a lot of packages that are not installed by default though, so you can leave these out.

---

### Post by UbuWu on 2005-12-10
> The easiest way to prepare your USB memory stick is to download netboot/boot.img.gz, and use gunzip to extract the 8 MB image from that file. Write this image directly to your memory stick, which must be at least 8 MB in size. Of course this will destroy anything already on the memory stick.
 (from the [installation guide]("http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/"))

Boot image is [here]("http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/").

---

### Post by ShiftyPowers on 2005-12-10
[QUOTE=UbuWu](from the [installation guide]("http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/"))

Boot image is [here]("http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/").[/QUOTE]

ubuwubu, thank you so much, that is exactly what I was looking for.

---

