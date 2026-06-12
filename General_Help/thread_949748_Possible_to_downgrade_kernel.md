---
title: "Possible to downgrade kernel?"
date: 2008-10-16
forum: General Help
---

### Post by detroit/zero on 2008-10-16
I've been having tons of trouble with slow USB transfer speeds for months now. Any search for "slow" and "USB" will turn up some of my posts.

For a while I thought the problem lies with GVFS, for a while I thought the problem was Nautilus. The only thing really left to check is the kernel.

I know for a fact that with Ubuntu's default install, I have lightning-fast USB transfer speeds. I'd like to download and compile kernel version 2.6.24-16 (I'm pretty sure that's the version on the live-cd). Where can I get this old kernel image? I don't see anywhere at kernel.org to download old versions. Who else would have that image?

---

### Post by bodhi.zazen on 2008-10-16
If you suspect it is the kernel, I suggest you start by trying an older kernel on a live CD :)

If you wish to compile your own kernel, try this link :

[ftp://ftp.kernel.org/pub/linux/kernel/v2.6/](ftp://ftp.kernel.org/pub/linux/kernel/v2.6/)

Be aware the Ubuntu kernels are patched :)

---

### Post by beno1990 on 2008-10-16
Pulling up Synaptic and searching for the kernel version you want gives some hits. You'll want the kernel image, kernel headers, and any other modules and such that you'll need on the older kernel version.

```

sudo apt-get install linux-image-2.6.24-16-generic linux-headers-2.6.24-16-generic linux-ubuntu-modules-2.6.24-16-generic

```

Should get you started. :) But don't forget to select the older kernel image on boot from your bootloader, so you might need to change your bootloader settings to allow you to select the kernel or make this one your default.

---

### Post by detroit/zero on 2008-10-16
Well, I just got done trying out the older kernel, and no dice. My transfers are even slower with the old kernel than they are using the current one.

If it was just USB, I could almost live with it, but it affects transfers between partitions, too, and moving files around becomes an all-day task.

How can I keep narrowing this problem down? I can transfer files between partitions and to USB devices at speeds approaching 30MB/s even using a live cd, and also on a fresh install. Something goes wrong after all the updates and a reboot...

How can I compare a list of packages/version numbers from a default install to how my system currently sits? Install 8.04 in a VM and do something like```
sudo dpkg --get-selections > packages.lst
```on both my systems and compare between them?

I never had this problem on Edgy, Feisty, or Gutsy, and even in Hardy I didn't have the problem until kernel 2.6.24-19 was introduced. That was back in June, I think, and it's hard to say what updates came along with that. I've even re-installed a few times since then to try and narrow the problem down.

I'm lost. Anybody got any ideas? How can I get my file transfer speeds back?

---

