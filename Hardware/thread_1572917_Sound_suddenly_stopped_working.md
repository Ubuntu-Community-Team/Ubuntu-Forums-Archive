---
title: "Sound suddenly stopped working"
date: 2010-09-11
forum: Hardware
---

### Post by ramsforums on 2010-09-11
I am using Ubuntu 10.04 When I installed everything was ok. I installed additional packages skype, chrome browser, flash player etc

I noticed my sound stopped working suddenly. With Google's help followed the instruction from this page

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Nothing works. I am new to Linux and trying to learn how to use. 
**[COLOR=#000000][FONT=Times New Roman][FONT=Helvetica Neue]sudo aplay -l[/FONT][/FONT][/COLOR]**
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
**[COLOR=#000000][FONT=Times New Roman][FONT=Helvetica Neue]lspci -v | less[/FONT][/FONT][/COLOR]**
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 30c0
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at e4804000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

Anyone help me? Appreciate it.

Thanks

---

