---
title: "Latest Kernel Update Trashes HP DV6000 Wifi"
date: 2008-02-04
forum: Hardware &amp; Laptops
---

### Post by ookook on 2008-02-04
!!!DO NOT UPDATE KERNEL IMAGE IF YOU ARE HAPPY WITH THE WAY YOUR DV6000  WORKS!!!

Was not paying attention and let Update Manager do the following to my HP DV6105us with Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01).

Upgraded the following packages:
linux-headers-2.6.22-14 (2.6.22-14.47) to 2.6.22-14.51
linux-headers-2.6.22-14-generic (2.6.22-14.47) to 2.6.22-14.51
linux-image-2.6.22-14-generic (2.6.22-14.47) to 2.6.22-14.51
linux-libc-dev (2.6.22-14.47) to 2.6.22-14.51


Via dmesg it looks like the bcm43xx driver no longer gets a valid interrupt and viola no wifi.

DV6000s are very touchy machines so... 

!!!DO NOT UPDATE KERNEL IMAGE IF YOU ARE HAPPY WITH THE WAY IT WORKS!!!

:oops: god i sound like such a noob learning the hard way...

Will force a downgrade to 2.6.22-14.46 in synaptic and will report results later...

RESULT I
No joy.  I started at .47 update went to .51.  Can only force back to .46 so an imperfect rollback.  Problem not solved.  bcm driver tries to initialize IRQ0 which is already assigned to timer so wlan radio never comes up.  Deep digging required --will check launchpad and the google.  Oh yah, APM trashed as well...

RESULT II
Changed kernel boot parameters via GRUB to NOAPIC NOLAPIC PCI=ROUTEIRQ and BCMxx drivers assigned an open IRQ and WIFI radio on = success

Ook

---

