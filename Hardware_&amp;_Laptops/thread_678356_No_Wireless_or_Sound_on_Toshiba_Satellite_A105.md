---
title: "No Wireless or Sound on Toshiba Satellite A105"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by Elrohir on 2008-01-25
hey there!

long time no post... so I decided to go the whole way with Ubuntu this time... but with Gutsy I'm having trouble with the wireless (not being detected) and sound devices (no sound at all)...

attached is the output of lshw... if u guys need more info, let me know...

I really want to make this work...

---

### Post by eggdeng on 2008-01-26
To fix your sound, do
```
sudo gedit /etc/modprobe.d/alsa-base
```
& add
```
options snd-hda-intel model=3stack
```
to the end of the file. Save & [COLOR="Red"]reboot.[/COLOR]

---

### Post by the_sorrow on 2008-01-26
What model of Wireless are you using?
Have you tried enabled it in the restricted drivers manager?

---

### Post by Elrohir on 2008-01-26
> **eggdeng said:**
> To fix your sound, do
```
sudo gedit /etc/modprobe.d/alsa-base
```& add
```
options snd-hda-intel model=3stack
```to the end of the file. Save & [COLOR=Red]reboot.[/COLOR]
already tried this one... no good... :(

---

### Post by Elrohir on 2008-01-26
> **the_sorrow said:**
> What model of Wireless are you using?
Have you tried enabled it in the restricted drivers manager?
Intel Pro 2200BG...

---

### Post by Elrohir on 2008-01-26
been checking the lshw output and it says its using sky2 driver... shouldn't it be using ipw3945? how can I change that?

---

### Post by Elrohir on 2008-01-27
nobody?

---

### Post by Elrohir on 2008-01-28
guess not...

---

### Post by Das Goat on 2008-01-28
I have a A105-S2141

No joy here either with *'options snd-hda-intel model=3stack'*

from a different post, 

>terminal
lspci

In the output:

Audio Device: ATI Technologies Inc. SB450 HDA Audio (rev 01)

I think we should be looking for help with that device. (at least for me)

---

### Post by Elrohir on 2008-01-28
Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

That's actually my output...

YAY!!! partially solved... downgraded the BIOS version and now wireless is working... 

Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

I've tried the following options named in the forums for a fix on this issue:
options snd-hda-intel model=toshiba
options snd-hda-intel model=6stack-digout
options snd-hda-intel model=3stack

no good none of them... ideas?

---

### Post by Das Goat on 2008-01-28
There is an answer!

Here is the original thread:    [http://ubuntuforums.org/showthread.php?t=451011](http://ubuntuforums.org/showthread.php?t=451011)

The instructions are from calgarystevens
[I]
OK, hope this helps, only try this if you have the same Intel AC97 onboard audio. When I run lspci I see this in the mix: 00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop ubuntu-minimal
sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=auto
sudo gedit /etc/modprobe.d/alsa-base
and add "options snd-hda-intel probe_mask=8 model=auto" to the end[/I]

Then reboot. Sound came on for me.

Now if I can just figure out why i have wireless last night, but can not get it back today.....

:lolflag:

---

### Post by Das Goat on 2008-01-28
The wireless on this unit is a true puzzle.

 If i plug in the wired LAN, then go to wifi radar and tell it to get an IP, it works. I unplug the wire and I am wireless. But if I reboot, no wireless. then plug in the wire, wifi radar to get an ip, then unplug the wire, it works again. wierd. Like WIFi radar can't auto connect for some reason.

:confused:

---

### Post by Das Goat on 2008-01-28
Ok, I have a wired answer for this too!

For some reason, when you configure WiFi Radar, select <null> or "blank" for the selection under "WiFi Options" "Mode"

you can set the channel, 6, which is most systems default.

Why this works, I have no clue. But it does work. Saving and rebooting and wireless works just fine.

:popcorn:

---

### Post by Elrohir on 2008-01-28
> **Das Goat said:**
> Ok, I have a wired answer for this too!

For some reason, when you configure WiFi Radar, select <null> or "blank" for the selection under "WiFi Options" "Mode"

you can set the channel, 6, which is most systems default.

Why this works, I have no clue. But it does work. Saving and rebooting and wireless works just fine.

:popcorn:
cheers! I just downgraded the BIOS from 2.0 to 1.7 and wireless works for me... does the same solution for an ATI sound device will work for my Intel sound device? I'll give it a try, just for the fun of it...

---

### Post by Elrohir on 2008-01-28
> **Elrohir said:**
> cheers! I just downgraded the BIOS from 2.0 to 1.7 and wireless works for me... does the same solution for an ATI sound device will work for my Intel sound device? I'll give it a try, just for the fun of it...
I take that back... I just saw the Intel AC97 part.. :P

wish me luck!

---

### Post by Elrohir on 2008-01-29
> **Das Goat said:**
> There is an answer!

Here is the original thread:    [http://ubuntuforums.org/showthread.php?t=451011](http://ubuntuforums.org/showthread.php?t=451011)

The instructions are from calgarystevens
[I]
OK, hope this helps, only try this if you have the same Intel AC97 onboard audio. When I run lspci I see this in the mix: 00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop ubuntu-minimal
sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=auto
sudo gedit /etc/modprobe.d/alsa-base
and add "options snd-hda-intel probe_mask=8 model=auto" to the end[/I]

Then reboot. Sound came on for me.

Now if I can just figure out why i have wireless last night, but can not get it back today.....

:lolflag:
nope! no good... now it doesn't even detect the sound card... appears a dialog saying there is no sound card configured... :( going for a fresh install... maybe something went wrong... now with the BIOS downgraded, should make a change... (or at least I hope)

---

