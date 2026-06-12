---
title: "[SOLVED] AMD64 driver"
date: 2005-12-27
forum: Hardware &amp; Laptops
---

### Post by Landice on 2005-12-27
Hi guys, hope you can solve this out for me. Do i need to install the AMD64 processor driver in my linux? How about my motherboard driver too? I opened up the device manager but i couldn't find any information of my hardware including BIOS, Processor, and etc.. All the information is unknown. Does this mean the system can't detect my hardware?

---

### Post by psusi on 2005-12-27
There is no such thing as a "processor driver", so no, you don't need to install anything.

---

### Post by Landice on 2005-12-27
Oops.. sorry.. i mean the AMD64 processor Cool and Quiet driver, just lazy to type the whole name.. How to make the device manager lists out all my hardware information just like windows' device manager?

---

### Post by psusi on 2005-12-27
You don't because it ISN'T windows' device manager.  As for the cool and quiet driver, that's a windows inf file, so is useless on Linux.  

Linux *should* automatically take advantage of the processor's ability to enter lower power states, but then again, windows should be able to do this as well.  Generally what happens though is stupid motherboard manufacturers ship their products with broken acpi bios then the cool and quiet driver corrects this problem.  If it is broken to the point that Linux can't use it, then it takes a bit more effort on your part to correct that.  

If you right click on your top pannel and add a new pannel, there should be something in the list you can add that monitors the cpufreq stuff and shows the processor's current clock rate.  Add that to your pannel and see if it is using the lower clock rate when not busy.  It should slow down to something like 800 MHz unless you're doing some serious number crunching.

---

### Post by Landice on 2006-01-06
Thanks, psusi..

---

