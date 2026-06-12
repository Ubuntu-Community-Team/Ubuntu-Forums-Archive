---
title: "Wondering How to Revert to Previous Drivers"
date: 2013-03-05
forum: Hardware
---

### Post by Highrise99 on 2013-03-05
After installing Steam, I noticed that I was unable to launch it due to my drivers being too old. I use an NVIDIA GTX 550 Ti, so Steam requires at least 304.22. However, it is experimental. Though the general consensus is that it is safe, I would like to be prepared in the case that something goes wrong. Basically, I would like to know how to revert to previous, stable drivers if the experimental ones cease to function.

I would also like to point out that in order for Ubuntu to work I have to modify several boot options. "quiet" is changed to "noquiet," "splash" to "nosplash," and "nomodeset" is appended. I am using Ubuntu 12.04.

---

### Post by Mark Phelps on 2013-03-05
There are probably more "elegant" solutions -- but back when I used to mess around with Beta ATI driver versions, the easiest and quickest way I found to handle this was to use Clonezilla to image off the current Ubuntu install to another drive.  Then, if the driver update went bad, rather than spend hours, or days, hacking around trying to fix it from the command line (because, all too often, the desktop would not come up), I just started Clonezilla selected the image backup and, 10 minutes later, I had everything back and working.

---

### Post by Highrise99 on 2013-03-05
Would Clonezilla overwrite any data on the disk it would be booted from? I have a dual boot system, so would I be able to back it up onto my Windows drive? Or would I need to re-partition it to avoid this?

---

### Post by Mark Phelps on 2013-03-06
> **Highrise99 said:**
> Would Clonezilla overwrite any data on the disk it would be booted from?
Depends on the option used to make the backup.  IF you just backup a partition, it will just restore that partition.  IF you backup the entire drive, it will restore the entire drive.
>  I have a dual boot system, so would I be able to back it up onto my Windows drive? Or would I need to re-partition it to avoid this?
If your Ubuntu install is to a separate Ext4 filesystem partition, you CAN write the backup to the Windows drive -- but do NOT do that to the same partition that contains the Windows OS.  I did Clonezilla backups like this -- but to a shared NTFS data partition.  Since Clonezilla only writes a compressed image file, I wasn't concerned that NTFS would not retain the Linux filesystem permissions.

The problem with writing to NTFS OS partitions using Linux utilities is that, sometimes, that can result in filesystem corruption, and if that happens, your Window OS is rendered unboootable -- making it really hard to fix it.

---

### Post by Highrise99 on 2013-03-06
Thanks. As I make regular backups of my files on Ubuntu to my Windows drive while using it for backups of Windows files, I would only be interested in backing up the necessary system files and the Windows backups.

> **Mark Phelps said:**
> [COLOR=#000000]IF you just backup a partition, it will just restore that partition. IF you backup the entire drive, it will restore the entire drive.[/COLOR][COLOR=#000000]
[/COLOR]
I'm guessing this would be possible by backing up the Windows files individually and then just the system partition of the disk?

> **Mark Phelps said:**
> Since Clonezilla only writes a compressed image file

If possible to backup only system files, about how much space do you think is required using LZMA?

---

