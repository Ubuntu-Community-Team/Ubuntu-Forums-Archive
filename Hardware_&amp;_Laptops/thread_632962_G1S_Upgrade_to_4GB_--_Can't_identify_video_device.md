---
title: "G1S: Upgrade to 4GB -- Can't identify video device"
date: 2007-12-06
forum: Hardware &amp; Laptops
---

### Post by Miyabina on 2007-12-06
I had Ubuntu 7.10 installed on my ASUS G1S-A1. Was starting to mess around with it a bit etc. I then saw a sale on some laptop memory. 

So I went out and bought it, and installed it... upgrading from 2GB to 4GB. BIOS saw the full 4GB just fine. 

Booted in to Ubuntu and it threw me a message saying that it couldn't find the video device and wanted me to configure it. So I did, but it wouldn't do anything other than the 800x600. I uninstalled/reinstalled envy, and rebooted... still gave me the message of not identifying the video. Did a sudo nvidia-xconfig and restarted X... still wasn't working right.
-- That was all under 32bit

So I tried to boot off of a livecd for 64bit... no splash screen while loading and then when it finally loads X or whatnot... gives me the same error of not detecting.

Vista boots/runs just fine (32bit though, so only sees a portion of the ram).

Really confused on whats going on here, any suggestions or advice would help. If you need more info let me know :)

---

### Post by daengbo on 2007-12-06
The integrated wideo uses shared emmory? Could that be part of the problem? Could the shared video RAM be above some limit in the driver? Finally, are you using the NV driver or NVidia's?

---

### Post by Miyabina on 2007-12-06
I think most if not all notebook video adaptors use system ram for extended video ram, at least in windows (but I believe that is coded in the drivers). It has the 8600m GT 256mb adaptor in it though, so it does have some vram. I've tried the nv driver thats on the livecd/base install and the downloaded one from nvidia. Both just made Ubuntu throw the "undetected video" error.

---

### Post by Miyabina on 2007-12-06
Yipe:
[http://forum.notebookreview.com/showpost.php?p=2738605&postcount=258](http://forum.notebookreview.com/showpost.php?p=2738605&postcount=258)

"BIOS 205 and early has address conflict with Intel PCIE Port. It mapped to the Video adapter memory range. Only Vista64, can remap resources, but i saw on Internet, that somebody tweak Linux kernel, so Xorg will remap Video Adapter, but this is not official kernel patch. I am waiting for Asus to fix it too. Mandriva 2008 64 will not boot to Xorg if you put 4GB RAM, only 2 working right now." -- os2 on notebookreview.com forums

full thread:
[http://forum.notebookreview.com/showthread.php?t=146088&page=26](http://forum.notebookreview.com/showthread.php?t=146088&page=26)

So... yeah... if someone can help me with a workaround perhaps that would be fantastic. Thanks.

---

### Post by Miyabina on 2007-12-07
I found a kernel patch here
[http://www.nvnews.net/vbulletin/showthread.php?t=96613&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=96613&page=2)

Patched/compiled/installed the new kernel
Now I don't have wifi or sound (old kernel I did)
Any ideas what I should do?

---

### Post by Miyabina on 2007-12-08
Well I copied my /lib/firmware/2.6.22-14-generic to /lib/firmware/2.6.22.9-custom and my WiFi started to work. Downloaded the newest alsa and did a make && make install for that and now sound works. So pretty much all up and running :)

---

