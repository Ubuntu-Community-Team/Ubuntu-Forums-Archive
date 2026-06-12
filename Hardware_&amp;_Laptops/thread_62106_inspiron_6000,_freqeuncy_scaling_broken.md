---
title: "inspiron 6000, freqeuncy scaling broken"
date: 2005-09-03
forum: Hardware &amp; Laptops
---

### Post by Houman on 2005-09-03
Hi all;
I have an inspiron 6000 centrino 1.86GHz runing ubuntu 5.04, I had set up freqeuncy scaling using the powernowd and everything was working alright, the content of /proc/cpuinfo always reflected the frequency of the cpu which varied in a predictable manner (if i was watching a movie it owuld go higher ...)
this was all good until i read this little howto : [HowTo](http://ubuntuforums.org/showthread.php?t=25510)  talking about cpufreqd, so i installed cpufreqd, and after that the cpu speed always stayed at maximum, i dont understand why this doesnt work and i am reluctant to go back to powernowd because it seems cpufreqd has more features and is more sophisticated than powernowd as can be seen here: [Power Management Guide](http://www.gentoo.org/doc/en/power-management-guide.xml)  

regards;
Houman

---

### Post by mlord on 2005-09-03
Go back to powernowd, simply because it works.  And configure it to use the kernel's "ondemand" CPU frequency governor, which seems to be the best solution for nearly all purposes.

If you're clever, you can do away completely with powernowd and cpufreqd, since neither of them need to be running once "ondemand" is activated in the kernel.  I didn't bother with that, though, and just leave powernowd active, but doing nothing.

Oh.. I suppose the stock Ubuntu 2.6.10 kernel probably does not have the new "ondemand" governor, in which case those daemons probably are needed to do real work.  But there are lots of compelling reasons (including "ondemand") for upgrading to a more modern 2.6.13 kernel..

Cheers

---

### Post by Houman on 2005-09-04
Hi mlord;

thank you for your response, I did just that and went back to powernowd and things are fine now, i guess i should try to download the new kernel but ill wait till breezy comes out as release and see what kernel they ship with it , if its still 2.6.10 ill go with a custom kernel;

actually, one thing i wanted was the gnome applet that you can download for cpufreqd that lets you view info about your cpu in the gnome panel and let the user change cpu freq manually;

thanks again;
Houman

---

