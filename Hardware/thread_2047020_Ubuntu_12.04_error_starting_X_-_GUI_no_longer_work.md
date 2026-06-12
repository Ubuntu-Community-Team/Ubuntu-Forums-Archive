---
title: "Ubuntu 12.04 error starting X - GUI no longer works"
date: 2012-08-24
forum: Hardware
---

### Post by LucasDavenport on 2012-08-24
I've been looking through the forums and internets over the past couple days to find a solution for my issue, but have been unlucky. I am posting here with hopes of finding a solution or at least a direction to search to solve my issue. I have a home built machine that contains a nvidia GeForce GTX 560Ti card. Everything was working well until last Saturday when things went haywire. I'd been having problems with my GUI freezing and I would have to go tty (CTRL-ALT-F1) and kill the lightdm process to restart. I applied system updates Saturday morning and decided to reboot b/c of some kernel updates that were included. After that, my GUI never came back up (lightdm failed during startup). I've tried installing gdm and disabling lightdm to no avail. I also tried selecting the previous versions of the kernel via GRUB but kept getting to the same place during startup (and failing).  I finally realized that the X server isn't starting up. I tried dpkg-reconfigure to make gdm the default (and vice versa) with no luck. When i attempt to startx, I am getting an error that states:

Inconsistency detected by ld.so: ../sysdeps/x86_64/dl-machine.h: 460: elf_machine_rela_relative: Assertion `((reloc ->r_info) & 0xffffffff) == 8' failed!

I tried nvidia-xconfig but that didn't work either.

I've attached the full output from executing startx at the command prompt as well as the Xorg.0.log and my xorg.conf file.

Any assistance you all can provide is greatly appreciated.

Thanks

---

