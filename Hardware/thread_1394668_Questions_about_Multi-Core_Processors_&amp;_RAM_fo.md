---
title: "Questions about Multi-Core Processors &amp; RAM for new laptop"
date: 2010-01-30
forum: Hardware
---

### Post by CottonCandy on 2010-01-30
I've been doing a lot of research, trying to figure these things out myself, but I just haven't been able to sort through all the technical terms & numbers to figure out clear answers for my questions. I'm hoping maybe someone here can help. 

I'm planning to buy a new laptop. I need it to be able to handle running multiple programs for hours at a time. I figured this meant a fast processor & lots of RAM. 

A few older articles I read suggested that having lots of RAM was more important for this kind of multi-tasking than the actual speed of the processor. What about now since the dual/quad/multi cores & hyperthreading are out? If I understand correctly RAM will still help, to a point, with multi-tasking & speed. (It seems 2-4GB is 'average' so I guess 6GB would be 'good/better' & 8 would be 'a lot'?) But is the number of cores now more important than the amount of RAM? Are they equally important?

Of course I want to have something fast, but the ability to run multiple programs simultaneously, including Inkscape, GIMP (with lots of layers), Firefox with multiple add-ons & tabs, music player etc. for several hours without lagging/slowing down/crashing is more important. It seems I should be focused on the number of cores & amount of RAM more than the processor speed for this. Is that correct?

This is probably an especially #-on00b kind of question but, can extra RAM help (to a point) increase the performance of a processor with less cores? Say for example a laptop with an Intel Core i5 processor (2 physical/4 HT cores) with 6-8GB RAM vs a laptop with an Intel Core i7 processor (4 physical/8 HT cores) with only 4GB. Would the one with the i5 be able to 'keep up' so to speak, or would the one with i7 be smoother/faster no matter the amount of RAM the one with i5 has because the i7's got more cores? 

Thanks for reading my post. :)

---

### Post by Yellow Pasque on 2010-01-31
> It seems I should be focused on the number of cores & amount of RAM more than the processor speed for this. Is that correct?
IMO, yes. Also, make sure you install 64-bit Ubuntu.

> can extra RAM help (to a point) increase the performance of a processor with less cores?

Extra RAM is only going to help if you've used up all the physical RAM and you're using swap memory (hard disk, SLOOOOOW). Other than that, quad-core will be faster than dual-core at a given clock speed, except maybe some tasks that can't take advantage of > 2 cores (dual-core could be slightly faster because of cache latency).

---

### Post by CottonCandy on 2010-01-31
> **Temüjin said:**
> IMO, yes. Also, make sure you install 64-bit Ubuntu.

Extra RAM is only going to help if you've used up all the physical RAM and you're using swap memory (hard disk, SLOOOOOW). Other than that, quad-core will be faster than dual-core at a given clock speed, except maybe some tasks that can't take advantage of > 2 cores (dual-core could be slightly faster because of cache latency).
Thank you for your help & for the reminder to install 64-bit. :D 
So basically, the more cores the processor has, the better it is for multi-tasking, & there's no such thing as too much RAM? :p heehee My thoughts exactly. :D But it looks like that will have to wait a year or 2 until I can buy or build a desktop computer. 

Would an i5 (dual core with hyperthreading) processor with 6GB RAM be sufficient for the kind of multi-tasking I want to do?
(Running Inkscape, GIMP (lots of layers), Firefox with multiple add-ons & tabs, music player etc. at once for several hours at a time.)

---

### Post by Yellow Pasque on 2010-01-31
Yeah, dual-core with hyperthreading should be good for your use. Quad cores are going to be expensive and much harder to cool in a notebook, otherwise I would say definitely go quad.

> & there's no such thing as too much RAM?
For the most part, yeah, but not if you can only use so much RAM in your max usage (then money is better spent on other components or more beer).

---

### Post by CottonCandy on 2010-01-31
Thank you so much for all your help. :D I very much agree with you. 
I want to get a quad core so I will do that when I can set up a desktop. For now I'll go down a level in the processor so I can afford a good screen. 

If you don't mind answering another question, do I calculate my potential max RAM usage by finding out how much RAM Ubuntu & all the programs I plan on running will use total?

Thanks again for your help!

---

### Post by coldraven on 2010-01-31
I'm probably out of my depth here but you may want to think about virtualization.
This means for example that you can run your legal copy of Win7 or whatever comes installed on your new box in a window inside of Ubuntu. (or fullscreen on another desktop).
Anyway on some laptops virtualization has to be enabled in the BIOS and some others (Sony I think) won't allow it.
This probably will not apply to those hyperthreading thingys. :p
I run XP inside VirtualBox, it's very good.
Have fun!

---

### Post by CottonCandy on 2010-01-31
Thank you. :) I've heard of virtualization but I did not know some laptops (or the companies who make them I guess) may not allow it. For now I don't think it will be a big problem. I've been using a mac for the last few years, so I don't think there's any windows-only programs I would need... though I could play games.
But when I get a desktop later I will want to keep this information in mind because at that time it may be important for me to have a virtual box set up, so thank you for telling me so I can make sure it will be allowed! :D 



Well, I'm off to figure out how to calculate my potential maximum RAM usage. Then back to the laptop hunt. Thanks again to Temüjin & coldraven for replying! I really appreciate it. :D

---

