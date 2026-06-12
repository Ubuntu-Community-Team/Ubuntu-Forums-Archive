---
title: "SATA Drive Problem"
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by Liehann on 2006-06-12
Hi,

When running the install cd the Ubuntu install has trouble detecting my dvd drive. The problem seems to be related to my system having an IDE dvd drive and a SATA hard drive. If I disable SATA in my BIOS the install app detects the dvd drive fine but does not detect the hard drivce. If SATA is configured to combined mode Ubuntu does not detect the DVD drive.

Update - Regardless of the SATA config in BIOS WinXP picks up the drive and starts up fine which at least indicates that the drive an mboard are functioning correctly. I have flashed the mboard BIOS to the latest version. I am running the live cd to try out Ubuntu but I won't be able to install given the current issues.

Update 2 - Found this thread:
[http://ubuntuforums.org/showthread.php?t=153384&highlight=sata]("http://ubuntuforums.org/showthread.php?t=153384&highlight=sata")
My mboard (Gigabyte GA-8I955X Royal) has onboard SATA 3TGb/s controllers. I think the drive is a SATA2 drive but I can't remember. Seagate Barracuda 7200, 250 Gbytes, (8T3250823A8). So if I understand the thread above correctly the problem may just be that the kernel in 5.10 doesn't support the newer SATA controllers.

Any suggestions?

Thanks,
Liehann

---

