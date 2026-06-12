---
title: "SMP problem I think"
date: 2005-05-29
forum: Hardware &amp; Laptops
---

### Post by jdholbrook33 on 2005-05-29
Hello.
Just found Ubuntu today and had a smooth install.
Previously I had been running Red Hat 9 but it's been a year or so since I messed with it.
I do remember using a kernal for SMP to take advantage of my multiprocessor system.
I'm running a dual 1ghz Intell PIII system with 1 gig ram and an Nvidia GeForce 200Ti

I loaded the NVIDIA drivers and everything worked great.
The problem started when I found the kernal for the SMP. It's ....686 SMP or something. Thru the package manager I installed that and rebooted.
X would not start after rebooting and gave an error of NVIDIA module not loaded (or something like that).
I restored my xorg.conf file from back up and booted into regular graphics mode withthe SMP kernal.
I tried installing the NVIDIA module again but it said the module was already loaded and didn't download anything. I went thru the entire procedure anyway thinking something just needed to be reset.
Still no dice. No NVIDIA driver is loaded.

Is there a problem with loading the SMP kernal?
Is there a problem with using NVIDIA with the SMP kernal?

Any help is much appreciated.

James

---

### Post by jdholbrook33 on 2005-05-30
just to reply to my own post.
I wound up reinstalling and the Nvidia drivers worked.
Installed them first thing before anything else. Rebooted and it came right up.

I did notice that things actually seem a little slower with the SMP kernal. 
Am I dreaming?

---

