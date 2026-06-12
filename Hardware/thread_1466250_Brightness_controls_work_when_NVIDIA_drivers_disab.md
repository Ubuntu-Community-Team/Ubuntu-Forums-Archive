---
title: "Brightness controls work when NVIDIA drivers disabled!"
date: 2010-04-30
forum: Hardware
---

### Post by sevenflo on 2010-04-30
Hey guys. I usually use 9.04, but 10.04 Lucid has been luring me in so I decided to give it a try. 

Thing is, in 9.04, my NVidia card (Sony laptop, Core2Duo) never let me change brightness. So I have been using nvclock to adjust my brightness.

BUT, here's what I noticed when I did a clean install of Lucid: Brightness keys worked!  That is, until I decided to install the NVidia Restricted drivers. Suddenly, back to the same problem: Gotta use ;nvclock -S 80; and so on.

I figured that might help some people. But at the same time.... it's pretty clear the Ubuntu devs are RIGHT on track. Is there a way to stop the NVidia drivers from breaking their work?

I'm running the "Version Current". I'm going to try 173 and see what happens.

Hope this helps. Try it out and let us know how it worked out for you.

---

### Post by sevenflo on 2010-04-30
bump

---

### Post by dino99 on 2010-04-30
as i understand you have installed the driver from nvidia, right ?

if so, goto synaptic and remove/purge each nvidia packages installed

sudo rm -f /etc/X11/xorg.conf

then install: nvidia-current, nvidia-current-modaliases, nvidia-common

reboot

nvidia-settings let you tweaks the settings

---

### Post by peepingtom on 2010-05-01
I don't think you should follow the advice given in the previous post, the proper way to switch between nouveau and the proprietary video drivers drivers in Lucid is using the Jockey aka System -> Administration -> "Hardware Drivers". Nouveau uses a different method of controlling the backlight than the nvidia driver does. When running the NVIDIA driver, try switching to VT1 (ctrl+alt+F1), change brightness, then change back to the VT running X (VT8 I think, now). Also, try this with the proprietary drivers: [http://www.nvnews.net/vbulletin/showpost.php?p=2204839&postcount=324839&postcount=32](http://www.nvnews.net/vbulletin/showpost.php?p=2204839&postcount=324839&postcount=32)

---

### Post by dino99 on 2010-05-01
> **peepingtom said:**
> I don't think you should follow the advice given in the previous post, the proper way to switch between nouveau and the proprietary video drivers drivers in Lucid is using the Jockey aka System -> Administration -> "Hardware Drivers". Nouveau uses a different method of controlling the backlight than the nvidia driver does. When running the NVIDIA driver, try switching to VT1 (ctrl+alt+F1), change brightness, then change back to the VT running X (VT8 I think, now). Also, try this with the proprietary drivers: [http://www.nvnews.net/vbulletin/showpost.php?p=2204839&postcount=324839&postcount=32](http://www.nvnews.net/vbulletin/showpost.php?p=2204839&postcount=324839&postcount=32)

using proprio drivers means putting users into troubles, do you know that ? If ubuntu devs tweaks and fine tune drivers, its not for nothing

---

### Post by wbloos on 2010-06-09
@peepingtom
your link solved my problem [http://www.nvnews.net/vbulletin/showpost.php?p=2204839&postcount=324839&postcount=32]("http://www.nvnews.net/vbulletin/showpost.php?p=2204839&postcount=324839&postcount=32")

Awesome stuff.
Just in case the link might once disappear:

> For those experiencing problems with backlight controls, can you please try adding the following line to /etc/X11/xorg.conf in the "Device" section for your GPU:

```
Option "RegistryDwords" "EnableBrightnessControl=1"
```
Then restart X and see if brightness controls work.

If they do, please post an nvidia-bug-report.log along with the make and model of your laptop. Thank you.

That posting the bug report etc would be on the forum that the link points to, not here.

---

### Post by coorior on 2010-10-22
THANK YOU , THANK YOU AND THANK YOU AGAIN !!!!

I've been using ubuntu since 7.10, and brightness control almost never did work for me (ibm x31, ibm60, ... , lenovo y450). BUT AT LAST I have found your post!!!!!!!!!!

---

