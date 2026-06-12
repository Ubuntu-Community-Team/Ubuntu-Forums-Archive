---
title: "Shows different memory usage using free and gnome-system-monitor"
date: 2008-12-22
forum: Hardware
---

### Post by cyrex on 2008-12-22
Hello all, i am confuse with something i have been seeing since 8.04. I am using 8.10 right now with the following configuration and services running:

+ Package sources are all activated (main, universe, multiverse, restricted) and all update types (security, updates, proposed, backports)
+ Have apache, mysql, php, svn (using all via gdm)
Hardware
CPU Intel E8500, 4GB Ram, 2HDD Samsung 1TB each, Nvidia 8500 using the restricted drivers. Mobo DP35DP.

I tipically use this to test out several distros with VirtualBox, test some programs with Wine, Use Amarok, Bluefish, Netbeans, CodeBlocks and other tools. Now i dont really turn off the computer, tipically it lasts between 1 week to 2 weeks on without resetting or turn it off. Am VERY happy with the performance of Ubuntu 8.10 although am a KDE user (sorry can't use kde until 4.2 for memory/cpu consumption issues). Now my problem is this, after several days online the memory starts leeking out. I mean this, gnome-system-monitor shows me between 5% to 8% usage when i only have lets say the amsn or amarok loaded. But if i type free -m it says i have used 2.9gb of the 3.8gb i have total.

I first thought it was when i loaded virtualbox, so i didnt load that one for 5 days to test it out, but the same thing happen. Now the crazy part is if i do a ps -aux to check who has the % of memory that i need almost everybody has 0.0% used, same for the gnome monitor. They both dont show who is consuming the invisible memory. I have to do a reset of the whole pc to get back that missing memory. Each test lasted about a week and it was with all the tools i mention above. Eliminated virtualbox for a week, then did not use wine for a week, same for netbeans, bluefish, mysql query browser, etc, etc. Normal days were between 5 to 7 days. Then i had to reset the pc to get the memory back.

2 questions i need to ask:

1. What could cause this and how can i study/attack the problem

2. What tool could go deeper into memory analysis than free, ps or the gnome monitor?


Thank you.

---

### Post by chrisamiller on 2008-12-22
Linux will aggressively use free memory to increase performance.  Here are some more details about what's going on with your system:

[http://www.novell.com/coolsolutions/feature/18990.html](http://www.novell.com/coolsolutions/feature/18990.html)

Quote:
What actually is happening here is that Linux has cleverly used my free memory to cache the system disk and speed up the system. However, as application needs arise, this memory will be re-allocated to those applications. So in reality, the memory really is "free" for use. 

See also, various threads like this one:
[http://ubuntuforums.org/showthread.php?p=5526097](http://ubuntuforums.org/showthread.php?p=5526097)

---

### Post by Greyed on 2008-12-22
FAQ.  Let me ask this, are you worried because you see memory being used or because you're noticing actual slowdown.  I'd bet cold hard cash it is the former and not the latter.

Run free in the command line and look at what the second line says, not the first.

---

### Post by cyrex on 2008-12-24
Thank you chrisamiller.

@Greyed - Good question. The only program that told me that the system was out of memory was wine when i tried to run i think it was Warcraft 3 o Max Payne. It said there was 92Mb free out of the 4GB, which was the same thing that free told me. For the slowdown, no, i did not have any application slowdown, all were running good. For the second line in the free do you mean the buffer/cache one?

---

### Post by Greyed on 2008-12-25
Yup. 

```

{grey@igbuntu:~} free
             total       used       free     shared    buffers     cached
Mem:        384376     379156       5220          0       3644     134760
-/+ buffers/cache:     240752     143624
Swap:       401400      76648     324752

```

The -/+ buffers/cache line shows you the used/free memory as if the buffers/cache were free.  They can be freed when programs need memory they are effectively free.  They are only used to provide the chance of speedups as the alternative is to not use them and have no chance for possible speedups.  Make sense?

---

### Post by cyrex on 2008-12-26
ok found something good here that maybe will help somebody else. Was looking into all the tools i use daily. So here i am making a new image in VirtualBox for windows XP. I was installing it all ok when suddenly i get a windows message (inside the VirtualBox environment that i dont have enough memory left. I quickly checked the memory with the free command and found out that i had 87MB free. So i am guessing that VirtualBox did not correctly send a message to the kernel asking for more memory so that the cached memory that was used by the kernel could be turn to the Virtualbox image i was working on. I reserved 512MB for the image. Am guessing this is a virtualbox not talking correctly with the linux kernel. I will have to do more checking and some more tests to be sure.

---

