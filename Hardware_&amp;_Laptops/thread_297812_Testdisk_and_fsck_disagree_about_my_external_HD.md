---
title: "Testdisk and fsck disagree about my external HD"
date: 2006-11-11
forum: Hardware &amp; Laptops
---

### Post by robenroute on 2006-11-11
Hi there,

I'm having problems mounting my harddisk (partition). I've let testdisk have a go at the partition (Analyze, Write FAT, Write MBR, etc.) and according to testdisk everything is hunky-dory now. Then, when I start the following command:

fsck -t vfat /dev/sdb1

fsck says it has to give up because of corrupted FAT. What's going on? How can fsck report corruption where testdisk says it's okay? The whole thing is definitely not okay, because I still can't mount my partition. I'm somewhat flustered.... Anyone?

Thanks a lot, Rob

---

### Post by robenroute on 2006-11-12
Anyone who can shed some light into my harddisk darkness?

Cheers, Rob

---

### Post by ncc74656m on 2006-11-12
Long shot, but could you try booting with another distro (Knoppix) and reading or formatting it from there?

---

### Post by robenroute on 2006-11-26
Hi there. Just got back from hols. So, I've tried other live CDs (Knoppix & old Mepis) and the problem remains.

What I suspect is happening is the following: (correct me if I'm wrong, please) files are stored in chuncks on the HD and each chunck has a pointer to the next chunck (at least it worked like that when I was doing my Comp. Sc. studies a fewyears ago). The FAT only contains a pointer mapping of the first chuncks of each file/directory, so testdisk can read and write the FAT correctly. However, if the pointer to the second chunck (in the first one) is missing (file corruption, virus?), fsck would fail, since it checks the whole chain of chuncks for each and every file. If this indeed is the case, the error message from fsck is a wee bit obfuscating....

Can anyone confirm my line of thought? Thanks.

Rob

---

