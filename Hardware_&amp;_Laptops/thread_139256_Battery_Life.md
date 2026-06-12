---
title: "Battery Life"
date: 2006-03-03
forum: Hardware &amp; Laptops
---

### Post by David Corrales on 2006-03-03
Hi everyone, I've been searching the forums around for concise information about why the battery life is so much shorter in linux than windows and for ways to achieve equal performance but I haven't been lucky yet.
I'd like this post to be stickied or something and serve as a faq/info concerning the issues and tricks to get the battery working as long as possible.
I read and have tried running **laptop-mode** but I don't see a big difference :confused: and I think it's very dissapointing to lose about 1hr of battery time when using linux.

---

### Post by byen on 2006-03-07
Ok. Though some might disagree with me. This is what my experience has been. I have a compaq presario laptop and my battery life on normal usage used to be about 2 hours using Windows XP. After switching to Ubuntu I got somewhere between 1.30 to 2 hrs depending on the usage.  I was satisifed with this until I changed my kernel that fits my processor. I have an Amd Athlon Xp processor and though the standard 386 kernel that comes with the default Ubuntu installation did well with my lappy I have seen a considerable amount of difference when I switched to the kernel(k7) that was optimized for my processor. I have not only seen a little difference in the battery life but also in the way my laptop responds when my laptop runs on battery.

To see if installing the right kernel helps...[check this thread.]("http://www.ubuntuforums.org/showthread.php?t=85917")

Hope that helps.Goodluck!

---

### Post by underwater on 2006-03-08
[QUOTE=David Corrales]Hi everyone, I've been searching the forums around for concise information about why the battery life is so much shorter in linux than windows and for ways to achieve equal performance but I haven't been lucky yet.
I'd like this post to be stickied or something and serve as a faq/info concerning the issues and tricks to get the battery working as long as possible.
I read and have tried running **laptop-mode** but I don't see a big difference :confused: and I think it's very dissapointing to lose about 1hr of battery time when using linux.[/QUOTE]


I have the SAME problem

I've basically lost an hour of time after switching to Ubuntu

so if anyone knows even why?  Unless it is that Gnu/Linux uses that much more processor power and system resources why would this happen???

---

### Post by tekwarren on 2006-03-08
did you not read the above post?? The basic Ubuntu install sets you up with the 386 kernal. A basic kernal that will run on nearly any machine. You need to start configuring your install for your computer. Install the kernal that fits your computer architecture (processor). I've recently went up to the smp kernal which lets me take advantage of the HT processor in my laptop. The great thing about linux is you can optimize it for your personal usage and your individual system.

---

### Post by jwbaker on 2006-03-09
Uninstall laptop-mode, install laptop-mode-tools.  Possibly configure some things in /etc/laptop-mode/laptop-mode.conf.  Yes, this is confusing.  I hope they fix it in Dapper.

Keep in mind that many, many, most, and nearly all PC laptops from major vendors like Dell, HP, and Acer come with completely broken ACPI power management tables.  The fact that Windows works well on these laptops is a miracle of staggering proportions.  Don't expect the same from Linux unless you use decent hardware that works properly.

---

### Post by underwater on 2006-03-23
[QUOTE=tekwarren]did you not read the above post?? The basic Ubuntu install sets you up with the 386 kernal. A basic kernal that will run on nearly any machine. You need to start configuring your install for your computer. Install the kernal that fits your computer architecture (processor). I've recently went up to the smp kernal which lets me take advantage of the HT processor in my laptop. The great thing about linux is you can optimize it for your personal usage and your individual system.[/QUOTE]


Yeah I did that-- went to a 686 kernel


I see no difference

---

### Post by David Corrales on 2006-04-02
I have laptop-mode-tools installed now and the difference is basicaly that you can run **laptop_mode** as a regular user but not **laptop-mode**. Installing laptop-mode-tools also makes **laptop_mode** get loaded automatically every reboot.
Still... I'm missing around 30 minutes or so of battery life when compared to Windows XP :(

---

