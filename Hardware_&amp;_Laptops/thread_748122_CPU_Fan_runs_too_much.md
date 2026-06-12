---
title: "CPU Fan runs too much"
date: 2008-04-07
forum: Hardware &amp; Laptops
---

### Post by runemaste644 on 2008-04-07
As the title says, my fan is running constantly. When it speeds up, it always stays in that general speed range. The laptop is a lenovo 3000 n100 and fairly new (1 year old) so i dont see what could be wrong. **This happens in both ubuntu and windows** and its obviously a hardware problem (probably dust). Is there any way to reduce the noise?

---

### Post by Toet on 2008-04-07
Is it an intel or amd cpu?

---

### Post by ShogunMaster06 on 2008-04-07
I have a similar issue with an HP 9000 (Intel).  I generally have a number of windows open at once and the problem gets worse if I also have a lot of tabs open in Firefox.  The fans increase in speed as my CPU gets above 30%

I'm interested to see if others are having this issue as well.

---

### Post by pixelhog on 2008-04-07
yep. I got the same issue.
My laptop is an HP dv9000z (amd turion x2).
Its only really bad when running off of the power cord.....when its on battery power its a heck of a lot quieter.
I guess its better to have a cooler running laptop through, so i wouldn't worry about it too much....

---

### Post by pixelhog on 2008-04-07
oh, and im dual booting XP and ubuntu,  and its really quiet in windows.   so theres some issue in ubuntu with the fan speed/ GPU temp

---

### Post by iansyngin on 2008-04-08
dual booting myself with XP / Ubuntu 7.10
On ubuntu, the fan is contantly running at full blast and very annoying.
XP is quite as a mouse.
Onviously this is a driver issue controlling the fan, the question is where do we start to try and solve this problem. anyone?
Running a Dell Latitude D630. I'd be happy to update to Hardy if the latest build resolves this issue.

Ian

---

### Post by DO55 on 2008-04-11
same problem with n100
the fan jump with high speed when the temp reach 50c !!

---

### Post by homeriq5 on 2008-04-11
do you have some sort of acpi program installed on your computer?  Chances are, you have a processor that can support frequency scaling (for example, intel's centrino) but dont have the scaling features for your processor enabled.  Hopefully these links will help:

[http://ubuntuforums.org/showthread.php?t=248867](http://ubuntuforums.org/showthread.php?t=248867)
[http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html](http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html)
[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

---

### Post by DO55 on 2008-04-12
> **homeriq5 said:**
> do you have some sort of acpi program installed on your computer?  Chances are, you have a processor that can support frequency scaling (for example, intel's centrino) but dont have the scaling features for your processor enabled.  Hopefully these links will help:

[http://ubuntuforums.org/showthread.php?t=248867](http://ubuntuforums.org/showthread.php?t=248867)
[http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html](http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html)
[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

i have doucore 1.8

---

### Post by iansyngin on 2008-04-12
installed 8.04 Beta on the Laptop and all is nice and silent now thank god.

---

### Post by digger95 on 2008-04-12
In my experience the newer Linux kernels (I'm currently using 2.6.24.4) have resolved a lot of acpi issues.  My system fans did not operate properly until I upgraded.

---

### Post by iansyngin on 2008-04-12
i presume i'll be able to upgrade to release  version with the beta?

---

### Post by runemaste644 on 2008-04-12
> **Toet said:**
> Is it an intel or amd cpu?
Intel core 2 duo and i think the processor # is 7500

---

### Post by Good_Newz on 2008-04-19
Same problem here. I have an AMD as well. I have frequency scaling enabled. Ubuntu by default is running a lot hotter than xp(which is as quiet as a mouse :)). It might be the graphics card (couse its build into the motherboard) and i am using xorg drivers. Or it could be the frequency scaling - they havent figured out a good algorithm for scaling. You could tweak it yourself [ here ]("http://gentoo-wiki.com/HOWTO_PowerNow!#Too_frequent_frequency_changes") but i dont want to bother. Hopefully the next 8.04 (as iansyngin pointed out) is going to be quieter - will find out in 5 days i guess. I had this problem since 6.10 and doesnt want to go away. 

Cheers guys!

---

