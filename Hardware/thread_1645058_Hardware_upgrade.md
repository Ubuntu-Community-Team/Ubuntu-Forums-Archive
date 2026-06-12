---
title: "Hardware upgrade"
date: 2010-12-14
forum: Hardware
---

### Post by P1C0 on 2010-12-14
Hello!

I currently have:
mobo -> ASUS M2NPV-VM
cpu -> AMD Athlon 64 X2 3800+
ram -> SuperTalent 2x1GB DDR2-667MHz CL5
drive -> Seagate Barracuda 80GB 7200 rpm - 8mb cache

And I am about to upgrade:
ram -> Kingston 4x1GB DDR-2 800MHz CL5 (KVR800D2N5)
drive -> Seagate Barracuda 320GB 7200rpm - 16mb cache

What I am interested in, apart from the obvious (bigger storage and bigger ram), is if the athlon X2 processor plays well with a fast memory of 800MHz.
In AMD site it says the memory controller inside supports [DDR2-800MHz]("http://www.amd.com/us/products/desktop/processors/athlon-x2/Pages/amd-athlon-x2-dual-core-processors-key-architectural-features.aspx"), but googling around there are some people saying it actually doesn't do very good use of a fast memory (bad memory controller) and some that state that DDR2-800 is the memory to go for, because only then you will reach the full potential of the CPU.  

Actually I needed the bigger ram, but if it comes with a performance gain it would be even better.  
So I'm just asking out of interest and curiosity, in hope of learning sth :)

Thank you.

edit://I forgot about the gpu, it is a Palit GeForce 210 DDR2-1024mb/128bit, love the frog.

---

### Post by mastablasta on 2010-12-14
> **P1C0 said:**
>  
What I am interested in, apart from the obvious (bigger storage and bigger ram), is if the athlon X2 processor plays well with a fast memory of 800MHz.

yes, as long as the motherboard plays well with (supports) the RAM ;-) Now it's already DDR3 available with 1300Mhz... but older motherboards might not support that.

---

### Post by gradinaruvasile on 2010-12-14
I would say that there will be no major performance improvements. Maybe if you run programs that use memory heavily. But i have 2 GB and i had never have any memory shortage related slowdowns on Linux (i playe wine-based games).
I had 533 MHz memory before and upgraded ito to 800 MHz and felt no big difference (probably the single core CPU was the bottleneck here).

A real performance gain for me was upgrading my Athlon 3200+ to a Athlon II 250 x2 and my M2V-TVM mobo to M3N78-VM. I use the same 800 MHz memory as before but the performance cannot be compared.

---

### Post by cascade9 on 2010-12-14
> **P1C0 said:**
> Hello!

I currently have:
mobo -> ASUS M2NPV-VM
cpu -> AMD Athlon 64 X2 3800+
ram -> SuperTalent 2x1GB DDR2-667MHz CL5
drive -> Seagate Barracuda 80GB 7200 rpm - 8mb cache

And I am about to upgrade:
ram -> Kingston 4x1GB DDR-2 800MHz CL5 (KVR800D2N5)
drive -> Seagate Barracuda 320GB 7200rpm - 16mb cache

What I am interested in, apart from the obvious (bigger storage and bigger ram), is if the athlon X2 processor plays well with a fast memory of 800MHz.
In AMD site it says the memory controller inside supports [DDR2-800MHz]("http://www.amd.com/us/products/desktop/processors/athlon-x2/Pages/amd-athlon-x2-dual-core-processors-key-architectural-features.aspx"), but googling around there are some people saying it actually doesn't do very good use of a fast memory (bad memory controller) and some that state that DDR2-800 is the memory to go for, because only then you will reach the full potential of the CPU.  

Actually I needed the bigger ram, but if it comes with a performance gain it would be even better.  
So I'm just asking out of interest and curiosity, in hope of learning sth :)

The athlon 3800+ likes DDR2-800. You can argue all day about if it 'needs' DDR2-800, they work with slower RAM, but to get the most out of a 3800+ you do need at least DDR2-800. 

The other thing that makes a difference is CAS rating. Lower CAS = faster RAM. In some ways, you are better off with slower RAM with a lower CAS rating than faster RAM with a higher CAS rating. 

BTW, why 4 x 1GB sticks? It would be cheaper and easier to get 2 x 2GB sticks. I'd also think about a bigger HDD......they arent much more expensive and the higher data density on the bigger drives make them faster.

---

### Post by P1C0 on 2010-12-14
Thanx for all the answers!

> BTW, why 4 x 1GB sticks?
They were in the qualified vendor list of the mobo and also in a good price :D Just wanted to freshen up a little bit the "old box", since I won't be doing any serious upgrades for as long as it lasts. 

And to be honest I wouldn't even need the +2GB of memory, but I also need to run win 7 and they were taking 51% of ram on a clean install with just msn and a firefox tab open.
It's scary to think what would happen with postreSQL, eclipse, netbeans, thunderbird, apache, media player, ANTIVIRUS, etc, running in the background.

---

### Post by P1C0 on 2010-12-15
I installed the new RAM today and ran hardinfo benchmark.

Before (2GB - 667MHz):
CPU Blowfish -> 9.337 (lower is better)
CPU Cryptohash -> 132.729 (higher is better)
CPU Fibonacci -> 3.664 (lower is better)
CPU N-Queens -> 19.448 (lower is better)
FPU FFT -> 8.550 (lower is better)
FPU Raytracing -> 14.292 (lower is better)

After (4GB - 800MHz):
CPU Blowfish -> 9.041 (lower is better)
CPU Cryptohash -> 136.735 (higher is better)
CPU Fibonacci -> 3.922 (lower is better)
CPU N-Queens -> 18.353 (lower is better)
FPU FFT -> 8.471 (lower is better)
FPU Raytracing -> 13.926 (lower is better)

Only fibonacci is worse, I dunno why..

Windows sees 4.0GB (4094M) of RAM whereas Ubuntu 3.9GB (3962M). Both OSes are 64 bit.
This is really not an issue, but I wonder why.

---

### Post by cascade9 on 2010-12-16
> **P1C0 said:**
> I installed the new RAM today and ran hardinfo benchmark.

Only fibonacci is worse, I dunno why..

Windows sees 4.0GB (4094M) of RAM whereas Ubuntu 3.9GB (3962M). Both OSes are 64 bit.
This is really not an issue, but I wonder why.

Hardinfo isnt really that great at benchmarking. It sort of works, but its not great. 

Windows is fibbing. It can probably only see 3962MB as well, just its saying 4GB.

*edit- I'd check in your BIOS and see what the CAS ratings are set at. Sometiems RAM wont run at maximum CAS rating untill you tell it to.

---

### Post by P1C0 on 2010-12-16
> **cascade9 said:**
> Hardinfo isnt really that great at benchmarking. It sort of works, but its not great. 

Windows is fibbing. It can probably only see 3962MB as well, just its saying 4GB.

*edit- I'd check in your BIOS and see what the CAS ratings are set at. Sometiems RAM wont run at maximum CAS rating untill you tell it to.Hardinfo probably doesn't make much use of memory, but focuses on the CPU.

I had a "memory calculations per second" index of 5.5 in win 7 and after installing new memory it climbed up to 6.4. (higher is better)
Also I have better timings for my own programs.

About Ubuntu showing 3.9gb available, I googled around and it is normal since "the OS has to live somewhere", so yes Windows kind of lies.

---

