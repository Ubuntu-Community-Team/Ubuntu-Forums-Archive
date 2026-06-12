---
title: "Natty and ThinkPad docking station (T420)"
date: 2011-10-05
forum: Hardware
---

### Post by mejo on 2011-10-05
Hello,

I just gave the ThinkPad Minidock 3 docking station a try with my ThinkPad T420 and Ubuntu Natty (x86_64). It seems like some things do work out of the box, others don't.

Booting the laptop connected to the docking station works flawlessly, except that the external USB keyboard doesn't work in grub2. It does work in the initramfs though. (passphrase to unlock the rootfs)

When docking the laptop while running Ubuntu, the laptop display is turned off and the external monitor (VGA) is used as main display automatically. Vice versa when undocking the laptop again. This as well works as expected.

Undocking the laptop when booted docked in doesn't work though, my laptop display displayed only garbage in that case.

I also discovered problems with enabling both displays (laptop + external VGA) at once. Sometimes the aspect ratio was flawed for either of the displays, and sometimes the external display was flawed in other ways (i.e. big black bar at the bottom).

Not sure whether all these problems (except the keyboard issues) are related to the i915 video support in Natty. I'm curious whether all or some of the issues are fixed in Oneiric.

Please share your experiences with Ubuntu and ThinkPad docking stations here.

Greetings,
 jonas

---

### Post by mejo on 2011-10-06
Interestingly the power button feature works when the laptop is docked while it doesn't work in normal laptop mode.

Ubuntu usually displays a dialog to choose between different actions (shutdown, reboot, suspend, hibernate, logout, ...) when one presses the power button. This doesn't work on my T420 with Ubuntu Natty. When the laptop is docked into the docking station, it works as expected though.

---

### Post by ultimatebuster on 2011-10-09
Isn't it a little late to post about natty things?

Should start looking at 11.10 atm: [http://ubuntuforums.org/showthread.php?p=11326588](http://ubuntuforums.org/showthread.php?p=11326588)

---

### Post by mejo on 2011-10-10
> **ultimatebuster said:**
> Isn't it a little late to post about natty things?

Should start looking at 11.10 atm: [http://ubuntuforums.org/showthread.php?p=11326588](http://ubuntuforums.org/showthread.php?p=11326588)

I'll give Ubuntu 11.10 a try as soon as it's released. For sure I'll share my experiences regarding issues with T420 in this forum.

---

### Post by mejo on 2011-10-16
> **mejo said:**
> I'll give Ubuntu 11.10 a try as soon as it's released. For sure I'll share my experiences regarding issues with T420 in this forum.

Just did: [http://ubuntuforums.org/showthread.php?p=11353524#post11353524](http://ubuntuforums.org/showthread.php?p=11353524#post11353524)

---

