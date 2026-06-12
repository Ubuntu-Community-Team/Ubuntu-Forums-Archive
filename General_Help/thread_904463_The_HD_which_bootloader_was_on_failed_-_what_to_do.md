---
title: "The HD which bootloader was on failed - what to do?"
date: 2008-08-29
forum: General Help
---

### Post by spacejanitor on 2008-08-29
Hi guys,

I have been dual-booting Vista and Ubuntu on my laptop.  It's a bit of an odd configuration, but I've partitioned the internal laptop drive to have Ubuntu on it alongside Windows, however on an external USB drive I had the bootloader installed.

Recently, this USB drive died, and now I can't boot into either OS.  On bootup, I have a Grub Error 21, understandably since the USB drive is missing.

My question is, can I reinstall the bootloader only on a different drive to make both OSes bootable again?

Thanks

---

### Post by maybeway36 on 2008-08-29
Was the /boot partition on the USB drive, or just the MBR portion? If you didn't have a seperate /boot partiton, go to:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

