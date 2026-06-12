---
title: "Iffy installation procedure, need verification"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by jjjjeremy on 2009-08-28
Some background:
  I recently installed a clean copy of 9.04 on my laptop after having dual boot with windows vista, and 9.04 installed through windows.
  After a day or so I noticed that the battery life was horrible compared to the windows-installed 9.04. Went on with it for a week or so, but yesterday I decided to go try out 8.04 instead for the battery life. I made a live8.04 usb and installed last night.
  Now (in 8.04) drives won't mount unless they are plugged in before boot, and the battery is just as bad.
  So, now I have a laptop that doesn't mount USB drives, and I don't have any blank CD's, but I want to install 9.04, and I think that I have a way, but I want some verification.

PS, this is the only computer I have access to, and I have 9.04 on an external drive that mounts if I have it plugged in and turned on at boot.

1. Boot with the live USB
2. Make a folder on my desktop "mkdir /home/jeremy/Desktop/Ubuntu9.04"
3. Mount 9.04 "mount -0 loop -t iso9660 /directoryof.iso /home/jeremy/Desktop/Ubuntu9.04"
4. Run the .iso
5. Install onto internal harddrive

In my head this works out perfectly, but, that could just be a horrible idea, let me know,

-jjjjeremy

---

### Post by jjjjeremy on 2009-08-28
I brought down and walked to the drug store and bought some blank CDs. 9.04 running well, although the battery is still ****


maybe only 50 min per charge

---

### Post by stlsaint on 2009-08-28
my other system also has a bad battery but thats cuz its old...how about your specs?

---

### Post by East82 on 2009-08-28
Vista has a several options for power configuration and the default configuration (balanced) manages power by throttling resources, mainly the CPU, thus extending battery life. If you installed thru Wubi, it's my guess that Vista is still managing power options. I've not fooled with power options in Ubuntu, but I would explore that.

HTH

---

### Post by jjjjeremy on 2009-08-28
The underlying problem is that I am running 9.04 alone now, and my battery life is significantly worse than it was when I was dual-booted with Vista and 9.04.

---

### Post by Karloman on 2009-08-28
there is a panel applet that let's you govern cpu speed manually - it's called "CPU Frequency Scaling Monitor"
my tip for you is to use that applet and change it to lower clockspeed when not using your system intensively

---

