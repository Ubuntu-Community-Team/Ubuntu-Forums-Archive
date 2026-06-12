---
title: "After upgrading from 8.04 to 8.04.1 renders compiz and desktop effects unusable"
date: 2008-07-20
forum: General Help
---

### Post by OneOfaKindDPC on 2008-07-20
Hello Everyone,

Ubuntu noob converted from PC here. I'm usually quite good at poking around till I can figure it out. But this issue has me stumped. 

I run the update manager daily, to make a long story short I upgraded to 8.04.1 (from the latest version of 8.04) and afterwards had to setup a monitor and the graphics card driver. After I did that I noticed that I had no desktop effects(compiz wouldn't work at all either). I checked my restricted drivers and saw that my nvidia driver was disabled. I re-enabled and did a restart like it asks me to. When the computer starts up it says the computer is running in a low graphic mode and I need to reconfigure the monitor and graphics card again. 

I tried uninstalling and reinstalling the driver with no such luck. and no one has reported any kind of a problem like this as far as I have seen. But no matter what I try, it ends with the computer restarting and it going back in to low graphic mode in which I cannot enable desktop effects. Here's some of the specs of my pc...

P4 3ghz single-core 64-bit (lg775)
3gbs ddr2 pc5400
Nvidia Geforce 7900 gt oc
Asus motherboard p5nd2-sli
on board sound
netgear NIC g302t
300gb sata drive 7200rpm

Any help would be very much appreciated. I had compiz running great, but a simple automated update killed that fun for me lol


If there's any other information I may need to apply to give anyone a better incite please let me know.

---

### Post by OneOfaKindDPC on 2008-07-22
^bump^

---

### Post by infiniah on 2008-07-22
Same thing happend to me.
This is what fixed it for me.
```


sudo dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by jimmy the saint on 2008-07-22
try opening a terminal and typing
```
sudo nvidia-xconfig
```

---

### Post by OneOfaKindDPC on 2008-07-22
No luck sudo dpkg-reconfigure -phigh xserver-xorg. no change at all.

I tried sudo nvidia-xconfig and got this...


d-rock@d-rock-desktop:~$ sudo nvidia-xconfig
[sudo] password for d-rock: 

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

---

### Post by jimmy the saint on 2008-07-22
nvidia creates a configuration file (xorg.conf) that makes the drivers work.  other specific devices may need to be configured manually.  did it fix your screen res?

---

### Post by OneOfaKindDPC on 2008-07-22
No, it made it worse lol. Now my max res is 800 x 600 instead of 1024 x 768. on top of desktop effects as well as the driver being disabled.



Also I noticed everytime I restart it reminds me I'm in low graphic mode. Before when i reselected the monitor and driver it would fix the resolution issue after a few restarts.

Thanks for the attempt though, if you have any other ideas please let me know.

---

### Post by OneOfaKindDPC on 2008-07-23
Would it be a good idea for me to just wipe and reload? This doesn't appear to be a common problem as far as I have seen. :confused:

---

