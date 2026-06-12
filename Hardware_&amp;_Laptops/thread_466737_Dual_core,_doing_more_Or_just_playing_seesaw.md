---
title: "Dual core, doing more? Or just playing seesaw?"
date: 2007-06-07
forum: Hardware &amp; Laptops
---

### Post by outlaw686 on 2007-06-07
<Heart warming story>
Hey there, 
I'm relatively new to the Linux community. I've been playing with various distro's over the years and one day finally decided just to jump in. Ubuntu is working great for me ever since I learned to use it, (with a few minor bumps along the way) as soon as I installed beryl, windows started looking worse and worse.
</Heart warming story>

Anyway on to the problem, I am running a dual core processor. When I was compiling the latest version of wine (can't live without wow) I opened the system monitor to see how much of my CPU I was using. Typically you think it would almost max out both cpu's. It showed both cpu's, however it seemed like the kernel didn't know how to use them. One would go up, and the other would go down exactly the same time like they were playing teeter-totter with each other. 

This isn't exactly an issue, other than performance, but I wonder if anyone has experienced the same thing or if someone could point me in the right direction to get some information on why this happens. Or, is it just normal?

Uname -r gives me 2.6.20-16-generic   Should I be running something different?
I am running the 32 bit version of "feisty fawn" and haven't tried the 64 bit yet.

If you need any more info let me know, I appreciate your reply. Oh attached is a screen shot of what I saw.

---

### Post by seamuso on 2007-06-07
The more you processes you add, the more cpu you'll use. You can also install something like this -

[http://www.cyberciti.biz/tips/setting-processor-affinity-certain-task-or-process.html](http://www.cyberciti.biz/tips/setting-processor-affinity-certain-task-or-process.html)

and add parameters to your commands to force core/cpu affinity. I used this with folding to get 100% cpu usage when I was idling my system .. prior to setting the affinity, I was running @ 50%

If your building anything and it can be built in parallel, make -j4 will put you right up to 100% on a dual core

---

### Post by trippinnik on 2007-06-07
Most programs will need to be written to be thread aware.  I am not sure how wine handles this, but a lot of programs still don't really take advantage of more CPUs or cores, but running other simultaneous tasks will still be faster.  A few languages do have better built in support (I know Java and probably C# or mono).

---

