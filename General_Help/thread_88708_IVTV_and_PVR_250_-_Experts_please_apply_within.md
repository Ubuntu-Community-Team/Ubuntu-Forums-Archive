---
title: "IVTV and PVR 250 - Experts please apply within"
date: 2005-11-10
forum: General Help
---

### Post by dbeckham32 on 2005-11-10
Okay, I've tried just about everything I can and I'm still having much trouble getting my new Hauppauge WinTV-PVR-250 working correctly with IVTV.

From what I can gather, I've install IVTV correctly (kernel headers and all - not bad for a recent Windows convert!) and I'm using the correct firmware. My dmesg reports that the module and firmware are loading okay -- but it's generating a very annoying "ivtv0 warning: i2c client" error.

Does anyone have experience getting IVTV working correctly on Breezy? I've already read most of the IVTV-related messages in this forum, as well as those on gossamer-threads.com and Christopher Scholz's website. I need help!

Attached below is my dmesg and a list of the device settings.

Any assistance would be very, very much appreciated. I refuse to boot to Windows to use my PVR!

---

### Post by dbeckham32 on 2005-11-12
Okay, I've managed to get the ivtv driver working great. I am able to caputre video using cat /dev/video0 > ~/test.mpg.

Still trying to get tvtime, xawtv and MythTV working. Wish me luck.

---

### Post by krye on 2005-11-12
Good Luck :)

---

### Post by micjustmic on 2006-01-05
[QUOTE=dbeckham32]Okay, I've managed to get the ivtv driver working great. I am able to caputre video using cat /dev/video0 > ~/test.mpg.

Still trying to get tvtime, xawtv and MythTV working. Wish me luck.[/QUOTE]

How did you get it working?  I'm getting the exact same errors.

Thanks,
Mic

---

### Post by micjustmic on 2006-01-05
Okay, here's a strange thing . . . I got the card working, but every time I reboot, it stops working . . . same errors . . . BUT . . . if I open the CMOS setup and change the IRQ for the PCI slot, it works again.

It doens't actually use the IRQ I set it to, and I don't even have to change the IRQ of the actual tv card, as long as IRQ steering is forced to reset the IRQs the TV card works again.  

Anyone have a clue on this one?
Mic

---

### Post by whoisvince on 2006-01-05
Yeah, I had a similar problem with a PVR-150.  I was able to fix it by clearing my NVRAM settings in CMOS.  Look for an option like "reset configuration data" in the PCI settings menu.  I was having the problem both in Windows and in Ubuntu and that fixed both.

---

### Post by micjustmic on 2006-01-05
Thanks for the reply, gave it a shot, didn't work.

I'm stumped.  

It's as if the drivers insist on the machine resetting the IRQ table before it will work.

At least I know now a way around it, I was frustrated for days when I'd re-install, it would work then on reboot, nothing.

Yeesh! 

What a PITA.  BUT, at least now I don't have to boot windblows to watch TV (No remote, yet, but I'm working on it.)  

Mic

---

