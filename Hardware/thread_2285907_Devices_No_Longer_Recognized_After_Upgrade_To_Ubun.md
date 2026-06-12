---
title: "Devices No Longer Recognized After Upgrade To Ubuntu 15.04"
date: 2015-07-09
forum: Hardware
---

### Post by jeffroaltiere1 on 2015-07-09
I recently updated my HP G42 laptop to Ubuntu 15.04 from Ubuntu 14.10. When I went to boot it back up, it started fine, as if nothing were wrong. But, when I went the my internet browser (Firefox), I had no connection, and that's when I noticed that I wasn't connected. The card, a Broadcom 4313 (I've already tried the general Broadcom thread for a fix here) won't even find any networks. I've tried inputting the network as a hidden network, and that doesn't work.  I tried to upload the drivers via a usb stick, and I noticed that when I plugged it into the laptop, it wasn't being recognized. I tried running the command in the terminal that shows all the devices, and I don't remember seeing the usb devices or the sticks listed in the list of devices.  If I could get any help with this, that'd be nice. I really would like to be able to use this laptop again without having to wipe it and start fresh (that'd be bad for the disk overall). I'll try posting the command (I think it was lspci) results when I run it again. I'm doing this from an iCloak Stick on said laptop.

---

### Post by dino99 on 2015-07-09
from your package manager (synaptic) check that the 'broadcom' or 'bcmwl-...' package is installed

---

### Post by jeffroaltiere1 on 2015-07-09
Okay, so I booted to the laptop earlier, and it seems that the system is recognizing my usb ports once again. I don't know why it refused to do it the last few times. I know it wasn't issues with the usb drives themselves. I guess I'll keep an eye out and have a look around or post again if it comes up.

As for the wireless issue, I checked Synaptic, and I have bcmwl-kernel-source installed, but that is it. I do NOT have the common files installed, nor the b43-fwcutter package installed. Perhaps I need those? I'm not sure.

---

### Post by jeffroaltiere1 on 2015-07-09
As for the list of recognized devices, they all seem to appear now. Here was the command I ran.

[ATTACH=CONFIG]263103[/ATTACH]

---

### Post by Vladlenin5000 on 2015-07-09
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by jeffroaltiere1 on 2015-07-09
I was looking for that. Thanks for that!

---

### Post by Vladlenin5000 on 2015-07-09
You're welcome.

If it's solved then please use the thread tools to mark it as such for the benefit of future forum users. Thank you.

---

### Post by jeffroaltiere1 on 2015-07-10
Okay, so the issue is solved, but I seemed to have found the root cause of the issue. I think I have to do a full refresh of Ubuntu. The upgrade went bad, and every time I go to update from the command line, I'm told: "557 packages are either no fully installed or missing".

---

### Post by dino99 on 2015-07-10
> **jeffroaltiere1 said:**
> Okay, so the issue is solved, but I seemed to have found the root cause of the issue. I think I have to do a full refresh of Ubuntu. The upgrade went bad, and every time I go to update from the command line, I'm told: "557 packages are either no fully installed or missing".

indeed that is more than expected ;)
again synaptic will help you upgrade step by step and will let you know what is wrong. Maybe first remove the cache: > sudo rm /var/cache/apt/archives/*
then update (only if your /etc/apt/sources.list is clean) after disabling the 'third party' sources into synaptic (if any)

---

