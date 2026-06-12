---
title: "Detecting Real CPU speed"
date: 2008-12-01
forum: Hardware
---

### Post by sombertattoo on 2008-12-01
Hey all,

I've overclocked my e2180 in my dell vostro 200 with a g33m02 mobo to 2.6ghz. Now, I can prove the pinmod overclock took because superpi times using the linux version went from ~23s to 17s. Vista detects the overclock using cpu-z. 

cat /proc/cpuinfo spits out 2ghz. 

dmesg | grep MHz shows 2659.991 mhz

System monitor shows the cpu id at 2ghz.

Is there any push to modify system monitor, cpu id, etc to show both stock and actual speeds? I know mine took but I think it's important to either have a standalone program or the stock tools to show the actual speed. Even the cpu freq power saver applet shows 1.2ghz, 1.6ghz, 2ghz.

EDIT: Could a mod move the thread...wrong forum...I thought this was a general hardware forum and not just laptops, ooops!

---

