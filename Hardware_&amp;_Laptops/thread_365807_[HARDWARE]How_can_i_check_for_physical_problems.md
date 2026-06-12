---
title: "[HARDWARE]How can i check for physical problems?"
date: 2007-02-20
forum: Hardware &amp; Laptops
---

### Post by eskimo on 2007-02-20
Hi!! i have a 120Gb internal IDE Hard Disk (maxtor) that had serious problems. MY ubuntu edgy used to boot once every ten or twenty tryes and i found the reason when on booting a message say to me: hei! fsck exited wrong! try fsck with hands... 

So i reinstalled ubuntu but problems with my home partition are still there!
The disk has 1 primary partition with windows (hda1 20gb) and and 5 logical ones:
hda5   /   7gb
hda6   swap 1gb
hda7   fat32  10gb
hda8   home (ext3 80gb)


when i reinstalled ubuntu i've only formatted all logical partitions, do you think i have to try to  "reset" the hd or they are physical errors???

**reset: i say reset to say when you re-do all partitions, so you have to rewrite partition table. Or if you do:     dd if=/dev/zero  of=/dev/hda



bye!!! Paolo

Thanks

---

### Post by Jussi Kukkonen on 2007-02-20
> MY ubuntu edgy used to boot once every ten or twenty tryes and i found the reason when on booting a message say to me: hei! fsck exited wrong! try fsck with hands...

So i reinstalled ubuntu but problems with my home partition are still there!
Did you try the suggested fsck?

---

### Post by eskimo on 2007-02-20
I tried the first time i saw problems: and the result was a long list of questions about error found.... 
so i reinstalled
and when i saw the error i retried fsck.... and another time questions:

error, ignore<y>?
re-write<y>?

clear<y>?



do i have to runh fsck -an   ????

---

### Post by Jussi Kukkonen on 2007-02-20
That's what I'd try.If it doesn't work, I don't have other ideas than reformatting (as in running mkfs on hda8)...

---

