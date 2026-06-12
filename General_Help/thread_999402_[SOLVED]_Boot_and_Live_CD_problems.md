---
title: "[SOLVED] Boot and Live CD problems"
date: 2008-12-01
forum: General Help
---

### Post by shortylonglegs on 2008-12-01
The other day I was installing a bunch of  updates when I ran into a problem.  I think it was installing a kernel update at the time, but I wasn't paying too much attention.  It failed, and gave an error like 'could not [something] ./boot/grub/[something]'.  I tried a second time to update, only to get the same result.  I thought perhaps the problem was from updating so much at once, so I tried to reboot.  I immediately got this:
```
GRUB Loading stage1.5.

GRUB loading, please wait...
Error 2
```
I then tried booting from the Live CD, having seen simmilar errors before, but that didn't work either.  I got to the screen where it asks what to do.  I pick 'Try Ubuntu...'  It hangs for a while then says:
```
invalid compressed format (err=2)

-- System halted
```
I also had a Live USB I had made earlier, so I decided to try that.  Again, I got to the screen where it asks what I want to do, and even shows the splash screen with the orange bar bouncing back and forth, but then stops and puts me in a shell:
```
BusyBox v1.10.2(Ubuntu 1:1.10.2-1ubuntu6)built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)_
```
I have no idea where to go from here.  I do have an encrypted partition with my home and root, and have boot on an unencrypted partition.  At this point my data isn't important, I have most of it backed up, but I can't even reinstall.  Can anyone help?

---

### Post by shortylonglegs on 2008-12-04
Acting on a hunch I got a DBAN iso and just wiped my entire hard drive, not really sure why but its working.  Reinstalling now.

---

