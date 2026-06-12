---
title: "boot a root filesystem in BTRFS"
date: 2009-07-26
forum: Installation &amp; Upgrades
---

### Post by bad_crow on 2009-07-26
HI everyone,

I tried to install btrfs on my root filesystem (/), this is what I did :

install linux with (server mode):
/boot (ext2) (for grub),
/ (ext3),
swap,
grub on MBR.

compile the 2.6.31-rc4 from kernel.org with btrfs support
test the new kernel by rebooting (worked fine)
install btrfs-tools from debian sid repository (0.19-2)

boot on a ubuntu 9.04 live cd
update the source.list with debian sid
install btrfs-tools from debian sid
convert my / to btrfs
reboot

then the system didn't boot. the kernel loads but freezes (when disabling quiet mode I had "waiting for root filesystem") and drop to busybox.

I tried to mount manually the /
but I got "couldn't mount because of unsupported optional features (1)" "open_ctree failed".

What I wanted to have is :
/boot (ext2)
/ (btrfs 0.19 with snapshot features and maybe compression)

what's the problem ? anyone can help ?
(I have no data on the hard drive, so if you have a better procedure to get the rootfs with btrfs...)

thanks in advance.

---

### Post by whoop on 2009-07-26
Well I'm interested to see how this will work out. I tried that a while back but failed as well. Don't remember where it went wrong for me exactly. Your approach was about the same as mine (as I can remember), so it seems a correct way to do it (to me at least).

---

### Post by bad_crow on 2009-07-27
HI, 

I succeeded doing it, in fact I forgot to patch the kernel to the last version (I forgot a command line) so I had written the partition with 0.19 and tried to read with 0.18.

I've done this, it hasn't been published so I don't know for how long it will be online.
[http://howtoforge.com/node/4665](http://howtoforge.com/node/4665)

Say if you can"t read it.


bad_crow

---

