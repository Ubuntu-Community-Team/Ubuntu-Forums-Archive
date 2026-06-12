---
title: "Help with networking?"
date: 2008-08-10
forum: Hardware
---

### Post by cankillar on 2008-08-10
I just picked up a Vista equipped Acer Extensa 5620z, the specs of which can be found _[here]("http://us.acer.com/public/page133.do?link=oln55.redirect&dau321.oid=30778&UserCtxParam=0&GroupCtxParam=0&dctx1=25&CountryISOCtxParam=US&LanguageISOCtxParam=en&ctx3=-1&ctx4=United+States&crc=799208601")_.  I installed Hardy Heron on a partition on one of the hdd's, using 8gigs for "/" and 19 for "/home/", with 521 b for swap space.

The wired connection doesn't work and neither does the the wireless.  I tried _[this tutorial]("http://ubuntuforums.org/showthread.php?t=868841")_ on the forum.  But it assumes your wired connection is working, and mine most decidedly isn't.  Everything works on the vista side, but not on ubuntu.

If it appears there is something wrong with my laptop and ubuntu can't fix it with less than 3 hours of work, I think I'm just going to give up and format over my partitions. :\

---

### Post by niccholaspage on 2008-08-10
This happens with almost ALL Windows laptop users.Wireless won't work.
I don't know about wired,But to get wireless working you need to do a search on your Network driver in Vista,And download a .inf file.
Then you can install ndisgtk via sudo apt-get install ndisgtk in a terminal.
After you do that,go to System>Administration>Windows Wireless Drivers and click Install New Driver and select your .inf file.

---

### Post by cariboo on 2008-08-10
We need to know what chipsets your network devices use. To find out in a Applications-->Accessories-->Terminal type:

```
lspci >lspci.txt
```

This will create a text file called lspci in your home directory. Copy it to your documents directory on your Vista partitionand attach in your nest post.

One other question, did you try networking with the LiveCD?

Jim

---

