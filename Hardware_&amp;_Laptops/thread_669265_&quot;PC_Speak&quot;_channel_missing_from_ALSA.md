---
title: "&quot;PC Speak&quot; channel missing from ALSA"
date: 2008-01-16
forum: Hardware &amp; Laptops
---

### Post by monki34 on 2008-01-16
I have an ASUS U6S laptop running Ubuntu 7.10.  The sound works great, but I'm having some difficulty with the PC Speaker.

Most people want to disable their PC Speakers, and there are several threads which describe how to use rmmod or modprobe -r to remove the module.  I'd like the PC Speaker to work.  The module exists, and is running by default on my install.  alsamixer and amixer however do not show a "PC Speak" channel.

```

$ lsmod | grep pcspkr
pcspkr                  4224  0 

$ uname -ra
Linux alf 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

```

In the "Sound Preferences" dialog, "Enable system beep" is checked.   I get no pc speaker output with from a console backspace or the "beep" program available on apt.

---

### Post by monki34 on 2008-01-16
I forgot to mention the following important information:

lspci -v gives:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: ASUSTeK Computer Inc. Unknown device 1765
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at febf8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

and alsamixer shows:
Card: HDA Intel
Chip: Realtek ALC888

---

### Post by peitschie on 2008-01-16
Often, the names ALSA displays are not phsyically what the sliders control.  For example, my front output is called "Surround", my back output is called "Left channel", and my Mic comes in on "Line in"!

Have  you tried turning all the sliders up?  You can type "alsamixer" in a terminal session to get the CLI version (which I prefer for debugging because it doesn't try and hide any controls from you).  Make sure each channel is about 80% or so, and see if that gives you any sound...

---

### Post by monki34 on 2008-01-16
Unfortunately, that's not it.  

None of the channels are muted, and all of them are at maximum volume.

---

### Post by Yellow Pasque on 2008-01-16
You could try to make a virtual pc speaker [http://gentoo-wiki.com/HOWTO_Virtual_PC_Speaker](http://gentoo-wiki.com/HOWTO_Virtual_PC_Speaker)

BTW, ALSA mixer doesn't actually control the PC speaker volume:
> Just to clear things up, the ALSA mixer entry called, "PC Speaker," is there because some sound cards (e.g. SoundBlaster Live!) have an internal connector that allows you to route the signal from the motherboard pins ordinarily used for the PC speaker into your sound card. It has no control over the volume of the signal sent to the PC speaker itself.


EDIT: Looks like it might actually be a bug/conflict with the snd_hda_intel driver
[http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg440828.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg440828.html)

---

