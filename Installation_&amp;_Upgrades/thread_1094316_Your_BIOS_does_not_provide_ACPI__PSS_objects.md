---
title: "Your BIOS does not provide ACPI _PSS objects"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by old_salt on 2009-03-12
Wondered if anyone has experienced this problem;

[Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.

Occurs after;
Installing Jaunty 64bit 

System Specs

Asus M3N78 Pro
AMD 5800 X2 64bit 3.0GHz
Corsair DDR2 Dual Channel 4Gb
WD 500Gb Drive Sata3
Seagate 1.5Tb Drive Sata3
HP 1070 Lightscribe burner
nVidia 8300 Video (integrated)
Hauppauge WinTV-PVR150


Any ideas or recommendations as to maybe some kernel booting parameters I may need to add?

---

### Post by Neo_The_User on 2009-03-12
Turn off powernowd on start-up. /etc/rc.X. or the easy way:

Terminal:
```

sudo apt-get install rcconf
sudo rcconf

```

Hit the space bar on everything that has to do with powernowd (turn off cups too unless you need it) then press Tab to select OK then press enter.

---

### Post by ea185028 on 2009-04-28
> **Neo_The_User said:**
> Turn off powernowd on start-up. /etc/rc.X. or the easy way:

Terminal:
```

sudo apt-get install rcconf
sudo rcconf

```Hit the space bar on everything that has to do with powernowd (turn off cups too unless you need it) then press Tab to select OK then press enter.


Hi i just did the sudo thing but i still have the same problem, i tried to do the startup fix but it says something about path. This is my first time using ubuntu.

And on the rcconf window i took out anything that was about ACPI in my case there were two but that didnt work either

---

### Post by griachae on 2009-11-04
Hey there !
 
I upgraded from 9.04 to 9.10 and the first time it worked really good but after updating i had the same problem with this firmware bug.
 
 
I tried:
 
```
sudo apt-get install rcconf
```
and
```
sudo rccon
```
then mark all with the spacebar and press tab and enter (ok)
 
but in my case it didnt work too and the problem is still the same:
 
[Firmware Bug]: powernow-k8:Your BIOS does not provide ACPI_PSS Objects in a way that linux understands. 
Please report this to the linux ACPI maintainers and complain to your BIOS vendor.
 
----------------------------------------------------------------------------
 
 
 
The real strange thing about it is that ubuntu 9.04 did run perfect with my BIOS settings and so does Vista.:???:
 
 
 
Well it would be great if somebody knows what to do to get ubuntu 9.10 run
 
thx

---

