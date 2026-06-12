---
title: "No option to boot to WinXP"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by i-like-food on 2009-11-03
I'll admit off the bat that I'm a real n00b when it comes to linux thus far.  I got Jaunty to dual boot with Vista on my every day laptop without many issues a week or so ago, and upgraded to Karmic easily.  I decided since things were going so well, I'd install it on my old laptop, which I had been running as a server on Windows XP.

Now the problem is that it boots straight to Ubuntu without giving me the option to select my old XP install.  I have the feeling this has something to do with what order my partitions are in, because my Ubuntu partition is first, and XP is second, due to the weird way I tend to set my computers up.

It would be great if someone could help me straighten this out, and I'll gladly supply any additional info that is needed

---

### Post by sliketymo on 2009-11-03
> **i-like-food said:**
> I'll admit off the bat that I'm a real n00b when it comes to linux thus far.  I got Jaunty to dual boot with Vista on my every day laptop without many issues a week or so ago, and upgraded to Karmic easily.  I decided since things were going so well, I'd install it on my old laptop, which I had been running as a server on Windows XP.

Now the problem is that it boots straight to Ubuntu without giving me the option to select my old XP install.  I have the feeling this has something to do with what order my partitions are in, because my Ubuntu partition is first, and XP is second, due to the weird way I tend to set my computers up.

It would be great if someone could help me straighten this out, and I'll gladly supply any additional info that is needed

Good info here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by i-like-food on 2009-11-04
I've read through a lot of that, and gathered that the problem is my XP partition isn't the first on the drive.  I tried using os probe to no avail.  I attempted to write a custom boot entry for XP, but it won't let me save it to the grub.d folder, even though I opened it through terminal as root.

Any advice?  Or perhaps an easier way...

---

