---
title: "Dual Screen not working after ATI Driver install"
date: 2009-03-03
forum: Hardware
---

### Post by kOna on 2009-03-03
Hi Guys & Gals, hope you can help me with this problem :)

I have just installed Ubuntu and first start up it detected my two monitors attached to my ATI Radeon 4850, the Restricted Hardware Installer prompted me to install the ATI Driver so I did - upon reboot Ubuntu no longer detects both screens!

I'm sure someone has had this problem before but I can't find a solution even after searching!

Cheers,

Craig

---

### Post by kOna on 2009-03-26
I've been away with work since I last posted so I haven't had a chance to update this thread, although it's had no replies.

I have managed to get dual screen working through the ATI Control Centre but it refuses to keep the settings for "Big Desktop" (spread the whole desktop over two screens) after a reboot. Does anyone know how to stop this from happening? If I can get this problem sorted I'll be able to use Ubuntu 24/7 rather than Vista at home, still stuck with Vista at work though.

Cheers,

Craig

---

### Post by kOna on 2009-03-30
I'm really surprised this thread has had no replies as it seems a lot of people are having exactly the same problem as me. I am still no further forward with this, being a bit of a newbie to Linux (although I've dabbled in the past) I don't really know where to start looking.

Any suggestions?

---

### Post by robobart on 2009-08-21
Hi, did you get this working?

I have the same problem.

---

### Post by Yellow Pasque on 2009-08-21
Put this is in the device section of /etc/X11/xorg.conf:
```
Option      "EnableRandR12" "false"
Option      "DesktopSetup" "horizontal"
```

---

### Post by robobart on 2009-08-21
Sorry but should it be like this?

Section "Device"
   Option      "EnableRandR12" "false"
   Option      "DesktopSetup" "horizontal"
EndSection

Should there be an identifier or anything? 
(I don't understand the xorg.conf file)

---

### Post by Yellow Pasque on 2009-08-21
Sorry, I should have said, "append" the lines to the device section. Yes, keep the identifier and driver lines (and whatever else you have there).

---

### Post by robobart on 2009-08-21
Didn't seem to work for me - Kona did you try this?

---

### Post by robobart on 2009-08-28
I got this working - check out

[http://ubuntuforums.org/showthread.php?t=1045822&page=2](http://ubuntuforums.org/showthread.php?t=1045822&page=2)

---

