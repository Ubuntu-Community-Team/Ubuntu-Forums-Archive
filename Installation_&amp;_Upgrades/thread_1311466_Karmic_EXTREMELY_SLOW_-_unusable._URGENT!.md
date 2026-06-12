---
title: "Karmic EXTREMELY SLOW - unusable. URGENT!"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by anandamide on 2009-11-02
Upgraded to Karmic today - system was fine previously.

Currently have no touchpad but can use USB mouse.

Screen effects fixed on 'basic', although 'standard' was selected prior to upgrade with no issues.

System is unworkably slow. This is NOT GOOD as I use this laptop for uni and am unable to continue until this gets sorted.

Tellingly, conky tells me that Xorg is chewing up about 30% of my CPU. Tried restarting Xorg and nothing changed except the resolution(!).

Any ideas? I'm stuck until this is fixed.

---

### Post by ajgreeny on 2009-11-02
What graphics card?  There seems to be a problem with some ati cards which can slow things down and also stop compiz being enabled.

---

### Post by anandamide on 2009-11-02
Thanks for the reply :-)

It's on-board - I just have a cheap laptop (I was amazed compositing could be enabled, to be honest).

If you need any hardware info can you give me the command to run and I'll copy-paste.

---

### Post by ElHermit on 2009-11-02
When I upgraded to 9.10 on my desktop, things were r..e..a...l   s...l...o...w, too.  Stellarium was updating at 0.04 FPS, not the expected 30 to 35 FPS.  It turns out is was a grub/menu.lst problem.  My menu.lst file did not get updated to start up the 2.6.31-14 kernel.  I was running an older version.

Try this from the terminal:  %uname -r

to see what kernel you are running.

---

### Post by ajgreeny on 2009-11-02
In a terminal run ```
sudo lshw -C display
``` to see your card maker etc.

---

### Post by anandamide on 2009-11-02
That could very well be it - I didn't update GRUB when installed as I've recently tweaked it.

uname -r = 2.6.28-16-generic

---

### Post by anandamide on 2009-11-02
```
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: latency=0
       resources: memory:f2000000-f23fffff memory:d0000000-dfffffff(prefetchable) ioport:1800(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f2400000-f24fffff

```

How do I update GRUB?

---

### Post by anandamide on 2009-11-02
Fixed GRUB - everything now fine, including touchpad. Thanks so much everyone, it's good to be back!

---

### Post by merlinof2 on 2009-11-02
Fixed GRUB

please share!

---

### Post by ElHermit on 2009-11-02
Here is the thread where I got information on GRUB:

[http://ubuntuforums.org/showthread.php?t=1304710&page=4](http://ubuntuforums.org/showthread.php?t=1304710&page=4)

---

