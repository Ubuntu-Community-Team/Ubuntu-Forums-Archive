---
title: "[SOLVED] Booting from external USB drive using a pendrive?"
date: 2008-07-18
forum: General Help
---

### Post by feistybill on 2008-07-18
I installed Ubuntu 8.04.1 to an external HD (usb) only to find that the "USB HD" boot support in my BIOS doesn't work at all. It can, however, boot USB pen drives.

I was wondering if there is a way to trick the pc into booting from the USB HD - for example, installing Grub onto an USB pen drive and configuring it to boot from the USB drive? I don't know if this is possible :confused:

Please help!

---

### Post by PmDematagoda on 2008-07-18
Perhaps(a big perhaps) you can try and install GRUB using the Live CD itself, although it would mean getting the partitions right and the config file. You can use the instructions given in the how-to [here]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by feistybill on 2008-07-18
Thanks for your reply.

Actually I think I just solved the problem! I installed Grub both on the USB pendrive and on the USB hard disk, then edited the pendrive's menu.lst and created an entry to chainload the other disk's Grub.

When I rebooted, the pendrive's grub (for which the BIOS has booting support) was loaded first and made it possible booting the external usb HD.

:guitar:

---

