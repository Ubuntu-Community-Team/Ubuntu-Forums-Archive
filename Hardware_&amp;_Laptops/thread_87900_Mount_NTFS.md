---
title: "Mount NTFS"
date: 2005-11-09
forum: Hardware &amp; Laptops
---

### Post by buhuuuhh on 2005-11-09
Hi,

I have a problem mounting my NTFS File System in Breezy. It is a harddisk
divided into 2 partitions (c/g). It worked perfectly with warty/hoary but now
something strange happens.

if i mount c it works. if i mount g with the same command, g is mounted
as well, no problems so far.

command:
mount -t ntfs -o uid=andreasb /dev/hda5 /mnt/windows/g
my notebook is a FSC AMILO 7400

but if i try to access g now in /mnt/windows/g/ at console my desktop always
freezes for a few seconds. work-freeze-work-freeze-> and so on. 
if i try to access by file browser, the browser always freezes for a few seconds.

Does anyone of you have suggestions how to solve this issue?

Greetz and thx in advance,
Andreas

---

### Post by majed on 2005-11-09
Here is the link from Ubuntu Help:

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-windows-partitions]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#fg-windows-partitions")

Good luck.. works fine here.. i'm doing both NTFS and FAT32..

---

### Post by buhuuuhh on 2005-11-09
Thx for your answer... the problem is I already mounted it, and it does not
work properly. 

When its mounted the desktop always freezes for some
seconds periodically, when i access it. again and again. So I can access the
data, but the freezing is definetly not good. I can not imagine what it could 
be, cause it worked fine in warty/hoary.

Greetz, 
Andreas

---

