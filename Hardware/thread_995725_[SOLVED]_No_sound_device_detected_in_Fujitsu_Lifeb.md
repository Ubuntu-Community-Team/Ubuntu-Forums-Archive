---
title: "[SOLVED] No sound device detected in Fujitsu Lifebook P5010 in 8.10"
date: 2008-11-28
forum: Hardware
---

### Post by prshah on 2008-11-28
Hello,

**Summary: I have no sound device detected on Lifebook P5010 with 8.10 kernel 2.6.27-7**

Details:
I have a Fujitsu Lifebook P5010 laptop / notebook.

I have been using Ubuntu since 7.10 on this laptop without any trouble, and have upgraded through to 8.04 -> 8.10 beta.

It is currently fully updated.

I have no sound on this with kernel 2.6.27-7. It was / is working fine with 2.6.24-21 and below. It is also working fine with Win XP Home (dual boot).

I have tried various suggestions to no avail.

I _suspect_ it is because I do not have "linux-ubuntu-modules-2.6.27-7-generic" installed, but I can't seem to find it:```

sudo apt-get install linux-ubuntu-modules-2.6.2[Tab][Tab]
linux-ubuntu-modules-2.6.22-14-generic
linux-ubuntu-modules-2.6.24-16-generic
linux-ubuntu-modules-2.6.24-17-generic
linux-ubuntu-modules-2.6.24-18-generic
linux-ubuntu-modules-2.6.24-19-generic
linux-ubuntu-modules-2.6.24-21-generic

```

I have tried running "sudo depmod -a" (exits successfully) and restarting, no effect.

I've tried manually loading all relevant modules, there is no error (either in screen or in dmesg) but the audio device is still not detected```

sudo modprobe ac97_bus snd_intel8x0 snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm \
snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer \
 snd_seq_device snd soundcore snd_page_alloc 

```

Some basic information:

```

~$ uname -a
Linux laptop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux

~$ lspci  |grep -i audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

~$ cat /proc/asound/cards 
--- no soundcards ---

~$ aplay -l
aplay: device_list:215: no soundcards found...

~$ sudo lshw -C sound
  *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

~$ lsmod | grep -i snd
snd_pcm_oss            46496  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83844  1 snd_pcm_oss
snd_seq_dummy          11012  0 
snd_seq_oss            39936  0 
snd_seq_midi           14368  0 
snd_rawmidi            29728  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                58352  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29448  2 snd_pcm,snd_seq
snd_seq_device         15500  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    64164  9 snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16776  1 snd_pcm

# below is the module listing with working sound in kernel 2.6.24-21
:~$ cat sndmodules
snd_intel8x0           35868  3 
snd_ac97_codec        102176  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            42528  0 
snd_mixer_oss          18048  1 snd_pcm_oss
snd_pcm                79748  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            35456  0 
snd_seq_midi            9504  0 
snd_rawmidi            25888  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54096  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24964  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59812  17 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         12552  2 snd_intel8x0,snd_pcm

#I have a disabled volume control applet on the panel (red cross)
# attempting to use it give the following message
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or **that you don't have a sound card configured**.

```

Any questions, comments, suggestions or insight welcomed, and much appreciated.

---

### Post by prshah on 2008-12-01
> **prshah said:**
> 
Summary: I have no sound device detected on Lifebook P5010 with 8.10 kernel 2.6.27-7


Fixed by upgrading to 2.6.27-9-generic when it became available ( 01/Dec/2008 ).

I'm guessing that something went wrong during the previous kernel update's 'Building modules for ... kernel, Please wait...' part (which comes immediately after a kernel upgrade) possibly because I had muted the sound during the upgrade from 8.04 to 8.10.

---

