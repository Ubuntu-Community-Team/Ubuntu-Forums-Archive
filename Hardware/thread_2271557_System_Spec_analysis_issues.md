---
title: "System Spec analysis issues?"
date: 2015-03-31
forum: Hardware
---

### Post by naataxcarr on 2015-03-31
Greetings. I'm gonna admit right away I'm here because I'm confused and quite lost and I don't even know what my problem is let alone how to search for it.

My friend got me a computer as a gift and so I'm trying to look at it's specs and I find myself finding discrepancies.

The salesman said the computer has **AMD A6 5400K APU with Radeon HD Graphics x2 3.6GHz **and a memory card for [B]4 gigs.

[/B]According to this link he seemed correct [http://www.newegg.ca/Product/Product.aspx?Item=N82E16819113282](http://www.newegg.ca/Product/Product.aspx?Item=N82E16819113282)

But my system says my CPU is this. Notice one core is **36.Ghz** and the other is at **1400 Mhz**.... This really confuses me? Why is this? is that normal?! I find the 3.6 label misleading...
[IMG]http://i.imgur.com/Xc3uBYo.png[/IMG]

Next is memory. Says **3 gigs** of memory?
[IMG]http://i.imgur.com/3GBj3cm.png[/IMG]

I went into the BIOS and double checked some things... but I'm a little more confused.

The Bios said my memory is **4 gigs** like the salesman said. So why does my OS read **3 gigs** and why is my free memory only **1.4 gigs** as it says in the picture.

The Bios said my CPU was 
        Speed: **3595.06 Mhz** (this seems more right)
         Clock: **99.85 Mhz** (but why is it clocked at 1/36th the speed?)

---

### Post by QIII on 2015-03-31
Hello!

Part of your memory is reserved by the motherboard for the system, the biggest chunk of which is for your graphics adapter, which doesn't have its own dedicated memory like a graphics card does.  An APU has the CPU and GPU on the same die, so the GPU depends on your RAM for its memory.

The difference in core speeds you see is because the cores are throttled if they are not under load.  That saves power and keeps the CPU cooler.  The speed rises to handle loads.  You would not want to have the gas pedal on the floor in your car while you are at a stop light.  Your CPU, like your car, idles when it's not busy.

---

### Post by naataxcarr on 2015-03-31
Thanks. This cleared up my questions.

:)

---

### Post by mastablasta on 2015-03-31
yeah all seems good to me.

the ram is often taken by applicaitons. so if you need to run them again they will start fast as they are already in RAM. to see system RAM consumtion you need to boot the PC freshly then check the ram usage. a good tool for that are command line tools simply because they themselves have a much smaller CPU and memorry imprint than GUI tools. 

command
```
free -m
```
Will give free memorry.

command
```
top
```
Will open something similar to widnows task manager only in text mode.

command
```
htop
```
*note: works only if htop is installed* will give similar interface than top but it is much imporved. might be easier to read.

if you wish to use a GUI then install something like gkrelm it also has much smaller foot print than default "task manager". another beautiful option is conky but it's a bit more hardcore. :)

anyway the OS on boot should consume between 200 and 400 MB RAM (depends really if you have 64bit installed or 32 bit), GPU chip takes 1 GB (you should be able to lower than in BIOS/UEFI if you need more RAM). so on boot you should have about 2.5 GB left for your applications. more than enough for most of them as well as some games.

---

