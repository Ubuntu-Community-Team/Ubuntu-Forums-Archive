---
title: "No sound when i plug in headphones"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by Benjamin_Vedder on 2008-01-08
I installed ubuntu on an packard bell laptop with an hda ati sb sound card. The problem is: I have sound from the built in speakers, but when i plug in headphones I have no sound from the speakers nor from the headphones. The headphones are okay because they work in vista (on the same laptop).

aplay -l gives: (swedish, i know)

**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: SB [HDA ATI SB], enhet 0: ALC861VD Analog [ALC861VD Analog]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0

cat /proc/asound/card0/codec#* | grep Codec gives:

Codec: Realtek ALC861-VD


When i add the line

options snd-hda-intel model=3stack

to /etc/modprobe.d/alsa-base

more mixerchannels appear, but playing around with them gives me no sound from the headphones.

I have spent hours and hours looking for an solution for this without any success. Any ideas?

---

### Post by Benjamin_Vedder on 2008-01-08
well, I think i have tried everything there is with the drivers. I followed this giude: 

[http://ubuntuforums.org/showthread.php?t=205449&highlight=alc861vd](http://ubuntuforums.org/showthread.php?t=205449&highlight=alc861vd)

first, and then i installed the new alsa driver, alsa lib and utilities from source. I think there is some mixer channel missing, and i have seen othen users with the same problem, like: 

[http://ubuntuforums.org/showthread.php?t=534070](http://ubuntuforums.org/showthread.php?t=534070).

I have also found this post:

[http://www.backports.ubuntuforums.org/showthread.php?t=616845](http://www.backports.ubuntuforums.org/showthread.php?t=616845)

and i tried every line he mentioned below my card. Some of them gave me more mixerchannels, some gave less and 2 of them made the card not work at all.

So.. is there something else i could try? btw, thanks for the reply

edit: I'm sure the hardware is fine, because just now I restarted the computer in vista and the headphones worked fine. I also noticed vista uses the alc861-codec, while ubuntu uses alc861vd. Could that cause problems?, if so, is there some way i can change the codec in ubuntu?

---

### Post by erykroom on 2008-01-08
I have pretty much the same problem. Sometimes my headphones work and sometimes not. The terminal says "sh: jackd: not found".  I'm useing the Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01) and strangely i have 2 codecs in use.
arko@erykroom:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: SigmaTel STAC9200
Codec: Conexant ID 2bfa

---

### Post by Benjamin_Vedder on 2008-01-08
> **adept said:**
> yeah.. the chance of the drivers being corrupt is quite less..
i think. it has something to do with the hardware...
does the sound works good with windows?

It does

---

