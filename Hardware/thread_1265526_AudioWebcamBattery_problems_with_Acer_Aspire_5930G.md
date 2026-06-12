---
title: "Audio/Webcam/Battery problems with Acer Aspire 5930G and Ubuntu 9.04"
date: 2009-09-13
forum: Hardware
---

### Post by andy80 on 2009-09-13
Hi all,

I've recently bought an Acer Aspire 5930G notebook and I've installed Ubuntu 9.04 on it (I'm not new to Linux... I use it since 1996 :P ).

Almost all is working fine, but there are some problems I'd like to fix if possible.

1) Internal Mic: internal mic is not working on Ubuntu 9.04. I've tried to use the LIVE CD of Ubuntu 9.10 ALPHA, installing Skype, and it looks like to work without problem. Is it possible to have it working on Ubuntu 9.04 too?

Technical info:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

snd_hda_intel         435252  5 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  18 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm

2) Headset is not working. When I plug the headset I continue hearing music from the notebook speaker and not from the headset. I've tried to see if this bug is fixed in Karmic Alpha 5 and it's only half fixed: the headset works fine, but even if the notebook speakers are mute (ad expected) I still can hear music from the notebook subwoofer.

3) The internal webcam is recognized by Skype, Cheese and even by Flash plugin but when I try to record some video (in Cheese for example) or when I do a video call with Skype, I've always the same problem, the video is delayed and flickered.

This is the integrated webcam: Acer HD Crystal Eye

4) Battery lasts only 1 hour and 20 :(
I've already done the usual charge/discharge sessions with the battery and it still can't last more than 1 hour and 20 minutes. The CPU stays at 800Mhz when using battery, the light of the display is well managed and the fan doesn't make noise. How can I improve it?

5) SD card reader doesn't work. When I insert an SD card, nothing happens, and I don't find anything neither on /var/log/messages
any idea how I can make it work?

Thanks for your help!

---

### Post by sittingpenguin on 2009-11-09
Hi,

I just found, after months of poking around, that the alsa option that works for the 5930g is model=acer-aspire-6530g, don't ask me why.

So (for the newbies) I changed the last line of the file /etc/modprobe.d/alsa-base.conf from "options snd-hda-intel power_save=10 power_save_controller=N" to "options snd-hda-intel model=acer-aspire-6530g power_save=10 power_save_controller=N".

With that option everything works as expected, including the tuba bass that gets muted upon headphones hook-up.

For some reason the pc beep didn't turn on using alsamixer, I activated it with the following command: xset b on. I use it in place of the darn logout sound that they insist not to implement.

For the card reader you can search the how-to's for the aspire one, there are different approaches, none of them clean in my opinion, I keep it deactivated because I don't need it. Forcing it on by passing pciehp.pciehp-force=1 at boot is not enough, you also want to enable power management for it or you risk data corruption on the memory sticks upon suspend of the laptop; there are a few scripts for it around but i can't remember exactly where right now.

Hope this helps.

---

### Post by sittingpenguin on 2009-11-09
I forgot to mention that for the webcam you might want to decrease the default resolution in the cheese preferences, to 640x480 for example, and use the highest setting for still pictures.

---

### Post by andy80 on 2009-11-09
> **sittingpenguin said:**
> Hi,

I just found, after months of poking around, that the alsa option that works for the 5930g is model=acer-aspire-6530g, don't ask me why.

So (for the newbies) I changed the last line of the file /etc/modprobe.d/alsa-base.conf from "options snd-hda-intel power_save=10 power_save_controller=N" to "options snd-hda-intel model=acer-aspire-6530g power_save=10 power_save_controller=N".

With that option everything works as expected, including the tuba bass that gets muted upon headphones hook-up.

For some reason the pc beep didn't turn on using alsamixer, I activated it with the following command: xset b on. I use it in place of the darn logout sound that they insist not to implement.

For the card reader you can search the how-to's for the aspire one, there are different approaches, none of them clean in my opinion, I keep it deactivated because I don't need it. Forcing it on by passing pciehp.pciehp-force=1 at boot is not enough, you also want to enable power management for it or you risk data corruption on the memory sticks upon suspend of the laptop; there are a few scripts for it around but i can't remember exactly where right now.

Hope this helps.

Hi, thanks for the tip, but I don't have that line in my file :\
This is the content of my file: [http://pastebin.ca/1664252](http://pastebin.ca/1664252)
where do I have to put that line you say? Thanks!

---

### Post by sittingpenguin on 2009-11-09
> **andy80 said:**
> Hi, thanks for the tip, but I don't have that line in my file :\
This is the content of my file: [http://pastebin.ca/1664252](http://pastebin.ca/1664252)
where do I have to put that line you say? Thanks!

Just add it at the end of the file. But if you're still on Jaunty you need to either upgrade to Karmic or update your alsa to 1.0.20 manually. Alsa 1.0.18 does not support our laptop at all.

---

### Post by andy80 on 2009-11-09
> **sittingpenguin said:**
> Just add it at the end of the file. But if you're still on Jaunty you need to either upgrade to Karmic or update your alsa to 1.0.20 manually. Alsa 1.0.18 does not support our laptop at all.

well... I do prefer trying to update only ALSA or keep the sound as is! You cannot imagine all the bugs I had with Karmic :(

Or better... look here: [https://bugs.launchpad.net/~andy80](https://bugs.launchpad.net/~andy80)

---

### Post by andy80 on 2009-11-09
> **sittingpenguin said:**
> I forgot to mention that for the webcam you might want to decrease the default resolution in the cheese preferences, to 640x480 for example, and use the highest setting for still pictures.

this workaround worked perfectly!

---

### Post by sittingpenguin on 2009-11-10
Well I have no bugs affecting me with Karmic. Actually, it is giving me the almost perfect unix experience with this machine. I see two differences between my setup and yours though: I use 64bit and my bios is version 1.23; not sure if that makes a difference.

---

### Post by sittingpenguin on 2009-11-21
Update: I contacted the alsa developers and they have modified the quirk for the 5930g according to my findings, so starting from 1.0.22 it should work without manually specifying any option. Thanks Takashi!

---

### Post by john1066 on 2009-12-12
Can somebody please fill me in on what this alsa is. I have an Acer Aspire 6930G and 9.10. Skype has two problems - doesn't give video and doesn't accept input from the webcam speaker. Packages such as the packaged audio recorder and Audacity also don't take their input from webcam speaker. Looks like Ubuntu is blind to Acer's crystal eye webcam.

Hope you can help,
John

---

### Post by Elisavet on 2010-05-26
> **andy80 said:**
> SD card reader doesn't work. When I insert an SD card, nothing happens, and I don't find anything neither on /var/log/messages
any idea how I can make it work?
Thanks for your help!

I've read somewhere, I can't recall now, that there's a bug on that.
The SD card will work perfectly in your system as long as you boot your computer with the card already inside the slot.

Have you had any luck with the audio/mic/battery problems?
I have almost the same computer (acer aspire 5930) and the audio problem really got me back to windows :( (at least a dual boot)

---

