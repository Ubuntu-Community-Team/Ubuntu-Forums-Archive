---
title: "Faster driver for Radeon X1200"
date: 2011-10-15
forum: Hardware
---

### Post by xodeus on 2011-10-15
Hi all.
My GF has a Toshiba Satellite A210 with a ATI Radeon X1200 graphics chip.
It seems though that no driver is loaded for this graphic chip or it isn't identified by Ubuntu. 
```
michelle@michelle-Satellite-A210:~$ lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS690M [Radeon X1200 Series] [1002:791f]

```
As seen in System Info it seems that no driver is loaded or it's unknown.
How do I load the Radeon driver on boot for a little faster Unity, Flash and Java performance?

Thanks in advance.

---

### Post by 2F4U on 2011-10-15
Look into /var/log/Xorg.0.log to see what driver X actually uses.

---

### Post by xodeus on 2011-10-15
Can't see which driver it loads.
It loads some modules like radeon, fglrx, vesa and ati and unloads some and loads some others, so I can't see which driver my Ubuntu is using.
Here's the log file [http://pastebin.com/St0u2FBu](http://pastebin.com/St0u2FBu)

---

### Post by foresthill on 2011-10-15
Might try logging in with Desktop Effects turned off. Those are a huge drain on your graphics resources, and IIRC, the Radeon X-1200 is not a very powerful chip, so could probably use all the help it can get.

Looks like you are using the open source "Radeon" driver, which should work fine for 2-D stuff, though I'm not sure if it will run Unity.

---

