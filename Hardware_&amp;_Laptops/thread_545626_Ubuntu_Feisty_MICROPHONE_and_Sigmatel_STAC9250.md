---
title: "Ubuntu Feisty MICROPHONE and Sigmatel STAC9250"
date: 2007-09-07
forum: Hardware &amp; Laptops
---

### Post by nefhyg on 2007-09-07
[SIZE="3"]Hi. I see that it's a common problem. So say I'm going to say what I have tried.

I have a Sigmatel STAC9250 on the laptop and I using ubuntu feisty.

I did some research and tried all "kmixer" tricks, that didnt work. Ive tried the editing the alsa-basef and putting that line at the end, it didnt work either. Ive tried this [http://ubuntuforums.org/showthread.php?p=2210477#post2210477](http://ubuntuforums.org/showthread.php?p=2210477#post2210477) . Ive tried all I could find using google and cant even remember all I ve tried. Then decided to try the alsa driver solution.

I then downloaded the alsa driver 15rc1 (what made me download the alsa-utils that made me download the alsa-lib that made me download gettext and ncurses and some other).

After successfully compiling and installing and following all instructions on the INSTALL file on the alsa driver, I still cant get the mic to work.

It isnt like I have no sound, its that when I try to record sound with the gnome recorder, it hangs. It doesnt matter if I use the "digital", "capture" or "capture mux" option. It just hangs.

If I try to test the sound, using the preferences/sound it gives me this error Failed to construct test pipeline for "gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat"

I accept any help from knowleageable users or developers who could help me make it work. It isnt a low priority problem for me since Im at the moment living very far from my wife and family and phone use isnt an option, so I need VoIP (skype for instance). Im this close to installing windows as dual boot (since I cant stay without linux because of development), so help me so I dont have to keep booting windows to talk to my wife and family.

please no "check if the sound isnt muted" or anything similar... ;)

But I accept any suggestions (besides that one).

I should say I have two jacks on the front of the laptop, a mic and an audio jack, there isnt any internal mic or anything.

Thanks. Ill reply with any logs as they are needed.[/SIZE]

---

### Post by nefhyg on 2007-09-07
[SIZE="3"]Here is the amixer output

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [0.00dB] [on]
  Front Right: Playback 31 [100%] [0.00dB] [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 15
  Front Left: Capture 15 [100%] [22.50dB] [on]
  Front Right: Capture 15 [100%] [22.50dB] [on]
Simple mixer control 'Capture Mux',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 4
  Front Left: 4 [100%] [40.00dB]
  Front Right: 4 [100%] [40.00dB]
Simple mixer control 'Caller ID',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 120 [100%] [30.00dB]
  Front Right: Capture 120 [100%] [30.00dB]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Front Mic' 'Line' 'CD'
  Item0: 'Front Mic'
Simple mixer control 'Off-hook',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off][/SIZE]

---

### Post by AlexanderN on 2007-09-18
ignore

---

### Post by wand on 2007-10-13
I also have a Sigmatel STAC9250 in my gateway MX series laptop.   The device is shown as follows in lspci:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

After trying every fix I could find online I concluded that the microphone is simply not supported by Linux at this time.  Fortunately I have been able to implement a workaround -- using a USB headset.  Mine was inexpensive and supported by Ubuntu without modification, however if I boot the computer with it inserted, internal sound does not work, so I must leave it unplugged when I boot.  After I plug it in I can configure skype settings to use it while other sound applications use the built in audio output.

---

### Post by treesurf on 2007-11-21
I'd like to bump this thread again, as I have the exact same problem.  This problem has continued following an otherwise flawless Gutsy upgrade.

I found a fix for this problem with a different SigmaTel card, but it is over my head.  Would anyone care to tackle this for the Sigmatel 9250? Here it is:

[http://mailman.alsa-project.org/pipermail/alsa-devel/2007-June/001414.html](http://mailman.alsa-project.org/pipermail/alsa-devel/2007-June/001414.html)

---

### Post by wayward on 2007-12-04
Bump.  I've been compiling ALSA from scratch in Feisty to get the sound to work after one of the Ubuntu's updates broke it, and I really don't feel like doing it again and again -- sound works, mic doesn't.  I'll continue searching for a way to make it work using Ubuntu-shipped ALSA and if I do find something, I'll let you know.

---

### Post by treesurf on 2007-12-04
Thanks, that's much appreciated.  For the moment I've resorted to a USB microphone so that I can make VoIP calls.  It took a bit of tinkering but the USB mic now seems to work fine with Gizmo.

---

### Post by pavkb on 2008-01-15
Starting this thread all over again, since there seem to be no resolution for this problem.

Not working in gutsy either.

Only difference i have with my gateway laptop is from the other in this thread is the following

> 
lspci
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)


as always, this is the only blemish in an otherwise awesome gutsy install.

regards

---

### Post by Ikith on 2008-03-14
Having the same problem as everyone in this thread I've tried everything to get this one single problem to work... EVERYTHING and I mean EVERYTHING else works perfect. I just can't get my MIC to work. I really need to record sound for my screencasts which are actually assignments for school :-(! Any fixes yet?

---

### Post by wayward on 2008-03-14
It's definitely an ALSA issue.  I've posted alredy on the alsa-devel list but received no response -- probably because they were driving towards 1.0.16 back then, and I was using 1.0.15.  I'll try again at some point in the future with the fresh sources from their Mercurial repo.  Lots of people are posting regarding hda-intel issues and, as far as I've seen, many of them get resolved and integrated into HG sources.  There's a chance that it has already been resolved.

I'll write here if/when I have something.

---

### Post by treesurf on 2008-03-14
Thanks.  Any positive information you find would be greatly appreciated.

---

### Post by jonaias on 2008-06-09
the same problem here!

---

### Post by KLineD on 2008-07-21
Same here

---

