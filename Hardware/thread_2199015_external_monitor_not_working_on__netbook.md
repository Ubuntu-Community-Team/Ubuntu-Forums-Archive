---
title: "external monitor not working on  netbook"
date: 2014-01-11
forum: Hardware
---

### Post by white88enochian on 2014-01-11
im running ubuntu on  HP-Mini-110-3700    i try pluging a dell 17 inch flat monitor into it threw vga. the monitor is detected and it changes my screen size  by more then half on the netbook  but nothing shows up on the monitor

i know the monitor works  i was using it perfect  in kali linux  last week on the same netbook.


my secound question is
the only option that shows up is mirror   why isent there a option for extend etc and is there any other software i can use to extend the desktop.

ubuntu 12.04  btw

---

### Post by mikewhatever on 2014-01-11
Are these specs about right: [http://reviews.cnet.co.uk/netbooks/hp-mini-110-review-49302563/?](http://reviews.cnet.co.uk/netbooks/hp-mini-110-review-49302563/?)

---

### Post by white88enochian on 2014-01-11
Just tryied another monitor  same exact thing happens no signal to the monitor  but ubuntu detects the monitor

---

### Post by white88enochian on 2014-01-11
yes thats it  altho  i think mine rginal had a 250 gb harddrive  and ithad  widows 7 starter not xp

---

### Post by mikewhatever on 2014-01-11
Well, I was mostly after the chipset, the HDD size is irrelevant. You could look into /var/log/Xorg.0.log for clues, but really, what do you expect from a 2008 Intel GPU. Intel graphics was a pretty nasty deal back then.

---

### Post by white88enochian on 2014-01-11
well on windows 7  and kali linux  they worked  fine.  i just want a bigger screen

---

### Post by mikewhatever on 2014-01-11
So, you have W7, 12.04 and Kali on that netbook, or are we talking about different hardware?
Regardless, W7 support has always been decent compared to Linux.

---

### Post by white88enochian on 2014-01-11
no i had windows 7  but i wanted linux   because of the low specs  so i had kali. i deciede after not using this netbook for awile thatid put it in my daughters room for netflix on a bigger monitor.     theres no work around for netflix on kali so i switched  it to ubuntu   for netflix  which works nicely.      the only os on here at this time is ubuntu  id rather not have to go back to windows just to watch netflix on a larger screen. im trying to identify  the graphics right now

---

### Post by white88enochian on 2014-01-11
description: VGA compatible controller
       product: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:56180000-561fffff ioport:40c0(size=8) memory:40000000-4fffffff memory:56000000-560fffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:56100000-5617ffff

---

