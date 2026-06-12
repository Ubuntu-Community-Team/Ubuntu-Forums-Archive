---
title: "ubuntu on dell adamo"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by mic_bey on 2009-10-17
hi there,

did anyone install ubuntu on dell adamo laptop? any troubles/tips?

---

### Post by avilella on 2009-10-17
Hi mic_bey, so far there's been only one issue reported on the Dell Adamo, regarding faded sound from the speakers:

[https://launchpad.net/~dell-adamo](https://launchpad.net/~dell-adamo)
[http://www.uluga.ubuntuforums.org/showpost.php?p=7164651&postcount=1](http://www.uluga.ubuntuforums.org/showpost.php?p=7164651&postcount=1)

This is for the current Dell Adamo btw, there is a new ultra-ultra-thin Dell Adamo XPS about to be released.

> **mic_bey said:**
> hi there,

did anyone install ubuntu on dell adamo laptop? any troubles/tips?

---

### Post by kpholmes on 2009-10-28
ya i just checked it out, looks really cool. 

i was looking at netbooks but i think i want one of those, puts my macbook to shame

---

### Post by SeanBlader on 2009-12-07
I'm a little late on this thread, but Karmic is really solid on the Adamo. The only things that I'm not sure work are the microphone, the built-in 3G GSM card, and while I have sound it's still a little faint on the speakers, but the headphones output is very good.

Bluetooth works for mouse and A2DP stereo headphones, simultaneously
Wifi works out of the box with Network Manager and connects to WPA2 nodes
DisplayPort works with DVI, HDMI, and VGA if you have the right dongles
e-sata works if you have something for it

Battery life is decent, I can do a solid use 3 hour meeting with the display dimmed. Startup times are insanely fast with the SSD, boot screen in about 12 seconds, working desktop about 10 after that. Basically I can't recommend the Adamo highly enough as an Ubuntu system. It's lacking the newest features like fingerprint reader and touchscreen, but it does everything else really well.

---

### Post by sagara on 2011-01-20
Installing ubuntu 10.10 was a breeze on the adamo.  I installed it from a USB drive as well.

So far the only problem I noticed was the microphone and headset not working.  However here is the fix for that:

Open a terminal and type:

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

this will open a text file, add the following line to the end of the file:

```
options snd-hda-intel model=dell-m6
```

close the text file and run this command:

```
sudo alsa force-reload
```

Your headphones and microphone should work now, enjoy!

---

### Post by jasonbobasin on 2011-04-30
Hi Sagara, thanks that helped to get my speakers working but I'm still having trouble with the microphone. What settings do you use in Alsa? I have tried both the analog microphone and internal microphone connectors and every combination of settings in alsa (IEC958, Mic Jack Mode, the sliders). How is yours set up?

---

