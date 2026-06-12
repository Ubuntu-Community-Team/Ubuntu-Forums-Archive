---
title: "Help - Graphic Card update installation"
date: 2009-02-16
forum: Installation &amp; Upgrades
---

### Post by Darkoan on 2009-02-16
Hi

Newbie who has just installed Ubuntu 8.10 - trying to install the Linux update for ATI Radeon 4800 series - using the command line, everything appeared ok until I got the following:


E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

Any ideas? Thank you

---

### Post by Partyboi2 on 2009-02-16
Make sure you only have one package manager running at a time eg synaptic, update manager etc...

---

### Post by Darkoan on 2009-02-16
Thank you very much, I will try that.

---

### Post by Darkoan on 2009-02-17
Yes I can confirm that was the problem, however...

When I went home to try reinstalling it, Ubuntu booted up normally until it got to the login screen, where I encountered a triple black screen of death! Black and fuzzy cga graphic style stalled screen repeated 3x vertically - I had to use the command line in safe mode to install the graphics card, whereupon it still failed, but at least when I rebooted for the 3rd time Ubuntu was back to normal.

---

