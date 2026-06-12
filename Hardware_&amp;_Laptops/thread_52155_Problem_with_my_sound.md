---
title: "Problem with my sound"
date: 2005-07-26
forum: Hardware &amp; Laptops
---

### Post by SethH on 2005-07-26
I just installed ubuntu and have no sound. I have onboard sound, and it sees my hardware, and says it's working, but still nothing. I have a PCChips M863G mainboard, SiS 741GX chipset. I hope someone knows what I can do.
Thanks.

---

### Post by varunus on 2005-07-26
Can you post the output of the following commands in a terminal:

```

lsmod | grep snd

lspci

```

Also, what happens when you try the following command:
```
aplay /usr/share/sounds/login.wav
``` 

Do you see output like "Playing login.wav at blah" or do you just a blank line and have to CTRL-C out?

---

### Post by SethH on 2005-07-26
lsmod

snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  1 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  2 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm


grep snd

Nothing. I have to Ctrl-C out


lspci

0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS]: Unknown device 0003
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)


aplay /usr/share/sounds/login.wav

Nothing. I have to Ctrl-C out

---

### Post by Curlydave on 2005-07-26
This is one of the most prominent Ubuntu hardware problems. The solution most people give is to disable onboard sound. Hope your not like me and use 2 devices for different tasks...

---

### Post by varunus on 2005-07-27
I found a page on the ALSA (Advanced Linux Sound Architecture) page detailing someone elses problems with this very sound card; they  fixed them by doing the following:

> 
Alsa 1.04 i8x0 audio driver works well, but:
after sucking for half a day, I figured out, that 
beside you unmute PCM, you have to mute the IEC958 Capture
Monitor, else there won't be any sound.
Hope it helps someone.


So to do this, open up a terminal and type
```
alsamixer
```

Then, use the left and right arrow keys to scroll until you see the Capture Monitor column, and press 'M' over it.

Also, I recommend following this howto, as the intel8x0 driver needs this for all sounds to work:
[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)
I have the intel card in my laptop, and I've found that the following asound.conf file works better then the one in that howto, I'd recommend you use this one instead:
```
pcm.card0 {

  type hw

  card 0

  mmap_emulation true

}

pcm.!output {
type dmix
ipc_key 1234
ipc_key_add_uid 1
slave {
pcm "card0"
period_time 0
period_size 1024
buffer_size 8192
rate 44100
}
bindings {
0 0
1 1
}
}

#
# DSNOOP output device
#
pcm.!input {
type dsnoop
ipc_key 4321
ipc_key_add_uid 1
slave {
pcm "card0"
period_time 0
period_size 1024
rate 44100
}
}

#
# ASYM duplex device
#
pcm.!duplex {
type asym
playback.pcm "output"
capture.pcm "input"
}

#
# Make the duplex device default
#
pcm.!default {
type plug
slave.pcm "duplex"
}

#
# OSS Compability

pcm.!dsp0 {
type plug
slave.pcm "duplex"
}

ctl.!mixer0 {
type hw
card 0
}

```

Good luck.  Post back with your results.

---

### Post by linux_fish on 2005-07-27
Thanks for your help! I thought all was lost.

---

### Post by SethH on 2005-07-27
Thanks varunus, it works!

---

### Post by djSHY on 2005-07-28
i have the same problem, but the output of lsmod | grep snd and lspci is a bit different, so i just  want to make sure of the tasks that need to be done to fix this. here is the output:

**lsmod | grep snd**

snd_emu10k1            81668  2
snd_rawmidi            22944  1 snd_emu10k1
snd_seq_device          8332  2 snd_emu10k1,snd_rawmidi
snd_ac97_codec         64608  1 snd_emu10k1
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_emu10k1,snd_pcm
snd_util_mem            4608  1 snd_emu10k1
snd_hwdep               9220  1 snd_emu10k1
snd                    50276  9 snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
soundcore               9824  3 snd

**lspci**

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
0000:00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
0000:00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
0000:00:0e.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
0000:00:0e.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 0a)
0000:00:11.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 440] (rev a3)

and the aplay commands outputs this:

Playing WAVE '/usr/share/sounds/login.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo

but no sound comes out :(

any ideas? thx in advance.

---

### Post by djSHY on 2005-07-28
alright, its working now, i just needed to run alsamixer and turn up the pcm controller and
with Multimedia System Controller, turn the both audio options to ALSA. just in case somebody needs it.

---

### Post by stimpsonjcat on 2006-03-30
and another one.. :) 
it is an "AC 97" on board sound device and doesn't work at all. I can use neither the gnome volume control nor alsamixer (see output below).

```
#lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x]  (rev c4)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro13 3x AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (r ev 22)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 10)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 10)
0000:00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
0000:00:0b.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP
```

ouput of lsmod | grep snd is empty.

```
alsamixer
alsamixer: function snd_ctl_open failed for default: No such file or directory

```
What can I do? Thanks.

---

### Post by swmiller6 on 2006-03-30
same card any help would be great............

---

### Post by stimpsonjcat on 2006-03-31
hi swmiller6

My card works now. I had to enable the sound controller in my BIOS, it was disabled for some reason... 

The module I use is snd-via82xx. (add snd-via82xx to the /etc/modules file, then reboot)
good luck!
stimpy

---

