---
title: "Possible GRUB misbehaviour after resizing/moving HDD partitions"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by kd70 on 2009-03-10
My laptop is dual-boot with Ubuntu 8.10 (Intrepid) and WindowsXP. I recently upgraded the internal HDD from 80GB to 250GB.

I used Clonezilla LiveCD (ver. 1.2.1-39) to save the image of the 80GB HDD and also to restore this image to the new 250GB HDD. As part of the restore-image I permitted Clonezilla to re-install GRUB in the MBR of the new HDD.

After restoring the image of the 80GB HDD to the 250GB HDD I was ready to check if both OS's were still intact and bootable. At this point both Ubuntu and WindowsXP booted as normal.

I then used GParted (ver. 0.4.2, on SystemRescueCD) to resize & move partitions in order to exploit the increased space of the 250GB HDD. I did not create/delete any partitions. GParted reported no errors.

After manipulation of partitions WindowsXP boots as before.

Ubuntu also boots successfully. However, instead of the usual boot-screen with the "UBUNTU" name and orange progress-bar, I have a brief glimpse of this screen before it disappears, to be replaced by text-based diagnostic info that is produced behind-the-scenes while Linux is booting. Also, when I shut down, the usual "UBUNTU" screen with progress bar is not present, instead I see text info detailing the shutdown procedure.

To repeat, Ubuntu works perfectly. It both boots and shuts down correctly. My only concern is that boot and shutdown procedures have changed: instead of "nice" graphics I get text. There has been no change to /boot/grub/menu.lst

Is is possible that there is a problem with GRUB? Could GRUB be looking for something at an address on the HDD that no longer contains the data it once did?

---

### Post by Neo_The_User on 2009-03-10
```

sudo update-grub

```

---

