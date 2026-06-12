---
title: "Live CD doesn't boot on laptop"
date: 2008-12-14
forum: Installation &amp; Upgrades
---

### Post by Donnw on 2008-12-14
I have tried to boot a Live CD on an Advent 5421 laptop. The initial boot menu loads ok but when the 30secs is up and the live cd tries to boot the orange horizontal progress bar works for a few seconds and then freezes. The CD drive then stops spinning and nothing else happens even if left for a long time. The versions of Ubuntu tried were 7.04 and 7.10.  I have now just tried 8.10 from a CD and a bootable USB stick with exactly the same result. On the USB stick the light stops flashing at the same point on the boot up as when the disk CD stopped spinning.

---

### Post by tjkeatts on 2008-12-14
I have the same issue on my laptop. I eventually got to X by pushing the arrow keys, enter and esc (randomly) until the orange bar started moving again. I then installed Ubuntu 8.10, ran updates and now still have the same problem. When I press Alt+Crtl+F1 on the boot I find that it hangs after "kinit: No resume image, doing normal boot..." if I hit enter then it will continue on to hang again at "starting common unix printing system: cupsd". After a long wait (2 min) it will eventually start X and everything is normal.

I am running the 2.6.27-9-generic kernel.

Thanks in advance for the help.

---

### Post by tjkeatts on 2008-12-15
Ok. I got it to work on my laptop by using the following:

Live CD
at the boot selection screen used the F6 option and select "APIC=off"

Installed
edit the "/boot/grub/menu.lst" file and add "noapic" to the end of the boot string

---

