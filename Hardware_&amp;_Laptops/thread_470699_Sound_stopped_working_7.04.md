---
title: "Sound stopped working 7.04"
date: 2007-06-11
forum: Hardware &amp; Laptops
---

### Post by crab on 2007-06-11
Hi,
I'm running 7.04 feisty on a dual boot windows/ubuntu Vaio VGN laptop. Everything was fine until last week when the sound stopped working:

Clicking on the panel volume control gives:

"No volume control GStreamer plugins and/or devices found." and  "The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plug-ins installed, or that you don't have a sound card configured."

alsamixer gives: "alsamixer: function snd_ctl_open failed for default: No such device
"

sound card is Intel AC97

I haven't, as far as i know, installed anything sound related apart from kernel update last week (how do i check what has been installed?). The sound does work in ubuntu up until log in and works fine on the same machine in windows. The problem is with all applications once logged in.

apart from that, Ubuntu is, as we say in London 'Wikid'

cheers

crab

---

### Post by muximus on 2007-06-12
recompiling alsa will definitely solve your problem
the link is here: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

b4 doing this, you might try 
apt-get remove alsa
then,
apt-get install alsa
it just might work.

---

### Post by crab on 2007-06-13
thanks for that...i also found this which solved the problem:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

sudo apt-get install linux-sound-base alsa-base alsa-utils

reboot

ta

crab

---

### Post by scohar70 on 2007-06-15
> **crab said:**
> thanks for that...i also found this which solved the problem:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

sudo apt-get install linux-sound-base alsa-base alsa-utils

reboot

ta

crab

My sound also stopped working in 7.04 Feisty.  I didn't install any updates or anything, and one day, the sound is off. 

I tried the above, but unfortunately it uninstalled my gnome desktop along with the alsa stuff, and didn't fix the sound problem!  ](*,)

I finally restored gnome desktop by doing the following.  (Followed by resetting up all my defaults for gdm).

```

sudo apt-get install gdm

```

And, finally, to fix the sound problem, I opened a terminal and typed **alsamixer**.   The PCM channel and the Master channel had for some reason been set to zero and they were both muted (the "MM" means mute).  I was able to restore the sound by changing these settings.

I think I could have skipped all the other steps and just done the **alsamixer**.

All is better now.

---

### Post by petyo on 2007-06-18
I have the same problem as above, however these solutions do not work for me. I am not sure if an update caused this, or maybe because I tried installing virtualbox. Really stuck with this one - I used the alsa-info script to generate this - 
[http://pastebin.ca/574853](http://pastebin.ca/574853)

Any ideas? I am not sure if this is an alsa problem, or I have done something wrong. Should I seek help in from the alsa guys? 

The alsamixer says 
alsamixer: function snd_ctl_open failed for default: No such device

I hear the drums right at the login screen. Not the following login music. 

Any help would be appreciated. This happens on IBM Thinkpad z60m.

---

