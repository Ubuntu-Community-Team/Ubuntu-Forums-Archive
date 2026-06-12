---
title: "lost screen resolution every boot with nvidia geforce 4400 64m"
date: 2010-12-26
forum: Hardware
---

### Post by uhhman on 2010-12-26
Dear All,
i am getting super frustrated by this issue ubuntu is having with the nvidia geforce 4400go 64m of my laptop.
I am running the ubuntu 10.10 64bit edition.

every time i boot the resolution of the password page is correct (1280x800) while once on the desktop is lower (1024x768)..
i then access the monitor preferences, select the right resolution, save to X configuration file..restart computer..and nothing changes :(

Any idea on how to solve this issue?
I have already tried without success "gksudo nvidia -settings"..

thanks for help!

---

### Post by searchfgold6789 on 2011-01-08
I cannot help you with this, but I am having the exact same problem and would like to bump this thread, because I am very interested in seeing how this thread is solved.
I think I will put a script to run at boot that automagically changes the screen resolution in the non-ui nvidia-settings.

---

### Post by Gs Dewd on 2011-01-08
I also cannot help you with this. I am having the same issue with Ubuntu 10.10 on a desktop system with a Ge force fx5700 card. It seems to be a issue with the 10.10 kernel and the Nvidia drivers.I have looked into a few things but have yet found a permanent fix for it.

---

### Post by Soulcage on 2011-01-08
Are the settings in /etc/X11/xorg.conf ?

---

### Post by giannib on 2011-02-17
same for me, quadro fx 1600 on 10.10

---

### Post by hsoulen on 2011-02-17
> **Soulcage said:**
> Are the settings in /etc/X11/xorg.conf ?

This is the answer...

In the "NVIDIA X Server Settings" application under System -> Administration when you change the resolution you need to also click the "Save to X Configuration File" button.

NVIDIA proprietary drivers require the xorg.conf file even if the newest version of X does not explicitly need it.

Give it a shot and let us know the results.

Cheers,

Hank

---

### Post by giannib on 2011-02-17
ah... Already done dozens of times, also with sudo, no way!

---

### Post by Gs Dewd on 2011-07-24
Ah I found a fix to my problem. I replaced the card with a Radeon x1550.:guitar:

---

