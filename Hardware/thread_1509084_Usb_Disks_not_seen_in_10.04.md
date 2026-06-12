---
title: "Usb Disks not seen in 10.04"
date: 2010-06-13
forum: Hardware
---

### Post by dlgehrt on 2010-06-13
I just got my laptop back from a repair, update Ubuntu swapped in my internal drive with 10.04 on it and now none of my USB rotating disk drives show up any where.  To complete this bizarre situation, I plugged in a flash drive and it was recognized and a file browser window opened to display its contents.

An afternoon searching has turned up no help. I am pretty much at my wit's end. 

Does anybody KNOW what is going on here?!?

dlgehrtI just got my laptop back from a repair, update Ubuntu swapped in my internal drive with 10.04 on it and now none of my USB rotating disk drives show up any where.  To complete this bizarre situation, I plugged in a flash drive and it was recognized and a file browser window opened to display its contents.

An afternoon searching has turned up no help. 

Does anybody KNOW what is going on here?!?

---

### Post by hsoulen on 2010-06-14
> **dlgehrt said:**
> I just got my laptop back from a repair, update Ubuntu swapped in my internal drive with 10.04 on it and now none of my USB rotating disk drives show up any where.  To complete this bizarre situation, I plugged in a flash drive and it was recognized and a file browser window opened to display its contents.

An afternoon searching has turned up no help. I am pretty much at my wit's end. 

Does anybody KNOW what is going on here?!?

dlgehrtI just got my laptop back from a repair, update Ubuntu swapped in my internal drive with 10.04 on it and now none of my USB rotating disk drives show up any where.  To complete this bizarre situation, I plugged in a flash drive and it was recognized and a file browser window opened to display its contents.

An afternoon searching has turned up no help. 

Does anybody KNOW what is going on here?!?

Hi,

Need a bit more info.

What do you mean by "USB rotating disk drives", and when you say "update Ubuntu swapped in my internal drive with 10.04 on it" what exactly do you mean?

Cheers,

Hank

---

### Post by dlgehrt on 2010-06-14
> **hsoulen said:**
> Hi,

Need a bit more info.

What do you mean by "USB rotating disk drives", and when you say "update Ubuntu swapped in my internal drive with 10.04 on it" what exactly do you mean?

Cheers,

Hank

Thanx for the response.  I am really baffled by this problem.I didn't mean to be obtuse, just brief describing my problem.

The "swap" refers to replacing a spare drive about whose contents I do not care that I installed in the laptop when I sent the laptop in for  a repair.  When it was returned I put my regular drive back in the laptop.  I then ran an update, and started to have this problem with the USB bus. (I didn't see anything in the update that I thought might be problematic before performing it.)

By  "rotating drive" I meant as opposed to flash drives to which most of the posts about USB problems seemed to refer.    I tried a flash drive (a SansDisk Cruzer) to make sure it was not recognized, and it was mounted, raising my confusion level about this problem to new heights. 

Just to furnish  all that I know about this problem:  I have tried  two different USB drives.  A 1 TB Seagate and a 500 GB Western Digital, neither was recognized

dlg

---

### Post by dlgehrt on 2010-06-14
After additional web searches I am beginning to think that my problem is actually the result of the kernel up grade from 2.6.22.33 to 2.6.22.36  at ~0400 on 2010/6/11.  I have sen many posts referring to problems with kernel version 2.6.22.36.  Research continues.

dlg

---

### Post by dlgehrt on 2010-06-14
Well I feel more than slightly stupid.  This morning fired up an old laptop that had not been updated for over a month.  [It has been running the chicken cam.] I tried a third external drive and when this system couldn't mount the disks, nor could a Windows system, I began to suspect the cable which had been known to be good a couple of days ago.  It turned out that the USB cable I was using went only partially bad.  Power was transmitted, but not data. When I tried another cable  it was completely dead. I hauled out a third USB cable used and now all remote disk are accessible.

It now occurs to me that I should have been more suspicious when flash drives were accessed OK and the external drives on a an USB cable were not.

Such is life!

dlg

---

### Post by hsoulen on 2010-06-15
> **dlgehrt said:**
> Well I feel more than slightly stupid.  This morning fired up an old laptop that had not been updated for over a month.  [It has been running the chicken cam.] I tried a third external drive and when this system couldn't mount the disks, nor could a Windows system, I began to suspect the cable which had been known to be good a couple of days ago.  It turned out that the USB cable I was using went only partially bad.  Power was transmitted, but not data. When I tried another cable  it was completely dead. I hauled out a third USB cable used and now all remote disk are accessible.

It now occurs to me that I should have been more suspicious when flash drives were accessed OK and the external drives on a an USB cable were not.

Such is life!

dlg

Awesome! Thanks for following up on this, glad to hear it was a "low-tech" problem I was doing a bit of research for you when I saw your response.

Cheers,

Hank

---

