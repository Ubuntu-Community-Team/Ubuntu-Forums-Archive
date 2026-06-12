---
title: "Yet another cs4237b-problem"
date: 2007-12-17
forum: Hardware &amp; Laptops
---

### Post by 1101001101 on 2007-12-17
So, I've got a problem, pretty clear, huh?
My problem: My ISA CS4237b soundcard in my Dell Latitude CPi D266XT
Well, some of you might already say: "oh, we know this problem, just do this and your sound card'll be detected:..."
Thats not my problem, well, it was at first, but i got it detected now (as a cs4236, dunno if thats good/bad?) and I can use alsamixer and soundplaying program, but I still get no sound through the speakers...
I got it detected by adding something about the snd-CS4232 in a new file called /etc/modprobe.d/sound
then, at startup I turned the splash in boot off, you know, to get all those lines about the booting sequence, and now, when he's at "loading hardware drivers", he says something about that cs4232, failed, but when booting is finished, and I login, my soundcard is detected as cs4236...
when I press the Fn+sound mute/unmute button on the keyboard, i can hear a little crackling click, but no sound, and i'm not sure when its muted/unmuted, but even when I try it twice, still no sound, even when I turn the volume all up...

suggestions, anyone?

edit: almost forgot to say, i'm running Xubuntu 7.10, tried ubuntu 7.10, but sound didnt work there either, so changed to Xubuntu

---

### Post by bigmo9 on 2007-12-17
I have the same problem with a cs4614 on my thinkpad t22, I get the crackling and a system beep though.  I tried this guide but it didn't help: [http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+problem+cs46xx](http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+problem+cs46xx)
I'm running ubuntu 7.10

---

### Post by 1101001101 on 2007-12-17
yeah, system beep worked from the beginning, so its really the sound card,
I tried pnpbois-tools, but i always get the error about "proc/bus/pnp" nonexistent
anybody knows how to fix that?
and I already tried that guide and every one I could find, none worked...:(

---

### Post by 1101001101 on 2007-12-17
checked it, at boot it says:

[  39.548000] CS4232 WSS PnP manual resources are invalid, using auto config
[  39.548000] CS4232 WSS PnP configure failed for WSS (out of resources?)
[  39.548000] PnP BIOS detection failed for CS4232

---

### Post by bigmo9 on 2007-12-17
I'm not sure if you are getting this error also but the output of my dmesg shows:
cs46xx: failure waiting for FIFO command to complete.

---

### Post by bigmo9 on 2007-12-17
Reading another post suggests that you check your bios and see if it is disabled in the bios.  I can't supply the post for you I don't remember where it was.  might be something to check.

---

### Post by 1101001101 on 2007-12-17
Well, bios won't be a good help, its the good ol' dell CPi bios, zero functionality

---

### Post by bigmo9 on 2007-12-17
This looks like a known bug, maybe this post can help.
[http://ubuntuforums.org/showthread.php?t=362505](http://ubuntuforums.org/showthread.php?t=362505)
I know you said you tried pnp tool

---

### Post by 1101001101 on 2007-12-18
meh, still no luck, and I figured out one thing, i've got no /etc/modprobe.conf, is that a problem?? anyone got the file, so I can "make" it?

---

### Post by leon_mcnichols on 2007-12-24
> **1101001101 said:**
> Well, bios won't be a good help, its the good ol' dell CPi bios, zero functionality

I'll have to stand up and say Howdy ! I too can't get into the borked di*k that dell has on thier CPi laptops. Can't do jack didlly you can change the dat time and the plug and pull drives but thats about it. niiiice. and Yea I got a 7.10 Kubuntu who's sound is also jacked and has no snd on the /ect/modules yet according the sys info its a sb pro or clone. :confused:

---

