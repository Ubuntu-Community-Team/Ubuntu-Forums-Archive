---
title: "Commands/Resources to learn RAM Type/Speeds?"
date: 2016-07-10
forum: Hardware
---

### Post by PAKeenan on 2016-07-10
Howdy Everyone!


Recently I bought some RAM for an old Asus EEE-PC Netbook running Ubuntu 16.04. I originally had 1GB of DDR2 @ 800MHz (PC6400), and replaced it with a 2GB stick of the same form factor and speed. After installing the new RAM, my system performance didn't seem to improve much, even though I had doubled the among of RAM I previously had. The system does see all 2GB of the new stick however. 

Is there a terminal command where I can see how much and at what speeds the currently installed memory is running at? Also, is there a way to see if maybe I was wrong about what my system's RAM requirements are? Worst case scenario it only knocked me back $15 so I can just buy a different unit again if I was wrong from the get-go. This netbook is 5+ years old and I'm not worried if there's little I can do to improve its overall performance, just wanted to extend its life as long as possible before I got to upgrade


Thanks a bunch!
-Patrick

---

### Post by weatherman2 on 2016-07-10
You can find a detailed hardware description of your computer (including RAM) by running the command "sudo lshw" from a terminal window.

You can see what speed the RAM is really running at by booting and running Memtest.  (Should be in the Grub boot menu if you have one.)

But the real benefit of more RAM is the ability to open more windows /programs at once.  It probably won't help start-up time or help performance at all if you have just a few windows open.

---

### Post by mörgæs on 2016-07-11
> **PAKeenan said:**
> This netbook is 5+ years old and I'm not worried if there's little I can do to improve its overall performance, just wanted to extend its life as long as possible before I got to upgrade


What needs upgrade is the software, not the hardware.
Ubuntu is heavy on the hardware, and I suggest a fresh install of Lubuntu in stead.

---

### Post by PAKeenan on 2016-07-11
Thanks guys for the input! Gonna give Lubuntu a try, lshw says 2GBs @ 667MHz

---

### Post by mörgæs on 2016-07-12
Good, please post the results.

---

