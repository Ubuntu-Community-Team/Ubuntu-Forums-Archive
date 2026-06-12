---
title: "Did my hard drive die?"
date: 2008-10-22
forum: General Help
---

### Post by es926 on 2008-10-22
Hello,

I was trying to install the gparted live cd on a small partition on my hard drive today and the results are very very bad. I used unetbootin, which seemed to think that my scsi drive was a usb drive, and then modified grub's menu.lst manually to add a gparted option. I then restarted and my computer said that there was no operating system found on the disk. I tracked down an actual livecd and booted it up hoping that I could fix this. Now for the punchline: fdisk -l doesn't show my harddrive at all. I'm scared and distraught right now, please offer any advice if you can.

Thanks

---

### Post by Yellow Pasque on 2008-10-22
Does the BIOS recognize the drive?

---

### Post by es926 on 2008-10-22
Few, I managed to fix the problem. Thanks for your reply. The live cd I was using was pretty old and I'm guessing that it just didn't support my drive. The solution once I could find my drive was just:

run 'grub'
enter 'find /boot/grub/stage1'
it outputed '(hd0,0)'
enter 'root (hd0,0)'
enter 'setup (hd0)'
enter 'quit'

and then that's it. Maybe if somebody finds my post that will be of use to them.

---

