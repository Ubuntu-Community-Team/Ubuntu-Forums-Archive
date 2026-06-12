---
title: "Oxygen8 USB Midi Keyboard"
date: 2009-03-13
forum: Hardware
---

### Post by Miserlou on 2009-03-13
Hello!

I'm having trouble getting my Oxygen8 USB MIDI keyboard to work in Ubuntu 8.04.

I have followed tutorials here:
[http://ubuntuforums.org/showthread.php?p=3726019](http://ubuntuforums.org/showthread.php?p=3726019)
[http://www.ricardocabello.com/blog/post/533](http://www.ricardocabello.com/blog/post/533)
[http://forum.jacklab.net/viewtopic.php?p=807&sid=29d364cdc6b15c283edc125267b79576](http://forum.jacklab.net/viewtopic.php?p=807&sid=29d364cdc6b15c283edc125267b79576)
and 
[http://ubuntuforums.org/archive/index.php/t-455902.html](http://ubuntuforums.org/archive/index.php/t-455902.html)

to no avail.

In all cases, the error message upon fxload is the same:

can't modify CPUCS: Broken pipe

I'm not sure what could be wrong here. fxload and midisport-firmware are both installed. I have no idea what CPUCS is.

Again, this is on Hardy Heron 8.04 running on an IBM Thinkpad Z60t.

Please help!
Thanks so much!
Rich

---

### Post by mattbrand on 2010-09-13
Hey all.

I am trying to install my MAudio Oxygen 8 in Ubuntu, and I am getting the following message when I try to run fxload:

"can't modify CPUCS: Broken pipe"

I have the device working fine in Windows. I see it listed properly in the USB devices when I run lsusb. I have tried fxload with MidiSportKS.ihx, with MidiSportLoader.ihx and MidiSportKS.ihx together, and ezusbmidi1x1.ihx.

Anyone have any ideas on what could be wrong?

---

### Post by edd275k on 2011-03-30
linux is just not up to windows standards of compatibility its always an **** to get anything working

---

### Post by jack_spratt on 2011-03-31
> **edd275k said:**
> linux is just not up to windows standards of compatibility its always an **** to get anything working

Windows itself has the worst compatibility of any major desktop operating system.

The problem is that *peripheral support* for GNU/Linux is not up to the standard of windows, which is explicitly a failing of manufacturers like M-Audio, and nothing to do with GNU/Linux itself. In fact documentation, community support, and the nature of Free Software means that it should be far easier and cheaper for M-Audio to develop GNU/Linux drivers than Windows drivers.

Try installing windows fresh on your computer and running it without any third party drivers for your hardware (good luck!).

Try doing the same on Linux and realise that GNU/Linux actually has the best hardware support of any OS in existence ;)

---

