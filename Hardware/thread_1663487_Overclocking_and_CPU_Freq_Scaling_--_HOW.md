---
title: "Overclocking and CPU Freq Scaling -- HOW?"
date: 2011-01-09
forum: Hardware
---

### Post by rookcifer on 2011-01-09
Ok, I have seen a number of threads about this issue, but thought I'd post my own since this issue affects everyone differently.

Basically, the problem is that whenever I overclock my CPU, the CPU frequency scaler (ondemand, performance, etc.) in Ubuntu will not recognize the overclock.  The stock CPU speed is 3Ghz, but I have it overclocked to 3.4GHZ and Ubuntu still just recognizes it as 3Ghz.  I can turn off the AMD "cool 'n quiet" in the BIOS and then Ubuntu recognizes the overclock.  That's well and good, but I really want to use the power saving features of "ondemand."  

As others have noted, Windows does not have this problem.  I have heard that this is because motherboard manufacturers tailor the BIOS towards Windows and that Windows has its own proprietary ACPI standard.  Whatever the case, it is a PITA that Linux has this issue.  Is there any workaround?

OS: Ubuntu Maverick x64

Hardware:

Mobo: Gigabyte GA-MA770T-UD3
CPU: Phenom II x2 545
Memory: 4GB Gksill 1600 DDR3

---

### Post by rookcifer on 2011-01-10
*bump*

---

### Post by psusi on 2011-01-10
I don't know how Windows doesn't have the same problem since this sounds like a bios error.  The bios hands the OS the table of available frequencies, so if it isn't updating that table when you overclock, then it's not doing it right and there isn't much the OS can do.

---

### Post by rookcifer on 2011-01-11
> **psusi said:**
> I don't know how Windows doesn't have the same problem since this sounds like a bios error.  The bios hands the OS the table of available frequencies, so if it isn't updating that table when you overclock, then it's not doing it right and there isn't much the OS can do.

Well the thing is that if I turn off CPU frequency scaling in my BIOS (in my case it is AMD cool 'n quiet), then Linux picks up the proper overclocked frequency.  It is only when I have cool and quiet enabled in the BIOS that Linux doesn't pick up any overclocks.  It's really annoying, but I suspect this has something to do with BIOS makers only caring about Windows.  I have heard Windows does not follow the accepted ACPI standards (big surprise, eh?  Who would have thought M$ would make up a standard of its own and snub its nose at the rest of the world?). :(

---

### Post by psusi on 2011-01-11
> **rookcifer said:**
> Well the thing is that if I turn off CPU frequency scaling in my BIOS (in my case it is AMD cool 'n quiet), then Linux picks up the proper overclocked frequency.  It is only when I have cool and quiet enabled in the BIOS that Linux doesn't pick up any overclocks.  It's really annoying, but I suspect this has something to do with BIOS makers only caring about Windows.  I have heard Windows does not follow the accepted ACPI standards (big surprise, eh?  Who would have thought M$ would make up a standard of its own and snub its nose at the rest of the world?). :(

Right, because with it disabled, the frequency is whatever the bios left it at and the kernel doesn't change it.  With cool and quiet enabled, it passes a table of available frequencies to the kernel to choose from.

If it works it windows, it may be because the ACPI bios enables ACPI P-States for windows to use, and that gets the correct frequencies, but disables P-States under Linux, so it falls back to the AMD k10ctl method, which they don't pass the correct frequencies to.

There was a kernel parameter to lie to the ACPI bios and claim that it is Windows.  That might help.

---

### Post by jnew93 on 2011-01-31
I have this same issue, and have been driven to simply disable scaling from bios. This is not what I want. I hope someone can actually address this problem, as it seems to effect every ubuntu user who overclocks with scaling enabled.

---

### Post by psusi on 2011-01-31
> **jnew93 said:**
> I have this same issue, and have been driven to simply disable scaling from bios. This is not what I want. I hope someone can actually address this problem, as it seems to effect every ubuntu user who overclocks with scaling enabled.

It doesn't affect me, though my new Asus P8P67 Pro board has a different bug.  If I overclock BCLK at all, it passes a P-state table that claims the processor runs from 1.6 GHz to 5.8 Ghz, even when it is only 0.1% overclocked from the stock 1.6 GHz to 3.3 GHz.  At a 3% oc the actual frequency is 1,648 MHz up to 3,811 MHz, but it still claims 1,600 to 5,800.  I have complained to Asus about it and they are brushing me off instead of fixing it.

---

### Post by cascade9 on 2011-02-02
Just out of intrest rookcifer, did you o/c to 3.4GHZ by raising the HTT or by bumping the multi? 

I'd guess that its a HTT overclock, and that bumping the multi might work better.

---

### Post by rookcifer on 2011-02-02
> **cascade9 said:**
> Just out of intrest rookcifer, did you o/c to 3.4GHZ by raising the HTT or by bumping the multi? 

You overclock the CPU by either raising the multi or the reference clock (or both).  My CPU doesn't have an unlocked multiplier, thus I had to raise the reference clock.  I don't overclock the HTT because it gives no performance advantage.  As for the Northbridge, I did overclock it because it gives an advantage to the speed of the IMC.  Right now I am not running any OC because I prefer to have the CPU frequency scaling since I leave my PC on 24/7.

---

### Post by cascade9 on 2011-02-03
Yeah, silly mistake....I really, really shouldnt talk about things on chating programs at the same time as I'm making a post about the same subject on a forum. :( 

I'm running virtually the same board (770T-USB3) and CPU (550) and I get the same issue. I tried bumping the host clock to 202MHz and cpufreq-infoI still listed 3.10GHz as the 'hardware limit'. Though I seem to actually get frequency changes, its not locked at 3100MHz.

---

### Post by GreatKeyHunter on 2011-03-15
I think its working correctly even though its reporting the wrong numbers.  I did several system benchmarks under the stock parameters of the cpu and tested again with the overclocked cpu.  and there was a big difference.

---

