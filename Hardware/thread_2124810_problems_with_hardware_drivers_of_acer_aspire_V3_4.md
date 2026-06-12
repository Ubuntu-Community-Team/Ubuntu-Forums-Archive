---
title: "problems with hardware drivers of acer aspire V3 471"
date: 2013-03-12
forum: Hardware
---

### Post by mohdforever on 2013-03-12
hello everyone.

i have just bought a new acer laptop model: aspire V3-471 3rd generation with i3 2.40 Ghz and 4GB RAM

the problem is in the first boot there was no OS and I've installed ubuntu 12.04 on it..... then 



the hardwares like .. 
mouse and wireless couldn't work seems to be nothing attached to the laptop.
I've updated the system kernal and so ... but no change.


now i'm using another laptop because of this problem.

i'm really need help .. i don't know what to do and why this issue happened.

thank you in advance and i'm so sorry for my language.

---

### Post by Mark Phelps on 2013-03-13
This is EXACTLY why I advise folks NOT to force Ubuntu (or any other Linux distro) onto an untried laptop.  You should ALWAYS try it out in LiveCD or Live USB mode first -- to find exactly the problems you ran into.  Then, you can do searches in the forums to see if there are drivers that fix those problems -- and if there aren't, you still have a working laptop.

The Ubuntu installer scans the hardware during the installation and installs the drivers needed for the hardware in the laptop.  Problem is, laptop suppliers are know to use specialized hardware for which, in many cases, there simply are no Linux drivers.

If the  mouse connects through USB, and it's not being detected, you should go into your BIOS and see if there is an option to enable USB Legacy mode.  IF that is there, enable it. The mouse should work after a reboot.

Wireless is a different problem, and running the command "lspci" will list out the hardware specs so we can at least see what wireless chipset you have on the laptop.  Once you see that, you could do a search on that information in the Networking section to see if anyone else has it working.

Another -- much more serious -- problem with wireless on laptops is that there is often a switch (or button) you use to turn ON the wireless in the laptop.  In Windows, this works just fine because the laptop OEMs were sure to include the special drivers needed to work that switch or button.  But once again, those drivers are generally NOT available in Linux.  On the Hp laptops I've use, the "button" always glowed BLUE when wireless was enabled.  I always kept Windows around on my laptops because that was the ONLY way you could re-enable wireless if the button got pressed accidentally and turned it off. You need to check the manual for the Acer laptop to see how that is done.  IF you find the button, and it is now glowing, and pressing it does not cause it to glow (presuming it SHOULD glow when wireless is enabled), then you're likely to be out of luck.

---

