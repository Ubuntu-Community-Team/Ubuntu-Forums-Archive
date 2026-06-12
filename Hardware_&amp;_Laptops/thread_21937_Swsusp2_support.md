---
title: "Swsusp2 support?"
date: 2005-03-24
forum: Hardware &amp; Laptops
---

### Post by hotplainrice on 2005-03-24
I found hibernate script in apt-get but how do i get the swsusp2 code in the kernel? I dont understand how initrd works and I'd rather use pre-built packages cos im sick of compiling (came from gentoo).

---

### Post by jerome bettis on 2005-03-26
to get software suspend 2 working you need two things:  the hibernate script, which you have and a kernel that has been compiled (oh noes) with their patch at [http://swsusp2.sf.net](http://swsusp2.sf.net)

download the patch for your kernel, extract it, cd to /usr/src/linux and do sudo /path/to/the patch/apply .. then recompile the kernel.  if you need help with that see the wiki, or ask us.

---

### Post by wittygame on 2005-03-28
Hi, 


What is the difference exactly between the hibernate which comes with Ubuntu,and the swsup2 package? arnt they supposed to be the same? and if swsusp2 works better, why not use it instead, or at least prepare some ubuntu official packages for it? 

This would increase the number of successes with laptops! woudnt it??

---

### Post by sMell on 2005-03-28
[QUOTE=wittygame]What is the difference exactly between the hibernate which comes with Ubuntu,and the swsup2 package?[/QUOTE]

swsusp2 has more features and is not in linus's kernel yet

---

### Post by jdong on 2005-03-28
Quoting a Ubuntu developer, the swsusp2 devs are on drugs or something like that...

I personally patch my kernels with swsusp2 anyway. It pages the cache to the disk, too, so the system is just as snappy after resume as before!

---

### Post by sMell on 2005-03-28
[QUOTE=jdong]Quoting a Ubuntu developer, the swsusp2 devs are on drugs or something like that...[/QUOTE]

Would you happen to know if it's safe to use a swap partition to save to?  swsusp does it by default on my system, but I'm wondering what would happen in the unlikely event that I would have more pages than swap?

---

### Post by toricred on 2005-04-14
I'm trying to compile swsusp2 into the kernel as well and keep getting problems saying the patch won't install cleanly.  I've tried both the 2.6.10 kernel source and the 2.6.11 kernel source.  Any suggestions?

---

### Post by Laurent Cazalet on 2005-04-15
were you patching against vanilla kernels (the ones you get from ftp.kernel.org)? 
correct me if I'm wrong, but I'm don't think that patching against the ubuntu kernel tree will work. 
I had no problem against 2.6.10 from kernel.org (using swsussp 2.1.7). 

And indeed from a user perspective, I find swsusp2 better: it display a gnome progress bar before hibernating, and lzw compression makes suspend faster... Never had any problem with it, using it every day or so.
Features of swsusp and swsusp2 are compared here: [http://www.suspend2.net/features](http://www.suspend2.net/features)

---

