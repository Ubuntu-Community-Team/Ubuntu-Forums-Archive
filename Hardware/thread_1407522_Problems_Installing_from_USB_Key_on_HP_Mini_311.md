---
title: "Problems Installing from USB Key on HP Mini 311"
date: 2010-02-15
forum: Hardware
---

### Post by JoshMiller79 on 2010-02-15
Hi

I recently bought an HP Mini 311 and planned to dual boot Qindows and Ubuntu on it.  I've used ubuntu quit a bit in the past and set it up numerous times on desktop PCs and normal Laptops.

Since this machine has no Cd drive I went for the USB Key installation.  It seems to hang partway through however.  Worst case is it just flashes a cursor on the screen, sometimes it runs through the Linux booting list of this and that (whatever that's called) and hangs on something about USB Interfaces.

I've tried several different keys to boot from.

I've tried booting into the "Try first" option and the "Install" option.

I've loaded it onto the key using the Ubuntu CD Key maker and using a Universal Key maker I found online.

I've also tried both regular and Netbook Remix Ubuntu as a base for the key as well as the Mint variant.

I've even tried the Wubi version which only sort of worked (it seemed to install, but booting into ti doesn't work, also after the install I had to go through not one but two of the Windows OS choice menu).

I will probably try using an external CD drive later today but I would still like to see if there's any ideas on what the hang up is with the USB Key version.

---

### Post by animool on 2010-03-05
I doubt the issue is the USB key - it is more than likely the Broadcom B43 wireless card. 

I found the following very useful:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/479597](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/479597)

None of the blacklisting seemed to work for me so in the end I did the following:

Removed "quiet" and "splash" in kernel lines to see where it was hanging (confirmed this was on the Broadcom Wifi); with the number of restarts I did I found it easier to remove these switches in Grub2.

Physically disconnected the Wifi card to see if it would boot from the USB key (it did)

Installed Ubuntu 9.10 from USB key

Installed the v2.6.32.9 kernel
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.9/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32.9/)
Still wouldn't boot when Wifi card was disconnected

Enabled the Unsupported updates (karmic-backports) Update manager --> Settings.
Enabled the restricted driver for Broadcom B43 wireless driver

It's going fine so far.

Slightly off the topic of your question but still relates to getting the HP mini 311 up and running - I suggest you download the proprietary NVidia drivers from Nvidia. I installed 195.36.08 and am very happy with the video performance.

Good luck!

---

### Post by JoshMiller79 on 2010-03-05
I ended up getting things working actually by digging out an external CD drive.

Thanks for the advice though.

---

