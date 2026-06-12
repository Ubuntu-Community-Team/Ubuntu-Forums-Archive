---
title: "Swapping audio channels"
date: 2010-05-16
forum: Hardware
---

### Post by ongun.kanat on 2010-05-16
I've got HDA ATI SB sound card with Realtek ALC883 chip.On windows i can change subwoofer and center channels.But i can't find any option on ubuntu.

---

### Post by ongun.kanat on 2010-05-16
any answers?

---

### Post by lidex on 2010-05-16
Alsamixer
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

Gnome-alsamixer
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
Use 'Edit -> Sound Card Properties' menu to enable elements.
Soundcard tab to select / adjust levels.

---

### Post by ongun.kanat on 2010-05-18
I can use alsamixer for adjust levels but i can't swap subwoofer and center channels.On windows with realtek hd audio manager app i can change swap center/sub.Is there any way to solve it.There's no need to be graphical i can edit pulseaudio..

---

### Post by lidex on 2010-05-18
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
*_Also helpful is the make/model of your PC/Laptop._*
Please post text output using code tags (the # in toolbar)

---

### Post by bfloeagle on 2010-10-15
I was the having the exact same problems...   The center channel was being sent to the sub-woofer and the sub-woofer channel was being sent to the center speaker.  Things didn't sound quite right...  :P

I'm using Ubuntu 10.10 now but I'm pretty sure this will work on Ubuntu 10.04 as well since I upgraded from it.  In System > Preferences > Sound I am using the "Analog Surround 5.1 Output" profile (the test speakers option confirmed my center and sub-woofer channels were swapped, versus me just having a messed up speaker system).  After snooping around on the net, I found that PulseAudio uses a channel map to figure out where to send sounds to (sorry, I'm not an audiophile or PulseAudio guru so I'm just posting things as I discovered them).  Someone mentioned "/usr/share/pulseaudio/alsa-mixer/profile-sets/" in their comments for an unrelated problem they were having.   I snooped around on my system and found a default.conf file in that directory with the following:
```

[Mapping analog-surround-51]
device-strings = surround51:%f
**channel-map = front-left,front-right,rear-left,rear-right,[COLOR=Blue]front-center,lfe[/COLOR]**
paths-output = analog-output analog-output-speaker analog-output-desktop-speaker analog-output-lfe-on-mono
priority = 8
direction = output

```So I changed the position of the lfe and front-center to the following:
```

[Mapping analog-surround-51]
device-strings = surround51:%f
**channel-map = front-left,front-right,rear-left,rear-right,[COLOR=Red]lfe,front-center[/COLOR]**
paths-output = analog-output analog-output-speaker analog-output-desktop-speaker analog-output-lfe-on-mono
priority = 8
direction = output

```I rebooted, but probably could have restarted PulseAudio, and now I'm good to go!  Sound is coming out of the correct channel in the speaker test and I'm finally able to listen in 5.1 Surround Sound on DVDs in Ubuntu.  :)

---

