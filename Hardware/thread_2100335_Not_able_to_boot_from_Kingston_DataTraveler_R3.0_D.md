---
title: "Not able to boot from Kingston DataTraveler R3.0 DTR30 16GB"
date: 2013-01-01
forum: Hardware
---

### Post by przemnet on 2013-01-01
Hi,

I bought a brand new 16GB USB stick Kingston DataTraveler R3.0 DTR30 and I wanted to install persistently Ubuntu/Lubuntu/Backtrack on it.

To do that, I use another USB with LiveUSB installation (it is recognized as /dev/sdb device because my primary hard drive is /dev/sda). I install system on /dev/sdc1 partition and install grub2 in /dev/sdc. Just like on this video: [http://www.youtube.com/watch?v=MSHB8-dBI2w](http://www.youtube.com/watch?v=MSHB8-dBI2w) (How to Install Ubuntu 10.04 LTS on USB Persistently)

Above procedure is correct, because I've done it many times and it works on other USB flash drives (e.g. Sandisk Cruzer Blade).

Unfortunatelly system does not boot from Kingston DTR30- even LED on this device does not blink during system startup.

I tried to create startup USB on my Kingston DTR30 with Startup Disk Creator and Unetbootin, but unfortunatelly even this was not possible- it was not possible to boot from it.

As I wrote before, I've done this many times on other USB sticks and everything was correct, so I did not make common mistakes like:
- BIOS settings (device boot sequence) are correct (other USB sticks boot)
- USB stick has bootable flag (as other USB sticks)
- grub is installed on /dev/sdX not on /dev/sdX1, /dev/sdX2 etc.
- all other USB devices are unplugged during system boot


Most probably problem is not related to Ubuntu, but it is a general issue with bootable capabilities of particular USB stick- I tried it on my SONY VAIO laptop and desktop computer without luck to boot on either of them.


Are there any tricks that I can try to get my brand new USB stick working as expected (to have persistent and BOOTABLE install of Ubuntu system there)? Or should I simply buy another one?

Looking forward,
Przemek.

P.S. Happy New Year and all the best in 2013 ;-)

---

### Post by TheFu on 2013-01-01
The simple truth is that not all USB flash drives are compatible in all aspects with every piece of hardware out there.  Some just will not support booting. Sorry.

---

