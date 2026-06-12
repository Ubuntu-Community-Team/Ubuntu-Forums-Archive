---
title: "ACER Travelmate 8104 and LIVE CD"
date: 2005-10-03
forum: Hardware &amp; Laptops
---

### Post by Mashang on 2005-10-03
Hi , I have had soem problems trying to test the live cd on my new born ACER TM 8104 ! ( he is only 7 days old ) anyhow  i conside r myself a newbie in ubuntu world so i wanted to try the live cd on my labtop however it freezes at the point of decompressing the Kernel it says OK but then freeze. I tried the 10.4 and 10.5 preview even the DVD for KUbuntu ! and nothing .. I know i can install it an d it might work but then again i want to be sure before doing that ! 
it would b great if anyone can guide me through !!!!!!!!!
BTW Ubuntu ROCKS !

---

### Post by Mashang on 2005-10-04
OK since i got no replies ..........................
I managed to pass through the first freeze by simply setting apsc= off on the command line.. 
however the installation procedes till the point of the boot up of the OS and then the monitor shuts down and no screen is viewable. I think i need a right VGA command too but cant figrue out which !!! 
help me .. 
have tried VGA=771 and no luck

Thanks

---

### Post by strandlooper on 2005-10-04
Hi 
You need to edit the xorg.conf. Add in the section device the line
Option          "MonitorLayout" "LVDS,AUTO"
Good Speed
Strandlooper

---

### Post by ola18 on 2005-10-04
run as sudo (sudo -s)

dpkg-reconfigure xserver-xorg


choose "vesa" as manufactorer.

---

### Post by Mashang on 2005-10-04
Thanx guys i tried but thsi time it stops at startign hotplug subsystem and it hangs !!! i can even see the ubuntu logo when it is initializing other subsystems but gets to this one hangs and then goes to terminal and stays there ! until i cut the power !!
thank you for the help

---

### Post by Mashang on 2005-10-06
I dont really know what to do now ! thre have been 41 views and no respond !!! althought he other two friends got me further than where i was ( respect ) but no hope .. i spend so much on this labtop to get my beloved ubuntu on it ! 
please help me my system pauses on "system hotplugs" and nothing more ..

---

### Post by strandlooper on 2005-10-07
Hi
I don't have a UBUNTU live CD and I don't know which version do you use, but on my Acer TM 8101WLMi with Hoary and Breezy the following boot options work for me 

vga=0x345 noapic quiet splash

Good speed

Strandlooper

---

### Post by cmnorton on 2007-07-15
I had purchased a Ubunto 6 LTS live/installation CD. When I booted my laptop with it and then went into the installation, everything froze. I shut off the laptop cold, rebooted, and used save mode. The installation was successful.

---

