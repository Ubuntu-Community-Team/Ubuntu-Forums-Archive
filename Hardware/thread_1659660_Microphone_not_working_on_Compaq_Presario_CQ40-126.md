---
title: "Microphone not working on Compaq Presario CQ40-126AU"
date: 2011-01-04
forum: Hardware
---

### Post by myChucky on 2011-01-04
Hello, I has upgrade my Ubuntu to 10.10. After that my microphone not working, I hope somebody will help me. Below is something about my system.

[IMG]http://img833.imageshack.us/img833/5839/screenshothrb.png[/IMG]

---

### Post by lidex on 2011-01-04
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by myChucky on 2011-01-05
I has try, but has some problem. I get this massage.

~$ wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh
--2011-01-06 05:54:32--  [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh)
Resolving [www.alsa-project.org](www.alsa-project.org)... 77.48.224.243
Connecting to [www.alsa-project.org|77.48.224.243|:80](www.alsa-project.org|77.48.224.243|:80)... connected.
HTTP request sent, awaiting response... 503 Service Unavailable
2011-01-06 05:55:28 ERROR 503: Service Unavailable.

---

### Post by myChucky on 2011-01-05
I has try again and I has the link: [http://www.alsa-project.org/db/?f=880275b3dbbf68d25e7df677ed2b91a870db9b30](http://www.alsa-project.org/db/?f=880275b3dbbf68d25e7df677ed2b91a870db9b30)

So what I can do rite now?

---

### Post by lidex on 2011-01-05
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=ref 
```
Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

The try these other models if that doesn't work:
```
auto
hp-hdx
hp-dv5
hp-m4

```
No space after the =, only one at a time, and reboot each time.

---

### Post by myChucky on 2011-01-05
> **lidex said:**
> Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```Insert this line at the bottom:
```
 options snd-hda-intel model=ref 
```Save. Close. Reboot. 
Check your levels in alsamixer.
```
 alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

The try these other models if that doesn't work:
```
auto
hp-hdx
hp-dv5
hp-m4

```No space after the =, only one at a time, and reboot each time.

I has follow this instructions and I has see the alsamixer. I also to try change Connector on Input tab at Sound. But still doesn't work, then I don't know how to use last code as you give me. Please help me, if can you can use picture to teach me. Sorry if I'm very noob.

---

### Post by myChucky on 2011-01-05
This some image from alsamixer:

[IMG]http://img29.imageshack.us/img29/6694/screenshotfi.png[/IMG]

[IMG]http://img26.imageshack.us/img26/4066/screenshot1qt.png[/IMG]

[IMG]http://img717.imageshack.us/img717/6171/screenshot2pg.png[/IMG]

I hope it will help you to solve my problem. Thanks.

---

### Post by BigBaka on 2011-10-14
Thanks for this,

I've managed to get my internal mic up and running on my CQ40-301TU by adding the following line to the file shown in the thread.

```
options snd-hda-intel model=hp-dv5
```

I couldn't get it going with the =ref alternative, but I could get it running using all of the others.

Namely;
=auto
=hp-hdx
=hp-dv5
=hp-m4

Although there does seem to be quite a bit of static when I use skype on internal mic, but still, it is better than nothing. Haven't tried using jack plugs yet.

As a side note I also had to go into the Sound preferences and go to the hardware tab and change the Profile to Analogue Stereo Duplex.

Many thanks 
BB

---

