---
title: "how to apply a patch?"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by lordy on 2009-03-21
Hi,

I am trying to apply the patch at:

[https://bugs.freedesktop.org/show_bug.cgi?id=17776](https://bugs.freedesktop.org/show_bug.cgi?id=17776)

the patch details are:

[https://bugs.freedesktop.org/attachment.cgi?id=22848&action=edit](https://bugs.freedesktop.org/attachment.cgi?id=22848&action=edit)

however, when I do this by doing 

'sudo patch -p0 < patchname' it fails.  Results are below:

sudo patch -p0 < sdvo-tv-0212.patch 
[sudo] password for myth: 
(Stripping trailing CRs from patch.)
can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/src/i830_display.c b/src/i830_display.c
|index 7a8e96d..114ae44 100644
|--- a/src/i830_display.c
|+++ b/src/i830_display.c
--------------------------
File to patch: ^C

I installed git but still nothing.  What am I doing wrong?  I assumed the files would be in git?  Do I need to install something else first?

Thanks

---

