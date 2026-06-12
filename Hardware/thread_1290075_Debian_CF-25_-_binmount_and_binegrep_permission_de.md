---
title: "Debian CF-25 - /bin/mount and /bin/egrep permission denied?"
date: 2009-10-13
forum: Hardware
---

### Post by hypercoffeedude on 2009-10-13
Okay, first my specs. 
```
Panasonic Toughbook CF-25, 48M RAM, 4GB CF Card on CF-IDE adapter. Cardbus/PCMCIA is a little buggy
```

Well, I installed using a different laptop on a compact flash card reader on expert mode (Debian 5.01 Full CD-1). I adjusted the necessary things such as: GRUB, fstab, etc. To make sure things pointed to/dev/hda1 (IDE HD) instead of /dev/sda1 (USB CF Reader). I did however forget to disable DMA which I think most Compact Flash cards do not support. I booted the system the first time immediatly after install, on the CF-25 with a GRUB tweak. Everything went well for the next several boots. 

Then I went to boot the system again and it was complaining about not being able to mount anything. It mounted root, but then DMESG showed: "-bash: /bin/mount Permission Denied" and and also "-bash: /bin/egrep Permission denied". Then the system hung. No kernel panic, it just stopped.

I then went to grub and changed "ro" to "rw" 
```
linux /boot/vmlinuz-2.6.26-2-486 root=UUIDxxxxxx ro" 
```

Now I can boot the system, and access/run most files/apps. But the mount/egrep programs still refuse to run. Also mtab is empty. I have even tried running mount myself it says "Permission Denied". However umount works fine.

Any takers on my problem? I am quite knowledgeable with linux, but I can't figure this one out. Google hasn't even been much help...  :(

Need more info? Please ask!

###***EDIT***###
I fixed egrep with a symlink to grep... now what?

---

