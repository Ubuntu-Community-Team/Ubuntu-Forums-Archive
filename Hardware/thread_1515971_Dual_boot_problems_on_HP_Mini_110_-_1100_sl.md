---
title: "Dual boot problems on HP Mini 110 - 1100 sl"
date: 2010-06-23
forum: Hardware
---

### Post by mcallisto on 2010-06-23
Hi all,

I installed Ubuntu netbook remix as dual boot on my new HP Mini 110 - 1100 sl.
Standard installation procedure, everything went fine; once in, I installed as suggested by the system the proprietary drivers for the wireless card and that is working as well.

But now I have some problems at boot with **GRUB (version 1.98-1ubuntu6)**:

[LIST]
[*]System don't boot at all if I choose **Ubuntu Linux 2.6.32-22-generic **option, screen goes black with cursor blinking forever. If at this option I press 'E' it shows:
[/LIST]
```

recordfail
insmod ext2
set root='(hdo,5)'
search --no-floppy --fs-uuid --set 645e458c-28a3-4f4e-b2e0-8072b5ac1ca8
linux /boot/vmlinuz-2.6.32-22-generic root=UUID=645e458c-28a3-4f4e-b2e0-8072b5ac1ca8 ro   quiet splash
initrd /boot/initrd.img-2.6.32-22-generic

```
[LIST]
[*]If I choose **Ubuntu Linux 2.6.32-22-generic (recovery mode)** different things may happen, randomly it seems to me:
[LIST]
[*]Process starts but it stops at this point (what I can see on screen...), cursor blinking forever:
[/LIST]
 
[/LIST]
```

Done.
Begin: Running /scripts/init-premont ...
Done.
Begin: Mounting root file system ... ...
Begin: Running /scripts/local-top ...
Done.
[    1.145491] usb 1-4: configuration #1 chosen from 1 choice
[ ...similar lines about ahci, scsi, b43-pci-bridge, ata... ]
[    1.316147] hub 1-0:1.0: unable to enumerate USB device on port 8

```
[LIST]
[*]
[LIST]
[*]Once it happened that UBUNTU was booted ok, ready to login
[*]Sometimes it reaches the Recovery menu, where choosing failsafeX it succeed in running in failsafe graphic mode
[/LIST]
 
[/LIST]
I am not at all an expert, but this behavior is quite puzzling to me.

Any idea / suggestion of what I could do?

Thank you in advance, Mario

---

