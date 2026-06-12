---
title: "NVIDIA Drivers 1st time linux"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by t3cKn0t0x1n on 2009-03-12
i just installed ubunutu about an hour ago, i got the wireless PCI adapter working, but i am running 8.10, i have a 9800gt from nVidia, and the drivers just wont install.


i pressed Cntrl + Alt+F2, i logged in, did sudo sh

did init 3
did sh NVIDIA-Linux-x86_64-180.29-pkg.run

and it still said you are running an X server,

but i though init 3 exited the X server


i even did /ect/init.d/gdm stop


and it said it couldnt find it


im really frustrated and im about to switch back to windows


:(

---

### Post by Cresho on 2009-03-12
did you try system->administration->Hardware drivers?

---

### Post by t3cKn0t0x1n on 2009-03-12
yes, whenever i try to install the NVIDIDA drivers from there, i press activate, and it says downloading and installing driver, and it stays at 0% for like 2 seconds then it closes, no error messages after either.

---

### Post by Cresho on 2009-03-12
did you reboot?

---

### Post by t3cKn0t0x1n on 2009-03-12
ugh dude, i honestly doubt that could be the problem, and im on limited time also, so ill give it a try.

keep on trying

---

### Post by Cresho on 2009-03-12
try this link

[http://guide.ubuntuforums.org/showthread.php?t=909460](http://guide.ubuntuforums.org/showthread.php?t=909460)

make sure you rebooted and its working.  look at the hardware drivers and see if its activated.  I remember windows.  I was in your situation for a bit.  I had a spanking new 8800gt and had problems recording from microphone in.  I got both those resolved.  Don't give up, ubuntu is really good.

---

### Post by t3cKn0t0x1n on 2009-03-12
Its a good link, but i think that was a tottaly different topic, i rebooted, and i tried to activate the drivers, same thing happened again,


ANDD. i cant even watch youtube videos, i tried downloading the latest flash player (.deb) and it says wrong arctitecture i386

i am extreemly frustriated

---

### Post by Cresho on 2009-03-12
what was wrong with the link i sent.  I expected it to be helpful.

---

### Post by t3cKn0t0x1n on 2009-03-12
Its was so close, that one had to do with 8.04 and the debate between the restriced drivers and the nVidia drivers, but i cent even install ANY drivers, whether it be from ubuntu or from nVidia


:(

---

### Post by Gaphumbala on 2009-03-12
I have not been able to get that driver version working either.  Try installing 177.82.33, it seems to work fine.

---

### Post by t3cKn0t0x1n on 2009-03-12
It says version 177 (reccomended) but it does the same exact thing, im about to put in the windows CD

:(((((

---

### Post by Gaphumbala on 2009-03-12
I assume you did a complete uninstall of the previous driver?

---

### Post by t3cKn0t0x1n on 2009-03-12
well im installing the 227 updates now, god im so stupid.

it might solve the problem. and im still giving a try with linux, windows 7 is a real treat though.

---

### Post by Gondee on 2009-03-12
Are you running a 64 bit version?? That could be the problem

---

### Post by oldos2er on 2009-03-12
> **t3cKn0t0x1n said:**
> i tried downloading the latest flash player (.deb) and it says wrong arctitecture i386

 You're running Ubuntu 64-bit? See [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

