---
title: "Blu-ray Drive Support in Interpid Ibex ?"
date: 2008-10-15
forum: Hardware
---

### Post by BMWDriver on 2008-10-15
I can't currently mount the BD drive when inserting a Blu-ray disc. However, no problems arise with a DVD or CD inserted.

I've followed the link [here]("https://help.ubuntu.com/community/RestrictedFormats/BluRayAndHDDVD") and tried to patch the kernel to support [UDF 2.5]("http://sourceforge.net/tracker/?group_id=295&atid=300295") following the instructions, but unfortunately, the command returns the error:

[COLOR="DarkRed"]can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- linux-2.6.24/fs/udf/inode.c.orig	2008-01-24 14:58:37.000000000 -0800
|+++ linux-2.6.24/fs/udf/inode.c	2008-01-30 13:39:05.000000000 -0800
--------------------------
[/COLOR]

I was in directory /usr/src/linux-headers-2.6.24-19-generic/ and that could be the wrong place to be.

Other than perhaps wanting a solution to the above, would Ubuntu 8.10 support Blu-ray natively ? Or should I rephrase that and say "support UDF 2.5".

Thanks in advance.

---

### Post by natetheskate on 2008-10-16
Blu-ray support? That would make Ubuntu the only thing you would ever need in life. I am ready to watch some HD Movies :popcorn:

---

### Post by zonyl on 2008-10-26
I thought Linux 2.6.27 (included in Ibex) had udf 2.6 support?  [http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-04/msg08754.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-04/msg08754.html)

Although I am reading from various sources that BlueRay mount still doesnt work in Ibex :(

---

### Post by BMWDriver on 2008-10-27
It's a bit difficult to find precise info on the subject. I wonder also about kernel 2.7 series. It will come sooner or later.

---

### Post by zonyl on 2008-10-29
I cannot believe the dearth of information on this topic.  Sadly even if the drive mounts a BD disc, I am not confident ill be able to decrypt/play anything with DumpHD.   Thats where I hit a dead-end last time with the UDF patch in Gutsy/Hardy.

---

I just installed Ibex RC on my media machine at home.  The Lite-On BD drive is at least recognized and mounted / played a DVD which is a good start. 

When I get home tonight Ill throw a BD disc in it, see if it can mount, and get a definitive answer for us once and for all.

---

### Post by zonyl on 2008-10-29
Yes, I am proud to report that BDROM Blue-ray discs CAN be mounted in the stock 8.10 Ibex distribution.  I can see the filesystem on the disc, however, as I suspected there is no magic in playing the encrypted video files.

Also of interest, gnome pops up a dialog asking for a program to play the "Blue-ray Video Disk", of which I know of none to select.

I grabbed the latest DumpHD and am trying to get that working right now.

---

### Post by BMWDriver on 2008-10-29
Excellent news. I shall try it out once it's out of Beta. 

Indeed finding a player that can handle the [AACS]("http://en.wikipedia.org/wiki/Advanced_Access_Content_System") encryption is yet to appear. So far, Cyberlink's PowerDVD, which seems to be the only commercial DVD player available for GNU/Linux based systems, has said to consider supporting the Blu-ray, but nothing yet. Likely they don't see the investment worth it yet.

Makes me wonder how big the GNU/Linux market is. The good news is that many hardware manufacturers are going the GNU/Linux way !

---

