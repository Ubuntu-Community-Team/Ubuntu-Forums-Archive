---
title: "Laptop hotter than expected"
date: 2012-02-24
forum: Hardware
---

### Post by frohfroh on 2012-02-24
Hi,
I've had a laptop for about two months, I've always been surprised by how noisy it was, and the fan seems to be running at all times. I checked therefore its temperature with lm-sensors, and found that its cores are at idle somewhere between 50 and 55 °C. I then used cpufrequtils to see at which frequency they were running, and found that all cores were at the minimum frequency (800).
I'm somewhat persuaded that this is right, because when it is under charge, the fan will go much noisier and temperature will go up to 80 °C. I thought that was normal and didn't spend any more time on that, till today.
I had to boot in another operating system to get a printer working for the first time, and to my surprise, it was very quiet. I decided to check its temperature when it was running this os, and at idle it was somewhere around 37 to 40.  
One may think there is no big difference between 40 and 50, but in the first case it was with fans off and in the second case with fans on.
I wonder what is going on, and if I can get it to run Ubuntu cooler and quieter

the cpu is an i7-2670QM CPU @ 2.20GHz
the laptop is Hp Pavilion dv6-6b71ef 15,6"

---

### Post by winh8r on 2012-02-24
First thing to check is that all the vents are free and there are no obstructions cause by dust etc,

Another common cause of overheating is a failing battery, so get your battery checked out too.

There are other threads on the forum where users have experienced similar issues.

---

### Post by prasadyc on 2012-02-24
I am using lenovo z560 it is having same problem it get more hottet than that of using windows on same laptop..............pls help
And also consuming more power

---

### Post by frohfroh on 2012-02-24
Thank you winh8R for your answer.
As the laptop is not yet two months old, I doubt there is too much dust inside. As for the battery, the laptop is currently plugged in and the battery is stored away.
But the point is that when running the other os, the temperature is kept much lower - and without the fan. 
I did see a few threads, but people were discussing if the cpu frequecy was being correctly set, and for the reasons I've exposed, I do think it is.

---

### Post by ahallubuntu on 2012-02-24
I agree - dust and dirt is a common cause of overheating on older laptops but it shouldn't be an issue on a two month old laptop.

Honestly, I'd expect an i7 to run pretty hot in a laptop.  Seems a bit of overkill to me, anyway, but I guess people want a super-fast CPU in everything these days.  Intel's spec on the i7-2670QM is only 45 Watt TDP, which doesn't seem horrible but how hot the laptop gets also depends a lot on the laptop design itself, what kind of graphics card you have, etc.   Google says you have a dedicated AMD graphics card in that laptop, too - so I'm not surprised at all that this thing is a heater.

FYI, when I upgraded the Core 2 Duo CPU in my Dell laptop, I got a faster CPU but one that has a lower TDP - I went from 35 Watt to 25 Watt, because I wanted a cooler design and presumably a little better battery life.

---

### Post by frohfroh on 2012-02-24
now you've said it, I thought about it and you're probably right.  As it is a switchable graphics laptop, tho other os most likely turn down the  dedicated graphics card at idle, while ubuntu keeps it running all the time.
Thank you, the noise will stay, but at least I (think I) know why

---

### Post by 0011235813 on 2012-02-24
My best guess for this is that Ubuntu is using the GPU on board, and the GPU is making a lot of heat and noise. Personally, if I want high performance, I'd want a desktop, not a laptop.

But in regards to your problem, have you checked drivers? Some GPUs allow the use of Intel integrated on idle to save power, but not having a properly installed driver could disable that function.

---

### Post by frohfroh on 2012-02-24
I guess that's what is happening. The proprietary graphics simply do not work, so I uninstalled it, and Ubuntu is using the default driver. I am pretty sure that means that the dedicated card is turned on all the time, because when I run lm-sensors I can see it's about 70° all the time.
I am not sure if this switchable graphics are or are not working in Ubuntu, there are an infinity of threads and they seem to get real complicated, and my BIOS does not allow me to simply disable one of them.
I'm somewhat puzzled by that increasing the CPU temperature by about 15K, but maybe that is normal?I've been also wondering, maybe the graphics card has a specific fan, and that's the fan I hear all the time?
Anyways, it's not a big deal, 60° C  is not too hot

---

