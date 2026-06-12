---
title: "Live CD can't mount itself"
date: 2006-01-16
forum: Hardware &amp; Laptops
---

### Post by Qwertie on 2006-01-16
I'm trying to use a live CD to extract data from a Windows partition that won't start due to registry corruption (apparently).  I have no reason to believe anything else is wrong with the system (it was working fine when I shut it off 36 hours ago).

Depending on how my drives are set up, one of two things happen, after it asks me about my language, country and keyboard:
(1) CD drive is primary master: After a productive-looking hardware detection process, Kubuntu says "No common CD-ROM drive is detected".
(2) CD drive is tertiary master (there's no secondary on my motherboard, apparently): Kubuntu freezes at a textless screen for a couple minutes and gives an error about being unable to mount the CD (I don't recall the exact message).

I've also tried DSL and Knoppix, which both fail much less gracefully.

Kubuntu gives a nice 'tmpfs'-rooted shell which I perhaps could use to investigate the problem if I knew how.

My questions are:
- What's wrong? What can I do to find or fix the problem?
- Kubuntu seems to get pretty far before failing.  How it is that so much can be loaded from a CD drive that is supposedly undetectable?

My computer is a one-year-old P4 3GHz on an Asus P5GD1-VM mobo.

---

### Post by Qwertie on 2006-01-16
Update! I realized that for a split second before the graphical boot screen appears, there is a warning message that appears on the screen first.  Luckily, the pause key worked and I caught the message:

IOLINUX 2.04 2003-06-16 isolinux: Loading spec packet failed, trying to wing it...
isolinux: Extremely broken BIOS detected, last ditch attempt with drive = EF
 Copyright (C) 1994-2003 H. Peter Anvin

Now does anybody have any more ideas for mounting this bastard?

---

