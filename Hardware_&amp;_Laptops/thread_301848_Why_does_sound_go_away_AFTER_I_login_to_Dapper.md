---
title: "Why does sound go away AFTER I login to Dapper?"
date: 2006-11-17
forum: Hardware &amp; Laptops
---

### Post by SupaRice on 2006-11-17
So, I've battled through getting RAID going on my laptop, and ATI proprietary video drivers to be confronted with an audio problem.  I'm sorta a n00b, but I follow directions pretty well! :)

Here's my problem, when I boot up to the login screen Ubuntu plays the little drum roll sound fine.  After login if I try to launch Totem it crashes and says "Could not establish a connection to the sound server".  Or something close to that.

So I tried to follow this article, and have had no luck:
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

I've uninstalled, and reinstalled alsa like the article said, and that didn't seem to work.  I've also tried alsamixer to see if it is just on mute, and it doesn't appear to be.

But here is some sample outputs from the commands it says to use:
```

root@ubuntu:/home/xman# cat /proc/asound/modules
0 snd_hda_intel

root@ubuntu:/home/xman# lspci -v
....
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)        Subsystem: Uniwill Computer Corp: Unknown device 9070
        Flags: bus master, fast devsel, latency 0, IRQ 50
        Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] #10 [0091]

root@ubuntu:/home/xman# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

root@ubuntu:/home/xman# cat /proc/asound/modules
0 snd_hda_intel

```

Can anyone tell me what I've done wrong, or what I'm missing?  I'm kinda stuck.

---

