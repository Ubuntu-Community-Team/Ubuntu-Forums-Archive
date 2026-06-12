---
title: "Acer laptop power management"
date: 2008-10-26
forum: Hardware
---

### Post by micdhack on 2008-10-26
My question is more of an informative one.
Since in windows acer has its one power management application and you can setup what kind of efficiency you need to get from your machine i am wondering whats happening in linux.
For example in windows i have balance mode when running on AC, to use maximum cpu, graphics and when im on batterys to use less in order to preserve energy.
So i am wondering whats the default for linux. I am having maximum performance when on AC or its like i am on batteries.

---

### Post by teaker1s on 2008-10-26
generally the answer would be that performance on ac/batt is the same, unless you enable laptop-mode and then you can make power savings(laptop-mode isn't enabled by default as sometimes causes bugs)

cpu scaling if in operation will work on both ac and battery. benefits are less heat,noise and longer battery life.


Hope this in some way goes to help with your question

---

### Post by micdhack on 2008-10-26
i downloaded kpowersave since its more advanced and i saw that cpu performance is dynamic...which flactuates my cpu frequency from 800 to 2000 depending on how much processing power aplications require.
My next question will be how can i verify if i have laptop-mode enabled or not?

---

### Post by teaker1s on 2008-10-26
Think this may help
[https://wiki.ubuntu.com/PowerManagement]("https://wiki.ubuntu.com/PowerManagement")

---

### Post by micdhack on 2008-10-28
I discovered that gnome also has an utility for this. You can add it on the upper bar. The name is something about CPU frequency(i dont use the english version). There you can specify what kind of scaling do you want (performance, ondemand(which is the default), powersave). You need to have a cpu that supports scaling of course.

So linux by default uses scaling with mode ondemand. Which in my case work fine..when pc is idling so does scaling, but when i play games or something else that requires cpu then scaling maxes.

---

