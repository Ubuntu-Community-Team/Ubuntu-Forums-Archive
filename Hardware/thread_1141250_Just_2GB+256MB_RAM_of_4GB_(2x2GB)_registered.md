---
title: "Just 2GB+256MB RAM of 4GB (2x2GB) registered"
date: 2009-04-28
forum: Hardware
---

### Post by mcmillion on 2009-04-28
Hello Guys,

I'm wondering whats wrong with my system.
When I use Windows Vista on my notebook (Dell Studio XPS 1340), I see 2x2GB memory within my notebook. At least the system information show this to me.

When I use Linux (and i'm love to use linux and I provide the usage of windows as far as possible), i got only 2GB+256MB memory shown in my system settings/information. 
Even when I take a look in the system settings, when I use htop or when I call "hwinfo --memory", the memory is shown as 2,2GB. 

May, I hope to get some help here in ubuntuforums. Do you know, what goes wrong on my notebook? I don`t know how to fix this memory "loss".

There should be 2x2GB DDR Ram built in. Can you help me?

regards
mcmillion

---

### Post by Barry Carroll on 2009-04-28
Your laptop seems to have hybrid sli with a combination of a dedicated graphics memory and shared graphics memory.  The specs show that the shared memory can reach 895MB, so your 2.2GB of recognised memory + roughly 0.9GB brings you up to around 3.1GB which is just about the limit of what a 32-bit OS can address.

Are you running 32-bit Ubuntu?  If so you'll get a fair bit more usable memory by trying out 64-bit.  You might also be able to tweak settings in your BIOS for "shared memory size" or "Hyrid SLI" or similar.

---

### Post by mcmillion on 2009-04-28
Hello,

well, that makes sense. The graphics card grabs some of the memory. Maybe up to 0,9GB. But whats with the rest? I thought a 32Bit OS can adress up to 3,7GB of memory?

Nevertheless I'll take a look into the bios.

Yip, I'm running a 32bit Ubuntu. A Change-Over to the 64Bit version isn't a good way at the moment. I'm heavy related to my *running system*, because of my actual master thesis.

---

### Post by Barry Carroll on 2009-04-28
It varies.  The best I've ever got with 32-bit is 3.25 and the worst is 3.06.  It's noteworthy that Vista after SP1 reports installed RAM but not the *usable* RAM.  You can get the true figure in the task manager.

---

