---
title: "XFS - Is it safe?"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by ozonehole on 2009-05-13
Hi All,

I've gotten interested in using a filesystem besides ext3 because of its "latency problem" (ie Firefox freezes, for example). For info on the latency problem in ext3, please take a look here:


> 
The problem, in short, is this: the ext3 filesystem, when running in the default data=ordered mode, can exhibit lengthy stalls when some process calls fsync() to flush data to disk. This issue most famously manifested itself as the much-lamented Firefox system-freeze problem, but it goes beyond just Firefox. Anytime there is reasonably heavy I/O going on, an fsync() call can bring everything to a halt for several seconds. Some stalls on the order of minutes have been reported.

[http://lwn.net/Articles/328363/](http://lwn.net/Articles/328363/)


I know about ext4. It's fast, but there are complaints that it's possible to lose data if you experience a system crash (such as losing electrical power).

I have heard that xfs had the problem with losing data too, but one poster (on osnews.com) said that this problem had been fixed. Doing some googling, I'm not finding any reliable info. The  [wikipedia page for xfs](http://en.wikipedia.org/wiki/XFS) says *Failure-handling policies can be improved* and then provides a [link to a pdf file](http://pages.cs.wisc.edu/~vshree/xfs.pdf) that goes into detail, outlining how xfs can lose data. But that pdf file may be way out of date.

So I really don't know if xfs is safe or not. I'd appreciate any info on this.

The Firefox freezing problem really is serious. I'm often forced to shut Firefox down by first running "*ps aux | grep firefox*" to find Firefox's process number, and then running "*kill -9 PROCESS_NUMBER*" and then restarting Firefox and hoping it doesn't freeze again.

I am currently dealing with this problem by running Chromium as my browser of choice. Chromium is alpha software, but does 95% of what I need. It's big limitation is bookmarks, which don't work yet - I deal with his by doing my bookmarks in Firefox, and cutting&pasting the url into Chromium when I need to. If you want to try chromium:

[http://www.stefanoforenza.com/chromium-on-ubuntu-how-to](http://www.stefanoforenza.com/chromium-on-ubuntu-how-to)

Since my data is valuable, I'd consider formatting my /home partition as ext3 and have the rest of the system  in ext4 or xfs. However, I wonder if that will solve the latency problem.

I'd appreciate any comments on xfs.

Thanks in advance,
Oz

---

