---
title: "Creative Zen X-fi Setup"
date: 2009-02-23
forum: Hardware
---

### Post by mdrake on 2009-02-23
Hi all,

First off, I'm a beginner at Linux so I apologize if I missed something that should be completely obvious, but anyway, here goes.

I've been reading around on trying to get the Zen X-fi to work with Ubuntu 8.10 and have had no luck so far. As far as I understand, all that needs to be done is to install the libmtp and libnjp packages and add specific lines to them. The line

# Creative Zen X-fi
ATTR{idVendor}=="041e", ATTR{idProduct}=="4162", SYMLINK+="libmtp-%k", MODE="770", GROUP="audio"

must be added to the libmtp file, under LABEL="libmtp_usb_device_rules" and LABEL="libmtp_usb_rules", and the line

# Creative Zen X-fi
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4162", GROUP="plugdev", MODE="0770"

must be added to the libnjp file. I've done these two and been unable to get gnomad2 or amarok to recognize the player. I've also tried to mount the player using

apt-get install mtpfs
mkdir /zen
mtpfs /zen

where zen is the folder that it should be mounted to. So far I've been unable to get any program to recognize it. In nautilus, it sees the zen mount, but it doesn't see any files on it. It also seems to be able to tell that there's 3.6gb free out of the 32gb total.

I know that usb is installed because I was able to hook up my external hard drive.

Any thoughts on getting it to work?

---

### Post by mdrake on 2009-02-23
bump

---

### Post by lavinog on 2009-11-11
Have you tried using your zen with karmic?

---

