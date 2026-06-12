---
title: "wanna get 5.1 channel configuration with MB Asus H97M-E + Xubuntu"
date: 2016-04-03
forum: Hardware
---

### Post by trigone on 2016-04-03
Hi!

My motherboard is an Asus H97M-E. Only three basics, typically "2.1" ports at the back of it (blue/line in, pink/mic, green/line out), so I thought it meant I had to add a sound card on PCIe to handle the [black-rear, orange-bass, green-front] jack connecters of my 5.1 speaker kit I recently bought. 

Yet here's what my MB configuration says:

> Realtek® ALC887 8-Channel High Definition Audio CODEC featuring Crystal Sound 2*[SUP]2[/SUP]
- Supports : Jack-detection, Front Panel Jack-retasking
**Audio Feature :**
- Audio Shielding: Ensures precision analog/digital separation and greatly reduced multi-lateral interference
- Dedicated audio PCB layers: Separate layers for left and right channels to guard the quality of the sensitive audio signals
- Audio amplifier: Provides the highest-quality sound for headphone and speakers
- Premium Japanese-made audio capacitors: Provide warm, natural and immersive sound with exceptional clarity and fidelity
- Unique de-pop circuit: Reduces start-up popping noise to audio outputs
It happens that apparently my MB should handle 5.1, even 7.1, natively! Apparently the three ports on the back should, depending on the "channel configuration" (2.1, 5.1, 7.1) behave differently, and if I'd be in an 5.1 config, the blue entry should work as a black one, and the pink as an orange one. If I wanted to get hypothetically a 7.1 config to work (which I don't though ^^), apparently I'd have to set, in the BIOS I think, the front panel port entry, as the "fourth port" aka as the port for the surround speakers (channel 7 and 8, considering the 5.1 has 6 of them technically, again *apparently*, coz if it's not clear at this point I'm a dabbler more than any kind of connoisseur, in sound technology)).

Hence, I'm trying desperately to find how to make my MB/OS realize that I'm in a 5.1 config, and thus that I want the blue/line-in to behave as a rear/surround 5.1 jack entry, and same for the pink/mic, as an orange/bass-center, if you follow my wording.

So far zippo: nothing in the BIOS, nor in PulseAudio control panel. I even tried to find the Windows Software used by the Microsoft users, called Realtek HD audio manager, and supposed to help decide what kind of jack you put in your motherboard. Again, weirdly, I only find drivers, but would it be that? didn't try, plus unless I'm strongly mistaken, windows drivers will do no good on linux, except maybe inside a Virtual Box...

Anyway, I just want to use the 5.1 channel configuration supposed to be supported by my MB, albeit in a way that seems weird to me! (double behavior of sound ports).

Anyone got it all? Knows how to help me? Please do so, after a whole 12h around GoogleLand without so much as a tiny half-result, I just got outright desperate ^^
Thanks a bunch in advance, have a nice day!

---

### Post by trigone on 2016-04-04
somebody? :/

---

### Post by Yellow Pasque on 2016-04-04
[http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/](http://voices.canonical.com/david.henningsson/2011/11/29/turn-your-mic-jack-into-a-headphone-jack/)

You didn't say what version of Ubuntu you're running, but 15.10/later should have hdajackretask easily available in the standard repos:
```
sudo apt-get install alsa-tools-gui
hdajackretask   #may need sudo, can't remember
```

---

### Post by trigone on 2016-04-05
True, I'm on 14.04 apparently, yet your solution software works like a charm! That's perfect, thanks a lot!

Just now the keys of my keyboard that I programmed to send classical XF86Audio signals (mute, volume ±) don't do a thing anymore, but maybe it will get back to it when I merely restart the computer, and pulseaudio with that (as I imagine it's the one that interprets said signals, but it's random guess); I'll try it soon I think, but in the meantime if anyone knows why it ceased to work, and how to fix it right away :)

Thanks again a lot, Temüjin!

---

