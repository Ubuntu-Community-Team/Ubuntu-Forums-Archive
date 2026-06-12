---
title: "FYI: Seagate FreeAgent Works Great!"
date: 2008-12-31
forum: Hardware
---

### Post by dasunst3r on 2008-12-31
I've been in the market for a new external hard disk to replace my other one (I replace these once every two years), and I settled on the Seagate FreeAgent XTreme.  I was a bit leery about buying one of these after reading that the drive remounts read-only if it goes to sleep, but Seagate's 5-year warranty and reputation simply couldn't be beaten!  So, I mustered up the guts (and money) for one.

After getting it, I ran some informal tests on my Ubuntu Linux 8.10 installation.  I wrote a file to it and left it alone until it went to sleep.  Afterwards, I went into the drive and successfully wrote another file to it.  I also like how it would turn on/off automatically when I connect or disconnect the drive -- that makes the drive last longer.  Therefore, for those of you who are in the market for external hard disks, the Seagate FreeAgent series is OK now.

Product information: [http://freeagent.seagate.com/en-us/hard-drive/Free-Agent.html](http://freeagent.seagate.com/en-us/hard-drive/Free-Agent.html)

---

### Post by Dourado on 2009-12-01
Not so great...

Seatgate FreeAgent Xtreme (1TB)

While the standby feature that you describe has indeed been fixed, there are still problems with this drive. I am *trying* to use this drive over USB on my server. It works fine for awhile, but suddenly disconnects, and the system can't find the drive again until I power-cycle the drive. This happens after some unknown amount of time and right in the middle of reading/writing to the drive, so it's not a power-savings feature issue.

It does run fine using USB1.1 (modprobe -r ehci_hcd). I see this fix posted everywhere on these forums. However, this is NOT an acceptable solution. I get about 20MB/sec transfer rates on ehci_hcd, but only 1MB/sec on uhci_hcd. A 20-fold difference in performance is a BUG, not a workaround, IMHO. It may just be faulty hardware (either my system, the drive, or the combination), but I haven't been able to narrow it down.

I've tried recompiling my kernels with different options removed and added to try to get this to work, but it appears to be an unresolved issue. If anyone has any suggestions, or would like to see my logs and debug information, please let me know.

---

### Post by willybanjo on 2009-12-07
> **Dourado said:**
> Not so great...

Seatgate FreeAgent Xtreme (1TB)

While the standby feature that you describe has indeed been fixed, there are still problems with this drive. I am *trying* to use this drive over USB on my server. It works fine for awhile, but suddenly disconnects, and the system can't find the drive again until I power-cycle the drive. This happens after some unknown amount of time and right in the middle of reading/writing to the drive, so it's not a power-savings feature issue.

It does run fine using USB1.1 (modprobe -r ehci_hcd). I see this fix posted everywhere on these forums. However, this is NOT an acceptable solution. I get about 20MB/sec transfer rates on ehci_hcd, but only 1MB/sec on uhci_hcd. A 20-fold difference in performance is a BUG, not a workaround, IMHO. It may just be faulty hardware (either my system, the drive, or the combination), but I haven't been able to narrow it down.

I've tried recompiling my kernels with different options removed and added to try to get this to work, but it appears to be an unresolved issue. If anyone has any suggestions, or would like to see my logs and debug information, please let me know.

i'm new to ubuntu but have totally (and bravely) taken windows off my laptop so there's no turning back now. 
i am slowly making things work properly but....

seagate freeagent 320g drive was accessible and i was able to write to it but now it mounts but just comes up with a file saying "lost+found" . i messed about with gparted (not knowing what the hell i was doing) for a bit but still no joy. perhaps that's where the problem is.

all my stuff is on there. i can't go back to windows.

please help!

---

### Post by coffeecat on 2009-12-07
> **willybanjo said:**
> now it mounts but just comes up with a file saying "lost+found"

A lost+found folder means that it is formatted ext3 or ext4 - these are Linux filesystems. There is no way that Seagate would ship a USB drive formatted ext3/4, so you must have reformatted it.

> **willybanjo said:**
>  . i messed about with gparted (not knowing what the hell i was doing)

Is this when you reformatted it?

> **willybanjo said:**
> all my stuff is on there. i can't go back to windows.

please help!

First thing - do not try to write to the drive. There are ways of rescuing data from reformatted drives but none are easy. Perhaps you'd better explain exactly what you did.

---

