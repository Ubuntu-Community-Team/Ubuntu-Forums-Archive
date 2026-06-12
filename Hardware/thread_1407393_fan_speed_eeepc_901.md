---
title: "fan speed eeepc 901"
date: 2010-02-15
forum: Hardware
---

### Post by vinthund on 2010-02-15
Hello,

I just installed Ubuntu NBR (9.10) on eeepc 901 and experience pretty noisy fan operation, even when CPU hardly work:

```
marek@marek-eee:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +52.0°C  (crit = +90.0°C)                  

eeepc-isa-0000
Adapter: ISA adapter
fan1:       1610 RPM
```

Until this new install fan was rarely ever heard (I used various distros). How can I make it silent? Is it right speed for such a temperature?

I know that this question had already been asked, but I really could not make any use of the answers (like setting BIOS: I do not see any such option in BIOS; so far I'd also rather not paste any scripts nor install any out-of-repo packages, at least until I am sure, that Ubuntu really is not capable of controlling fan speed).

So, finally: is there any Ubuntu package that would fix it? Or maybe you can explain, how to fix it in BIOS (eeepc 901).

---

### Post by josepaul on 2010-02-15
> **vinthund said:**
> Hello,

I just installed Ubuntu NBR on eeepc 901 and experience pretty noisy fan operation, even when CPU hardly work:

```
marek@marek-eee:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +52.0°C  (crit = +90.0°C)                  

eeepc-isa-0000
Adapter: ISA adapter
fan1:       1610 RPM
```

Until this new install fan was rarely ever heard (I used various distros). How can I make it silent? Is it right speed for such a temperature?

I know that this question had already been asked, but I really could not make any use of the answers (like setting BIOS: I do not see any such option in BIOS; so far I'd also rather not paste any scripts nor install any out-of-repo packages, at least until I am sure, that Ubuntu really is not capable of controlling fan speed).

So, finally: is there any Ubuntu package that would fix it? Or maybe you can explain, how to fix it in BIOS (eeepc 901).

Does it go to 52.0°C when its idle?, my processor is at about 28°C when its under about half-load (stock Intel fan), maybe your processor is getting too hot?

---

### Post by josepaul on 2010-02-15
check this out, it might help **[http://en.gentoo-wiki.com/wiki/Asus_Eee_PC_901#Fan]("http://en.gentoo-wiki.com/wiki/Asus_Eee_PC_901#Fan")**

---

### Post by vinthund on 2010-02-15
System monitor graph on panel shows hardly any activity. The only apps that I use are terminal and this sole window in firefox. But still:
```
marek@marek-eee:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +52.0°C  (crit = +90.0°C)                  

eeepc-isa-0000
Adapter: ISA adapter
fan1:       1560 RPM
```
So, is this temperature too high?

---

### Post by josepaul on 2010-02-15
> **vinthund said:**
> System monitor graph on panel shows hardly any activity. The only apps that I use are terminal and this sole window in firefox. But still:
```
marek@marek-eee:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +52.0°C  (crit = +90.0°C)                  

eeepc-isa-0000
Adapter: ISA adapter
fan1:       1560 RPM
```
So, is this temperature too high?

I'm not too familiar with laptops (do they run at a higher temperature? I dunno) but for desktop, this temperature is too high, under my stock cooler, no overclocking, it runs at ~28°C and about your idle temperature 52°C when its under full load

Did you check out the link I sent you, it seems to be able to control the fan speed using a program which increases it in relation to the cpu temperature, also, do you have cpu frequency scaling enabled, cause your processor might be running full on for no reason and maybe thats whats causing this heat?

---

### Post by vinthund on 2010-02-15
1. About this gentoo link - so far I am just not sure, that I need to create own new files to achieve such an ordinary thing as fan control. I think the cause must be elsewhere, so first I'd rather check other possiblities, before I start to install new scripts etc (particularly from gentoo, which I think is in a way something opposite to simple and ready "out of box" (more or less) Ubuntu). I suppose the solution lies within my Eeepc ;) 

2. Maybe the cause is the temperature? It seems it may be comparatively high. How can I enable frequency scaling? Is it in BIOS? If so, then I think I have it enabled.

---

### Post by josepaul on 2010-02-15
> **vinthund said:**
> 
How can I enable frequency scaling? Is it in BIOS? If so, then I think I have it enabled.

try this, right click on the top panel of your computer and click **"Add to Panel"**, then select **"CPU Frequency Scaling Monitor"**

after you do this, left click on the new icon on your panel and change the speed of your CPU, to the lowest you can choose, then see if the temperature goes down and ultimately, if the fan quietens down

---

### Post by josepaul on 2010-02-15
> **vinthund said:**
> 1. About this gentoo link - so far I am just not sure, that I need to create own new files to achieve such an ordinary thing as fan control. I think the cause must be elsewhere, so first I'd rather check other possiblities, before I start to install new scripts etc (particularly from gentoo, which I think is in a way something opposite to simple and ready "out of box" (more or less) Ubuntu). I suppose the solution lies within my Eeepc ;) 


ps, I didn't mean you should install that script or something, just thought it might provide some insight

---

### Post by vinthund on 2010-02-15
> **josepaul said:**
> change the speed of your CPU, to the lowest you can choose, then see if the temperature goes down and ultimately, if the fan quietens down

Thanks, I just tried this and I was able to change frequency between 800 and 1600, but it did not help.

I found however, that temperature of 50-something C is quite ordinary in eeepcs, so I should probably find a way to set fan start temperature to a higher level. I only need to learn, what levels are safe and actually how to do it :)

---

### Post by josepaul on 2010-02-15
> **vinthund said:**
> Thanks, I just tried this and I was able to change frequency between 800 and 1600, but it did not help.

I found however, that temperature of 50-something C is quite ordinary in eeepcs, so I should probably find a way to set fan start temperature to a higher level. I only need to learn, what levels are safe and actually how to do it :)

oh really?, but then again, I'm not that familiar with laptops but anyway, I'm sure there are eee-pc ubuntu owners with the same problem, so good luck :)

---

