---
title: "Strange SSD Booting Issues"
date: 2009-03-15
forum: Hardware
---

### Post by tutwabee on 2009-03-15
Earlier today Firefox froze in a very odd way and my filesystem and window manager started acting very unusual. I rebooted and upon booting received a corrupted filesystem error.

After being dropped to a shell I fscked the drive and robooted.  After initially rebooting, the OS booted without problem except that my wireless card was unrecognized.

I rebooted again and received an error regarding the UUID of my bootable solid-state drive.  I used a rescue disk to edit grub and boot manually to /dev/sda1.

Now whenever I boot grub still errors out with a message like this:
```
ata1: COMRESET failed (errno:-16)
```

The strange thing is if I run "ls -l /dev/sda*" within the first 10 seconds no files are returned.  If I wait for about 30 seconds and run "ls -l /dev/sda*" I can see /dev/sda, /dev/sda1, and /dev/sda5.  I can then hit CTRL+D to boot properly.

Also, the BIOS loading screen now takes a considerable amount of time to load (probably about 20 seconds whereas it previously took about 5).

I am baffled as to what is going on here.  Is my solid-state drive corrupted?  What is causing the delay in /dev/sda1 being seen?  I tried toggling the SATA mode in the BIOS, but this did not fix the problem.

---

### Post by tutwabee on 2009-03-17
I still don't know what caused the problem, but it now seems to be fixed.  I hibernated my computer and upon booting it resumed the image properly.  Since then I have not had any problems when rebooting my computer.

---

