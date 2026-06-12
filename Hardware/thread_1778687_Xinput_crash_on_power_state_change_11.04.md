---
title: "Xinput crash on power state change 11.04"
date: 2011-06-09
forum: Hardware
---

### Post by buigretta on 2011-06-09
Since the 11.4 upgrade, every time my laptop power cable is unplugged I get some degree of loss of input control.  Mostly mouse clicks are unrecognized, although sometimes keyboard input is gone too.  Currently my workaround is to log in via TTY and kill the X server (if the keyboard input has not crashed!).

From what I've been able to determine, pm-powersave seems to trigger the crash.  My amateur sleuthing through the log files has yielded nothing fruitful.

Any help would be appreciated!

Acer Extensa 4420, Ubuntu 11.4 64bit

---

### Post by buigretta on 2011-06-12
*BUMP*
Well, I've looked a little further into it and see that pm-powersave runs all of the scripts in /usr/lib/pm-utils/power.d, but I still can't figure out which one is causing the input to go haywire.

Anyone have a clue what they've changed in 11.04?  I did not have this problem in 10.10, and it's really getting in the way, as my laptop cord is janky and gets disconnected frequently.

Here's a list of the scripts:

/usr/lib/pm-utils/power.d/95hdparm-apm
/usr/lib/pm-utils/power.d/anacron
/usr/lib/pm-utils/power.d/disable_wol
/usr/lib/pm-utils/power.d/hal-cd-polling
/usr/lib/pm-utils/power.d/intel-audio-powersave
/usr/lib/pm-utils/power.d/journal-commit
/usr/lib/pm-utils/power.d/laptop-mode
/usr/lib/pm-utils/power.d/pcie_aspm
/usr/lib/pm-utils/power.d/readahead
/usr/lib/pm-utils/power.d/sata_alpm
/usr/lib/pm-utils/power.d/sched-powersave
/usr/lib/pm-utils/power.d/wireless
/usr/lib/pm-utils/power.d/xfs_buffer

---

