---
title: "System Borked After a Windows Reinstall"
date: 2007-02-15
forum: Hardware &amp; Laptops
---

### Post by arthurbarnhouse on 2007-02-15
I didn't quite know where to put this so excuse me if this is the wrong spot.  

I had two linux distros installed, (one for classes and another for home) Mandriva and Ubuntu, on a logical partition.  However, I ended up needing Windows XP again, so I pulled some space from the Ubuntu distribution and set it up as FAT32 to install XP.  XP refused to install on the partition I set up for it, after numerous formatting efforts.

In addition to this, nothing will load on my computer anymore, when I startup all it gives me is the white on black lettering saying, "Error loading operating system."  As an added bonus, XP won't boot from the CD anymore.  Does anyone have some idea of what I did wrong and if my partitions are salvagable?

---

### Post by goatflyer on 2007-02-15
For starters, why not boot using LiveCD, drop into terminal and post us the output of:

```

fdisk -l

```

As to why you could not install XP on a FAT32 partition, likely candidates are:

- The FAT32 was not first partition.
- The FAT32 partition was too small.

As to whether your data is salvageable, I'd guess yes.  I think you only borked your master boot record.  Search 'reinstall grub' in the forums for hints how to get grub back.

Hope this helps.

---

### Post by towsonu2003 on 2007-02-15
> **goatflyer said:**
> 'reinstall grub'
this link may be helpful for that: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by arthurbarnhouse on 2007-02-15
Ah, it wasn't the first partition, so hopefully that was it.

I don't have a live CD handy (I'm working at my job ATM), so I'll post the fdisk -l result later.

---

### Post by stalkier on 2007-02-15
I have found it easier to install Windows first, then install your other OS's. I know this is a HUGE pain and you would lose a lot of data but it makes it a bit easier. I am sure there is a much easier way. This is just a suggestion.

---

