---
title: "Built-in Microphone Volume issues with Pulse Audio"
date: 2010-04-14
forum: Hardware
---

### Post by Tangent on 2010-04-14
I've been searching the forum and google for several hours no, and I've found several complaints about the same problem from as far back as 3 years ago, but no actual solutions.

I'm using a dell inspiron 1720 laptop which works very well right after install with karmic, but I'm having issues with Pulse. My digital mic which is above the screen next to the webcam records audio at an extremely low volume even when the volume is maxed out in Pulse.

I tried setting the boost in alsamixer, but nothing I do with it seems to have any effect so long as Pulse in installed. I removed Pulse and while the microphone works fine without it, the overall audio system is buggy and overall Karmic clearly doesn't like being without Pulse. I have also had some success with increasing the volume to ridiculous heights in pacmd, but the changes never stick.

So I was hoping someone could help me find a way of increasing my mic volume more permanently. I don't know much about pulse, but I was hoping there might be some config file in which I could just manually set the microphone volume. Any help would be greatly appreciated.

Additional information:

The make of the mic is sigmatel audio, though I don't remember the specific model number.

I'm running the 64-bit version of Ubuntu.

---

### Post by lidex on 2010-04-14
Try working through these threads first and let me know how it goes:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by Tangent on 2010-04-14
Thanks for replying. I tried those two threads, but unfortunately neither of them seem to have done any good.

When editing /etc/pulse/default.pa though, I tried inserting the command: set-source-volume 1 300000

which kind of works, but it still requires that I run pacmd (whether or not I actually run any commands in it before closing it again) to apply the setting after a reboot. It's definitely a step up though.

Do you have any thoughts on how to better solve it or make my fix work better? I'll do my best to give you any information you need.

Thanks again!

---

### Post by lidex on 2010-04-14
Did you install the alsa-backports?
What is the output of these commands:
```
aplay -l
head -n 1 /proc/asound/card*/codec#* 
```

---

### Post by Tangent on 2010-04-14
I believe I did install them, but I could have messed up.

For aplay -l I get:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and for head -n 1 /proc/asound/card0/codec#0:

```
Codec: SigmaTel STAC9205
```
though codec#1 gives
```
Codec: Conexant ID 2c06
```

---

### Post by lidex on 2010-04-14
Try this. Open this file for editing:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Add this line at the bottom:
```
options snd-hda-intel model=dell-m44
```
Save. Close. Reboot. Now open alsamixer and press F4 to select capture devices.

---

### Post by Tangent on 2010-04-15
I added the line to the file and maxed out the volume on all of the capture devices on alsa, but it didn't seem to make much difference in the function.

---

### Post by lidex on 2010-04-15
> **Tangent said:**
> I added the line to the file and maxed out the volume on all of the capture devices on alsa, but it didn't seem to make much difference in the function.

Did you reboot?

---

### Post by Tangent on 2010-04-16
Yeah, I did, sorry, I probably should have specified that.

---

### Post by dalyx on 2010-09-12
> **lidex said:**
> Try this. Open this file for editing:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```
Add this line at the bottom:
```
options snd-hda-intel model=dell-m44
```
Save. Close. Reboot. Now open alsamixer and press F4 to select capture devices.

This worked for me. Mic volume was low (couldn't find the "mic boost" switch in alsa) but it is now pretty good now.

I have a inspiron 1520, with same outputs as Tangent for # aplay -l and # head -n 1 /proc/asound/card0/codec#0. Running Ubuntu 10.04 LTS.

---

