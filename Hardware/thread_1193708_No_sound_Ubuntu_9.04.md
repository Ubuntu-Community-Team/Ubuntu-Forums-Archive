---
title: "No sound Ubuntu 9.04"
date: 2009-06-21
forum: Hardware
---

### Post by rfkrocktk on 2009-06-21
I just installed Ubuntu 9.04 64bit on my desktop computer.

I have a Realtek AC '97 soundcard built into my motherboard and a Creative X-Fi card as well. I can't get sound out of either. I installed the creative driver, and I was still unable to get sound. I found this post: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810) and ran the ALSA upgrade script, but it still didn't work and appeared to have removed my Creative card from my ALSA list of mixers and ins/outs. 

I can still see the driver in the Hardware Drivers application, but I still am getting no sound at all on either the Creative soundcard and/or the AC '97. 

After running the remove command which is supposed to restore the system to Ubuntu's default configuration with ALSA, I found that all of my inputs/outputs/mixers were wiped in the process and that I now only have a "Null Output" type of in/out/mixer.

:( Is there anything I can do to remedy this WITHOUT installing a fresh Ubuntu?

---

### Post by vegkitty on 2009-06-21
I had the same problem a while back.  Make sure that you have the pulseaudio plugins installed.  That was my issue.

---

### Post by linux_trojan on 2009-06-22
I am having the same trouble, it appears that I do have the pulseaudio software installed but there are various types, I am  not sure which all all those files you are refering too.  I dont see anything with PLUGIN that applies per se.

---

### Post by rfkrocktk on 2009-06-22
I'll try (re)installing Pulse Audio stuff, hopefully that works :)
I'd just really like to get some sound out of this computer :P

---

### Post by rfkrocktk on 2009-06-22
I just made sure pulseaudio is installed and it is. The problem is that I'm not seeing any of my audio hardware any more. PulseAudio, ALSA, and OSS are all installed and working, but I cannot see any of my hardware any longer. What can I do to make Ubuntu (or ALSA/Pulse) find my hardware?

---

### Post by rfkrocktk on 2009-06-23
Is there any way I can force Ubuntu to redetect my sound hardware? Surely there must be an application somewhere which can do it for me. If not, there's gotta be something I can do to make my kernel redetect my hardware, right?

---

### Post by rfkrocktk on 2009-06-24
Can anyone help me?

---

### Post by Yellow Pasque on 2009-06-24
Before you do a reinstall, try OSS4: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
The OSS4 X-fi driver is currently basic (no surround or hardware mixing), but it's better than no sound.

---

### Post by rfkrocktk on 2009-06-24
Thank you! I'll go ahead and give that a try. 

Do you know of any way to force redetection of audio hardware?

---

### Post by Yellow Pasque on 2009-06-24
> Do you know of any way to force redetection of audio hardware?
No. That doesn't make sense to me.

---

### Post by rfkrocktk on 2009-06-24
Sorry to sound like a newbie to this, I am one :(

Basically, ever since I upgraded to the newer version of ALSA (development version), my inputs/outputs/mixers basically only show ALSA/PulseAudio/OSS where they used to show things like "Playback: Creative X-Fi ..." before. Does that make sense? I just can't see any hardware in System->Preferences->Sound. It's really weird.

---

### Post by Bniewo on 2009-06-24
I have had this problem I am using the Alsa drivers. What I had to do to get it to work was right click the speaker at the top and click Open Volume Controls. It gave me three sets of volume bars the master volume bar, PCM volume bar, and Front. The PCM was completely down basically muted, so I slide those bars up and I had sound afterward. Hopefully this is your problem its an easy fix

---

### Post by rfkrocktk on 2009-06-24
I kind of wish that was my problem :) but alas, it's not :(

---

