---
title: "Can't get any Sound on S/PDIF"
date: 2019-04-15
forum: Hardware
---

### Post by theswissgabe on 2019-04-15
Hey guys

  I'm trying to get sound on my 5.2 Sound System, that is connected with S/PDIF. Unfortunately, I don't get any sound...
  I already tried to solve this with this troubleshooter: [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
  The SPDIF Channel was muted, I unmuted it, but I'm not able to raise  the sound. I also tried to change the input with Paulseaudio, but it  doesn't work. I also installed the newest alsa-mixer software version.
  (When I tested the system first on a different HDD, I actually also  installed the newest Realtek-Soundcarddriver, and didn't have any sound  at all afterwards). 
  So those are the steps I already tried:
  
[LIST]
[*]Unmuting the SPDIF Channel 
[*]Updating alsamixer 
[*]Changing input with Pavucontrol 
[*]Updating all drivers -Rebooting the System 
[*]Unmuting the input with the command "sudo iecset audio on" 
[*]Disabling an activating the "auto-mute" function 
[/LIST]

Here's my Alsamixer-Status:
  [IMG]https://i.imgur.com/MZs9hJq.png[/IMG]

Is there anything else to try or should I just give up[SUP]?

[/SUP]

  Thanks for your help.

  Cheers

  Gabe

---

### Post by CatKiller on 2019-04-15
> **theswissgabe said:**
> The SPDIF Channel was muted, I unmuted it, but I'm not able to raise  the sound. 

S/PDIF is a digital stream. You wouldn't expect to have a volume control until it's been converted into an analogue signal. 

> Here's my Alsamixer-Status:

You still have your S/PDIF output muted.

---

### Post by theswissgabe on 2019-04-15
Okay, I enabled this channel, but I still don't get any sound.

Edit: Or to put it differently: When I close the mixer, the channel gets muted automatically.

---

