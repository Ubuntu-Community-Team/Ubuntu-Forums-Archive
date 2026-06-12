---
title: "Sound no longer works in jaunty"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by gralco on 2009-04-26
For some odd reason in every release up until jaunty my sound has worked well (though my microphone didn't which now does), I've installed PulseAudio and have fallowed many guides. Any who here are some outputs of my card and such:

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

~$lspci -v | less
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller
 (rev 03)
        Subsystem: Gateway 2000 Device 0690
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f4600000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

and this one [http://paste.ubuntu.com/158994/](http://paste.ubuntu.com/158994/)

---

### Post by rasto1968 on 2009-04-27
I'm in exactly the same boat as you with exactly the same sound card. Worked fine in 8.10 but whatever I do (followed loads of guides) I can't get any sound (other than the system beep) in 9.04.

Rob

---

### Post by lbravo on 2009-04-27
I no longer see pulseaudio on my Sounds & Video menu -- I even reinstalled.  I get music from my bluetooth headset, but no other sounds.  Weird.

---

### Post by rasto1968 on 2009-04-28
See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363721](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/363721)

But since we don't seem to be getting any responses to that bug (I guess there are lots of problems elsewhere), can anyone suggest a way of getting alsa to recognize my sound card when using 'alsactl init' which produces the following output:

Unknown hardware: "HDA-Intel" "SigmaTel STAC9227" "HDA:83847618,102801dd,00100201" "" ""
Hardware is initialized using a guess method

---

### Post by gralco on 2009-04-28
needs a bump

---

### Post by emreakbas on 2009-04-28
I have the same problem. Sound system was working properly on Kubuntu 8.04. Here is my configuration: 

```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

```
~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```




```
~$lspci  -v
...
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Device 01dd                                                      
        Flags: bus master, fast devsel, latency 0, IRQ 16                                
        Memory at dffdc000 (64-bit, non-prefetchable) [size=16K]                         
        Capabilities: <access denied>                                                    
        Kernel driver in use: HDA Intel                                                  
        Kernel modules: snd-hda-intel
...  
```


```
~$ alsactl init
Unknown hardware: "HDA-Intel" "SigmaTel STAC9227" "HDA:83847618,00000100,00100201" "" ""
Hardware is initialized using a guess method
```

---

### Post by dmazzone on 2009-04-28
Okay so I am not sure if this is the same cause, but I too lacked sound from  a fresh install of Jaunty except using OSS, but then only through certain programs.

The problem I found out was even though my sound card was the default output device all of the streams still were sent to the rtp multicast sink. Once I moved them to my sound card everything seems to be okay now.

---

### Post by emreakbas on 2009-04-28
How can I check that? and how can I correct it? Thanks

---

### Post by emreakbas on 2009-05-02
I got mine working by appending the following line to "/et/modprobe.d/alsa-base.conf" and rebooting:

```
options snd-hda-intel model=ref
```

---

### Post by sanketh_shetty on 2009-05-07
Thanks Emre. 

Sound now works on my system.

---

