---
title: "trying to optimize my RAM"
date: 2012-04-10
forum: Hardware
---

### Post by hopefulkayaker on 2012-04-10
I'm pretty green when it comes to hardware. I have a Dell Inspiron 530 desktop, which is only 2 or 3 years old, so I will not be in the market for a new computer for quite some time. So in the meantime, I'm interested in maximizing the speed of that current desktop.

Using CPU-G I know the following:

CPU: Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz
RAM: 3GB

I've also read that my motherboard supports the following kinds of RAM: DDR2 PC2-5300, DDR2 PC2-6400, and DDR2 (non-ECC). (This is the only page I've found which talks about that: [http://www.myfreetechsupport.com/hardware/memory/dell-inspiron-530s-memory-upgrade](http://www.myfreetechsupport.com/hardware/memory/dell-inspiron-530s-memory-upgrade))

I know I have 2 DIMMS, and that they are both currently in use. 

So...I have some questions:

1 - How can I confirm that list of compatible type of RAM for my system?

2 - How can I determine exactly what kind of RAM each of the two sticks I'm using are?

3 - Is the difference in speed/performance between the three RAM types listed significant enough that I should replace the slowest of the three, if I'm using any, with the fastest?

4 - Which of those three is fastest? Which is in the middle? Which is slowest?

---

### Post by Ms. Daisy on 2012-04-12
1. Look at the specs of your machine. I found them here: [http://reviews.cnet.com/desktops/dell-inspiron-530/4507-3118_7-32953389.html](http://reviews.cnet.com/desktops/dell-inspiron-530/4507-3118_7-32953389.html) (make sure that's really the right one)

2. There's probably a prettier command to use, but this will list what you've got
```
sudo lshw -class memory
```

3. According to the spec I gave you above, your computer is designed for 5300.  

4. I would think that because your computer was designed for 5300, then that would be the fastest option.  But hopefully you'll get some other opinions on that.

---

### Post by hopefulkayaker on 2012-04-12
Thank you for your help. I managed to figure it out both with the help of a friend, and opening my computer case. Looking inside I discovered all four sticks of RAM I currently have installed are PC2-6400, two of which shipped with the system.

So I'm going to get more PC2-6400, which apparently is the same thing as saying I'm going to get DDR2 800mHz RAM.

---

