---
title: "HD trouble"
date: 2006-10-31
forum: Hardware &amp; Laptops
---

### Post by jimtb on 2006-10-31
From the time I installed Dapper, I was having some occasional system crashes and I wasnt able to do anything but reset the PC. After a problem I had with OpenOffice.org, which crashes my system every time when I try to launch it and after a while with dpkg, I understood that something was wrong. The kernel logs are full with these three messages:

```
Oct 31 23:08:06 jimakos-desktop kernel: [17180014.968000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Oct 31 23:08:06 jimakos-desktop kernel: [17180014.968000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Oct 31 23:08:06 jimakos-desktop kernel: [17180014.968000] ide: failed opcode was: unknown
```

So...I'm sure it is the hard drive causing all the problems, after I managed to reproduce the crash many times with various different ways. What exactly is going wrong here? Is there anything I can do to fix it?

PS. XP on the same Disk dont seem to have any problem.

---

### Post by jobou on 2006-11-12
I have the same problem. I spent the day trying to install ubuntu and seeing it freezing until i run it without the flash screen.  Then i saw it was freezing on that hda dma error. I took out the drive ( were xp was installed) and ubuntu started perfectly.
For me two xp work fine on that drive.
Could someone tell me if I should dump the hd  ??

Thanks

---

### Post by scrooge_74 on 2006-11-12
I had a similar kind of problem with the first release of Dapper, are you using the latest Dapper ISO?

---

