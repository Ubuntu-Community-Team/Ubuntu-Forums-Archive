---
title: "how good dual CPUs work in ubuntu ?"
date: 2006-05-01
forum: Hardware &amp; Laptops
---

### Post by medya on 2006-05-01
hey I have a question ,
800 MHZ CPUs are pretty cheap, I am thinking about buying two of them and buying a dual-cpu supporter motherboard.

would two 800 MHZ Intel CPUs be equal to one 1600 MHZ intel cpu ?
how ubuntu would use two cpus ?

---

### Post by Kethinov on 2006-05-01
The Linux kernel has SMP support which decides on its own how to most efficiently use the two processors. It's handled well.

---

### Post by Jason_25 on 2006-05-01
Two 800 mhz cpus would be better on some tasks and worse on others than a 1600 mhz cpu.  It depends on whether the data you are working on can benefit from parallel processing.  Be sure to install the corresponding smp kernel for your hardware from the repos.

---

### Post by medya on 2006-05-02
thanks for repling,I

I want it for normal use , "surf interent" listen to music, watch movie , do some C++ programming , and sometimes play... and copy CD-Rs , do these things use parrallel processing ? 
can u tell me what uses parralel processing and what uses other thing ?

is dualCPU good for parallel proccessing or it is worse for paralllel ?

what is SMP and how I can install it ?

---

### Post by Jason_25 on 2006-05-02
Well I was referring to the CPU performance focused on one single task.  For doing alot of different things at once, two cpu's would be great too.

The SMP kernel, like all the others are available from the repositories.

---

### Post by medya on 2006-05-02
so why stupid ppl dont buy 2 Cheap CPUs instead of one expensive ?
I can buy two 800 MHZ CPU  for less than $30 .
while a 1.6 GHZ CPU would be more than $100 .

there should be something wrong that ppl dont buy two cpus instead of one cpu.... may be because of power usage... does it use much power ?
do you know any link to tell me more about these thigns ? 
I know nothing .


+by the way do you recommend any good Dual Core Motherboard ?

---

### Post by tribaal on 2006-05-02
Well I am pretty sure you would loose the money on the price of the motherboard... Dual CPU mobos are sensibly more expensive than single CPU mobos.

Of course, this is pure speculation, I never bought or looked for dual CPU motherboards ;)

Plus as Jason_25 said, the 2 CPU setup would be inferior for some tasks. For example you could play Quake3 (using one CPU - 800Mhz) and encode a DVD *at the same time* (800Mhz again). But your playing experience would definately not be as good as if you had one 1,6Ghz CPU, and you would encode a DVD much faster one a single 1,6Ghz, too.

Basically it's "trading quality for quantity" - multitasking.

- trib'

---

### Post by kazad on 2006-05-02
i would buy the Asus A8N32-SLI Deluxe. it's the best dual core mobo out there (pcworld did some reviews and it got top marks) it supports AMD socket 939  FX, X2 Athlon, Sempron also is SLI x16 so you get the full 32x when on SLI. It cost me about $350 and that's canadain. So if you live in the U.S it would be cheaper. I have a AMD X2 4200+ and works like a dream. Mind you you don't have to go for the 4200+ cuz it's pricey.

---

