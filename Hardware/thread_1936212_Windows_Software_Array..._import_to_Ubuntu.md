---
title: "Windows Software Array... import to Ubuntu?"
date: 2012-03-05
forum: Hardware
---

### Post by ericargyle on 2012-03-05
Moving to Ubuntu 11.10 from Windows 7.  It's been several years since I've moved full-time to a debian based consumer OS, so I wanted to ask a question before flipping the switch.

My question is... I have a 3TB NTFS Stripe that is configured as a software array on Windows 7.  This backs up incrementally to a single 3TB drive nightly.

Is there anyway to import this 3TB Stripe array into Ubuntu, or will I have to kill the array and rebuild on Ubuntu, formatted as ext3...  Then copy the backup drive contents to it?  Also, has writing to NTFS drives improved over the years.  Supported natively yet?

I'm comfortable having a ext3 drive array as my primary data drive, but I'd prefer not to have to wipe my NTFS drive in the process.

Thoughts?  Anything else I should be aware of?

Thanks all.

---

### Post by An Sanct on 2012-03-05
NTFS read/write access (WinXP through Win7) is no problem for Ubuntu, I use it all the time (on an unimportant partition) to directly share data between my dual boots (10.10 / Win7)

Ext has also moved forward a bit, to Ext4 (it is backward compatible - tho)

I personally would recommend, that you make a Live USB of your wished distribution and check if you can access the files (read/write/delete - a sample target file, placed there for those purposes)

---

### Post by gordintoronto on 2012-03-05
"I have a 3TB NTFS Stripe that is configured as a software array on Windows 7." I have no idea what that means. Could you explain?

Windows 7 includes a tool to reduce the size of a partition. Then you could install Ubuntu on the space which is freed up.

---

