---
title: "internal microphone not recording"
date: 2012-05-30
forum: Hardware
---

### Post by amarumayo on 2012-05-30
Hi all,

I have been searching for answers to no avail.  My internal microphone will not record any sound from any source (Skype, Sound Recorder, via terminal arecord).  I have made adjustments with Pulse Audio Volume Control as well as with the ALSA mixer. 

Soundcard is:
amarumayo@bird:~$ sudo aplay -l
[sudo] password for amarumayo: 
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Ubuntu 12.04 (32) running on Lenovo Essential G575 with Dual-core AMD E-300 processor.

I don't really know what to do.  Any help would be greatly appreciated. 
Thanks

---

### Post by ajgreeny on 2012-05-30
Does it work at all; can you hear sounds from mic through your speakers, or is everything muted?

---

### Post by amarumayo on 2012-05-30
Nope, can't hear a thing.

---

### Post by irv on 2012-05-30
Does your sound setting in 12.04 look like mine.
[ATTACH]218954[/ATTACH]

---

### Post by amarumayo on 2012-05-30
It doesn't have a section for microphone like yours does.  Only analog input.

---

### Post by irv on 2012-05-30
> **amarumayo said:**
> It doesn't have a section for microphone like yours does.  Only analog input.

Do you have a mic switch somewhere that might be turned off.
Or maybe it is turned off in your BIOS.

---

### Post by amarumayo on 2012-05-30
No switch.  Don't see option to enable in BIOS...

---

### Post by irv on 2012-05-30
You got me stumped on this one, maybe someone else might jump in here. I have no idea why your sound setting does not have an option for the mic.
Maybe you can open sound recorder and see if it sees your mic.
Mine is set to Master.
[ATTACH]218957[/ATTACH]

---

### Post by Talareño on 2012-06-01
Hello,

I'm a relative newbie to Ubuntu(12.04)..and Linux. I have the same mic problems. I tried Skype and played around with some of the sound and sound recorder buttons without success. I next played around with the Gnome Alsa Mixer and Skype together. I have had a little luck but it was not repeatable all the time. In GAM I played with buttons and at times succeeded in getting the mic to work. I have tentatively concluded that the problem is in the communication between GAM and AA1 AOA 150.

I hope someone with more knowledge can use this information.

---

### Post by jocefus on 2012-06-12
On my Alienware M14x there are no inputs listed in the new "improved and simplified" sound settings menu. I was able to play around in pavucontrol and get the internal mic working sometimes.

Check bug report #946232.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/946232](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/946232)

The workaround in comment #32 worked on my laptop (Alienware M14xR1).

Apparently there are "tweaks" that need to be made for all these affected machines. You should submit your alsainfo to this bug so your model can be added to this ever growing list. Yet another thing in Ubuntu that was not broken, but apparently needed fixing.

---

