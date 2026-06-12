---
title: "Operate remote device as if local?"
date: 2008-02-22
forum: Hardware &amp; Laptops
---

### Post by Mortie on 2008-02-22
Hi there, a slight problem.

I have a local system (L) running Ubuntu 7.10  and a remote system (R) running a rather minimal Debian 4.0r3 intallation (in my closet and local network, so not allt that very remote though).  :)  The R system has a serial port (/dev/ttyS0) which I would like to "mount" (or equivalent) on my L system. The intention is that my L system (after doing the "mount" or whatever thing) should then be able to use the remote device (ttyS0) as if it was a local one.

I have been doing a somewhat extensive googling on the subject, and the best I could find was this ([http://lkml.org/lkml/1997/2/22/60]("LKML: mdean: Remote Device Control Under Linux")) thread over at LKML. 

*mdean* appears to have had the same approach that I first had: sharing the device over NFS on my R system and mounting it on my L system. This, however, turned out not to be working very well, so now I turn to the forum for help and ideas :)

To be honest I quite didn't understand Alan Cox' answer, can anyone help me with that?

Is it possible to do something like "mounting" a remote device on a local system and use as if local?

Thanks in advance, the Ubuntu forums are great :)

Martin

---

