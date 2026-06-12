---
title: "Seagate external HDD totally freezes gutsy when writing"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by davyike on 2008-01-10
Hi all,
I have looked in a lot of places for someone with the same problem as me, but nothing so far. I have a Seagate FreeAgent Pro 750GB external HDD, connected via eSATA, running Gutsy. Originally the HDD was NTFS, which mostly worked fine - I could read anything, and write small amounts of data, but writing larger amounts than about 100MB seemed to totally lock up the system, requiring a hard reboot. I thought it may have been the NTFS, so moved everything off it, and went to format it as ext3 - but everything locked up again when starting the format. So it seems to be unrelated to the file system, I'm not sure what to try next. Any tips would be great.

Cheers

---

### Post by torac on 2008-01-10
Maybe there is a problem with eSATA. I have several external HDDs connected via USB and they all work without any problems... I don't have eSATA in my computer so I have no experience with that.

---

### Post by kvonb on 2008-01-10
-

---

### Post by davyike on 2008-02-02
It seems to be the eSATA by the way - only when writing larger files. Small changes are ok. What I'm doing now is using eSATA most of the time, if I only need to read the disk (it's mostly for backups). Then if I need to write to it I either switch to Windows or use the USB interface instead. Unfortunately doesn't solve the original problem but couldn't find any further info.

---

### Post by davyike on 2008-02-02
Just thought - eSATA is just regular SATA with an external cable... and it doesn't happen to my internal SATA drives, so maybe it's just the drive itself? But then it doesn't lock using USB. Possibly a combination of the two causes the electron gremlins inside the computer to get upset and refuse to work. Damn gremlins...

---

### Post by torac on 2008-02-04
Yep, I agree. It's the gremlins fault :)

---

