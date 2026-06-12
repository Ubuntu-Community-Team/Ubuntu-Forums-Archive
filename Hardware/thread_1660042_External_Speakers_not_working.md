---
title: "External Speakers not working"
date: 2011-01-04
forum: Hardware
---

### Post by Danny830x on 2011-01-04
Hey,

I just installed Ubuntu 10.10 today so I am a little unfamiliar it.
I have logitech S220 speakers and a Dell Inspiron 7010 notebook. 

When I was doing the pre-install test, the external speakers were working fine. However, when I finished the install I noticed that the speakers are not working and the sound is now coming out of my laptop speakers.

I'm not really sure what kind of info you guys need, but this is the audio controller from the lspci:

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)

Thank you

---

### Post by lidex on 2011-01-05
You may just need to switch default sound device. You can do that via 'Sound Preferences'. Are the logitech speakers usb? What is the output of:
```
aplay -l
```
In a Terminal="Applications->Accessories->Terminal"

---

### Post by Danny830x on 2011-01-05
```
card 0: Intel [HDA Intel], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by Danny830x on 2011-01-05
Speakers are not USB. They hook into my headphone jack on the laptop.

---

### Post by Danny830x on 2011-01-05
Something else I just noticed.. my volume buttons do not work. Hopefully whatever fix we come up with will fix both problems

---

### Post by lidex on 2011-01-05
> **Danny830x said:**
> Speakers are not USB. They hook into my headphone jack on the laptop.

So what we have here is no line/headphone output. I'll need more info. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Danny830x on 2011-01-05
[http://www.alsa-project.org/db/?f=d52a74459443dfe4836e4fa284e7125df1fbc34c](http://www.alsa-project.org/db/?f=d52a74459443dfe4836e4fa284e7125df1fbc34c)


Thanks for your help.

---

### Post by lidex on 2011-01-07
Best thing I can suggest now is updating your alsa modules:

Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
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

