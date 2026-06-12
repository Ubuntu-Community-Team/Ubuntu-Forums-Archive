---
title: "hardy to jaunty upgrade, failure on freetype"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by glok_twen on 2009-04-27
hi. i just executed an upgrade from hardy to jaunty. it seemed to go fine until after the reboot, when it goes through the boot sequence and hangs. now i can't boot from any kernel either.

the error is:
ubuntu is running in low graphics mode
failed to load module "freetype" (module does not exist, 0)
cannot open device /dev/input/wacom


as an aside, i haven't been able to get to a command line either. when i choose at the grub menu to run a given kernel and do so in recovery mode, i get prompted to log in as root. of course i had just always used sudo and my root account is not enabled. but recovery mode seems only allow logon of that account, for which my user account with sudo priv is not allowed.

so then i started to figure out grub in order to change the commands in the grub entry to boot from the new kernel. the closest i could come up with to force it to only console mode was to add in the command "single" after the "root ...", kernel "..." and initrd "..." commands in the grub sequence. do you know what the command sequence looks like in grub to force a console login where i can enter my user account login? and, from grub, how to i set up a new entry with that sequence and make sure it's saved so that i can select it from the grub menu?

thanks,
gr

---

