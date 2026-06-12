---
title: "Cannot format NTFS HDD that came from WIN10"
date: 2021-09-27
forum: Hardware
---

### Post by vulpes7k on 2021-09-27
So, I recently migrated to Linux from Windows, and I have two storage devices, a ssd which holds the ubuntu installation, and a hdd which I would like to use for whatever. I used both of them in Win10, ssd was the install drive and hdd whatever drive. I didn't format the hdd during ubuntu installation because I needed some files in it. When using lsblk command the hdd is listed as 'sda' but no other info, just 'sda'. The disks app shows it as a 4gb disk (it's actually 1tb) and the assessment is "Disk is OK, one bad sector". The mkfs command outputs 1 warning: "could not read block 0: Input/output error", and also "Writing superblocks and filesystem accounting information: mkfs.ext4: Input/output error while writing out and closing file system". The mkfs command but for NTFS outputs "/dev/sda is entire device, not just one partition. \n Refusing to make a filesystem here!". I also went for the dd command which outputted "writing to /dev/sda: Input/output error \n 1+0 records in \n 0+0 records out". Help, please?

---

### Post by yancek on 2021-09-28
>   The mkfs command but for NTFS outputs "/dev/sda is entire device, not  just one partition. \n Refusing to make a filesystem here!"

I'm not familiar with 'Disks' but have you tries getting the output from fdisk, gdisk or gparted to see if that software shows the correct drive size?  Gparted is on the Ubuntu install medium (USB or DVD)  The error above indicates you need  a partition on the device in order to create a filesystem.  Not sure why that happens but it is simple enough to create a partition and then create a filesystem.  Try that to see if it works.

---

### Post by vulpes7k on 2021-09-28
That was precisely it, I was able to create a partition and then mount it, you helped me a lot! Thank you very much.

---

### Post by hk42 on 2021-09-29
I believe the mistake was that you don't format a HD (sda)
You first have to create at least a partition (sda1,sda2, etc)

---

