---
title: "laptop overheating on ubuntu 9.10"
date: 2009-12-14
forum: Hardware
---

### Post by Abdul99 on 2009-12-14
PLEASE all,

I recently installed ubuntu 9.10 on my Compaq presario c700 laptop, it gets very hot without doing any intensive operations on it. temperature shows 55.0 degree C it is on "ondemand" mode. i have looked at many threads however none of them seem to be doing the job for me. the fan works and i didnt hav any prob w/ it when on windows 7 two weeks ago. ubuntu also seems to be a bit slow-performing. can it be the display control? here's the output from "lspci -v | less" command: 

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 30d9
        Flags: bus master, fast devsel, latency 0, IRQ 26
        Memory at 51000000 (64-bit, non-prefetchable) [size=1M]
        Memory at 40000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 30d0 [size=8]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 30d9
        Flags: bus master, fast devsel, latency 0
        Memory at 51100000 (64-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>


Thanks for any help

---

### Post by oshunluvr on 2009-12-14
Are you sure it's actually overheating and not a false report? Some BIOS' have a PCHEALTH section that should show temperature.

---

### Post by Yellow Pasque on 2009-12-14
55C is warm, but not overheating. If that's as hot as your CPU gets, it's okay. If it gets to the 60's, then start worrying.

---

### Post by luigi6699 on 2010-06-29
Did you get this solved?  I have a Presario C700 with heat problems.  Even just leaving it running in X, the fan is on all the time and it's quite warm to the touch.  Not so in Vista.  

Running top shows that everything sits idle.  X.org is at the top of the list with 5% cpu usage at most.  The CPU is at it's "idle" speed of 1ghz (2ghz processor).  That being said, the areas of the laptop that get hot are consistent with the GPU... which shares a heatsink with the CPU.  So I'm starting to wonder if the issue is a video driver problem.  

This system comes with a crappy Intel X3100 card, which might be the problem... Any ideas?

---

### Post by IcarusR on 2010-06-29
Are you sure this is not a dust related heat problem ??
Get an air duster aerosol & with it switched off blow air in through the exit to blow any dust out. 
Laptops are susceptible to dust gathering in the air vent path because they are small.

---

### Post by nmaster on 2010-07-02
what are you using to report the temperature? i also have a compaq presario c700.  i didn't realize that 55C (131F) was too hot.  when i run 'acpi -tf' at the command line i often get something hotter (much hotter when watching a flash video) but it tells me that everything is okay.

EDIT:I'm back at home now on my personal laptop and i also see 55C as the temp.  i don't think its a big deal.  the CPU is barely doing anything.

---

