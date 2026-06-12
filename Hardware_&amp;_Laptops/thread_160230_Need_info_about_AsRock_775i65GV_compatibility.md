---
title: "Need info about AsRock 775i65GV compatibility"
date: 2006-04-14
forum: Hardware &amp; Laptops
---

### Post by alea on 2006-04-14
Hallo, 

Could anyone please tell me whether the motherboard AsRock 775i65GV is supported by Ubuntu? Especially the onboard ethernet card, the onboard graphic card, the onboard ide controller and the onboard sata controller.

Further, I read in its manual, that the bios supports suspend to ram. Could anyone please tell me whether ubuntu will override it and allow a suspend to disk? 

The specs say that the ethernet card supports wol. Will I be able to wake the computer up by wol, after it has suspended to disk (or ram)? 

Finally, what ubuntu version should I use to have the features indicated above? 

Thanks in advance. 

alea

---

### Post by Faust942 on 2007-03-21
I have problems with this motherboard too.

Whenever it tries starting up it gives me a bunch of text that scrolls across the screen. I have tried Safe Mode and that hasn't worked.

I'm pretty sure it the Hardware Drivers.

Can anyone help us out?

P.S.
Is there a way I can take a screenshot with garbbled text on the screen and able to transfer it on here? Print Screen is the only way I know for un-GUI.

---

### Post by gsiliceo on 2008-04-25
I have that motherboard and it works everything out of the box with all the ubuntu releases, i haven't tried hardy yet thou. Will this afternoon.
I used to have problems with that motherboard and my graphic card a fx5200, you might have them with another nvidia cards too, and it won't boot, i solved it adding this line
> blacklist intel_agp 
to this file
> /etc/modprobe.d/blacklist
You might need to open the file with sudo rights or
> gksu gedit /etc/modprobe.d/blacklist

---

