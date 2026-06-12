---
title: "Ubuntu Hardware Specific?"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by Steve60938 on 2009-11-06
ok My sister saw my pc and decided she wants to have ubuntu as well. Can i just install it on her hard drive using my pc and just make sure the packages for her vid card and sound and stuff are installed or is it like windows where the operating system has to be installed from the same pc or you get blue screen.........for example if i had xp installed and tried to move the hard drive to a new pc it would give me a blue screen of death. I really hope someone understands this lol.

---

### Post by SunnyRabbiera on 2009-11-06
Ubuntu should have no issues here actually, with linux unlike windows it does a very good job at detecting hardware when it comes to moving the hard drive from computer A to computer B.

---

### Post by Steve60938 on 2009-11-06
cool thanks, her pc is slow and annoying thats why if you were wondering why i would wrather install using my hardware lol

---

### Post by SaintDanBert on 2009-11-06
> **SunnyRabbiera said:**
> 
Ubuntu should have no issues here actually, with linux unlike windows it does a very good job at detecting hardware when it comes to moving the hard drive from computer A to computer B.


Unlike win-dose, the install does not embed disk drive or other hardware details into the target files. It does not try to use workstation-A knowledge to prevent or otherwise cause grief when installing onto workstation-B.

I routinely use an open-chassis box to complete installs. I then grab the drive and move it into an alternate box with similar hardware.
Boots and runs fine.  Even if there are minor differences in hardware, boot time hardware fondling sorts this out in most cases.

Good Luck,
~~~ 0;-Dan

---

### Post by Steve60938 on 2009-11-07
ok having an issue here, i installed ubuntu updated to 9.10 then transfered the hard drive to a new pc. everything works including 3d effects and what not HOWEVER i cannot change the resolution 'cept bewteen 640x480 and 800x600 The video driver is installed and the compiz effects are enabled on full so i'm lost.

---

### Post by Steve60938 on 2009-11-07
help?

---

### Post by coffeecat on 2009-11-07
> **Steve60938 said:**
> The video driver is installed

What video driver?

It sounds as though the problem is with your sister's monitor not putting out any/readable EDID data, so the xserver has to default back to safe resolutions. The xserver has been autodetecting the monitor in versions going back a year or more now, which is why with recent versions of xorg you get no or a minimal xorg.conf.

However you can create your own xorg.conf with monitor resolutions in it. If it's present, xorg will use those settings, otherwise it has to rely on autodetect.

You need to post details of the monitor - make, size, optimum resolution, and so on. If you need help creating an xorg.conf, someone should be able to help.

---

### Post by Steve60938 on 2009-11-10
ok well i figured out how to write a new config file all on my own go me, thanks for the help guys

---

