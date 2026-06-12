---
title: "How can I reduce boot time"
date: 2008-10-16
forum: General Help
---

### Post by DrMega on 2008-10-16
Hi.

I am currently in the process of rebuilding my media PC for nth time. Each time I make a bit more of an effort to get it just right.

How can I reduce boot time?

I know that when booting up, Ubuntu starts all sorts of services, some of which I will never need on my media PC. For example that cupsys print service.

What can I safely strip out and how would I go about doing that?

Cheers.

EDIT: I forgot to mention I'm still using Gutsy (7.10) because Hardy doesn't work on my media PC (random freezes and the odd full blown crash).

---

### Post by Patb on 2008-10-16
Try this [http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

Also look into 'readahead' if you do not have it installed already. 

Cheers, Pat.

---

### Post by kerry_s on 2008-10-16
hibernate

try it, in terminal> sudo s2disk
see what happens.

---

### Post by Yellow Pasque on 2008-10-16
Personally, I always initially remove brltty(I'm a bit near-sighted, but I don't need visual assistance), cupsys (I don't have a printer), bluetooth/bluez* (I don't have bluetooth devices). Disabling the splash screen shaves a few seconds too.

Other optimization guides can be found by trawling the web. If you use the concurrency=shell hack, beware of this bug on Gutsy [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/149881](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/149881)

---

### Post by DrMega on 2008-10-17
Thanks all. I'll try all these suggestions later on after work.

---

### Post by cj2003 on 2008-10-17
You might also learn something from this how-to:

[Improving boot performance of Ubuntu Hardy Heron ]("http://ubuntu-news.net/modules/news/article.php?storyid=5083")

---

### Post by mtausig on 2008-10-17
What I did, to reduce the boot time on my HTPC, was to play a bit with the start priorities. Usually, the display manager gets started at the very end of the boot procedure. I just moved a lot of processes that I actually wanted to use, but which are not neccesary at the start time of the UI (like sshd) toward the end of the boot process. 
This way, you get your screen earlier, but still are able to start everything you want.

---

