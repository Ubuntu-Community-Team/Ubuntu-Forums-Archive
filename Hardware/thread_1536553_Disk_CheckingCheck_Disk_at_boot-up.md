---
title: "Disk Checking/Check Disk at boot-up"
date: 2010-07-22
forum: Hardware
---

### Post by gnik1 on 2010-07-22
Ubuntu is doing a disk check on boot-up every so often and I am wondering what the cause of it is.

Does Ubuntu have a routine for doing so on it's own or is something going wrong that is causing it to check the drive on boot-up?

I haven't lost power to the pc or found that it's off because of any other reason than my purposely shutting it down via the shutdown feature on the menu bar.

Thanks in advance for explanations

---

### Post by IcarusR on 2010-07-22
By default fsck (file system check) runs on every 30th boot.
For some ideas on how to change the interval, to disbale or to have checks done every week, month etc read this thread...

[http://ubuntuforums.org/showthread.php?t=300477]("http://ubuntuforums.org/showthread.php?t=300477")

---

### Post by gnik1 on 2010-07-22
Thank you for this information. It put my mind at ease as I was worried about hdd problems.

---

