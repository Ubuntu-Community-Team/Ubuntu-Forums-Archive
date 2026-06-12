---
title: "Fan problems"
date: 2011-10-26
forum: Hardware
---

### Post by chinchiLa on 2011-10-26
Hello guys :)

I am a new user to linux, and had till now Win7 Ult x64 on my HP laptop. The configurations are:
[LIST]
[*]HP Pavilion dv7-4295us mit Intel Core i7-2630m , 1TB HDD, Amd Radeon HD 6570, 8GB RAM .
[*]It is bought in May this year. :confused:
[/LIST]
Is there anyone who could suggest me or give me a tipp how to solve the problem of overheating the cores. Had anyone experieced something like this before.
 
[LIST]
[*]I couldnt open a case to clean the CPU-s cooler.
[*]The BIOS is also updated,fans cleaned and still it is heating a lot. The temp rises till 70 degrees C.
[/LIST]

And I tought if I installing Ubuntu before this problem appeared but coudldnt in time, so I gave it in tought if I install it now (multi-booting with Win7), would it solve something even if fans are not related with OS. 

PS: All fans are working but as I noticed not "fast", they are really slow...

---

### Post by nothingspecial on 2011-10-26
Thread moved to Hardware and Laptops.

---

### Post by diasf on 2011-10-26
70C max under heavy use (even more if it is games or anything that uses a lot of VGA) is normal. 
BUT, if gets there when idle, then you have a problem. 

Btw, my HP (touchsmart tx2) only makes the fans go faster near 90C. HP is messed up on this kind of stuff....

---

### Post by chinchiLa on 2011-10-26
> **diasf said:**
> 70C max under heavy use (even more if it is games or anything that uses a lot of VGA) is normal. 
BUT, if gets there when idle, then you have a problem. 

Btw, my HP (touchsmart tx2) only makes the fans go faster near 90C. HP is messed up on this kind of stuff....

yes I noticed that already...
but how can I fix my problem, when it gets too hot it also slows down the performance. It is really annoying, I cannot use my lap... 

is there any program with which I can check the fans, are they are working or not ??

---

### Post by diasf on 2011-10-26
If HP made your PC as cheaply as made mine, the sensors barely work. Check lm-sensors, then "sensors-detect" and then "sensors". If you have the sensors hooked up, it will show. Easier way is to just see it, hard to miss something turning that fast :)

Additionally, you might consider a custom cpufreqd.conf file. You can do a lot with it...

---

### Post by chinchiLa on 2011-10-26
> **diasf said:**
> If HP made your PC as cheaply as made mine, the sensors barely work. Check lm-sensors, then "sensors-detect" and then "sensors". If you have the sensors hooked up, it will show. Easier way is to just see it, hard to miss something turning that fast :)

Additionally, you might consider a custom cpufreqd.conf file. You can do a lot with it...

I still do have warranty, but unfourunately I am now in Austria not US;studies, so I cannot use it :/ I am going to buy Cooler with 3 fans,and later go to the technician and let them open the case and check if everything is ok with sensors and fans... What do you think of this solution?? Any tipps?:rolleyes:

---

### Post by blackbird34 on 2011-10-26
What about using the Jupiter applet : [http://ubuntuforums.org/showthread.php?t=1854019](http://ubuntuforums.org/showthread.php?t=1854019)

and reading though this [http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html) 
**[Linux Kernel Power Issue / Overheat Workaround]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html")**

---

