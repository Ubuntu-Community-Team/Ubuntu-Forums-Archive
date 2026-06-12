---
title: "Grub failure, cannot load boot entries"
date: 2009-08-25
forum: Installation &amp; Upgrades
---

### Post by 0x656b694d on 2009-08-25
Hi

i just ran another update of my 9.10 on 64-bit system (ext4). Then i changed an entry in /etc/defaults/grub.cfg file -- set timeout from 0 to 3, then removed 3 old kernels keeping the latest one (which were running, 2.6.31-7, afair) only. It did update-grub several times for each of the kernels being removed.
Then i tried to reboot.
Saw grub loading and it stopped with the following message:
> 
Booting 'Memory test ...
error: zImage doesn't support 32-bit ...
Failed to boot default entries
Press any key to continue...

I have (had?) Windows in the list also (i saw it had been found in the update-grub log).
So, do i have to reinstall grub2? How do i do that? (writing from splashtop embedded linux now)
Any ideas how do i boot Windows in this situation to burn a 9.10 Live CD?
I have only ubuntu 8.04 Live CD here.

Thanks!

---

### Post by P4man on 2009-08-25
eek.. been there, done something similar. Had a HELL of a time fixing grub2.
I finally went back to grub 1, and even that wasnt easy to accomplish. Dont ask me how I did it :s

Anyway, just a wild idea.. if you have an usb stick or  partition  that your ubuntu 8.04 can mount with enough free space, you could boot 8.04 to download a 9.10 iso and burn it to cd (or stick). Clumsy, but should work.

Not that you'll be out of the woods once you have that cd.

good luck!

---

