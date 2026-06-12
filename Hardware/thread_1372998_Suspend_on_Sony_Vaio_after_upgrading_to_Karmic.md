---
title: "Suspend on Sony Vaio after upgrading to Karmic"
date: 2010-01-05
forum: Hardware
---

### Post by gabrielitos on 2010-01-05
Hi Everybody!
I read tons of posts on suspend problems after upgrading to Karmic but I can not find the solution for my problem. My laptop is a Sony Vaio VGN-SR19VN.

Here what it happens: the hibernation is working fine. The computer goes into suspend but when I ask it to resume the screen is completely black and I cannot ssh into it. 
I paste the interesting part of my pm-suspend.log:

```
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
/etc/pm/sleep.d/10_grub-common suspend suspend: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: stop: Unknown instance:
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: kernel.acpi_video_flags = 0
Allocated buffer at 0x11000 (base is 0x0)
ES: 0x1100 EBX: 0x0000
success.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
mar gen  5 13:16:12 CET 2010: performing suspend
```
The last line refers to the push of the button for the resume: this is the last line, it doesn't appear the "Awake" status.

I tried to downgrade the kernel to the 2.6.27 mainline kernel and with this the system successfully come back from suspend:
```
/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend suspend: success.
/etc/pm/sleep.d/10_grub-common suspend suspend: success.
/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: stop: Unknown instance:
success.
/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend suspend: success.
/usr/lib/pm-utils/sleep.d/99video suspend suspend: kernel.acpi_video_flags = 0
success.
/etc/pm/sleep.d/action_wpa suspend suspend: success.
mar gen  5 13:14:04 CET 2010: performing suspend
mar gen  5 13:14:19 CET 2010: Awake.
mar gen  5 13:14:19 CET 2010: Running hooks for resume
/etc/pm/sleep.d/action_wpa resume suspend: success.
/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video resume suspend: success.
/usr/lib/pm-utils/sleep.d/96laptop-mode resume suspend: success.
/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
```
I would use it, but I noticed some problems with AppArmor compatibility...

I tried with the 2.6.33-rc2 mainline kernel but the suspend is not working, like in the 2.6.31 karmic kernel.

Is it a kernel problem? What can I do to make it working?
Thanks

---

### Post by gabrielitos on 2010-01-05
N.B. I tried almost all the solutions proposed here:

[http://ubuntuforums.org/showthread.php?t=1307618&page=29]("http://ubuntuforums.org/showthread.php?t=1307618&page=29")

without success...

---

### Post by gabrielitos on 2010-01-06
I cannot resume from suspend neither with the Live Cd.
I tried to install the 2.6.28 and 2.6.30 kernel and only with the former the resume is working, with the latter the behaviour is the same of the karmic kernel. Ibernation is always working fine.
I'm quite sure it's a kernel problem, does anybody have the same issue/a solution?

---

### Post by gabrielitos on 2010-01-09
bumpete! :)

---

### Post by derekmbarnes on 2010-01-09
I'm having this problem too; go to bugzilla.kernel.org and see if a report has been filed yet. A bunch of the problems with Karmic right now (suspend, CPU temperature, graphics card) are looking more and more interrelated...

And will someone please tell me what "N.B." stands for?

---

### Post by Glikegluk on 2010-01-09
Nb stands for nota bene = take good note.
cheers

---

### Post by gabrielitos on 2010-01-12
I filed a report in launchpad: I'm not sure it's a kernel problem, it can be only an Ubuntu kernel version issue. Give your feedback here:
[https://bugs.launchpad.net/bugs/506355](https://bugs.launchpad.net/bugs/506355)

Is N.B. not international, like i.e.? [http://en.wikipedia.org/wiki/Nota_bene](http://en.wikipedia.org/wiki/Nota_bene)

---

