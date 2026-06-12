---
title: "Does my Windows RAID-1 work properly in my newly installed gOS?"
date: 2008-04-06
forum: Hardware &amp; Laptops
---

### Post by eldudorinio on 2008-04-06
Hello everyone, this is my 1st post here.

I've just installed the Rocket BETA version of gOS. I already have Windows XP as well on the same machine and have no problems with dual booting.

The problem is that when I first installed gOS, before any updates were made, my RAID-1 hard drives were seen separately (I could see 2 hard drives on the desktop). Note down that I have no operating systems on the RAID-1. It is used just for storage. So after installing updates and rebooting the system back to gOS, I could only see one of the two hard drives that belong to my RAID-1. 

I tried to paste a small file in the hard disk, and when I went back to Windows XP the file was there. Does this mean that my RAID-1 works properly in the gOS distro?

Thanks in advance

---

### Post by sdennie on 2008-04-06
It's probably not working right, no.  The Windows software RAID does some Odd Things(TM) to the partition table of the disks and, from what I've seen, linux (or anything not Windows) doesn't know how to deal with it properly.  If you are able to see files written by linux on the disks from Windows, it's not necessarily a good sign.  It sounds like you are writing to just a single disk in the array.  I'm not a RAID expert but, I think that as soon as you start writing to just a single disk, you've invalidated the mirroring of RAID1 until you've "rebuilt" the second disk to match the first.

---

