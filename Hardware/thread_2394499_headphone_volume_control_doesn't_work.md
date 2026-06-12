---
title: "headphone volume control doesn't work"
date: 2018-06-17
forum: Hardware
---

### Post by rlaace423 on 2018-06-17
Hello, I'm enjoying ubuntu 18.04 on my laptop since last month. 

And I plugged headphone on my laptop, It makes me surprised because volume was too loud.

So, I tried to lower volume, but it didn't work. It always makes loudest volume.

And weird thing is, when I control system volumes to louder direction,

from middle range, It makes sound both headphone and notebook...


When I plug earphone or headphone, should something appeared at "System --> sound" ?? 
I just see "speaker-internal audio" in "choose sound device" area (It can be different because I use another language).


This happens both my headphone and earphone. My detail info is below.


* laptop: MSI gs63vr 7rg
* inxi info 
    Audio:     Card Intel CM238 HD Audio Controller driver: snd_hda_intel
         Sound: Advanced Linux Sound Architecture v: k4.15.0-23-generic
* ubuntu version : Ubuntu 18.04 LTS

---

### Post by ajgreeny on 2018-06-17
As I have just said in a reply to another thread about a similar problem, [https://ubuntuforums.org/showthread.php?t=2394496&p=13776813#post13776813](https://ubuntuforums.org/showthread.php?t=2394496&p=13776813#post13776813), open pulseaudio volume control either with command **pavucontrol** or by clicking on **Sound Settings** from the volume icon (not sure where that is in Ubuntu as I use Xubuntu).

You should in the **Output Devices** tab find both speakers and headphone settings separately in a dropdown box where you can set the volume of each.
See screenshot.

---

