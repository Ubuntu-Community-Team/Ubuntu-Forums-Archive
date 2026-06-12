---
title: "Bug Fixed But Help Needed"
date: 2008-05-22
forum: Hardware
---

### Post by Wish4Me on 2008-05-22
I had a bug with my hardware that was cross platform(Not just on Ubuntu). With some troubleshooting for about 10ish hours we finally found a fix.

It was fixed on Fedora 8 by booting into Runlevel3, logging in as root, typing command "system-config-display --reconfig", and then reselecting my driver/manu model.

I had an error that sent signals that said "out of range" but that resulted in a full system crash if i updated to proprietary drivers. Problem was, I couldn't log into ubuntu without the proprietary driver so everyone who i talked to was baffled in the Ubuntu camp. But I like Ubuntu so how do I replicate this in Ubuntu. The bug occurs randomly when using X.

---

