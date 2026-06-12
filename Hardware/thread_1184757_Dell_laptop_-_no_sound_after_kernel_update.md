---
title: "Dell laptop - no sound after kernel update"
date: 2009-06-11
forum: Hardware
---

### Post by Blendee on 2009-06-11
Hi
I posted this question in soundcheck's ALSA upgrade script thread but didn't get any feedback so I'm trying my luck with a new thread.

My fiancee has a Dell Vostro  A860 (T2410) laptop running Ubuntu 8.04. It comes with an Intel 82801H on-board soundcard. "lspci -v" command gives me this:
```

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02) 
	Subsystem: Dell Unknown device 029a 
	Flags: bus master, fast devsel, latency 0, IRQ 7 
	Memory at f6dfc000 (64-bit, non-prefetchable) [size=16K] 
	Capabilities: <access denied>

```
The sound was ok until a major update. Right now the system is updated to 2.6.24-24 kernel. There is no sound whatsoever, no login sound, no headphones, no built-in speaker. The volume control applet on the taskbar is crossed by a red line. If I click it it says: "No volume control GStreamer plugins and/or devices found". The soundcard is ok because everything works fine if I load a previous kernel (2.6.24-22). 
Can someone please tell what can I do to solve this problem for my fiancee? I am a noob so I don't dare messing around with commands or purge/installs out of fear of losing GDM (that would leave me in the dark :( ) or screwing things up even more. I tried the ALSA upgrade script, which updated ALSA, but the sound is still dead. I figure ALSA supports this card since it worked fine in other kernel version.
Thank you.

---

### Post by gradinaruvasile on 2009-06-11
You could try reinstall alsa :

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

the "Getting the ALSA drivers from a *fresh* kernel" section

Do not forget to reinstall the gdm...

---

### Post by Blendee on 2009-06-11
Thank you. That's what I was afraid of. I just wanted to see if there is any other solution. Working with just the teminal means I can't check a webpage for help in case I screw up or copy/paste some commands. I know it's supposed to be a painless operation but things go rarely according to plan so I might be forced to "improvise".
Thanks again for your answer, gradinaruvasile.

---

### Post by Blendee on 2009-06-11
Ok, I followed the guide, purged, reinstalled ALSA - **no success**.
Compiled the driver using alsa-source, all went fine, no errors - **no success**! There still is no sound. Applet icon appears crossed.
"sudo modprobe snd-" gives me:
```
FATAL: Module snd_ not found.
```
Does anybody know what is happening here? I'll post logs if you need, just tell me what's going on. Is there soemthing I could do or should I tell my fiancee to give up hope on hearing any sound in Ubuntu?
Thank you.

---

### Post by Blendee on 2009-06-12
Today I've installed the latest ALSA modules (1.0.20) following [[COLOR="Red"]this[/COLOR]]("http://www.linlap.com/wiki/configuring+the+audio+and+updating+alsa+for+ubuntu+8.04") guide. However, synaptic shows me I have "alsa-base 1.0.16-0Ubuntu4" installed.
Needless to say, **aplay -l** still gives me "no soundcards found..." and there is no sound.
Are the latest ALSA modules properly installed? Is there a way to tell? What can be done?
This card has to be supported since it worked fine in 2.6.24-22 so this could be a bug or I may be doing something wrong (ok, not in that order).
Did someone ever encountered a similar problem? I invite you to to share with the less fortunate what worked. Thank you.

---

