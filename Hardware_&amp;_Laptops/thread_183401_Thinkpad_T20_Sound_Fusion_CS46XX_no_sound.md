---
title: "Thinkpad T20 Sound Fusion CS46XX no sound"
date: 2006-05-27
forum: Hardware &amp; Laptops
---

### Post by rudyard on 2006-05-27
Hi, just coming from Windows and Macs and cam work behind the scenes on both, took a Linux class but still new. Have a TP T20, running 5.1 and sadly, the sound card doesn't work. It's recognized, to the best of my knowledge. I found this in the archives.

I had a similar problem with my Sound Fusion CS46XX card. I observed that the "ADC" and "DAC" in the "Input" tab of kMix were set to 0. I increased the values of these and I get the sound now. Note that this may have to be done separately as each user in kMix. Doing this only in root will do it only for root.

Uh, how do I find kMix? Or does anyone have any other suggestions?

thanks

-Rudyard

---

### Post by slimdog360 on 2006-05-27
try dapper, the final version should come out in a few days and fix that

---

### Post by rudyard on 2006-05-28
Thanks SD, I just searched dapper and nothing appropriate came up, can anyone fill me in? Also, I've tried something in terminal called alsamixer, turned on DAC as recommended (and anything else that would turn on) and in Volumn COntrol prefs turned every slider on, including ext amp.

-Rudyard

---

### Post by Azrael on 2006-05-29
Heh... sound worked fine on my Thinkpad T20 in Breezy (and earlier releases), but stopped working after I dist-upgraded to Dapper yesterday. I got my sound back by doing

sudo modprobe snd-cs46xx

and sudo alsamixer to unmute (press m) the master channel. I suspect the Dapper devs made a sloppy omission here somewhere. :-?

edit: If the above works, add *snd-cs46xx* to /etc/modules to have sound working on every startup.

---

### Post by rudyard on 2006-05-29
Thanks Azrael, the upgrade brought my ethernet card online and the modprobe got the sound to work. Thanks

---

