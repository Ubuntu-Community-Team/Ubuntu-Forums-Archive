---
title: "Unable to Install"
date: 2005-07-27
forum: Hardware &amp; Laptops
---

### Post by Oline61 on 2005-07-27
I am unable to install Ubuntu on my system  ](*,) .

I start the install, but when it starts loading stuff from the PC it always stops at e2fsprogs-udeb (or something very similar to that). I can go no further. Please help me!

CD Drive: Plextor PX-740A (latest firmware, or course).
HD: Seagate Barracuda 7200.7 SATA NCQ
Mobo: MSI K8N Neo4 Platinum
CPU: A64 3200+ Venice

Using AMD64 Ubuntu.

I figure the problem is either the Hard drive or the CD drive which is brand spankin' new, so I'm going to RMA the hell out of it if it's the problem.

---

### Post by sethmahoney on 2005-07-27
I would recommend downloading the ISO again and burning a new CD.  A lot of people have had similar install problems, and this seems to help.

---

### Post by Oline61 on 2005-07-27
I should have put this in my original post, but I had 1 disc that worked in my old computer, so I tried it in this one, and it had this problem. I redownloaded the iso, burned with Nero (data verification completed successfully), and ended up with the same problem again.

---

### Post by guggi on 2005-10-02
i have the same problem istalling ubuntu with px-740a! on a kanotix mailinglist another guy solved this problem by passing nodma bootparameter for this drive, dunno how to do this with ubuntu.
you could also try to install a second cd-drive and than disable dma for the px740a by using hdparm. I solved it this way.

---

### Post by WetWilly on 2005-10-02
I have the exact same problem with my Plextor PX-740A!! It say that the error correction failed on the cd even though I installed from that disc before and it went fine but now I got this new dvd-burner and it screwed up =(

Very annoying, what exactly did u do guggi to fix it? :confused:

Forgot to mention it was on Breezy preview..

---

### Post by kkappel on 2005-10-29
[QUOTE=guggi]dunno how to do this with ubuntu.[/QUOTE]

at UNUNTU-Boot-Prompt: linux nodma

---

### Post by WetWilly on 2005-11-11
the linux nodma doesnt solve this problem....

Bug:

[http://bugzilla.ubuntu.com/show_bug.cgi?id=16901](http://bugzilla.ubuntu.com/show_bug.cgi?id=16901)

And it also exist in Breezy, sadly enough.

---

