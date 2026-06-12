---
title: "Hard disk issue when exiting Feisty."
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by TmP on 2007-04-21
Hey!

Overall I like Feisty pretty much, but some things bother me:

When I try to turn off my laptop, first everything goes fine, untill the Linux suddenly stops my hard disk.

Its like it is applying a hand brake to stop it immediately - and a large audiable CLICK can be heard...

Now you might say I'm over sensitive, but my oil-bearing disk does not even make the slightest sound whan I'm using it and the CLICK does not happen when exiting Windows ( It's a dual boot) - it just winds out untill it stops. Also, my last laptop disk failure left me having to use a LiveCD untill i could afford a new HDD.

I assume it's something like a "park disk" command as was used in the times of DOS. 

I want it out of my Ubuntu!

---

### Post by kripkenstein on 2007-04-21
I did a bug search, and yes, this is indeed a current bug in Feisty. You can look here at the details, see how they are progressing in fixing it, etc.:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810")

What is important is that this bug is confirmed in the upstream, that is, the Linux kernel people confirmed that this is indeed a bug in the Linux kernel. They take these things very seriously, so hopefully this won't remain an open bug for long.

Reading the comments, there seems to be a 'hackish' solution, posted by one Martin Koßler. If you are adventurous you can try to do that. Otherwise, it seems they are progressing on a fix, so it might be out soon.

---

### Post by TmP on 2007-04-21
There seems to be a big discussion going on about this problem:
_[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810)_
including a workaround which I have yet to test. Also, sb is reassuring that stopping the disk is ok.
Somehow I am not convinced. If Toshiba wanted my disk stopped it would include it into the windows drivers.

[http://bugzilla.kernel.org/show_bug.cgi?id=7674](http://bugzilla.kernel.org/show_bug.cgi?id=7674)

This bug is recognised in Lounchpad: Bug #67810 in linux-source-2.6.20 (Ubuntu)

---

### Post by TmP on 2007-04-21
Thanx Kripkenstein!
You confirm my research. I am a bit sensitive to this stuff as my HDD died some time ago (I dont blame Ubuntu though - i blame Toshiba)  and I lost lots of stuff.

---

