---
title: "no cdrom drive"
date: 2010-01-16
forum: Hardware
---

### Post by Willyweasel on 2010-01-16
Okay just installed Ubuntu 9.10 on my desktop installed from cd and everything went fine during install. Loaded up Ubuntu for the first time and no cdrom drive at all. Did the modprobe ide-cd and ide-generic in the terminal, and it's response is  FATAL: Module ide_cd not found. By the way if this makes any difference my hard drive is SATA running in native ide mode, and my cdrom drive is a ide dvd/cd burner. Any help is appreciated

---

### Post by Willyweasel on 2010-01-16
can someone help?

---

### Post by Willyweasel on 2010-01-18
Well solved my own problem, first I ran sudo gedit in the terminal and opened up /ect/modules and added ide-cd ide-disk ide-generic all on there own line in that order. 
It looked like this:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

ide-cd
ide-disk
ide-generic
lp
rtc

Then ran sudo gedit in the terminal again, opened /ect/default/grub and found the line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and changed it to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off modprobe ide-cd modprobe ide-disk modprobe ide-generic". Ran sudo 'update-grub' in the terminal. restarted and my dvd drive worked!

---

### Post by hughcharlesparker on 2010-01-20
Thanks for that - I just had the same problem, and your post sorted it out for me.

I only changed /etc/modules - it doesn't seem that the other file is needed.

---

