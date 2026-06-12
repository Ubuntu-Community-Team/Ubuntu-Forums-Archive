---
title: "LG R700 notebook wireless device has disappeared"
date: 2008-09-17
forum: Hardware
---

### Post by Kossilar on 2008-09-17
Hey all. 

I just installed Fluxbuntu on my R700 and everything works well other then the video card which unfortunately is not supported in Linux by either NVIDIA or LG.

The wireless was working fine until today when suddenly the system can no longer detect the wireless at all. 

I checked to make certain that I hadn't disabled it accidentally and restarted the notebook several times but to no avail. The wireless lan device simply isn't being detected anymore.

Does anyone know what could be causing this? :confused:

---

### Post by Kossilar on 2008-09-17
I just tried booting into safe mode and in safe mode the wireless is working. Does anybody know what's causing it to fail on normal boot? 

I'm running Fluxbuntu 7.1 on an LG r700 laptop.

EDIT: Apparently this problem is being caused by the OS loading the wrong kernel on boot. I'm not certain how I ended up with a server kernel being loaded, but apparently it doesn't detect my wifi card. now I need to figure out how to disable that kernel in grub so that the generic kernel is loaded by default.

---

