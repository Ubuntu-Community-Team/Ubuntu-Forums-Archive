---
title: "How to get back the memtest86+ grub boot menu option?"
date: 2018-02-25
forum: Hardware
---

### Post by xucaen on 2018-02-25
This questions is in 2 parts:

1) I had installed Ubuntu years ago, maybe in 2011 or 2012... and it had a memtest86+ boot menu option in grub. I recently installed Ubuntu 17.10 and there is no memtest86+ boot option. I checked and I do have memtest86+ installed. How do I get the boot option to appear? Yes I know there is a memtest86+ boot CD and I already have that but I want the convenience of having it in a GURB boot menu option like I used to have years ago.

2) Is there some way to also get a check disk boot menu option along with the memtest86+ boot menu option? I would like to check the hard disk in addition to the memory. If the only way to do this is with a boot CD, can someone please recommend an easy to install CD image along with instructions? Though I would prefer ubuntu do the check disk.

---

### Post by ajgreeny on 2018-02-25
Is your computer using UEFI?
Memtest86+ will not work and therefore does not show on a UEFI system, though I believe there is another memtest you can use instead.

You need to download and run the version from [http://www.memtest86.com/](http://www.memtest86.com/) which I understand works on UEFI systems, though I have never used it.

---

### Post by xucaen on 2018-02-25
I never even heard of uefi before 2 weeks ago. I was forced to turn it off in the bios because windows wouldn't boot after installing ubuntu. The computer I installed ubuntu on back in 2011 was very old - 2001 I think - and I am 99.99% certain it did not have uefi.

---

### Post by ajgreeny on 2018-02-26
In that case I am not sure why memtest86+ is not shown in your grub menu; I think it should be there.

---

