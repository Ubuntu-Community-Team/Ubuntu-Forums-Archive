---
title: "New to Ubuntu - Need audio driver"
date: 2008-12-29
forum: Hardware
---

### Post by MikeBaum on 2008-12-29
I need the driver and installation instructions pls for the following audio hardware:
intel 82801hb ich8 high definition audio [b1]
I'm running Edubuntu

---

### Post by hotweiss on 2008-12-29
See if this helps:

[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

---

### Post by halovivek on 2008-12-29
see this 
[HOWTO: PulseAudio Fixes & System-Wide Equalizer Support]("http://ubuntuforums.org/showthread.php?t=789578&highlight=audio+pulse")
this may help you.

---

### Post by MikeBaum on 2008-12-29
Hi. Still in need of assistance.

---

### Post by skern03 on 2008-12-29
> **MikeBaum said:**
> Hi. Still in need of assistance.

Please don't take the following in the wrong way. You said you're new, so it's hard to gauge your level of knowledge. 

If you can tell us what assistance you need, that would be helpful. Are you having difficulty with the instructions in the URL? Do the instructions work, but not resolve the problem? Does the audio function at all? Or...? 

The Pulseadio fixes in the URL posted by halovivek are what I've used to configure Ubuntu 8.04. There are also instructions for 8.10. I went from sound at 1/3 volume level to full sound, although I think that Windows is actually a bit better. But then, I have a chipset-specific driver set up for Windows (this machine is dual-boot, XP and Ubuntu 8.04).

---

### Post by MikeBaum on 2008-12-30
Hello, nope I didn't take it the wrong way. Last night I upgraded to Ubuntu 8.10. I have no audio at all. The tests don't even allow audio to play so I'm under the impression that I need to manually load my driver. I tried following the instructions but I don't even understand yet how to open a shell or dos window or whatever its called to type in code. And it would seem that it would be easier than that to get an intel driver but I guess I need to follow the steps I'm given. I just need the most fundamental steps that someone could articulate. Thanks everyone for helping the newb of newbs here. I know it can be frustrating.

---

### Post by linux_tech on 2008-12-30
Applications>Accessories>Terminal-
In terminal, what is output of 
```
aplay -l

cat /proc/asound/card0/codec#* | grep Codec

amixer info

lspci -v | fgrep -i AUDIO 

 lsmod | grep snd

```

---

### Post by skern03 on 2008-12-30
> **MikeBaum said:**
> Hello, nope I didn't take it the wrong way. Last night I upgraded to Ubuntu 8.10. I have no audio at all. The tests don't even allow audio to play so I'm under the impression that I need to manually load my driver. I tried following the instructions but I don't even understand yet how to open a shell or dos window or whatever its called to type in code. And it would seem that it would be easier than that to get an intel driver but I guess I need to follow the steps I'm given. I just need the most fundamental steps that someone could articulate. Thanks everyone for helping the newb of newbs here. I know it can be frustrating.

Okay, here's what you do. Follow the steps in the instructions posted earlier at this URL:

[http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio](http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio)

When it says type things that start with "sudo" or other commands (as I recall, those are all in text areas with different backgrounds in that post, just like your original message above), you need to be in a terminal window. You find that from the top menu - Applications, Accessories, Terminal.

You can copy the lines in the quotes for the terminal. Instead of Ctrl+V to paste into the terminal window, use Shift+Ctrl+V. Or, you can type it directly into the terminal window.

The first time you do anything starting with "sudo" (super user), you'll be prompted for a login password. Just enter the password you used when you set the system up.

BTW, you won't often find proprietary drivers here, although there are a few. Only a few manufacturers actually provide Linux drivers, and I don't think Intel is one, although I'm often mistaken about stuff like this ;-). Most of the drivers are community supported If Ubuntu detects a card for which a driver is available, like the Broadcom wireless cards or the NVidia video cards, you'll see a small icon in the notification area (the spot in the upper right menu bar on the top next to the clock).

Before you do anything with the drivers, be sure your system is up-to-date. The first time you load from a CD, there are usually about 200 updates. Sometimes that resolves the issue, and sometimes a new driver is available that wasn't on the CD.

Also, 8.10 is a bit flaky. I have one machine that won't load it in any flavor, except the Live CD. On a 5-year-old laptop, it installed. But the first time, I had no network. I just reinstalled it, and the network (both wired and wireless) were there. If the fix for PulseAudio doesn't work, try reinstalling.

HTH...

---

### Post by MikeBaum on 2008-12-31
> **linux_tech said:**
> Applications>Accessories>Terminal-
In terminal, what is output of 
```
aplay -l

cat /proc/asound/card0/codec#* | grep Codec

amixer info

lspci -v | fgrep -i AUDIO 

 lsmod | grep snd

```



I pasted this info into terminal and here's what it I've got:

administrator@administrator-laptop:~$ aplay -l
aplay: device_list:215: no soundcards found...
administrator@administrator-laptop:~$ 
administrator@administrator-laptop:~$ cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory
administrator@administrator-laptop:~$ 
administrator@administrator-laptop:~$ amixer info
Card default 'pulse'/'PulseAudio'
  Mixer name	: 'PulseAudio'
  Components	: ''
  Controls      : 0
  Simple ctrls  : 0
administrator@administrator-laptop:~$ 
administrator@administrator-laptop:~$ lspci -v | fgrep -i AUDIO 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
administrator@administrator-laptop:~$ 
administrator@administrator-laptop:~$  lsmod | grep snd
snd_hda_intel         381488  0 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
administrator@administrator-laptop:~$

---

### Post by MikeBaum on 2008-12-31
> **skern03 said:**
> Okay, here's what you do. Follow the steps in the instructions posted earlier at this URL:

[http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio](http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio)

When it says type things that start with "sudo" or other commands (as I recall, those are all in text areas with different backgrounds in that post, just like your original message above), you need to be in a terminal window. You find that from the top menu - Applications, Accessories, Terminal.

You can copy the lines in the quotes for the terminal. Instead of Ctrl+V to paste into the terminal window, use Shift+Ctrl+V. Or, you can type it directly into the terminal window.

The first time you do anything starting with "sudo" (super user), you'll be prompted for a login password. Just enter the password you used when you set the system up.

BTW, you won't often find proprietary drivers here, although there are a few. Only a few manufacturers actually provide Linux drivers, and I don't think Intel is one, although I'm often mistaken about stuff like this ;-). Most of the drivers are community supported If Ubuntu detects a card for which a driver is available, like the Broadcom wireless cards or the NVidia video cards, you'll see a small icon in the notification area (the spot in the upper right menu bar on the top next to the clock).

Before you do anything with the drivers, be sure your system is up-to-date. The first time you load from a CD, there are usually about 200 updates. Sometimes that resolves the issue, and sometimes a new driver is available that wasn't on the CD.

Also, 8.10 is a bit flaky. I have one machine that won't load it in any flavor, except the Live CD. On a 5-year-old laptop, it installed. But the first time, I had no network. I just reinstalled it, and the network (both wired and wireless) were there. If the fix for PulseAudio doesn't work, try reinstalling.

HTH...



I ran the following commands and received the following responses (it's the first step from the link you provided):

administrator@administrator-laptop:~$ $ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
bash: $: command not found
administrator@administrator-laptop:~$ $ sudo rm -r ~/.pulse ~/.asound* /etc/asound.conf
bash: $: command not found

---

### Post by skern03 on 2008-12-31
> **MikeBaum said:**
> I ran the following commands and received the following responses (it's the first step from the link you provided):

administrator@administrator-laptop:~$ $ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
bash: $: command not found
administrator@administrator-laptop:~$ $ sudo rm -r ~/.pulse ~/.asound* /etc/asound.conf
bash: $: command not found

Mike - your problem is that you have an extra "$" - it should be just the text, i.e., 

[INDENT]sudo rm -r.... etc.[/INDENT]

---

### Post by MikeBaum on 2009-01-03
I'm learning. I ran the commands as advised in the pulseaudio link for appendix a and c. My audio card is still not detected and is actually needed first before a couple of those steps will function accordingly. Still need a hand if you can please.

---

### Post by MikeBaum on 2009-01-03
THis might help a bit:
When I go to System, Preferences, Sound and go to Sound Capture, I have the following listing: Pulseaudio Sound Server. 
Now when I hit test it gives the following error:

gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Failed to connect stream: Invalid argument

---

### Post by MikeBaum on 2009-01-03
Two insignificant updates:
I installed cheese apparently

When running the following command the following response occurs:
administrator@administrator-laptop:~$ cat /proc/asound/card0/codec#*
cat: /proc/asound/card0/codec#*: No such file or directory

I ran this command too:
administrator@administrator-laptop:~$ aplay -l
aplay: device_list:215: no soundcards found...
administrator@administrator-laptop:~$ 

When running find /lib/modules/`uname -r` | grep snd 
a long list of items appeared which apparently is good.

When running lspci -v | less
this appears:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Mitac Device 8227
        Flags: fast devsel, IRQ 22
        Memory at fc200000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel


?????????????????????????????????????????????????
Thanks in advance to anyone's guidance

---

### Post by skern03 on 2009-01-03
> **MikeBaum said:**
> Two insignificant updates:
I installed cheese apparently

When running the following command the following response occurs:
administrator@administrator-laptop:~$ cat /proc/asound/card0/codec#*
cat: /proc/asound/card0/codec#*: No such file or directory

I ran this command too:
administrator@administrator-laptop:~$ aplay -l
aplay: device_list:215: no soundcards found...
administrator@administrator-laptop:~$ 

When running find /lib/modules/`uname -r` | grep snd 
a long list of items appeared which apparently is good.

When running lspci -v | less
this appears:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Mitac Device 8227
        Flags: fast devsel, IRQ 22
        Memory at fc200000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel


?????????????????????????????????????????????????
Thanks in advance to anyone's guidance

Mike - the good news is that it does recognize that you have a sound card! Now you need to find the appropriate driver and install it. At the top of the Multi-Media and Video forum you'll find a couple of sticky posts. Here's a link to the first:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

In it, there is a link to the alsa drivers page, and detailed instructions on how to install. It is a bit lengthy, but I bet if you persevere, you'll have video soon!

Good luck, and post back how you fare!

---

### Post by MikeBaum on 2009-01-03
> **linux_tech said:**
> Applications>Accessories>Terminal-
In terminal, what is output of 
```
aplay -l

cat /proc/asound/card0/codec#* | grep Codec

amixer info

lspci -v | fgrep -i AUDIO 

 lsmod | grep snd

```



administrator@administrator-laptop:~$ aplay -l
aplay: device_list:215: no soundcards found...
administrator@administrator-laptop:~$ cat /proc/asound/card0/codec#* | grep Codec
cat: /proc/asound/card0/codec#*: No such file or directory
administrator@administrator-laptop:~$ 
administrator@administrator-laptop:~$ amixer info
Card default 'pulse'/'PulseAudio'
  Mixer name	: 'PulseAudio'
  Components	: ''
  Controls      : 0
  Simple ctrls  : 0
administrator@administrator-laptop:~$ lspci -v | fgrep -i AUDIO 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
administrator@administrator-laptop:~$ 
administrator@administrator-laptop:~$ lsmod | grep snd
snd_hda_intel         384176  0 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
administrator@administrator-laptop:~$

---

### Post by MikeBaum on 2009-01-03
Skern03 ~ It appears that the ALSA PROJECT members create audio drivers for linux/ubuntu and they have not yet developed this Intel driver. Check this out and tell me if you concur:
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)

---

### Post by steveneddy on 2009-01-03
@skern03

in your sig - it's supposed to be

ID 10 T

as in

"If you can't figure it out, just submit an ID-10T form and we'll call you."

To the OP:

I believe going with ALSA will solve your issues.

---

### Post by skern03 on 2009-01-03
> **MikeBaum said:**
> Skern03 ~ It appears that the ALSA PROJECT members create audio drivers for linux/ubuntu and they have not yet developed this Intel driver. Check this out and tell me if you concur:
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel)

You're correct, I don't see ICH8. However, I wonder if an earlier version might work.

Although I doubt it will help, you could download an ISO for Ubuntu 8.04 or 8.10, burn it to CD and then run it live, rather than installing it. If you can get sound to work, then you can install Ubuntu - maybe even dual-boot with Edubuntu.

---

### Post by skern03 on 2009-01-03
> **steveneddy said:**
> @skern03
in your sig - it's supposed to be ID 10 T

@steveneddy:
I did the sig that way in_10_tionally :P

---

### Post by MikeBaum on 2009-01-04
Addnotes....


I ran the command   modinfo soundcore    and got:

administrator@administrator-laptop:~$ modinfo soundcore
filename:       /lib/modules/2.6.27-11-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     E4F49ED9C4CFD1A5A923330
depends:        
vermagic:       2.6.27-11-generic SMP mod_unload modversions 586 
administrator@administrator-laptop:~$

---

### Post by MikeBaum on 2009-01-29
Well I don't want to be a nuisance but I do want to try to spread the word that I still need an audio driver in order to truly use ubuntu and replace microsoft's crap.

---

