---
title: "Wired Broadband Internet Connection In 8.10"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by ironblossom on 2009-03-03
Im a newbee on the linux world. recently installed ubuntu 8.10 but my internet connection is'nt setup yet. heard that ubuntu sets up internet connection automatically.....!!!
i use realtek ethernet lancard/modem......it works fine in my xp.
i tried 'HARDWARE DEVICES'.....from the 'SYSTEM'....on taskbar in my ubuntu 8.10....but there's no hardwares.......not even a single one.

while browsing i got some blurry advices about this, such putting codes on 'TERMINAL'.....like *ifconfig*

but still cant find the way to solve........all i can say to guys that 'help me!!!!':(

---

### Post by LegendofTom on 2009-03-03
So have you tried typing "ifconfig" into the terminal?  Your first step should be to make sure Ubuntu is recognizing your hardware.  Did you have your box connected to the internet when you installed Ubuntu?

---

### Post by ironblossom on 2009-03-03
yeah........tried ifconfig.......but cant show u the output as a have to switch to ubuntu from xp, where no wired connection......i tried 'HARDWARE DEVICES'..........which outputs something like 'NO prop............hardware found'.

---

### Post by LegendofTom on 2009-03-03
Try "sudo /etc/init.d/networking restart" in the terminal. If that doesn't work, try to force your eth0 to start, with "ifup eth0".  If it still doesn't work after that, reboot, and cross your fingers.

---

### Post by ironblossom on 2009-03-03
[ATTACH]105258[/ATTACH]

[ATTACH]105259[/ATTACH]


this is the output. i also attach the output of *ifconfig*

---

### Post by LegendofTom on 2009-03-04
I see your eth0 is up, but has no IP.  Are you sure DHCP is enabled?  Also, "permission denied" is just Ubuntu's way of telling you to use sudo.  So, try "sudo ifdown eth0" and then "sudo ifup eth0".

---

