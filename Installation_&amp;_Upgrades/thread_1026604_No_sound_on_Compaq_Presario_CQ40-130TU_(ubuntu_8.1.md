---
title: "No sound on Compaq Presario CQ40-130TU (ubuntu 8.10)"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by liew on 2008-12-31
Dear all,
My laptop's speaker not working after installed ubuntu 8.10. 
Any one please help.:confused: 
Thanks.

---

### Post by lemming465 on 2009-01-01
I looked on HP's web site and couldn't figure out what the sound chip is, sorry.  If you post the output from **sudo lspci -v** you may get more advice.  In the meantime, if you run **alsamixer**, does it show more than one device?  And are they all turned on?

---

### Post by liew on 2009-01-08
Dear Sir,
This is Liew again. My laptop still not working. Please help!!!

---

### Post by kranny on 2009-01-08
post the o/p of lspci|grep Audio

---

### Post by salem7 on 2009-01-24
Hi. I'm facing the same problem too. The output of my lspci|grep Audio is:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

What shall i do? TQ in advance.

---

### Post by ronronron on 2009-01-27
I'm using Compaq Presario CQ40-126AU but the sound is no problem here after installing ubuntu 8.10. I think the sound card is same.

---

### Post by ceguhadi on 2009-01-28
try adding this "options snd-hda-intel enable_msi=1" in the /etc/modprobe.d/alsa-base . works for me..:D

---

### Post by jhahoneyk on 2009-02-10
Hey thanks, it perfectly worked. By the way, what does that line do?

---

### Post by Anh.Takaji on 2009-03-17
Thank you so much :) I faced the same problem and now I can solve it already :)

---

