---
title: "Why kernel is always generic?"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by adamitj on 2009-04-15
I figured that the kernel version for my architecture (AMD 64) is always "generic" (now I'm using linux-image-2.6.27-11-generic). 

Before migrating to Ubuntu, I used Debian and when there was an kernel update it was always named as "AMD64" (in my case it would be linux-image-2.6.27-11-AMD_x86_64 or something like that).

This is not a problem, I want just to know if there is a best kernel compilation for my systems.

---

### Post by benmarvin on 2009-04-15
From my basic understanding, generic just means it's the main version of the kernel. There are other custom kernels that you can compile for specific needs, and installing custom kernel modules into the generic kernel.
Sorry, perhaps a programmer or a more of an expert can answer better.

---

### Post by laluz on 2009-04-18
I have the same situation and actually have a bit of a problem with it. Some packages are explicitly compiled for 64bit and 32bit, the 64bit ones can not be installed. For a office suite it may not matter at all, but when installing a video transcoder this might bring inefficiencies, I guess.
I have searched for a amd64 kernel for intrepid but could not find one. 
So is it a design or we can do something to change it locally on our system?

---

### Post by glotz on 2009-04-18
Do compile your own, it's not too hard, you get a wee bit of education and to have a lot of fun with it. Not to mention the geek cred. :)

```
$ uname -a
Linux libero 2.6.26**mf** #1 Tue Mar 3 21:41:46 EET 2009 i686 GNU/Linux
```
(it's an older kernel but it's a custom job neverthless)

---

### Post by LoloftheRings on 2009-04-18
If you want to compile your own kernel, you'd best download the source using ```
sudo apt-get install linux-source
``` rather than downloading it from kernel.org.
You may also need some additional tools, not sure which ones.
Just google for help :D

---

