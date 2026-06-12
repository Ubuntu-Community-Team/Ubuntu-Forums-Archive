---
title: "Xserver-xorg ati driver not working 16.04"
date: 2016-04-30
forum: Hardware
---

### Post by Benjamin_Goldstone on 2016-04-30
Amd laptop steam not working

---

### Post by yoshii on 2016-04-30
yeah, unfortunately your thread title sums it up.  and this has been documented.  Really, there should be a "sticky" forum thread explaining all the ATI and Xorg incompatibilities with v16.04 and it's Linux kernel.  Keep reading the other threads about this.  I have tried to post some info up about this and there's a little bit of info in the v16.04 release notes.  

Basically support for the old ATI video driver was dropped by ATI, but they haven't finished making the replacement driver and won't be done till later this year.  
To make matters worse, the newer version of Xorg doesn't seem to work with some of the alternative configurations or something like that (i forget).  

So most ATI users are stuck without the main old one and without the main new one, and the open source ones don't always work either. 
And from I can tell, I'm not really even sure which driver is actually being used in v16.04 for ATI users.  
On my computer, I had run everything as "nomodeset" as a kernel parameter which I guess disables all video hardware acceleration.  

You'll definately be reading more errors like this all summer long until the Ubuntu support communities get more publicity and info out about this issue.  
Putting a tiny note into the release notes wasn't really enough.

---

