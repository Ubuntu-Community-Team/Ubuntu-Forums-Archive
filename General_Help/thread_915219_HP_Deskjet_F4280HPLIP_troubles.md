---
title: "HP Deskjet F4280/HPLIP troubles"
date: 2008-09-09
forum: General Help
---

### Post by dcast on 2008-09-09
Hi, I'm running Kubuntu 8.04 64 bit on my laptop and I am trying to configure a new all in one printer/scanner/copier. It is an HP Deskjet F4280 I installed the latest HPLIP (2.8.7) from the .run file and haven't been able to get the printer working. It claims that the printer is busy or is in an error state, I try and run the hplip again and it will tell me that CUPS isn't installed when it definitely is. Hopefully someone can help me get this working, I feel like it should be pretty easy since it is definitely supported by hplip-2.8.7. Thanks for your help in advance.

DCast.

---

### Post by LowSky on 2008-09-09
after installing HPLIP unplug the printer and restart your computer
then once the computer has rebooted, plug the printer back in. It should now install just fine.

---

### Post by dcast on 2008-09-09
I tried the restart, it didn't get me any further. Thanks for your reply.

DCast.

---

### Post by PsychoBee90 on 2008-09-09
Argh, I bought this printer because HPLIP said it was supported. Ubuntu recognizes and installs the printer when I plug it in, but printing won't work. The job is in "processing" mode for a few seconds, then it says "complete" even though nothing ever printed. Please, does anyone know how to fix this? :(

---

### Post by PsychoBee90 on 2008-09-10
I was using HPLIP from the repos and after installing the version from the HPLIP website it works like a charm!

---

### Post by dcast on 2008-09-10
Hi guys, got it working now, thanks for your help.

DCast.

---

### Post by BCtom on 2009-01-22
I'm curious, has anyone ever got the HP F4280 to work with Open Office? 

I've installed it on a friend's machine, who just bought one, and it prints fine from the HPLIP GUI, but doesn't from Open Office. Is there a fix for this?

FYI I had to install it from the HPLIP Web-Site, the repos did not work for me either.

---

