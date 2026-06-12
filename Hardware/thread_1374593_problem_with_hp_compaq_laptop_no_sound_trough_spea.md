---
title: "problem with hp compaq laptop no sound trough speaker"
date: 2010-01-07
forum: Hardware
---

### Post by norgeek on 2010-01-07
* Edit post
    * Delete post
    * Report this post
    * Reply with quote

no sound through speaker on hp compaq laptop =(


Hello  i bought a hp compaq cq71-235so three weeks ago and I thought i wanted to have linux on it only to find that it has no sound on the speakers . I hope you guys can help me. Or I have to stay on windows 7 i have installed mint 8 (based on (ubuntu carmic) but there is no sound through the speaker only with headphones on i hear when im playing things

I have asked the at the fedora forum too (same problem) but they gave me no response =(
Thank you for your time i hope i can fix this problem and finaly enjoy nix with sound =D
[http://h10025.www1.hp.com/ewfrf/wc/prod](http://h10025.www1.hp.com/ewfrf/wc/prod) ... oc:0&cc=us

---

### Post by lidex on 2010-01-07
Some info from you would help. Can you post the output of these terminal commands?

```
sudo lshw -C sound
```
```
aplay -l
```
```
aplay -L
```
```
head -n 1 /proc/asound/card0/codec*
```

---

### Post by TBABill on 2010-04-26
> **lidex said:**
> Some info from you would help. Can you post the output of these terminal commands?

```
sudo lshw -C sound
```
```
aplay -l
```
```
aplay -L
```
```
head -n 1 /proc/asound/card0/codec*
```
I have the same problems...headphone sounds fine, no internal speaker sound.

sudo lshw -C sound 
 *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:21 memory:f9bf8000-f9bfbfff
  *-multimedia UNCLAIMED
       description: Multimedia video controller
       product: NEC Corporation
       vendor: NEC Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 0b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f9efe000-f9efffff memory:f9efd800-f9efdfff

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

aplay -L
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
bill@bill-desktop:~$ aplay -L
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, AD198x Digital
    IEC958 (S/PDIF) Digital Audio Output

head -n 1 /proc/asound/card0/codec*
Codec: Analog Devices AD1984B

Any suggestions? I have searched the forums, the web, Launchpad bugs, etc., but nothing that pointed to a solution that worked for me.

---

