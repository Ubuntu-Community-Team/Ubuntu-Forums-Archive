---
title: "AMD 555 and 550 Black Edition"
date: 2010-07-18
forum: Hardware
---

### Post by AltomineUK on 2010-07-18
Hello,

Ok this may be the wrong place to post this but here goes...

I have a PC that runs the AMD 555 X2 Black Edition that runs both Windows and Ubuntu. I did consider the 550 Black Edition, but it had no unlockable cores to make it a quad core. However a friend of mine thinks it's a load of tosh and there are no such things as unlockable cores. 

Someone please confirm that the 555 has unlockable cores and that 550 is a dual core.

---

### Post by cascade9 on 2010-07-18
And here is the 'friend'. Looks like as usual, you are accussing people of 'not reading' when you fail at that yourself. he actually post that started this was- 

> Not the first time you've posted complete tosh, like "old PC's (9-10 years old) all have AGP as well PCI" or "although if you want to unlock two extra cores you have to go for its bigger brother..... 555 Black Edition.".[http://ubuntuforums.org/showthread.php?p=9604585#post9604585](http://ubuntuforums.org/showthread.php?p=9604585#post9604585)

Now, where did I say that "there are no such things as unlockable cores"? I never even suggested that.

What I was saying was that 'you dont need a 555 to unlock cores, the 550 should work as well'. (and I did say that on the thread that lead to that). 

There is no Phemon II 'X2' architecture. They are all X4 or X6 core models, with cores locked. (The X2s should all still be X4s, I havent heard of anyone unlocking a X2 to X6 yet). 

> We managed to activate both blocked cores on our Phenom II X2 550 sample and turn it into a fully-functional quad-core CPU without any effort. By the way, it immediately overclocked to 3.8GHz.[http://www.xbitlabs.com/articles/cpu/display/phenom-athlon-ii-x2_15.html](http://www.xbitlabs.com/articles/cpu/display/phenom-athlon-ii-x2_15.html)

> **THE PHENOM II** X2 550 Black Edition chip is much more than a simple "low-end" Phenom II. First tests show that not only is it a joy to overclock, but if you hook it up to the right mainboard, you can activate all four cores on the processor.             Yes, that's right. The cheapest Phenom II around can have all four cores activated... for free. Using AMD's OverDrive we were able to switch on all four cores through the ACC. Unexpected to say the least.
[http://www.theinquirer.net/inquirer/news/1184444/phenom-ii-x2-550-black-edition-surprise](http://www.theinquirer.net/inquirer/news/1184444/phenom-ii-x2-550-black-edition-surprise)

I personally have a (non-black) X2 550 that unlocks just fine. OK, I'm lying, its not my X2 550, its my housemates, but near enough....

*edit lshw readout as X2- 

> *-cpu
          description: CPU
          product: AMD Phenom(tm) II X2 550 Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Phenom(tm) II X2 550 Processor
          slot: Socket M2
          size: 800MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 200MHz


Readout as X4- 

> *-cpu
          description: CPU
          product: AMD Phenom(tm) II X4 B50 Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Phenom(tm) II X4 B50 Processor
          slot: Socket M2
          size: 3100MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 200MHz


---

### Post by BritishEmperor on 2010-07-18
oh I didn't know that lol...thanks for the info!!!

And please don't use Forums to have fights...be friends and share!!!

---

### Post by tealio on 2010-07-21
I just got the x2 555 and it unlocked in bios, but ubuntu wouldn't boot. I got a kernel panic message. From my reading, this may mean that I got unlucky, and I Got one with damaged cores? Any info on this would be great. 

I still feel like I got a good deal. I easily over clocked from 3.2ghz to 4.0, but I am keeping it at 3.7 because the frequency scaling won't work above 3.7ghz. Also any info on this would be appreciated. I'd like a scalable 4.0 ghz processor...

---

### Post by cascade9 on 2010-07-22
It could be a damaged core...or it could be the motherbaord needs a newer BIOS, or you dont have a big enough power supply...

What motherboard/video card/ram/power supply/etc are you running?

---

