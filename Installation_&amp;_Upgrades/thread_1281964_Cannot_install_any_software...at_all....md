---
title: "Cannot install any software...at all..."
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by lukus on 2009-10-03
Hi there everyone,

I've been using linux/ubuntu for around 3 years... never came across anything this bizzare.

I don't know what I've done. Just tried to access Synaptic, and I get this error:

> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
...of course, I've tried executing this. The output is as follows:

> $ sudo dpkg --configure -aSetting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-15-generic
cpio: ./bin/udevinfo: Function stat failed: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.28-15-generic
dpkg: subprocess post-installation script returned error exit status 1I have tried to use aptitude, apt-get and synaptic, and the error is consistent.  I have restarted etc.

This error occurs just after loading any GUI

if i'm correct, initramfs isnt really used unless booting the system... and I can boot just fine! Essentially it is basically for loading OS files into ram in order to start...

I have ran sudo apt-get clean to see if that makes any difference. It does not.

I'm just a little stumped and wondered if anyone could shed a little light please...

I am running Ubuntu with Gnome, 9.04 Jaunty, my kernel is 2.6.28-15-generic.

Please ask if you need any more details.

Cheers!

Luke

---

