---
title: "Nvidia Driver problem"
date: 2009-04-03
forum: Installation &amp; Upgrades
---

### Post by silentviper324 on 2009-04-03
I'm brand new to linux and I have an Nvidia 9800 GTX graphics card in but ubuntu won't let me change the resolution to above 800x600 (the monitor is widescreen and supports up to 1650x1080 i believe. i have followed many other tutorials about installing an nvidia driver and none have been successfull. i've already tried apt-get install nvidia (or something close to that), i've tried manually changing the xorg.conf file with no luck. Does anyone have anything else i could try doing to help me get past this problem? All help is greatly appreciated

~Blake

---

### Post by Starmartyr on 2009-04-04
Try using this: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Hope it helps

---

### Post by silentviper324 on 2009-04-04
Thank you very much for the reply. It didn't fix the problem though. Come to find out, i didn't have all of the libc headers that were required in the installation. So the problems fixed. Thanks though. :D

---

### Post by NooNoo on 2009-04-04
hi i have a similar problem is there any chance you can recall what libc headers you installed or where they were from ???

---

### Post by silentviper324 on 2009-04-04
I used System>Administration>Synaptic Package Manager and I searched for libc. I didn't know specifically what ones nvidia needed so i just selected a good chunk of them (no dev files though) then reran the installer and it worked. If it doesn't work the first time, go select some more. I know thats not a very good way of solving problems like this but it worked and I have plenty of disk space to spare. :D Good luck. Let me know if it worked.

---

