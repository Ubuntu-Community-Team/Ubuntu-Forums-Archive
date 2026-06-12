---
title: "No Sound in the headphone"
date: 2008-04-25
forum: Hardware
---

### Post by pangpangalex on 2008-04-25
Hello,I've installed 8.04 Hardy on my laptop and the speaker work fine. When I plug in the headphone in the socket, there is no sound in the headphone and the speaker still giving out sound. 

 I was using 7.10 before 8.04 and it's fine when i plug in the headphone (sound was coming out both speaker and headphone)

But it doesn't work after I've installed 8.04
Any help please, thanks a lot

---

### Post by raiwo on 2008-04-26
fixed for me by adding following line:

```
options snd-hda-intel position_fix=1 model=lenovo
```

in /etc/modprobe.d/alsa-base

if this is not working try
```
options snd-hda-intel position_fix=1 model=asus-dig
```

remember reboot!

---

### Post by szako on 2008-04-26
Hi there!

The solution depends on the notebook type.

Check [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt").

Do:

```
lspci | grep Audio
``` and

```
cat /proc/asound/card0/codec#* | grep Codec
```

See the results and choose the appropriate model, then do:
```

sudo gedit /etc/modprobe.d/alsa-base

options snd-hda-intel model=MODEL

```

for example, for my ASUS A6VA laptop the working model was w810

---

### Post by ratazana80 on 2008-04-26
Hi szako!

I also own a Asus A6VA - A6Q00VA. I've tried> w810, z71v, asus, asus-w1v, asus-dig, asus-dig2, but I can't make the headphone output work!

How about your Ati X700, is your working correctly???

---

### Post by mempman on 2008-05-13
In the past I have experienced such problems and have spent many many hours, trying to fix them.  Ultimately, I have found the only solution to sound problems are upgrading to the lastest alsa (assuming you r running alsa) package.  Or, if you are already running the latest alsa release, I would suggest downgrading to a prior release of alsa, which can be found on alsa website.

---

### Post by Mistron on 2008-05-14
I saw something on the net about changing to PCM device, This isn't what I eventually did but I went to volume control and changed device and turned every volume up, changed to next device and did the same. Eventually it worked. O_o
Maybe I (or somebody else) will eventually find something to change this.

Edit: I have this exact model:
Asus A6Q00VA, sticker on the bottom with serial key says: A6VA-Q016H.

And I have pulled the plug out and than I get a peeping noise, not the ultimate solution yet. >.<

Second Edit: Playing around with all the different volumes solves this, Though I don't know what exactly solves this.
I don't even exactly know what I am doing.
But hey it's a start... I think it has something to do with putting microphone up, (same kind effect a holding mic before boxes.)
Though others also change sound quality.

---

