---
title: "Need help making software PATA RAID an extra drive across OSs"
date: 2006-07-19
forum: Hardware &amp; Laptops
---

### Post by mrwilloby on 2006-07-19
So after going through a couple of PATA RAID cards I think I've found that the cheap ones (I'm not willing to spend a lot of money on this old extra system) are all fake RAID cards, as in not true hardware RAID controllers.  I think it will be OK if someone can help me answer a few questions or even help with a solution.

What I want to know is if this 'dmraid' I've read about will allow me to use data on the array in multiple Linux distros and in Windows.  I'm not trying to boot from it even.

My drives are like this, all IDE.

12GB- Half Windows NTFS, ~Half Xubuntu + swap (hda1, hda2, hda5)
40GB- hoped for part of RAID0 array, ext3
40GB- hoped for part of RAID0 array, ext3

I've left my 12GB drive on the Primary IDE controller on the MB along with an IDE CD-RW.  I've tried to put the 40GB drives on the add-on card on the secondary channel as cable select drives.

When running the Xubuntu setup in Text Mode to just see what it sees, the drives are labeled hdc, hdd, hde with the last being the 12GB (it should be hda).  I've already installed Xubuntu without the card plugged in but I don't care if I have to wipe it.  When I plug the card back in, Xubuntu hangs when "Waiting for root filesystem".

So, can I use this dmraid to get my array correct and usable in Windows as well?  I would rather not wipe the Windows partition to get this working, but I suppose I would if it's the only solution.  Nothing else on any hard drive matters either.

How does installing with dmraid work?  The fakeRAID howto seems to talk about installing to it too much for my needs.

Thanks so much to anyone with any solutions.

---

