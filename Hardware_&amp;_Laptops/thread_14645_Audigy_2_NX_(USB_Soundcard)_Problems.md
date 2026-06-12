---
title: "Audigy 2 NX (USB Soundcard) Problems"
date: 2005-02-08
forum: Hardware &amp; Laptops
---

### Post by USSJoin on 2005-02-08
I can't get my Audigy 2 NX working. I am running the following system config:
Inspiron 8600 (1.8GHz, 512 RAM, DVD+-RW, Centrino 2200BG)
Ubunty Warty, shifted to Hoary (Including newest kernel, 2.6.10, 686 version)

When I cat /proc/asound/cards, it shows me that my Audigy NX is on card 1, and my built-in is on card 0. I can get sound out of my built-in card without problems, over ALSA.

I can ./alsa stop both cards, then start just #1, and then mp3 players say they are playing-- but nothing comes out. I know the setup is fine, because it works perfectly in Windows.

I will post any files/whatevers that people want, just tell me what else I should be including.

Thanks in advance, for your help getting this working!

---

### Post by kleeman on 2005-02-09
Checkout this troubleshooter particularly with reference to the multiple soundcards:

[http://alsa.opensrc.org/index.php?page=TroubleShooting](http://alsa.opensrc.org/index.php?page=TroubleShooting)

---

### Post by edebont on 2005-02-28
What might be idea if you have several multimedia devices for example like a sblive card and an usb webcam with build-in microphone (caused issues)  to have a look at 

*/etc/modprobe.d/alsa-base *

you see at the end something
[I]
# Prevent abnormal drivers from grabbing index 0
options snd-atiixp-modem index=-2
options snd-bt87x index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2[/I]

By adding the following line at, it prevented my webcam microphone for becoming the primary sound device.
[I]
options snd-usb-audio index=-2[/I]

Maybe you can do same for your soundcards.

Hope it helps !

---

### Post by WMCoolmon on 2005-04-11
If you're still having trouble, check out my second post in this thread:
[http://www.ubuntuforums.org/showthread.php?p=125941#post125941](http://www.ubuntuforums.org/showthread.php?p=125941#post125941)

---

