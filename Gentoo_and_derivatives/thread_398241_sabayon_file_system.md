---
title: "sabayon file system"
date: 2007-03-31
forum: Gentoo and derivatives
---

### Post by tchoklat on 2007-03-31
Hello,
 
Have a new PC with a G/B SLI mobo that I cannot get any version of Ubuntu to operate on with even with the 'noapic' boot option. 6.06 Live runs but will not install, 6.10 and 7.04b do not run as live. So I uinstalled Sabayon 3.25 (wauingf for th 3.3 DVD tro arrive.
 
I have a problem. When I load GPartEd it sees all partitions but says the Sabayon partition is an unknown file format and I cannot resize it or do anything to it. Any ideas? I want to shrink it to create another partition.
 
tnoy

---

### Post by zaratustra on 2007-04-01
I think that sabayon makes an LVM's or something called similar :P I don't know is parted able to handle these, but they are made to make shrinking easier

---

### Post by igknighted on 2007-04-01
> **zaratustra said:**
> I think that sabayon makes an LVM's or something called similar :P I don't know is parted able to handle these, but they are made to make shrinking easier

Yeah, LVM is standard.   Use a Fedora disk or the Sabayon disk when you get it to do the partitions.  I would recommend (a) doing a manual partition to avoid LVM unless you know what it is and why you want it, and (b) Don't use the DVD, save yourself about 8 hours, tons of bandwidth, and a lot of headaches and frustration later and get the 3.3 mini edition.

---

