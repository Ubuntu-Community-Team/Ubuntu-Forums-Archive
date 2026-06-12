---
title: "Disappearing hard-drive problem"
date: 2006-07-18
forum: Hardware &amp; Laptops
---

### Post by pwaller on 2006-07-18
Here is what I have done so far:

I got a new laptop, completely fresh with nothing on it. I have the DVD version of the 6.06 install/livecd. It boots fine (though with a minute or two wait at the "Mounting root filesystems..." screen.

I then proceeded to partition and install linux, everything seems fine.

Restart, and after waiting at the "Mounting root filesystems..." screen for quite a while (5 min+) I get "Alert! /dev/sda1 does not exist. Dropping to a shell". It then gives me a shell in which I can't seem to do anything.

Rebooting back into the livecd, /dev/sda1 (the root partition) and /dev/sda5 indeed don't exist. However, they are listed under fdisk -l, and displayed in gparted. However I can't seem to access them for love nor money.

Deleting the partition, and creating a new one - I can mount it, and write files to it happily. If I reboot back into the livecd, it disappears, and I haven't yet found any way of accessing it.

complete dumps of dmesg and lspci -v can be found at [http://misc.randomphp.net/dmesgdat](http://misc.randomphp.net/dmesgdat) and [http://misc.randomphp.net/lspcidat](http://misc.randomphp.net/lspcidat)

Any help is greatly appreciated. I currently don't have a functioning computer to work on! :(

---

### Post by UberIcarus on 2006-07-18
I have something somewhat similar wrong with my laptop, although I have no errors or loss in functionality. My harddrive has disappeared from my filebrowser under Computer. I only have the DVD Player and the Filesystem.

I can still install things okay though, I guess.

---

### Post by k420 on 2006-07-18
what does your fstab look like

---

### Post by pwaller on 2006-07-18
[http://misc.randomphp.net/fstabdat](http://misc.randomphp.net/fstabdat)

Note that this is all booted from the livecd. I haven't successfully booted into the installation yet because of this problem. I have several times performed a complete install.

- Pete

---

### Post by pwaller on 2006-07-19
This is looking a lot like a bug,

I just ran the knoppix livecd and it happily found and mounted the partitions that were made with ubuntu. (and I could see and access the files therein).

I have submitted a bug report here

[https://launchpad.net/distros/ubuntu/+bug/53385](https://launchpad.net/distros/ubuntu/+bug/53385)

---

### Post by rev_1318 on 2006-07-19
Just a thought: is it a SATA-disk? (since you mention sda instead of hda)
Then maybe the sata-modules are not loaded (in initrd) before the root partition is being mounted...

Paul

---

### Post by pwaller on 2006-07-19
yes, indeed it is a Sata hard-drive. How do I load the sata module(s)?

How would I go about putting them in the init? Isn't that contained on the very hdd that can't be loaded?

- Pete

---

