---
title: "X-fi FATAL1TY almost working?"
date: 2008-04-09
forum: Hardware &amp; Laptops
---

### Post by Thermonuclear on 2008-04-09
So I heard that the OSS drivers support my videocard, X-fi Fatal1ty, and I installed the package just find using adept and it even listed my card as supported while installing.  Now before I installed it everytime I boot kubuntu it gave me and error that no sound card drivers could be loaded, now it doesn't.  Only problem is I still don't have sound???  I'm kinda of a Linux newb and can't seem to figure it out, anyone have any idea.  I'm running the latest Kubuntu with KDE4 plz help.

---

### Post by Yellow Pasque on 2008-04-09
Let's make sure you have OSS installed correctly What's your output from?:
```
ossinfo
```
Now try the following (might be loud):
```
osstest
```

---

### Post by Thermonuclear on 2008-04-10
Result from ossinfo
```
Version info: OSS 4.0 (b1015/200803240317) (0x00040003)
Platform: Linux/x86_64 2.6.24-15-generic #1 SMP Mon Apr 7 16:37:53 UTC 2008 (Kubuntu-Linux)

Number of audio devices:        2
Number of audio engines:        10
Number of mixer devices:        1


Device objects
 0: osscore0 OSS core services
 1: sbxfi0 Sound Blaster X-Fi (SB046x/067x/076x) interrupts=39517 (39517)
    PCI device 1102:0005, subdevice 1102:0023
 2: ossusb0 USB audio core services
 3: vmix0 OSS transparent virtual mixer


Mixer devices
 0: Sound Blaster X-Fi (SB046x/067x/ (Mixer 0 of device object 1)

Audio devices
Sound Blaster X-Fi (SB046x/067x/076x) output  /dev/oss/sbxfi0/pcm0  (device index 0)
Sound Blaster X-Fi (SB046x/067x/076x) input  /dev/oss/sbxfi0/pcmin0  (device index 1)
```

And osstest
```
Sound subsystem and version: OSS 4.0 (b1015/200803240317) (0x00040003)
Platform: Linux/x86_64 2.6.24-15-generic #1 SMP Mon Apr 7 16:37:53 UTC 2008

*** Scanning sound adapter #-1 ***
/dev/oss/sbxfi0/pcm0 (audio engine 0): Sound Blaster X-Fi (SB046x/067x/076x) output
- Performing audio playback test...
  <left> OK <right> OK <stereo> OK <measured srate 47512.00 Hz (-1.02%)>
/dev/oss/sbxfi0/pcmin0 (audio engine 1): Sound Blaster X-Fi (SB046x/067x/076x) input
- Skipping input only device

*** All tests completed OK ***
```

But I hear nothing through the headphones?  And yes they're turned up and I tested them in Windows so they aren't the problem.

---

### Post by Thermonuclear on 2008-04-15
Bump, nothing?

---

