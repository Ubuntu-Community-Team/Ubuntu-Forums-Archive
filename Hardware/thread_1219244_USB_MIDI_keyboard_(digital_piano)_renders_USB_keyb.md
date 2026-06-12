---
title: "USB MIDI keyboard (digital piano) renders USB keyboard sluggish..."
date: 2009-07-21
forum: Hardware
---

### Post by prasadbrg on 2009-07-21
Hello everyone, 
  This is my first post on this (rather excellent) forum. I'm running Xubuntu Jaunty on a Compaq Presario 2184 AT notebook, with a Celeron processor and 1 Gig of ram. It's a 2003 model, and the keyboard finally became unusable a few days ago. I picked up a nice external usb keyboard, and just discovered a serious issue. Whenever I connect my digital (midi) piano through USB, the keyboard becomes sluggish and unresponsive. I checked with [xev]("http://www.xfree86.org/current/xev.1.html"), and it confirms that one in every dozen or two keystrokes are actually being logged. The moment I unplug the piano USB (or switch it off), the keyboard works fine. The mouse is not affected by the piano USB. I don't have this issue when a USB pen drive is mounted.
  I did a bit of googling, and the closest match to my issue seems to be [this thread]("http://ubuntuforums.org/showthread.php?t=710799"). However, I don't have the sound issues that the OP in that thread has (on the other hand, I don't use the audio apps the he does...). But his description of the keyboard problems is spot on. That thread, however wasn't resolved completely, and the temporary workaround that the OP found there was to use the normal linux kernel ( as opposed to the linux-rt kernel), which is what I'm using anyway! So I'm back to square one...
  I also came across [this thread]("http://ubuntuforums.org/showthread.php?t=677362"), but when I attempted the prescribed```

``` solution, I got this:
```
$ sudo modprobe -r -v ehci_hcd && sudo modprobe -v ehci_hcd 
WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.
FATAL: Module ehci_hcd not found.
```
... which lead me to [this thread]("http://ubuntuforums.org/showthread.php?p=7085858"), which seems somewhat vaguely related, in that it involves USB and sluggishness. Yet, no resolution...:(.
  Incidentally, my notebook is ancient enough to have a PS2 port in it. I have a USB to PS2 adaptor (which however needed a reboot for the keyboard to be detected). Strangely, the same issue persists, even when the keyboard is connected through the PS2 port!
  I've also noticed, that during startup, in the GRUB menu, the arrow/enter keys work quite well, even when the keyboard is connected. Suggests to me that it is an OS issue...
  I'd appreciate any pointers in this regard. It is quite important for me to use both the keyboard together. 
Thanks in advance!
Cheers,
Guru

P.S. The "digital piano" happens to be a Casio CTK-3000 keyboard, which I use as a MIDI controller. I avoided using the proper term "MIDI keyboard" to avoid potential confusion with the computer keyboard... ;)

---

### Post by prasadbrg on 2009-07-22
Hello everyone, 
  My apologies. It turns out that the USB to PS2 adapter solves the problem, and doesn't need a reboot... so this is a viable workaround for me. Either my earlier observation was a one-off fluke, or (more likely), I must have mixed up my observations!:oops: 
  However, I can confirm that the problem **does** persist when the keyboard is connected directly to USB. So any inputs would be appreciated!
Cheers,
Guru

---

