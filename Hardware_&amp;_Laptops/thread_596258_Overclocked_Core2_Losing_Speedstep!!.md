---
title: "Overclocked Core2 Losing Speedstep!?!?"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by gururise on 2007-10-29
I've got a Q6600 Quad with a modest overclock to 3ghz. The system is perfectly stable; however, Ubuntu reports upon bootup that there is a problem with CPU frequency scaling, and that my CPU will run w/o frequency scaling.

This is normally not a problem, but I'm trying to run a server, and would like to save electricity by enabling frequency scaling. When the CPU is not overclocked (stock 2.4Ghz), frequency scaling works great.

Has anyone else experienced the loss of Frequency Scaling on overclocked intel cpu's?

---

### Post by gururise on 2007-10-31
So many people are using overclocked Core2 Duo and Quad processors... are you guys also losing speedstep, or is it just me?

---

### Post by simoncullen on 2008-02-18
I'm running a C2D not a Quad -- but that is precisely what happened to me : [http://ubuntuforums.org/showthread.php?t=695232](http://ubuntuforums.org/showthread.php?t=695232)

---

### Post by 444 on 2008-02-18
Well it's standard for Speedstep to be disabled if you change the vcore. You should be able to still overclock, but without changing the voltage.

---

### Post by ori_ab on 2008-04-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/213119](https://bugs.launchpad.net/bugs/213119) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				same problem here - overclocking disables cpu frequency scaling.

tested on hardy beta with kernel 2.6.24-12 and 2.6.24-15.

motherboard is gigabyte ga-p35-ds3l.

see - [https://bugs.launchpad.net/bugs/213119](https://bugs.launchpad.net/bugs/213119)

---

