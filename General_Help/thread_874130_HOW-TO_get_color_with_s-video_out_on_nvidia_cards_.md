---
title: "HOW-TO get color with s-video out on nvidia cards no black and white"
date: 2008-07-29
forum: General Help
---

### Post by onesojourner on 2008-07-29
It has taken my 4 days worth of research but I think I have finally figured out how to fix the svideo out only displaying black and white. This is a bug with the nvidia driver. Luckily its an easy fix once you know how to do it. If any one finds anything else that works or that this does not work please report back.

```
sudo nvidia-xconfig --tv-standard=NTSC-M --tv-out-format=SVIDEO
```
"NTSC-M" Is what worked for my system. You can change it to any of the following: "PAL-B", "PAL-D", "PAL-G", "PAL-H","PAL-I", "PAL-K1", "PAL-M", "PAL-N",   "PAL-NC",   "NTSC-J","NTSC-M", "HD480i", "HD480p", "HD720p", "HD1080i", "HD1080p", "HD576i", "HD576p".

You can also change the "SVIDEO" to "COMPOSITE" depending on what output your card uses.

Then you just need to reboot and you should be good to go. Hopefully you have a media center that is displaying color when it comes back up.



[IMG]http://www.aeonproject.com/images/aeon_showcase1.jpg[/IMG]

---

### Post by onesojourner on 2008-07-29
For those with ATI cards I think this will work for you as well. I don't have a card to test on though so you are treading new ground.

```
cd /etc/X11/
sudo cp xorg.conf xorg.backup
```

```
sudo gedit /etc/X11/xorg.conf
```

Add this under the "SCREEN" section.

Example:
```

Option "TVStandard" "NTSC-M"
Option "TVOutFormat" "SVIDEO"

```
You can cahnge the options to any of those listed in the first post.


if is fails type this to get your last settings back:

```
cd /etc/X11/
sudo cp xorg.backup xorg.conf
```

---

### Post by wootah on 2008-07-29
PS: Check my sig. for a guide for this on ATI cards :) There is also a known issue for you Sapphire card users (especially the 9600/x1050 users) of the manufacturer not setting the jumper correctly so the default mode out is PAL.

---

### Post by ModdTaco on 2008-07-29
Going off topic is that a pic of a media center for Linux?

---

### Post by jimv on 2008-07-29
Odd, I never has a problem with s-video out.

---

### Post by onesojourner on 2008-07-30
> **ModdTaco said:**
> Going off topic is that a pic of a media center for Linux?


[offtopic]It works best on an HD tv, but I have it running fine on an SD tv. Some of the fonts are a little hard to read in SD but other than that its great.

[http://www.aeonproject.com/](http://www.aeonproject.com/)
[/offtopic]

---

