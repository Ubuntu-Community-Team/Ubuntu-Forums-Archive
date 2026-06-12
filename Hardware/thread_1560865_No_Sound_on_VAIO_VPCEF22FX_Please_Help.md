---
title: "No Sound on VAIO VPCEF22FX Please Help"
date: 2010-08-25
forum: Hardware
---

### Post by West201 on 2010-08-25
I'm new to linux, and decided to installing Ubuntu 10.04. Everything went pretty smoothly during the installation, but I realized hours later there was no sound anywhere at all. The disk is fine because ubuntu is working perfectly on my Dell desktop, but not on the Sony laptop 
I've spended hours trying many methods posted on other forums, but no solution yet. I've tried ALSA Mixer, Sound Preference, removing audio pulse, and reinstalling everything.  

ALSA recognizes the sound cards I know that. 

Thanks for any help given :D

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Morm on 2010-08-25
In Synaptic, enable the Backports repository and install the Alsa driver backport. Worked for me (different Vaio, though).

---

### Post by lidex on 2010-08-26
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by West201 on 2010-08-26
> **Morm said:**
> In Synaptic, enable the Backports repository and install the Alsa driver backport. Worked for me (different Vaio, though).

How do I enable the Backports repository and install Alsa driver backport ? Thanks in advance

---

### Post by West201 on 2010-08-26
> **lidex said:**
> Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```Reference the Ubuntu-Bug Audio link in my sig.

I tried that solution but no luck. If you have another solution please let me know

---

### Post by lidex on 2011-01-13
> **jessejj89 said:**
> How do I enable the Backports repository and install Alsa driver backport ? Thanks in advance

Try updating your alsa-driver-modules.
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

### Post by West201 on 2011-01-14
I fixed the sound by simply upgrading from Ubuntu 10.04 to Ubuntu 10.10 Maverick :)

---

### Post by lidex on 2011-01-15
> **jessejj89 said:**
> I fixed the sound by simply upgrading from Ubuntu 10.04 to Ubuntu 10.10 Maverick :)

Good. I usually don't suggest that as most folks don't want the hassle of re-installing their entire system and/or want to stick with lts release.

---

