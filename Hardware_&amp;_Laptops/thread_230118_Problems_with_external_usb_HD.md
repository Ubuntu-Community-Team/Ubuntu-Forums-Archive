---
title: "Problems with external usb HD"
date: 2006-08-05
forum: Hardware &amp; Laptops
---

### Post by aracon on 2006-08-05
Hi everyone.

I'm just new to ubuntu, been running Dapper less than 2 months. Last week I purchased an external usb case + HD (outex 3,5" usb case + maxtor sata 300 gb disc) so i can store my files there. It was fine until it begun to corrupt filesystem, at such rate today i'd to reinstall ubuntu. 

The problem is that when i was using the disc other hd randomly became read-only, and that screwed my running programs. I have (in my pc) 2 sata disc (of 120g each), running 3 jfs partitions: one for /, one for /home and one for random data/utils (mounted at /media/p2p). As a result of the locks on read-only (as an example) this morning /home became corrupted and "dissapeared" (i'm so thankful to jfs for recovering my files later :o ).

I've read that i can solve that read-only issue changing fstab (and so i've done) to errors=continue. My 2 questions are:

- 1) I've read that with this change when i have an error the system will mark filesystem as erroneus and go on without locking on read-only. This will be solved after a reset (filesystem error, i mean) or it can have a "bad behaviour" and broke my system? Can that be a solution? Or a bad one?

- 2) Anyone has had a problem like this and can help me?

- Bonus question: When i connect external HD dmesg|tail shows:

[17182901.848000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17182901.852000] SCSI device sdc: 586114704 512-byte hdwr sectors (300091 MB)
[17182901.852000] sdc: assuming drive cache: write through
[17182901.852000] SCSI device sdc: 586114704 512-byte hdwr sectors (300091 MB)
[17182901.852000] sdc: assuming drive cache: write through
[17182901.852000]  sdc: sdc1
[17182901.876000] sd 4:0:0:0: Attached scsi disk sdc
[17182901.876000] sd 4:0:0:0: Attached scsi generic sg2 type 0
[17182901.884000] usb-storage: device scan complete
**[17182903.208000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!**

How can i change charset of hd to avoid that last message? And to which charset must i change?

Thanks for reading and answering :)

---

