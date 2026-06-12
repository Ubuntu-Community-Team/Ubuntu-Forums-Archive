---
title: "Suspend: i810 video not resuming"
date: 2007-01-22
forum: Hardware &amp; Laptops
---

### Post by IntuitiveNipple on 2007-01-22
I'm having a *few issues* getting a Sony Vaio notebook to suspend/resume correctly. 

To begin with it wouldn't even suspend/hibernate (blanked the screen then just sat there everything still running) but I found that by removing all the suspend scripts from **/etc/acpi/suspend.d/** and the adding them back one-by-one I was able to identify those that caused suspend/hibernate to fail.

The PC will now suspend to RAM, and resume afterwards but it resolutely refuses to restart the Intel i810 (i815 chip-set) video.

When its running Gnome the system log shows gdm can't restore video state, but, if I stop Gnome and run **/etc/acpi/sleep.sh** from a terminal the same thing happens - no video on resume.

The log files show the system has resumed but obviously for some reason hasn't woken the video.

I've done a lot of reading on this, and have disabled the VBE and POST options in **/etc/default/acpi-support** but not yet identified why the video won't resume.

---

