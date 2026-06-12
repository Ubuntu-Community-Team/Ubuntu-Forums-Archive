---
title: "LG GSA-H55N CD/DVD-Drive issue"
date: 2009-02-10
forum: Hardware
---

### Post by K-Meister on 2009-02-10
Hello!

Here's the thing. Can't burn (or mount) cd's with any software under ubuntu. Still it recognises blank cd's in burning software. Tried k3b, gnomebaker and brasero. The drive is LG GSA-H55N cd/dvd writer. So whenever I start burnin something it starts, writes 1% or so and stops. Unknown error message is all i have. Have been trying to google for an answer with no luck. Maybe drivers would help? Tried to find one but the only link was down. Any ideas? Help a newbie. Thanks.

---

### Post by Aviendha09 on 2009-03-02
You are not alone, I have the same problem. Though mine did work for more than a year, it recently started acting up, just like yours; kernel upgrade problem ? did you try working it with a different distro ? I think I will...

---

### Post by ohme on 2009-03-10
had a similar problem, and I found out that  starting the burning program as a superuser (sudo) solves it. I think it is related to the fstab entry not mentioning rw, but i did not try it (yet).

---

### Post by Aviendha09 on 2009-03-10
Thank you for your help. I managed to solve my problem this way: I changed my flat cable for one that doesn't have a broken connector. No more I/O problems!!

---

### Post by wlangston on 2009-04-11
I also had problems with this drive.  I couldn't play DVDs at all with it and burning anything was hit or miss.  At first I thought it was a problem with my software setup.  I finally figured out it was the drive and it needed a firmware update.  You can get updated firmware from LG's website.  My GSA-H55N now has firmware version 1.06 (it was 1.03) and it's working without any issues now.  Unfortunately the firmware update is only available as a windoze executable.

---

### Post by Aviendha09 on 2009-04-12
I have a better one for you. The drive only worked as a CD volume, I couldn't access any of its DVD capabilities though I could read and write to it. 
Well it turned out the I/O cable was plugged in backwards! My cable is not keyed, but it has a red line along it's side; it was plugged in the wrong way!! T
Try to troubleshoot that, the drive was still accessible as a CD-ROM!! Well, it works now!!
:lolflag:

---

