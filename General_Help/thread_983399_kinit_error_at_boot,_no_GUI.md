---
title: "kinit error at boot, no GUI"
date: 2008-11-15
forum: General Help
---

### Post by Charles.Strahan on 2008-11-15
Hello,

I recently performed a "safe-update" in aptitude on my Kubuntu installation (on my desktop computer).  I haven't used this computer in a while, but now, after rebooting, I get the following error (after the GUI flickers on/off several times, showing a generic "X"-cursor):

> Starting up ...
Loading, please wait...
usplash: Setting mode 1152x864 failed
usplash: Usinging mode 1024x768
kinit: name_to_dev_t(/dev/disk/by-uuid/7295e312-0852-40e2-a49e-fc14dbfb926c) = sdb6(8,22)
kinit: trying to resum from /dev/disk/7295e312-0852-40e2-a49e-fc14dbfb926c
kinit: No resume image, doing normal boot...

Ubuntu 8.04.1 charles-desktop tty1

charles-desktop login: [   74.5954894] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   74.595524] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[   74.595524] ata2.00: status: { DRDY ERR }
[  398.431242] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  398.431305] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[  398.431362] ata2.00: status: { DRDY ERR }
[  398.432455] ata2.00: CDROM (ioctl) error, command: Test Unit Ready 00 00 00 00 00 00

Ubuntu 8.04.1 charles-desktop tty1

charles-desktop login:

I'm a relatively new Linux user (about a week or two of use), so I'm not sure where to even start at diagnosing this.  If there's anything I can do to assist someone interested in helping me out, please let me know.

Oh- and before I forget, does anyone know how to get an error log when a system crashes like this?  What I mean is that I had to hand type the above error messages, and it sure takes forever :) - surely there's a better alternative.

Thanks a million!
-Charles

[UPDATE]
On a hunch, I tried running xinit to see what would happen, and I get a message about a failure to launch the nvidia kernal module.  With my limited experience, I would imagine that some how the nvidia "drivers" got hosed during the update... Perhaps accidentally removed due to dependency issues?  I had compiz and the "new" nvidia driver installed prior to the update - and I forgot to update everything right after installing kubuntu, so that could have something to do with it also.  I think I will try reinstalling, immediately update, get the nvidia driver and update again, skip compiz and reboot, and see what happens.  I'll let you all know what happens... hopefully I'll be able to just dismiss this error.

---

