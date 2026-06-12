---
title: "Where did my network cards go, why doesn't my mouse work?  (Solved)"
date: 2007-01-23
forum: Hardware &amp; Laptops
---

### Post by rsay on 2007-01-23
On a recent reboot of my Dell Inspiron 5100 laptop running edgy from a fresh install I experienced something very puzzling to me. 

- My mouse and synaptic touchpad suddenly stopped working but not consistently. They mysteriously work every 5th or 6th boot. I  swapped mice to prove this was not a mouse hardware issue. 

- Coincidentally,  both of my network cards had also disappeared

```
ifconfig -a
``` showed only the loopback device.

```
lspci | grep Broadcom
``` showed my broadcom 4401 and 4309 wired and wireless cards

```
lshw -C network
``` was more interesting

*-network:0 UNCLAIMED
description: Ethernet Controller
product: BCM4401 100Base-T
etc.

*-network:1 UNCLAIMED
description: Network Controller
product: BCM4309 802.11a/b/g
etc.

I realized that if the proper kernel module was functioning, these cards should not be unclaimed. 
```
lsmod
``` did not show driverloader, b44 or bcm43xx drivers and I couldn't modprobe them which finally gave me the clue I needed to solve the problem.

I solved this by going to a shell (ctr-alt-F3) and doing

```
dldrconfig
``` and following the defaults.

This rebuilt the kernel modules and everything began working fine again on the next reboot. I thought this was confusing because I was initially fooled into thinking this was a mouse probelm caused by a recent xserver-xorg upgrade and spent a lot of time looking at this as a mouse issue before I realized the network cards were also gone. Hopefully this will be helpful to someone else in the future who also uses driverloader.

Moral of the story. If your mouse doesn't work, make sure your network cards are okay.

---

