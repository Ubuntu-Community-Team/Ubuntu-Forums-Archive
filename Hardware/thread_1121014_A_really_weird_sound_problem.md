---
title: "A really weird sound problem"
date: 2009-04-09
forum: Hardware
---

### Post by Kondor István on 2009-04-09
Hi!

I am trying to get my sound work just like many of You. I tried google and some guides here, especially these ones:
[http://ubuntuforums.org/showthread.php?t=1066212&highlight=pulseaudio](http://ubuntuforums.org/showthread.php?t=1066212&highlight=pulseaudio)
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

I did everything what the latter one suggests, almost everything seems to be working just fine.

So _why_ is it weird? Because sound works just fine through HDMI, I get a really distorted sound in the headphone (I am only able to hear a noise), and absolutely nothing through the stereo laptop speakers.

I wrote earlier that almost everything looks OK. Except one thing: in puleaudio volume control I have a red sign on the small speaker icon. It is _not_ muted anywhere else and not even here. A screenshot is available here: [http://bayimg.com/image/haobgaabo.jpg](http://bayimg.com/image/haobgaabo.jpg)
I am trying to tell that I have this small red sign even when it is unmuted also here in pulseaudio volume control. So my best guess is that somehow my speakers are disabled via/by the kernel(?).
However, I get only this during boot:
kernel: [...] input: PC Speaker as /devices/platform/pcspkr/input/input7

I tested it under 8.10 and 9.04 beta, both 64 bit versions. I tried the pulseaudio version 9.0.15 from the PPA source refered in the first link and the script found at [http://www.linlap.com/wiki/audio+tester](http://www.linlap.com/wiki/audio+tester)
Absolutely no luck. Same distorted sound in headphones and nothing through the speakers. That's why I am starting to think that it is not related to the sound server (maybe not even the driver), but something else.

My machine is an ASUS N51Tp, sound is:
~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfacf4000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfadec000 irq 19

I am really greatful for any idea how to solve this. Thank You for Your efforts in advance!

---

