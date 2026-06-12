---
title: "Mounting a Kingston Data Traveller"
date: 2005-08-28
forum: Hardware &amp; Laptops
---

### Post by Cervantes on 2005-08-28
Hi all.  Mayhaps someone remembers I posted a problem a long time ago about mounting a USB key.  I've still got the same problem, though I've made some progress on it.  I've discovered that the problem originates from the usb key itself.  My Dad's **Verbatim** usb key works terrifically when I plug it in, though my **Kingston Data Traveller** does not.  

When I try to mount it, it replies that I've got the wrong fs type, bad superblocks, or too many mounted filesystems (which I don't).  Then it asks me if I'm trying to mount an external filesystem, rather than some internal logical partition", or something like that.

I've fiddled around with it.  I've tried changing the filesystem on it, like so:
```
sudo mkfs.vfat /dev/sda1
```
To which the terminal spits back something about "I will not do it".  (Dual boot going here, as I haven't gotten internet working yet for ubuntu.)

I've also tried formatting it as ext3:
```
sudo mkfs.ext3 /dev/sda1
```
It seemed that sort of worked, as I could then mount it, though I couldn't access it.  Also, windows wouldn't read that, and I need to windows to be able to read my usb key.  

(As a small aside, it seems I lost 10 mb of space on my usb key when ubuntu formatted it.  I suppose I could use any partition program I like to get it back, though I'm wondering if there's one that comes with ubuntu.)

Would anyone be so kind as to give me a step-by-step guide as to how to fix this problem?  I'm quite new to linux, so don't expect that I know very much.   ;-) 

Thanks for your time!
Cervantes

---

### Post by A-star on 2005-09-06
maybe this can help you?
[http://www.kingston.com/support/faqs/datatraveler/faq_dt2plus_1.asp](http://www.kingston.com/support/faqs/datatraveler/faq_dt2plus_1.asp)

---

### Post by oldHat on 2007-04-28
> **A-star said:**
> maybe this can help you?
[http://www.kingston.com/support/faqs/datatraveler/faq_dt2plus_1.asp](http://www.kingston.com/support/faqs/datatraveler/faq_dt2plus_1.asp)

I was having similar problems with a 4GB Kingston Traveller: readonly filesystem and writing past the end of the device.

The only part of this FAQ that helped me was the suggestion to reformat the drive with mkfs.vfat.  I used mkfs.vfat -F32 -n someLabel /dev/sdX1

This seems to have solved my initial problems.  It now automounts in a usable state.  I can write to it an and read from it.

However, there are still problems.  It unmounts when I work it hard.  This is probably a separate issue.  (Hmm, is it bad to stuff 4000 files into a vfat directory?).

---

### Post by p_quarles on 2007-05-04
I had the same problem with a 2 GB Data Traveler (i.e., read-only in linux, couldn't change the permissions; plus it had a bunch of junk files already present). The Kingston FAQ didn't help me, since I'm not yet confident in my ability to translate instructions for a root user to a sudo configuration. 

In any case, I'm a linux newbie and still kind of scared of the command line (particularly for formatting a drive). So: I booted Windows and formatted the drive from there. It now works fine in both Windows and Feisty. Hopefully this will be helpful to the other newbies out there.

---

### Post by oldHat on 2007-05-07
> **oldHat said:**
> I was having similar problems with a 4GB Kingston Traveller: readonly filesystem and writing past the end of the device.

The only part of this FAQ that helped me was the suggestion to reformat the drive with mkfs.vfat.  I used mkfs.vfat -F32 -n someLabel /dev/sdX1

This seems to have solved my initial problems.  It now automounts in a usable state.  I can write to it an and read from it.

However, there are still problems.  It unmounts when I work it hard.  This is probably a separate issue.  (Hmm, is it bad to stuff 4000 files into a vfat directory?).


Hehe, when I tried it on a windows system, it filled up after 2GB.  I reformatted yet again with Windows, and now it seems fine.

---

