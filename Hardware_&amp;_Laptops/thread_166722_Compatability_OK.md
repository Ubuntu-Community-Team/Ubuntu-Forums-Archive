---
title: "Compatability OK???"
date: 2006-04-26
forum: Hardware &amp; Laptops
---

### Post by xelink on 2006-04-26
I have recently purchased and should be receiving/have received the following

AMD Opteron 165 socket 939(just think of it as an Athlon X2 which begs for overclocking)
DFI Ultra-D Motherboard
7800GT(trying to swap it for a 7900GT via EVGA's Stepup program)
2GB DDR500sd RAM

and am wondering as to how linux compatable(ubuntu in specific) these parts are. I've seen people here recomending the Ultra-D and woudl have gotten it regardless to how good I've heard it to be on other tech forums, though I'm wondering about it's ethernet and integrated sound(I think it uses something better than AC97 as I heard the sound on it is good) and I opted for a nVidia card for linux support, though I don't know if it's supported fully yet or if I will be in VESA-land... I am also wondering about running a dual core proc.

is there anything I should know about firsthand before assembling my beauty?

---

### Post by nanotube on 2006-04-27
well, first thing you should know is to seat your memory well. and to make sure you get good thermal compound if you are gonna be overclocking. :)

best thing for hardware compat is to get a livecd, and see how that plays with your hardware. if breezy doesnt detect something, then try the dapper beta. dual core processors are supported, both with regular kernel (but you cant take advantage of the dual-coreness) as well as with the smp kernel. 
so ... enjoy. :)

---

### Post by xelink on 2006-04-27
would it be to my advantage to just go daper straight off, or would I be fine just using the 686 kernal? I am a bit of a linux beginner though and enjoy the conveneince of automatix... I've done a little research, but not a phenominal amount. 

I am assuming my motherboard is well supported, am I correct in that?

also, while I am thinking about ti, should I be fine without swap space, I have 2 GB of ram?

I'm also comparing myself tot his guy
[http://ubuntuforums.org/showthread.php?p=680910&highlight=ultra-d#post680910](http://ubuntuforums.org/showthread.php?p=680910&highlight=ultra-d#post680910)

---

### Post by nanotube on 2006-04-27
[QUOTE=xelink]would it be to my advantage to just go daper straight off, or would I be fine just using the 686 kernal? I am a bit of a linux beginner though and enjoy the conveneince of automatix... I've done a little research, but not a phenominal amount. [/quote]

both dapper and breezy have a 686 kernel... so it's not about the kernel really. if breezy works with all your hardware, stick with breezy until dapper is released. i would say go to dapper only if breezy has problems, because after all, dapper is still "beta".

> I am assuming my motherboard is well supported, am I correct in that?

not sure. you should look around and see.

> also, while I am thinking about ti, should I be fine without swap space, I have 2 GB of ram?

it never hurts to put in like 500m of swap, "just in case". but yea, with 2gb you would be ok without any swap.

---

### Post by Ocxic on 2006-04-27
with 2 GB of ram, you could do without, the swap space, I only have 1GB and I don't use a swap, haven't had any problems yet.

---

