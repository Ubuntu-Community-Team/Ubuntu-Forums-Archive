---
title: "HP Compaq 6720s network problem"
date: 2010-06-02
forum: Hardware
---

### Post by Crisa on 2010-06-02
I just installed Ubuntu 10.04 on this laptop and after installation I was unable to use any network devices. So no ethernet or Wlan. Can someone help me with this. 

lspci shows: 
network controller Broadcom Corporation bcm4311

sudo lshw -C network:
ethernet interface 82562GT 10/100 
Vendor Intel Corporation

---

### Post by claracc on 2010-06-16
I have the same laptop model, yet i haven't upgrade to lucyd 10.04 (so I don't know how it works), I am still with karmic koala (solid rocks) 9.10, and the network is recognized and working.

I don't use network-manager from gnome, it was always connecting and disconnecting,  but wicd (it is in the repositories) works very well.

So I recommend to install karmic koala 9.10 and wicd as manager of the net. It works for me.

---

### Post by freacert on 2010-11-19
Just are doing a try-out on a hp-compaq 6720s and notice there is no wired internet available. Did a bios upgrade as recomended, but no luck either. So next step will be to turn the acpi off as recomended at this thread [http://ubuntuforums.org/showthread.php?t=1483292&highlight=hp-compaq+6720s](http://ubuntuforums.org/showthread.php?t=1483292&highlight=hp-compaq+6720s)
hope you solved your problem, and that it will solve mine.

Good luck

---

### Post by freacert on 2010-11-21
Note 2 days later, as the wired network was not working with the life-cd, after installing to the harddisc there was no problem at all to install 10.04 and wired networking worked straight out of the box.

---

