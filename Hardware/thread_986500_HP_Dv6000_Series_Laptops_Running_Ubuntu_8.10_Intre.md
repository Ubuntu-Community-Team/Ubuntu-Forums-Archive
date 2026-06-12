---
title: "HP Dv6000 Series Laptops Running Ubuntu 8.10 Intrepid Ibex"
date: 2008-11-18
forum: Hardware
---

### Post by bluefox83 on 2008-11-18
I want to start this thread so people can find out what happened at the end of several other threads that were posted under this topic while Intrepid was still in beta, and the threads have since been closed. 

I would like information as to whether a solution has been found for the boot-up issue, where you need to hold a key in order for the status bar to finish and for the gnome login screen to come up.


Also I have noticed that there were posts about really bad battery life in the DV6000 series in Intrepid. Have there been any discoveries about this at all? any fixes?

Some folks reported issues with the nvidia card drivers and wifi drivers not working, have those issues been resolved? 

I personally have the boot-up and battery issues, however I got my nvidia card and Wifi card to both work just fine by re-loading the drivers.

Any info will help!

---

### Post by RSVampire on 2008-11-23
I have an HP DV9608nr laptop and while I don't share your driver problems I do have the boot-up issue that you describe. I also have the same issue while it's shutting down the machine as well. Other than these minor (yet still VERY inconvenient) I've been doing great with the new Ibex install.

---

### Post by bluefox83 on 2008-11-24
did you do a fresh install of Intrepid or did you upgrade from hardy?

---

### Post by elhijodelpeje on 2009-03-13
I have the same boot up problem with my HP DV-6646US, and after several atempts, found that it is a problem on ubuntu 8.10, either fresh installed from alternate or live CD or upgrading from 8.04, because I re-installed Ubuntu 8.04 and had no problem at all, except you have to update it cable connected to internet in order to have your broadcom Wi-Fi and Nvidia video working. Then when I upgrade it to 8.10, it started hanging at boot, requiring to press any key to continue.
I suggest to either get used to the "press any key" solution, or re-install Ubuntu 8.04 which works perfectly after updates, but DO NOT, I repeat, DO NOT UPGRADE TO 8.10 until somebody finds a fix to that.

R. Robles

---

### Post by elhijodelpeje on 2009-03-13
Just found the fix in another forum, go to [http://ubuntuforums.org/showthread.php?t=972910](http://ubuntuforums.org/showthread.php?t=972910) and look for an answer from Josueped, 
it says you should go in terminal and do  sudo gedit /boot/grub/menu.lst
then enter your root password, then add acpi=noirq  to the end of line
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=3593af83-0c05-49cd-ae39-d3d4ebb8c8f4 ro quiet splash     so it looks like 
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=3593af83-0c05-49cd-ae39-d3d4ebb8c8f4 ro quiet splash acpi=noirq

save it and restart 

It worked for me
Enjoy the best linux ever
R.Robles

---

