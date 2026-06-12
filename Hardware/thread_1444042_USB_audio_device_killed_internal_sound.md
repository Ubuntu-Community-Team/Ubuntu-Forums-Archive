---
title: "USB audio device killed internal sound"
date: 2010-03-31
forum: Hardware
---

### Post by ImSorryDave on 2010-03-31
Help for a Linux n00b?

HP DV6253 cl laptop  Karmic

The integrated sound was working ok (some intermittent clicks) until I plugged in a ESI Maya 44 USB external soundcard. Now pretty much all the ALSA folders and files show a "locked" symbol and sound is completely gone. I've done some searches and tried some fixes. I'm stumped. Any feedback would be much appreciated.

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Hewlett-Packard Company Device 30b7
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at b0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel

xxx@xxxxxx:~$ cat /proc/asound/version
cat: /proc/asound/version: No such file or directory

xxx@xxxxxx:~$ sudo aplay -l
[sudo] password for xxx: 
aplay: device_list:223: no soundcards found...

---

