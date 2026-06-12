---
title: "after Kubuntu 18.04 upgrade, Intel audio C230 stopped working"
date: 2020-01-31
forum: Hardware
---

### Post by dchmelik on 2020-01-31
Early last October in my Kubuntu 18.04 PC, this was working: "Audio device: Intel Corporation 100 Series/C230 Series Chipset Family HD Audio Controller (rev 31)"--lspci.  Since then I wasn't using that for anything but tried a few days ago; now it's not working: kernel driver is loaded (if it's snd_hda_intel) but in system settings, the chip is greyed out... detected, but not select-able (other audio works.) It was working before a kernel/OS upgrade in/to 18.04.3.

    I'm trying to check if hardware was damaged, or like many cases within last six to 10+ years, /kernel/driver change made someone hardware stop working, then was fixed or they recompiled.  The problem is steps for older *buntu no longer work. Main older solution seems install dkms w/oem-audio-daily-dkms ( [https://askubuntu.com/questions/471433/sound-card-not-detecting/863157#863157](https://askubuntu.com/questions/471433/sound-card-not-detecting/863157#863157) .)  However the page says for 18.04.1, oem-audio-daily-dkms failed...

I've used POSIX-based operating system (OS) distributions (distros) since mid-to-late 1990s (and normally use strictly Unix[-like], i.e., non-systemd.)  I administered a Kubuntu fork several years (GNU/Linux Mint KDE) for average users, then Kubuntu for them, and now after needing AMDGPU-PRO drivers for a PC, chose Kubuntu.

    I feel shocked how much kernel is updated.  On strictly Unix[-like] OSes, some only suggest kernel security updates (until new stable/decimal-numbered ISO release.) I see Kubuntu updated dozens times with no explanation/choice, perhaps for "bleeding-edge"... even though not installing proposed or backport changes.  Unless something else I shouldn't necessarily include ('updates?') that style doesn't seem stable/Unix-like... I don't want "bleeding-edge"... so if/when AMDGPU-PRO or Radeon Open Compute (ROCm) is available on strictly Unix[-like] OSes I'll switch back... for now it's worthwhile learning Kubuntu to help users.

---

### Post by dchmelik on 2020-04-30
Worked after blowing dust out, and reinstall to 18.0.4

---

