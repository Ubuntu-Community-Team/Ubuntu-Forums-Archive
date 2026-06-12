---
title: "Compatible Nvidia Cards with"
date: 2008-06-03
forum: Hardware
---

### Post by pancakelizard on 2008-06-03
If you're like me and trying to find a video card that works with Linux (and doesn't require spending 234234 years configuring) check out this link:

[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.05/README/appendix-a.html]("http://us.download.nvidia.com/XFree86/Linux-x86/173.14.05/README/appendix-a.html")

It contains a listing of video cards that are supported by the Nvidia Restricted Driver.

:popcorn:

---

### Post by EXCiD3 on 2008-06-03
And heres a quick tut on how to install the new nvidia driver 173.14.05 on Hardy (The driver was release May 28th and hasnt made it into the repos yet) 

**Thanks to starcannon for posting this! **[http://ubuntuforums.org/showthread.php?t=813931&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=813931&highlight=nvidia)

---

### Post by stchman on 2008-06-03
> **pancakelizard said:**
> If you're like me and trying to find a video card that works with Linux (and doesn't require spending 234234 years configuring) check out this link:

[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.05/README/appendix-a.html]("http://us.download.nvidia.com/XFree86/Linux-x86/173.14.05/README/appendix-a.html")

It contains a listing of video cards that are supported by the Nvidia Restricted Driver.

:popcorn:

Nvidia cards 8xxx series and down work very well with Ubuntu after restricted driver install.

---

### Post by EXCiD3 on 2008-06-03
Should note that the driver list is for the graphics cards running driver version 173.14.05 (May 28th) which **ISNT** the version currently in the repositories.

---

### Post by Sef on 2008-06-04
I have an 8600 NVidia and it worked fine OOTB (Out of the Box.)  I did install the restricted drivers because I wanted to use compiz-fusion.  Have had no problems at all with it.

---

### Post by pancakelizard on 2008-06-04
> **Sef said:**
> I have an 8600 NVidia and it worked fine OOTB (Out of the Box.)  I did install the restricted drivers because I wanted to use compiz-fusion.  Have had no problems at all with it.

8600 or 8600gt?

---

### Post by EXCiD3 on 2008-06-04
But out of the box the cards are just running the "nv" driver which isnt related to the restricted driver "nvidia". "nv" has much more compatibility because all it has to do is the basic 2D graphics rendering.

---

### Post by Unix_Slayer on 2008-06-05
See this thread. ===>[http://ubuntuforums.org/showthread.php?t=819043]("http://ubuntuforums.org/showthread.php?t=819043")

---

