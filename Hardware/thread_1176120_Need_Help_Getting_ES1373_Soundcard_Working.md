---
title: "Need Help Getting ES1373 Soundcard Working"
date: 2009-06-02
forum: Hardware
---

### Post by stoi2m1 on 2009-06-02
I have looked in countless locations and done a number of things, but I still can not get my soundcard working. I installed Ubuntu without a soundcard with the desire to only use it as a server. But now I want to use it for more then that.

Here are some outputs for these commands just to help you help me get going in the right direction.

lspci

00:09.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)

So I know the hardware is there.

lsmod | grep snd
snd_ens1371            30880  0 
gameport               19468  1 snd_ens1371
snd_ac97_codec        111652  1 snd_ens1371
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  10 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  1 snd_pcm

I think this proves the driver is installed.

aplay -l
aplay: device_list:215: no soundcards found...

This shows what obvious, no soundcard found.

@server:~$ sudo modprobe snd_ens1371
[sudo] password for stoi2m1: 
@server:~$ cat /proc/asound/cards
--- no soundcards ---

So I tried this and still no soundcard.
 
sudo gedit /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
snd-ens1371

And finally I have done this so it works once i get the soundcard working it will work after I reboot.

I know I am missing something but it is not obvious to me what it is. Can someone help me out with this.

Thank, Jesse

---

### Post by stoi2m1 on 2009-06-02
I found this tutorial [Comprehensive Sound Problem Solutions Guide v0.5e]("http://ubuntuforums.org/showthread.php?t=205449")

I was following all of the instruction, but I get to the step Getting the ALSA drivers from a *fresh* kernel, and the build fails. The failure is happening at step 4.4.6 If you chose module-assistant
Code: sudo module-assistant a-i   alsa-source.

The error I am getting is:
Build of the package alsa-source failed! How do you wish to proceed?

Any thought or comments?

Thank,
Jesse

---

