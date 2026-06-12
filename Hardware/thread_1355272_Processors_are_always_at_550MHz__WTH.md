---
title: "Processors are always at 550MHz???  WTH?"
date: 2009-12-14
forum: Hardware
---

### Post by Digikid on 2009-12-14
Greetings all.

I have a AMD Turion X2 CPU....which should be running at over 2GHz.  However whenever I go and look it appears that they are ALWAYS just at 550MHz.  I have throttling turned off.

Can anyone else confirm this?

---

### Post by Digikid on 2009-12-16
Please advise.

---

### Post by Digikid on 2009-12-19
Keep bumping until I get an answer.  I am a very persistent person.  :D

---

### Post by Dark_Stang on 2009-12-20
What is the exact model of your processor? I too, have an AMD Turion X2 ( TL 58 ) and mine throttle between 800mghz to 1.9ghz.

---

### Post by Digikid on 2009-12-20
[IMG]http://img192.imageshack.us/img192/681/cpuzz.png[/IMG]

A picture is worth 1000 words.  :D.  Had to use Windows for this to work.  :(

This is with the power plan edited to full performance.  Even then....where is my other 1ghz?????

---

### Post by Dark_Stang on 2009-12-20
Your processor is only going to clock as fast as it needs to. Can you add the CPU frequency scaling monitors to your panel? If you can, do that and then run some CPU intense programs or stress tests to see if they scale up.

---

### Post by Ayuthia on 2009-12-20
Mine generally runs at 525MHz but if I try watching something through YouTube, the /proc/cpuinfo results show 2100MHz.

I can't remember which version of Ubuntu you are using (Kubuntu or Ubuntu), but under Kubuntu in the Power Management section of the System Settings, you can edit the Performance profile so that the CPU Frequency Scaling is set to Performance.  If I recall correctly (I am currently in Gentoo), Ubuntu defaults to Dynamic and that causes it to scale down.  I don't recall how to configure it through Ubuntu.

---

