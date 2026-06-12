---
title: "Sound problems as for upgrade from 8.04 to 10.04"
date: 2011-04-03
forum: Hardware
---

### Post by ashgard on 2011-04-03
Hello,

As the title indicates I have sound issues since I upgraded from Ubuntu 8.04 (where I did not have any sound issues at all) to Ubuntu 10.04. Somehow my sound is working properly; every once in a while (lets say that the average occurrance is every 10 sec) the sound stops for a couple of ms and than continues again, which is very annoying to listen to. 

So I started to debug a bit on my own first. Using the  lspci -v | less command I found my Audio Device: 

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: COMPAL Electronics Inc Device 0025
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

I also have, but as far as I am concerned im not using it.

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: COMPAL Electronics Inc Device 0025
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at f8400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

I noticed the following:

1. The intel Audio Device seems not to be supported: [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel). But if that is true, then why did it work on my 8.04 system? Should I report this on the alsa project website?

2. On google I found some people with comparable issues on the intel audio device. Some of them removed the PulseAudio and got it working again. This also works for me! Without pulse audio I have no sound issues. 

Regarding the second point I think I have to options on how to proceed, but if there are any other suggestions I'd like to hear them.

A. Keep on working without pulseaudio. The downside is that my gnome-volume-control-applet is not working anymore. Is there an alternative for this?

B. I can imagine that the pulseaudio is not installed for nothing. So I rather get it working again. Now my question is: How to do so? Is there anything I can try to get it working with my hardware on 10.04?

Hopefully someone can advice me on how I should proceed? 
Thanks a lot for your help in advance.

Ashgard

---

