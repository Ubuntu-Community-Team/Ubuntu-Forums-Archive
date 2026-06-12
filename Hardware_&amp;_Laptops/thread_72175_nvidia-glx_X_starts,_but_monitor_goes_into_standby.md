---
title: "nvidia-glx: X starts, but monitor goes into standby"
date: 2005-10-05
forum: Hardware &amp; Laptops
---

### Post by TDKBacke on 2005-10-05
Hello,

a couple of days ago I installed Ubuntu 5.04 (386) on a machine with the following video hardware:
**graphics card:** Gainward 6600GT Golden Sample (PCIe)
**monitor:** Hyundai Deluxscan 15G

Everything worked from the beginning, including X (using the "nv"-driver).
Then I did the well-known "apt-get install nvidia-glx; nvidia-glx-config enable" and the fun was over. ;) Since then the monitor goes into standby whenever X starts. Judging by the output of startx (please scroll down to see the whole log and the content of xorg.conf) and the kde startsound coming out of the boxes, X itself seems to work without problems. If I change the driver section in xorg.conf back to "nv" or "vesa", the problem with the self-deactivating monitor is gone.
Neither the manual installation of the 7667 drivers from the nvidia-homepage nor additions to xorg.conf like "Option "nvagp" "0"" helped.

There are only two warnings in Xorg.0.log. The first complains about the missing apm-device. This shouldn't be a problem since I'm using acpi.
The second says the given values for hsync and vsync would be out of range. This is strange because according to [this site](http://hanzubon.jp/Vine/VineSeed/sparc/Vine/instimage/usr/X11R6/share/Xconfigurator/MonitorsDB) the values are correct and I used that monitor before with an G4 Ti4200 under Debian with the same settings and didn't experience any problems then.

Any ideas? Thanks in advance!
(I found a few threads adressing this problem here and in other places but no solution, so I think it was correct to start this one.)

[xorg.conf](http://jonathan.sv.fh-mannheim.de/~t.kraemer/diverses/xorg.conf)
[Xorg.0.log](http://jonathan.sv.fh-mannheim.de/~t.kraemer/diverses/Xorg.0.log)

---

### Post by brentoboy on 2005-10-05
what is your motherboard?

---

### Post by TDKBacke on 2005-10-05
motherboard: Asus A8N-E (socket 939)
CPU: Athlon64 3200+ Venice E6
RAM: 2*512MB DDR400 Corsair Value Select
PSU: Seasonic SS-350ATC (Hm, maybe 350W are not enough when the hardware acceleration kicks in but the requirements shouldn't be too high when starting a 2D desktop environment ...)

---

### Post by TDKBacke on 2005-10-06
Seems to be a hardware problem.
Today I installed Windows XP and it shows exactly the same behaviour: As long as the standard drivers are used there are no problems. After installing the drivers from nVidia and a reboot the monitor goes into standby. Again, the startsound indicates an otherwise normal start of the desktop environment.

Would you agree that the relatively weak PSU is the troublemaker? (Unfortunately I don't have access to another motherboard supporting PCIe, so I can't test the graphics adapter.)

---

