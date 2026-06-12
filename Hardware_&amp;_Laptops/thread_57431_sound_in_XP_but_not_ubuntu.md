---
title: "sound in XP but not ubuntu"
date: 2005-08-16
forum: Hardware &amp; Laptops
---

### Post by tonysathre on 2005-08-16
i have a dell 4550 with an intel sound card. i have xp on hda1 and ubuntu on hdb1, i installed xp then ubuntu then installed all the drivers on windows for my hardware and i dont have any sound in linux but in windows i do ...what could the problem be, any help would greatly appreciated

---

### Post by varunus on 2005-08-16
Can you post the output of "lsmod | grep snd" and "lspci" in a terminal?

Do you have an intel High Definition Audio card or an Intel Integrated Sound Card?  The second should work with Linux, the first needs some configuring...not too hard though...

---

### Post by tonysathre on 2005-08-16
Intel Integrated Sound...alright ill post it, another thing, i have installed ubuntu before and sound worked fine so this is kinda strange

---

### Post by varunus on 2005-08-16
Hmm...go ahead and post...maybe a config problem?  I dunno...

I have the same card, and I had to tinker a little to get all programs to play sound.  Here's what I did:
1.  Install "libesd-alsa0" from synaptic (it might be libesd0-alsa, can't remember).
2.  Create the following file in your home folder, call it ".asoundrc"
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
3.  Go to System->Preferences->Multimedia Systems Selector, change both values to ALSA.  (Make sure you have the "gstreamer0.8-alsa" package from Synaptic).
4.  Reboot.

You do NOT need to disable the GNOME sounds or the GNOME sound server with the intel cards (as many other howtos tell you to do); they work nicely with both the sound server and other sounds on.

---

### Post by tonysathre on 2005-08-16
alright ill try when i get home since im at school now, thanks alot, ill post back tomorrow to see if it worked

---

### Post by tonysathre on 2005-08-17
will that work if i use kde or does some thing have to be different. under /dev/dsp it says that  the device is busy, this has to do with sound i think so what does this error mean

---

### Post by varunus on 2005-08-23
If you're on KDE, you should skip all of the "esd" or "gstreamer" related steps.  Then go set KDE to use ALSA for sound output in the sound server module in the control center.  This should work.

---

### Post by tonysathre on 2005-08-25
i fixed it.. the problem was that in the volume control it was set to analog instead of ALSA like you said, thanks, and also it was muted, dont know how it happened but thanks for helpin

---

