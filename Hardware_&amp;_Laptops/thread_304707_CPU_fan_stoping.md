---
title: "CPU fan stoping"
date: 2006-11-22
forum: Hardware &amp; Laptops
---

### Post by digitalfreedom on 2006-11-22
this is going to sound nuts but my cpu fan stops when i run Ubuntu.its the 6.10 version.i can see my fan through my case side panel and it stops as sure as im alive.Its an Intel celeron 1.79 GHZ.i had to take a case fan and put onto the fan assembly to keep it  cool.any suggestions? and the cd tray wouldnt open after i finished the full install.other than this it works fine.

---

### Post by bigken on 2006-11-22
buy a new fan its sticking and the cd ejects its self during the reboot process

---

### Post by digitalfreedom on 2006-11-22
i dont need a new fan.it works fine under windows and at the GRUB screen its only when i boot into Ubuntu it stops.

---

### Post by bigken on 2006-11-22
go into the bios and check your fan temp settings

---

### Post by digitalfreedom on 2006-11-22
the bios? are kidding me...its not my computer.its this ubuntu software thats stopping it.so no help here so bye

---

### Post by clementine on 2007-01-07
Same problem here. The fan runs at startup, in grub, and if I boot into WinXP, but if I'm in Ubuntu (6.10) -either Gnome or KDE- no fan. 
Though the fan does not run, the system can indicate fan state and what seems to be accurate temp readings, and when it hits a certain temp, BYEBYE!- computer shuts down. That's a drag. It would also be a drag to burn out the CPU. 
I'm new to Ubuntu and Linux but I'm totally willing to try any terminal commands that will activate the fan. So far all I've read seems to apply to laptops (This is a cheap old eMachines tower)- or is way over my head. Any suggestions?

---

### Post by zgornel on 2007-01-08
Check for the fan module (lsmod |grep fan). If it is not present, modprobe fan

---

### Post by esaym on 2007-01-08
Worse case there are adapters available that will run the fan off of one of the power supply plugs instead of the small plug on the mother board.

[http://www.svc.com/3pinto4pinad1.html](http://www.svc.com/3pinto4pinad1.html)

that one will retain the rpm sensing ability but you will lose any kind of fan rpm control if that is even supported...

---

### Post by glabouni on 2007-01-08
I would recommend using dapper drake instead of edgy eft.

> [COLOR="Red"]Also note that Edgy 6.10 is considered a development platform for testing new ideas,and technology. Use of this version,and coming versions there after are at your own risk.[/COLOR]
**First Time Linux/Ubuntu users are advised to use dapper,and not edgy as their frist step into Linux. **

(...)

**Note: New users who choose to use edgy as their Operating system are urged to used caution,and advised to know and understand how to fix your own issues. You have been warned.**
[http://ubuntuforums.org/showthread.php?t=286209](http://ubuntuforums.org/showthread.php?t=286209)

---

### Post by tweedledee on 2007-01-09
> **clementine said:**
> Same problem here. The fan runs at startup, in grub, and if I boot into WinXP, but if I'm in Ubuntu (6.10) -either Gnome or KDE- no fan. 
Though the fan does not run, the system can indicate fan state and what seems to be accurate temp readings, and when it hits a certain temp, BYEBYE!- computer shuts down. That's a drag. It would also be a drag to burn out the CPU. 
I'm new to Ubuntu and Linux but I'm totally willing to try any terminal commands that will activate the fan. So far all I've read seems to apply to laptops (This is a cheap old eMachines tower)- or is way over my head. Any suggestions?

Try following this thread to see if you can get accurate readings and/or regulate it: [http://www.ubuntuforums.org/showthread.php?t=250025](http://www.ubuntuforums.org/showthread.php?t=250025).

---

