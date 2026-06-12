---
title: "Buffer I/O error on device sda after update"
date: 2010-07-24
forum: Hardware
---

### Post by Lepy on 2010-07-24
I moved to a new place and finally have the time to setup my mythbox with our new cable provider. It has been running fine for for listening to music while unpacking and using xbmc, but since it had been disconnected from the internet for about a week, I decided to install the 51 updates available (including kernel 2.6.32-24-generic).

After a successful update, I rebooted and was greeted with a constant string of "Buffer I/O Error on device sda, Logical Block 0" and another error about requests.

I can successfully boot with a livecd, mount all the partitions, and copy files to and from the disks without error. So, the sda seems to be fine. I guess something in the update may have borked the system or perhaps grub. 

I will try reinstalling grub but does anyone have any clue as to what might have happened and an easy fix?

---

### Post by Lepy on 2010-07-25
It seems to be fixed now.

I had to load up a 64bit livecd and chroot in using:
```
mount /dev/sdb1 /mnt
mount -o bind /dev /mnt/dev
mount -o bind /proc /mnt/proc
sudo chroot /mnt
```

From there, I changed my /etc/defaults/grub. I had originally been using a multitude of kernel options including acpi=noirq. These settings had worked for well over a year, but somehow broke after the update, I guess. I replaced the acpi=noirq with irqpoll and ran update-grub. 

Upon reboot, the latest kernel loaded without problem. If anything changes though, I'll report back.

---

