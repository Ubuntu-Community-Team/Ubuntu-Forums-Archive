---
title: "HDD cannot be mounted"
date: 2008-01-06
forum: Hardware &amp; Laptops
---

### Post by ferus on 2008-01-06
Hi, 

recently I installed Kubuntu 7.10 on my desktop and I came across a problem. The installation went fine, the system works.
However, after I connected my other HDD (NTFS with WinXP) this HDD can't be mounted.
Anytime I try to mount it I get the message:

hal-storage-fixed-mount-all-options refused uid 1000

I presume this question was asked many times but the search didn't give me any specific results.
Can anyone here help me?

PS: I did ask also on [www.kubuntuforum,com](www.kubuntuforum,com) but I didn't receive any reply yet and I need my other HDD to work asap.

Thanks in advance.

---

### Post by metalpancake on 2008-01-06
I think Gparted (available in repos) could help you. I have never used it, so I don't know.

---

### Post by vanadium on 2008-01-06
One reason might be that the ntfs file system is not clean. You should check your ntfs filesystem (preferably do that from within Windows. Make sure that you properly disconnect the drive in windows, of completely shut down Windows before disconnecting the drive, i.e. no hibernation, but full shut down.).

---

