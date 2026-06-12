---
title: "Installing drivers?"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by Radijs on 2009-06-26
I'll come straight out on this, I'm a complete noob when it comes to ubuntu.
I installed it on my laptop (Sony Vaio VGN-A115M) And I've been toying with it for about a week or two with mixed results.

One of the things I've not been able to manage yet is to install drivers for my video card. I think its nessecary because I can't even properly play some video files.

I downloaded the driver off the ATI website. And its got a .run extention. How do I install it?

---

### Post by wpshooter on 2009-06-26
What makes you think that you need a driver other than the one that was installed by the Ubuntu O/S installation ?

What do you mean when you say "I can't even properly play some video files" ?

Have you downloaded and installed Adobe FlashPlayer for Linux from the "REAL" (as opposed to one of those fake ones) Adobe website ?

---

### Post by Radijs on 2009-06-26
Well when I'm on youtube and I try to play a video on high quality or HD mode the playback stutters even when the video has been completely loaded (so its not a networ/streaming issue).
I guessed a driver update would be the key since I had the same trouble with my laptop after a clean windows install before reinstalling the ATI drivers.

---

### Post by Sef on 2009-06-26
System > Administration > Hardware Drivers

Have you tried that?

---

### Post by Radijs on 2009-06-26
Yeah I've looked through there. And it just says that there are no drivers available.

---

### Post by Mark Phelps on 2009-06-27
That because ... wait for it ... there are NO restricted drivers available!!  According to Google, your machine came with an ATI Radeon chipset, and AMD/ATI has dropped support for that chipset in their newer drivers.  The last drivers that supported it (Catalyst 9.3) won't run with the Xorg built into Ubuntu 9.04.  If you force an install of current ATI drivers, you'll simply hose your machine.

A simple forum search would have yielded dozens of posts about this very issue.

---

