---
title: "So I pretty much broke the CRAP out of my computer."
date: 2009-02-05
forum: Hardware
---

### Post by shadowhacker on 2009-02-05
I downloaded the new Nvidia 180 driver from their website, in hopes of getting better video playback with their new API. Instead I broke Ubuntu :(

I got an error upon boot saying something about type 1 and to check if I had a supported card, which I do according to the notes on the Nvidia page I downloaded it from. I got it started in default graphics mode, and I tried going into synaptic and reinstalling all of the 177 stuff. I also re-enabled 177 in the hardware manager.

After doing all of this, X won't start at all, and I can't load Gnome. When I was running the Nvidia installer, it said it was creating a backup of my current config, as a matter of fact, I said yes to it. Does anyone know how to load this back up? I hope I didn't screw myself by trying to reinstall all of the 177 stuff instead of restoring the backup. I knew there was a reason I always bought ATI...

Thanks in advance for the help.

---

### Post by xopher_mc on 2009-02-05
You need to log into the computer with the non graphical Ctrl + F1

then log in

then type 

cd /etc

ls | grep xorg

this will show you the xorg files that you have. The backup one should be listed

sudo cp xorg.conf[name you've found] xorg.conf

---

### Post by shadowhacker on 2009-02-05
```
ls | grep xorg
```
doesn't display anything.

I typed dir in /etc/ just to be sure, and no files have anything to do with xorg.

Any other ideas?

---

### Post by xopher_mc on 2009-02-05
doh! sorry

cd /etc/X11/

---

### Post by shadowhacker on 2009-02-05
No problem, and thank you, it worked. However, the only backup file I can boot with is the xorg.conf.failsafe one. This starts x with the vesa driver. I tried re-enabling 177, and I quickly returned to the same results. When the nvidia 180 driver was installing, it said something about recompiling the kernel and X-server. Do I need to compile these back with the 177 driver? If so, how? Thanks again for the help.

---

### Post by shadowhacker on 2009-02-05
I don't know if it matters, but I'm running 8.10 AMD64. Anyone else have any ideas?

---

### Post by xopher_mc on 2009-02-05
try 

```
 dpkg-reconfigure xserver-xorg 
```

That wont give you the nvidia driver but should make it go back to before.

---

### Post by shadowhacker on 2009-02-05
Good Idea. Thanks again for all of your help. This too, allows me to boot Ubuntu with the base Vesa Driver. Unfortunately, it has no 3D acceleration, and it's so slow that I almost can't use it. When I tried to reinstall the 177 (old-stable) nvidia driver I got the same no-boot condition.

Do you think it's possible to use that command on my kernel? The reason I ask is that the new 180 driver was supposed to integrate an API: into the kernel I think. I think that this might be causing my problem, as my kernel is trying to use this with all video drivers, not just the 180 one. I could be completely off here though, I'm not sure.

I'm starting to wish I'd known to put /home on a different partition so that a re-install wouldn't be such a hassle.

Thanks again for all of the good ideas xopher_mc.

---

### Post by dabl on 2009-02-05
The procedure is pretty much as described here (post #3):

[http://kubuntuforums.net/forums/index.php?topic=3100807.0](http://kubuntuforums.net/forums/index.php?topic=3100807.0)

except "gdm" instead of "kdm" for Ubuntu.  Before you start, make sure you

```
sudo apt-get update && sudo apt-get install build-essential linux-headers-`uname -r`
```

---

### Post by shadowhacker on 2009-02-05
Worked like a charm. THANK YOU! Holy crap this thing is fast now. Definite improvement from 177.xx to 180.22. Thanks again!

---

### Post by dabl on 2009-02-05
:cool:

---

### Post by ricardo_78 on 2009-02-06
Cool ...it took me  a while to get the 180 driver installed but my system is now rock solid as opposed to prone occasional crash....

Only those that are able to persevere can get the benefit of such and gr8 environment....:p

---

