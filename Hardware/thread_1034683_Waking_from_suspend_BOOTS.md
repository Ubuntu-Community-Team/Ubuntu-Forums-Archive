---
title: "Waking from suspend BOOTS"
date: 2009-01-08
forum: Hardware
---

### Post by tylerious on 2009-01-08
I have an eMachines M6811 laptop running 8.10 (amd64) and am having problems waking from suspend. The laptop seems to go to sleep alright, but when I press the power button to wake it, it boots up like it had been turned off! I have had a lot of suspend issues with linux, but never this one! 

Here is my /var/log/pm-suspend.log:
```
Initial commandline parameters: --quirk-dpms-on
--quirk-vbestate-restore
--quirk-vbemode-restore
--quirk-vga-mode3
--quirk-vbe-post
--quirk-reset-brightness
Thu Jan  8 22:57:24 EST 2009: Running hooks for suspend.
/usr/lib/pm-utils/sleep.d/00clear suspend: success.
/usr/lib/pm-utils/sleep.d/01PulseAudio suspend: success.
/usr/lib/pm-utils/sleep.d/05led suspend: not applicable.
/usr/lib/pm-utils/sleep.d/10NetworkManager suspend: sudo: no passwd entry for 1000!
success.
/usr/lib/pm-utils/sleep.d/48hid2hci suspend: not applicable.
/usr/lib/pm-utils/sleep.d/49bluetooth suspend: not applicable.
/usr/lib/pm-utils/sleep.d/50modules suspend: success.
/usr/lib/pm-utils/sleep.d/90clock suspend: success.
/usr/lib/pm-utils/sleep.d/94cpufreq suspend: success.
/usr/lib/pm-utils/sleep.d/95anacron suspend: success.
/usr/lib/pm-utils/sleep.d/95led suspend: not applicable.
/usr/lib/pm-utils/sleep.d/96laptop-mode suspend: success.
/usr/lib/pm-utils/sleep.d/98smart-kernel-video suspend: not applicable.
/usr/lib/pm-utils/sleep.d/99video suspend: Allocated buffer at 0x11000 (base is 0x0)
ES: 0x1100 EBX: 0x0000
success.
Thu Jan  8 22:57:28 EST 2009: performing suspend
```

Any suggestions?

---

