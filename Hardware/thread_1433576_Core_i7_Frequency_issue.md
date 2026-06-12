---
title: "Core i7 Frequency issue"
date: 2010-03-19
forum: Hardware
---

### Post by darkcrawler on 2010-03-19
Hello!
My system:
i7 920 D0
gigabyte ex58-ud5
3x2GB OCZ Gold pc3 12800

I OC the cpu from bios to 3,4 GHz (200*17), with eist and c1e on it idle at 2,4GHz (200*12). With Win7 it's all right and cpu-z shows that the idle/full frequency works correctly.
In Ubuntu 9.10 64bit that doesn't work.. In idle the cpu runs at about 1,60 GHz and in full sometimes reaches 2.26 GHz.. I tried to look at the gnome frequency scaling applet and it shows available frequency between 1,60 and 2,26 GHz.. So what could i do to make my cpu run correctly at 2,40 or 3,4 GHz?

Thanks!

---

### Post by darkcrawler on 2010-03-19
I found that the problem is in the bclk..
Ubunt still considers it at 133, while for sure is at 200..
The frequency scaling applet goes with multi from 12x to 17x (as set in bios), infact in Ubuntu the frequency goes from 1,60 (133*20) to 2.26 GHz (133*17).. So the wrong reading of the bclk is a Kernel issue or what?

---

### Post by keep you kimi on 2010-03-19
I have the same problem with both i7 and atom - ubuntu is not able to change the fsb, just switches through multipliers. 
is there a way to change it?
my atom n270 runs minimum @600 in WinXP with fsb 100 and in ubuntu it goes only to 900Mhz @133 fsb.. 
so my problem is opposite, i want battery not Ghz;)
but with i7 i cant reach more than 1600Mhz on the other extreme.

---

### Post by darkcrawler on 2010-03-19
Then we have the same problem with the i7.. it's strange because my last CPUs (e4600 and e8500 both in OC) never had problems with FSB changes..
I think that the true frequency is however the one set in the bios, Ubuntu can't change the fsb itself, in our case i think it just get a wrong read of it.. So in my situation i **_think_** i have the right frequency but Ubuntu shows a wrong read of it.

Let's hope someone can turn on a light with this issue. ;)

---

### Post by darkcrawler on 2010-03-22
I installed the 2.6.32-02063209 Kernel but nothing changed; always the same wrong frequency shown.. Other ideas on how to solve this issue?

---

### Post by keep you kimi on 2010-03-22
Yeah... I heard it is the 2.6.33 kernel that brings full support to i7 including the turboboost. 
We have to wait till ubuntu 10.10 to solve this.

---

### Post by cascade9 on 2010-03-22
Or complie your own kernel..or run a distro that already has 2.6.33. I've been running 2.6.33 for a while now.....

---

### Post by darkcrawler on 2010-03-22
> **cascade9 said:**
> Or complie your own kernel..or run a distro that already has 2.6.33. I've been running 2.6.33 for a while now.....

Then i could try the 2.6.33 kernel on my Ubuntu 9.10 and see if it solve something..Right? The latest i found is the 2.6.33-020633..

---

### Post by darkcrawler on 2010-03-22
> **darkcrawler said:**
> Then i could try the 2.6.33 kernel on my Ubuntu 9.10 and see if it solve something..Right? The latest i found is the 2.6.33-020633..

I installed the latest 2.6.33-020633 Kernel and still nothing changed.. :confused:

---

### Post by cascade9 on 2010-03-24
Overclocking might be you problem...try it at stock speeds.

---

### Post by darkcrawler on 2010-03-24
> **cascade9 said:**
> Overclocking might be you problem...try it at stock speeds.

At stock it works good, the problem is that Ubuntu doesn't recognise the increase of the bclk..

---

