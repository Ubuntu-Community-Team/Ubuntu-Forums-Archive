---
title: "Laptop Microphone Not Working Toshiba Satellite C650D"
date: 2011-01-01
forum: Hardware
---

### Post by jmate on 2011-01-01
Hey everyone,

I am running a Toshiba Satellite C650D. The laptop comes with a microphone and webcam inside the monitor. The webcam works fine; however, the microphone is not working.

I went to System -> Preferences -> Sound -> Input
and there is only one input I can adjust. There should be two. There should be one for a microphone that you plug in into the audio jack on the side of the laptop. There should be a second one for the microphone that is inside the laptop. The second one is missing.

Let me know what other information you guys need.

Cheers,
Joseph

---

### Post by lidex on 2011-01-01
This will be helpful. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by sanderd17 on 2011-01-01
I don't think you should see two sliders. But be sure that you don't set your volume too high. I don't know how it comes, but if I put the volume too high, I hear nothing, if I lower it, I can hear sound.
(you should see bars moving when you make a sound)

and check that you selected the right input from the drop-down list.

---

### Post by jmate on 2011-01-01
lidex:
Here is the result from the alsa-info script:
[http://www.alsa-project.org/db/?f=d2f9a70014cbe861df3b7375dae20cff996fd940](http://www.alsa-project.org/db/?f=d2f9a70014cbe861df3b7375dae20cff996fd940)


sanderd17:
Which drop down are you talking about?
If you are talking about the drop down list under the Sound's Hardware Tab then my options are:
* Off
* Analog Stereo Input
* Digital Stereo Duplex (IEC958 )
* Digital Stereo (IEC958 ) Output + Analog Stereo Input
* Analog Stereo Output
* Analog Stereo Duplex
I have Analog Stereo Duplex selected.

If you are talking about the radio list under Input Tab, underneath the label "Choose a device for sound input:" then I only have the option:
* Internal Audio Analog Stereo

Cheers

---

### Post by jmate on 2011-01-01
I looked through the output and it only recognizes one device:

```

ARECORD
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Shouldn't there be an additional recording device for the laptop microphone?

---

### Post by lidex on 2011-01-01
OK. Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=thinkpad 
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

---

### Post by jmate on 2011-01-01
That fixed it! Thanks a bunch.

---

### Post by lidex on 2011-01-01
You're welcome. Happy New Year as well.

---

### Post by jmate on 2011-01-01
Happy New Year lidex.

---

### Post by yagolf on 2011-01-03
Hi there and happy new year to all of you!

I know this thread is marked as solved but I've just stumbled upon it and thought my problems were solved but I'm afraid it ain't true...

I have the same machine as jmate and I've followed your instructions about editing the alsa-base.conf file but to no avail...

[here]("http://www.alsa-project.org/db/?f=68d6a22c41b28275d1650215114a40b3d5572ad3") is the result of running your script. As you can see I'm running Julia at the moment but I had maverick till very recently and everything was the same.

A difference I can see between my machine and jmate's is that I don't seem to have ALSA libraries installed (though I do have  the libasound2 package installed (1.0.23))
Another clear difference is in:
> APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

As you know jmate's machine recognises two subdevices under playback devices, and the CAPTURE device figures under Subdevice: 1/1 in his machine. As to the relevance of that, I haven't the faintest, I just don't know enough... ](*,)

Any help would be eternally appreciated!

:guitar: Rock on!

---

### Post by lidex on 2011-01-03
@yagolf
Eternally, eh? That's a lot of beer.
Yeah your libraries are out of order. An alsa re-install should fix it. Try this method.
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

---

### Post by yagolf on 2011-01-03
Success!!! :guitar:

If I ever get to Ohio or you ever come to London, man you've got as many beers as you can drink on one night on me!!

you have made me a very happy man indeed.

---

### Post by nanonils on 2011-01-30
> **lidex said:**
> @yagolf
Eternally, eh? That's a lot of beer.
Yeah your libraries are out of order. An alsa re-install should fix it. Try this method.
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**


Oh my god that did it! :guitar:
Only cost me half a day to come across your post and fix it. THANK YOU MUCH!
Purchased a cheap Toshiba-Satellite Laptop / Intel® Core™ i3 Processor / 15.6" Display-Black-C655-S5061, SKU: 1552571 for my mother in Europe and figured the reason why Google Video Chat microphone input was not working was that she is a computer illiterate... Now that it's working I'm realizing not having a microphone might not be such a bad thing (*cough*).

---

### Post by cptnmurff on 2011-03-31
Thank You _Lidex_ for all your posts on "Laptop Microphone not working" !
They made is so easy to fix our Mic issuses... You da Man :KS

---

