---
title: "[SOLVED] Easy way to switch from AiGLX to Xgl"
date: 2008-11-18
forum: General Help
---

### Post by ciscophoneguy on 2008-11-18
Hello Everyone!

This is my first thread. 
Nothing is wrong with my system, but I wanted to try out Xgl over AiGLX. I've started to experience a few issues with Elsa, Google Earth, and Firefox when effects are running and wanted to see is running Xgl would alleviate those issues. Is there an easy way to switch back and forth from Xgl and AiGLX? I've found tutorials that will show me how to switch to Xgl from AiGLX, but not the other way around.

Also, It should be noted that I’m running an Intel X3100 onboard graphics chip.

Thanks!

---

### Post by binbash on 2008-11-18
Those issues will not be fixed till DRI2.

---

### Post by Izek on 2008-11-18
> **binbash said:**
> Those issues will not be fixed till DRI2.

And just so you know, DRI2 has many issues with ATI if I'm not mistaken. Though it's really getting bland now, it's like I should expect it.

---

### Post by ciscophoneguy on 2008-11-18
I didn't know about that, I just read this:

> After Intel developers revealed they were working on the management of graphics memory with GEM (Graphics Execution Manager), aimed at replacing TTM, Kristian Høgsberg has proposed rethinking DRI2. He is proposing to back out DRI2 from the X Server 1.5 release. The development of GEM is progressing with kernel patches being released to the Linux Kernel Mailing List, aiming for inclusion in Linux 2.6.28.

Adam Jackson, X developer removed the code of Xgl from the source code management of the X.org X server. The future of Xgl is not rosy; the code had not been updated to a current equivalent of other distributions, and newer distributions primarily use Aiglx for the base technology for desktop effects with Compiz and the like.

This was dated August 5. So... Going Xgl might not be a good idea. I've been looking around for some fixes or work around, but have not found any for the issues I’m experiencing.

Thanks allot for your replies, much appreciated!  \\:D/

---

