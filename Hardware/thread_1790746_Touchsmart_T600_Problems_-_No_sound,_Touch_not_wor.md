---
title: "Touchsmart T600 Problems - No sound, Touch not working"
date: 2011-06-25
forum: Hardware
---

### Post by Legend Ownz on 2011-06-25
[CENTER][LEFT][SIZE=2]Hey everyone, I'm new here on the forums and I just installed Linux (Ubuntu 11.04) on my Touch-smart T600. It took me like 3 hours to fix the graphics card to work, but I finally got it! (if you are stuck on getting it worked out I can help you). So now all that is left is the sound and touchscreen to fix.[/SIZE]

 [SIZE=2]Please post any suggestions on how to fix this. I looked it up on Google/YouTube for an hour and all I found were outdated tutorials that would probably ruin my system :([/SIZE]
[B]
UPDATE: Touch system is now working thanks to one little DEB file :D If you need it I will Upload it.[/B]
[/LEFT]
  
[B]MOD INFO

snd-atiixp-modem: index=-2[/B] [B]
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2
snd-hda-3stack-hp: index=-2

[/B]Alsa Info:[ http://www.alsa-project.org/db/?f=5d92537efd6e12d6d7087f0fe823501f6f0cca94]("http://www.alsa-project.org/db/?f=5d92537efd6e12d6d7087f0fe823501f6f0cca94")

[/CENTER]

---

### Post by Legend Ownz on 2011-06-25
72 views no reply?

---

### Post by lidex on 2011-06-26
Wow. Please be a little more specific. 
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Legend Ownz on 2011-06-27
Sorry, like I said I'm new to Ubuntu and Linux in general. :)

---

### Post by lidex on 2011-06-27
You added the touchsmart model switch which is for a different model/codec. You should remove it. In its place you could try these, reloading alsa for each change.
```
3stack-hp
auto
3stack-6ch
3stack-6ch-dig
3stack-dig
6stack-dig
```

```
sudo alsa force-reload
```

---

### Post by Legend Ownz on 2011-06-27
I tried all those, and reloaded the alsa every time I changed. sadly none of them worked :(

---

### Post by lidex on 2011-06-27
What is your current modinfo;
```
modprobe -c|sed -n 's/^options \(snd[-_][^ ]*\)/\1:/p'
```

---

### Post by Legend Ownz on 2011-06-28
Here is my modinfo; 

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2
snd-hda-3stack-hp: index=-2

Thanks for all the codes by the way :)

---

### Post by lidex on 2011-06-29
> **Legend Ownz said:**
> Here is my modinfo; 

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2[COLOR="Red"]
snd-hda-3stack-hp: index=-2[/COLOR]

Thanks for all the codes by the way :)

Not sure what that last line is about but I would suggest removing it.

---

