---
title: "Sound card not detected on Ubuntu 18.04.3 LTS"
date: 2019-08-28
forum: Hardware
---

### Post by krishnart1701 on 2019-08-28
Hello Guys, 

I am old to Linux but haven't learnt much. after installing ubuntu on my old desktop, i found that sound isn't working. 
Sound settings show dummy output only. Below are the screenshots to show my system info, sound settings, alsa -l 
output and pactl list output (only for card #0. 

I have tried all options like force reloading alsa, reinstalling alsa, installing kernel devel etc. as suggested in forums. 
Can some one kindly let me know how to diagonise the problem and solve it.
[ATTACH=CONFIG]283890[/ATTACH][ATTACH=CONFIG]283891[/ATTACH][ATTACH=CONFIG]283892[/ATTACH][ATTACH=CONFIG]283893[/ATTACH]

---

### Post by mörgæs on 2019-08-28
Hi, welcome to the fora. 

If you copy terminal output and paste it as text using CODE tags there is a better chance that people (and search engines) will read it. Not everyone bothers to click on an image link.

---

### Post by Yellow Pasque on 2019-08-28
Start here: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
Upload the info and give your link.

---

### Post by krishnart1701 on 2019-08-29
Hello Guys .. this is the link to alsa info of my system.. Please check once and help me out .. 
thanking you in anticipation. 

[http://alsa-project.org/db/?f=20f3390d360f907c143b1bc59bc6dd3a8ad8b02f](http://alsa-project.org/db/?f=20f3390d360f907c143b1bc59bc6dd3a8ad8b02f)

---

### Post by Yellow Pasque on 2019-08-29
Remove this line from your /etc/modprobe.d/alsa-base.conf file:
```
snd_hda_intel: model=ati
```

Then, get the info after you boot without it.

---

### Post by krishnart1701 on 2019-09-01
Dear Yellow Pasque 
This is the alsa info after i removed that line. 
[http://alsa-project.org/db/?f=1df9f3c94ab7fbb7d4785177f2c2dbf59d5c219f](http://alsa-project.org/db/?f=1df9f3c94ab7fbb7d4785177f2c2dbf59d5c219f)

---

### Post by Yellow Pasque on 2019-09-01
```
[   16.248315] snd_hda_intel 0000:00:14.2: no codecs found!
```

Thank you for the feedback. I am not sure what to suggest, other than to reset your CMOS/BIOS (either by selecting the reset to default option in your BIOS or using the appropriate jumper on your motherboard as detailed by the motherboard's manual).
Another possibility is trying to manipulate "snd_hda_intel probe_mask=xxxx" but I can never google an easy/reliable guide on how to use that...

---

