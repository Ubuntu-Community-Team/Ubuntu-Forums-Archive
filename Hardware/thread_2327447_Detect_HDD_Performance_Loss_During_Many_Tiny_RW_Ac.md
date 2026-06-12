---
title: "Detect HDD Performance Loss During Many Tiny R/W Accesses"
date: 2016-06-11
forum: Hardware
---

### Post by mikey93898 on 2016-06-11
Hello everyone!

As we all know, one huge problem with hard disks is that when your PC is accessing many small files rapidly, you lose a great deal of performance due to waiting for the needle to seek back and forth; A disk that can read 200MB/s contiguously, can quickly degrade to under 1MB/s.

I've been suspecting this type of thing occurring at my station from time to time, for quite awhile now. It happened back when I was still using windows, it happens now on Ubuntu (although less often). Tonight it happened when I opened up a billion Chromium tabs too quickly. I want to get an SSD to cure the problem, but being a cheap [censored], I'd like to prove this is really what's happening.

So ... my question is: Is there a tool I can use that is specifically designed to detect this type of thing? I have an XFCE4 plugin measuring disk throughput, but it's not measuring seeks-per-second. I have CSF (config server firewall) that I use on headless servers, but that only measures disk performance at regular intervals and not exactly detection of needle-slamming (plus, this is my desktop/baby and I don't want to put CSF on it). 

Is there any good tool out there to help me measure this? Preferably with a GUI?

~Mike

---

