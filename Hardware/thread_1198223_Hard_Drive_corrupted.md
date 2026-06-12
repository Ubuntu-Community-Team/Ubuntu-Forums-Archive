---
title: "Hard Drive corrupted"
date: 2009-06-27
forum: Hardware
---

### Post by comradejanus on 2009-06-27
I understand this is not strictly a ubuntu or even linux question but it was caused by an attempt to install the operating system, and also i'm sure the people here will have a solution.

It all started when I was trying to install Ubuntu 9.10 onto a 60GB Pata hard disk. It was about half way though, but then either my computer crashed or the power went off I cant remember.

Since then whenever I try to boot a computer with that hard disk attached to the live CD I get a message that reads "buffer I/0 error on device, logical block X" with X being a number ranging from 1 up to 46 or something.

When the Live CD eventually boots , if I click 'Install Ubuntu' the partition editor eventually comes on with a message saying that there are no devices attached.

I've also tried using GParted but that programme also fails to boot, and shows similar errors.

My question is, is there any way to rescue this hard disk? Or is it completely useless now?

Many thanks.

---

### Post by milton1 on 2009-06-27
sounds like your hard disk may have kicked. try disconnecting it, then boot from the live CD to see if you still have trouble. If it boots fine, then you have confirmed the bad disk. Try reattaching it, and reformatting it with the live CD, or Parted Magic. If it still does not work, well... hard disks are cheap.

---

### Post by comradejanus on 2009-06-27
Yea, I neglected to say that the computer boots up fine with anouther hard disk that I have.

I've tried booting using GParted and the ubuntu live CD, but the partition editor just gives a message saying that It can detect no disks.

I need some kind of way to format it without booting into anything (like bios level, if that makes any sense).

But thanks for your help.

---

### Post by milton1 on 2009-06-27
Really sounds like the drive is toast. As a last, desperate attempt, and if you have the hardware, you could try plugging the trouble drive into a healthy system as a secondary/slave, and see if you can mount and reformat it. Failing that, take a hammer to the old drive to vent your frustrations and secure any old data, and go buy a new one.

---

