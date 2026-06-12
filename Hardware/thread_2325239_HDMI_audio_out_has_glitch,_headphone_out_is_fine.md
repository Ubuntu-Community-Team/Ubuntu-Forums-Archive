---
title: "HDMI audio out has glitch, headphone out is fine"
date: 2016-05-20
forum: Hardware
---

### Post by bastienauneau on 2016-05-20
Hi All

I have ubuntu 16.04, using gnome shell
Asus MB (H110M-A), I5 processor
No graphic card

Audio is working perfectly fine when using headphone (front audio connector on the tower)
When using HDMI audio out, the sound plays but with glitches. Every few seconds, it's as if the track jumps few msec (or so)

I also have a laptop with ubuntu 16.04, and the same screen in HDMI audio out works fine

So looks like it's config related to the very tower, not the screen
Havent' found anything related to my problem on the net, only case where HDMI audio out doesn't work at all. Tried some audio troubleshooting from ubuntu forum, but didn't help
Tried to get info about audio out buffer, but found nothing useful

Anyone has an idea ?

Cheers
Bastien

---

### Post by slickymaster on 2016-05-20
*Thread moved to **Hardware**.*

---

### Post by QDR06VV9 on 2016-05-20
> **bastienauneau said:**
> Hi All

I have ubuntu 16.04, using gnome shell
Asus MB (H110M-A), I5 processor
No graphic card

Audio is working perfectly fine when using headphone (front audio connector on the tower)
When using HDMI audio out, the sound plays but with glitches. Every few seconds, it's as if the track jumps few msec (or so)

I also have a laptop with ubuntu 16.04, and the same screen in HDMI audio out works fine

So looks like it's config related to the very tower, not the screen
Havent' found anything related to my problem on the net, only case where HDMI audio out doesn't work at all. Tried some audio troubleshooting from ubuntu forum, but didn't help
Tried to get info about audio out buffer, but found nothing useful

Anyone has an idea ?

Cheers
Bastien

Glitches, skips or crackling

The newer implementation of the PulseAudio sound server uses timer-based audio scheduling instead of the traditional, interrupt-driven approach.

Timer-based scheduling may expose issues in some ALSA drivers. On the other hand, other drivers might be glitchy without it on, so check to see what works on your system.

To turn timer-based scheduling off add** tsched=0** in[B] /etc/pulse/default.pa:
[/B]
/etc/pulse/default.pa
```
load-module module-udev-detect tsched=0
```
Mine looks like this but I have no glitches
```
### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
```

Then restart the PulseAudio server:

```
$ pulseaudio -k
$ pulseaudio --start
```
Do the reverse to enable timer-based scheduling, if not already enabled by default.

If you are using Intel's IOMMU and experience glitches and/or skips, add **intel_iommu=igfx_off** to your kernel command line.

Some Intel audio cards using the snd-hda-intel module need the otions **vid=8086 pid=8ca0 snoop=0**. In order to set them permanently, create/modify the following file including the line below.
etc/modprobe.d/sound.conf
To This
```

options snd-hda-intel vid=8086 pid=8ca0 snoop=0
```
Hope this is helpful.
Kind Regards

---

### Post by bastienauneau on 2016-05-24
Thanks for the answer. Just tried :
_  tsched=0, didn't help
_  vid=8086 pid=8ca0 snoop=0, didn't help either

I've restarted the machine after the second test
Is it glitches, skips or crackling ? 
every 5 to 10 sec, the sound get's weird for one second or so. It sounds as if it was bubbling instead of normal talking
If it's music pretty much the same. I don't think the tempo is lost (so no skip?), but the sound does "blup", or "klrp"

---

