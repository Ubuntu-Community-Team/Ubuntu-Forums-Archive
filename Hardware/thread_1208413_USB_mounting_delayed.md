---
title: "USB mounting delayed"
date: 2009-07-09
forum: Hardware
---

### Post by wessel_k on 2009-07-09
Hi,

I'm starting to run out of options.
I've installed UNR 9.04 And did some tweaking on the battery life and (u)mounting CIFS drives. But that's about it. 
I've also followed the guides on the ubuntu site to get the most out of my Aspire One 110L. 
But now I'm stuck. Since I've tinkered with it last week the USB drives I attach take some time to be eventually mounted. There is no specific time set for this to happen. Sometimes it's within one or two minutes sometimes it takes 10 to 30 minutes to get mounted.
I can't find any errors in dmesg or anywhere else.
I'm close to reinstalling the netbook. Even my backup already contains the issue. So I can't revert.
Is there anybody who can help me here?

Regards,

Wessel

---

### Post by wessel_k on 2009-07-11
I found the issue. It had to do with the fstab trying to mount an unavailable network drive. Any suggestions how to cancel the search for these drives. 

Regards,

Wessel

---

