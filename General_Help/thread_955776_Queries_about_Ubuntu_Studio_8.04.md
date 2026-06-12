---
title: "Queries about Ubuntu Studio 8.04"
date: 2008-10-22
forum: General Help
---

### Post by Nabanna on 2008-10-22
Hi,

i have some queries about Ubuntu Studio 8.04...

1. Can i upgrade from Ubuntu 8.04.1 to Ubuntu Studio 8.04.1(i have DVD), and if yes, how?

2. If i install Ubuntu Studio from scratch, does it allow Partitioning(manual partitioning) same as Ubuntu (because i already have installed MS WinXP & have only one HD)..??

3. Does Ubuntu Studio requires higher system spec (Graphic cards etc)??

---

### Post by caleb12 on 2008-10-22
Ubuntu Studio is not a separate distribution... it is Ubuntu. You can upgrade by opening Synaptic and doing a search for Ubuntu Studio and installing everything you find. 

The main difference, aside from the slew of multimedia applications and accessories that it includes by default, is the RT Kernel (RT = Real Time) a pre-emptive kernel allowing most tasks to function in real time. From what I understand (and who knows, I could be wrong - happy to hear corrections if that is case) a real time kernel allows demanding processes to be addressed immediately instead of waiting for kernel threads to become available - in other words it will drop kernel threads, preempt, in order to address other tasks. 

So... that being said. An RT Kernel could create some problems in hardware... who knows. Install and find out, best way would be to use the install DVD to run it live and see how it performs. I would do my best to stress test it... 

Also, here be lots of answers: 

[http://ubuntustudio.org/support](http://ubuntustudio.org/support)

there's also a mailing list... which always has good stuff and lots of friendly people. Personally, I run Intrepid with the Studio packages - but, obviously, not the RT kernel (hasn't been developed for Intrepid yet). Everything works great for what I want to do...

---

### Post by simtaalo on 2008-10-22
following this advice is the best way to get studio
[http://ubuntuforums.org/showthread.php?t=900676](http://ubuntuforums.org/showthread.php?t=900676)

---

### Post by Nabanna on 2008-10-23
> **caleb12 said:**
> Ubuntu Studio is not a separate distribution... it is Ubuntu. You can upgrade by opening Synaptic and doing a search for Ubuntu Studio and installing everything you find.

> **simtaalo said:**
> following this advice is the best way to get studio
[http://ubuntuforums.org/showthread.php?t=900676](http://ubuntuforums.org/showthread.php?t=900676)

Thank you,
but i dont have fast internet, the DVD itself is 1.1Gb, i wonder if this much i have to download i would have to left my PC on for more than 24 hours :( .

I saw that the installation is not graphical, but is there provision to do 'Manual Partitioning' as it is in Ubuntu..??

---

