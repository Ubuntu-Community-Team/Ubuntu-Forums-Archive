---
title: "vaio sound too low"
date: 2008-08-23
forum: Hardware
---

### Post by noremaku on 2008-08-23
I have a Sony VAIO VGN-G1 and I recently installed Ubuntu heron. Everything works out of the box, but the sound on the laptop speakers is really low. I maxed the master volume and I turned each and every slider in the volume conrol to max, and it hasn't fixed the problem. Obviously I can plug in speakers and I'll be fine, but surely there is a solution? Is there a driver or driver update I can install? What if you somehow modified the volume control to go higher?

---

### Post by mcmonkeys1 on 2008-08-23
i have the same problem with my laptop, using hardy.
definitely a software issue.

---

### Post by evilmango on 2008-11-01
Same here. I've tried specifying the model for the snd-hda-intel module in /etc/modprobe.d/alsa-base but without any luck. Annoyingly I had it working under feisty with:
options snd-hda-intel model=sony-assamd
...but that no longer seems to work.

Any suggestions much appreciated.

---

### Post by pihhan on 2008-11-01
Try model=vaio for snd-intel-hda module, it might work.

---

### Post by samsom on 2009-02-07
Hi,
I am a Linux newbie and have recently installed Ubuntu on my Sony VGN-G11XN and it has got the same problem i.e extremely low volume. I have searched on google and this same issue seems to be posted on a number of forums, but there does not seem to be a clear solution anywhere. 
Could anyone help please?
Thanks
Samsom

---

### Post by noremaku on 2009-04-05
8 months and a new release later, still haven't found a solution. If I need sound other than through my headphones and I'm away from home (thus away from my speakers) I have to boot up Windows, which is depressing.

---

### Post by Leot351 on 2009-07-31
I solved this issue a couple of months ago (it is now July). From the get go my headphone jack didn't work so I looked around and finally solved it. Well after I solved that issue the volume on the speakers was wayyyyy lower than before. I tried a couple of things and nothing worked so I gave up on it and just cranked my sound on my speakers all the way up. Then out of curiosity I installed kubuntu and surprisingly when it started I had the option to turn it up all the way. After that it went back to normal in Ubuntu and Kubuntu. Please forgive my English, it is not my first language.

---

### Post by maxw9 on 2010-04-26
Just fixed this on Ubuntu 9.10 on Sony vaio G118GN.

The trick was to add:
> options snd-hda-intel model=basic
into /etc/modprobe.d/alsa-base.conf

model=vaio as suggested above does not work.

---

### Post by afridz on 2010-04-27
juz do the driver update

---

