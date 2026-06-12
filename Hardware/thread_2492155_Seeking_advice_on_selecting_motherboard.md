---
title: "Seeking advice on selecting motherboard"
date: 2023-11-01
forum: Hardware
---

### Post by satimis on 2023-11-01
Hi all,

I'm going to build a new desktop PC.  Please suggest a motherboard for
**[COLOR="#FF0000"]AMD Ryzen 9 7950X Processor 16C 32T Socket AM5[/COLOR]**

I don't game neither I need WiFi.  I'm prepared to build a fast desktop PC running Oracle VirtualBox.

**RAM 64G DDR4/DDR5**

My preference is ASUS motherboard.  I have been running ASUS motherboards on other PCs for years without problem.  But also I'll consider other brands suggested.

I have no preset budget but don't expect to get a too expensive motherboad.

Thanks in advance.

Regards

---

### Post by aljames2 on 2023-11-03
Well you have the makings of a beast of a machine, a ton of horsepower.

I like the Asus ROG series of boards.  A requirement of any board I get is it must have an Intel NIC.  I also look for no wifi, although it's not a deal breaker if it has it because I can disable them.  

Most of the AMD CPUs do support ECC ram now, and your does, BUT if using error correcting RAM is important to you, then check to be sure the mobo also support ECC.  However, if you've already bought the RAM and it's not ECC then probably not worth re-buying your RAM.  Most folks aren't looking for ECC RAM unless maybe if running ZFS, and even then it's not required, but also other OS's that natively run on ZFS like FreeBSD, and others.  ZFS likes ECC ram.

---

### Post by satimis on 2023-11-03
> **aljames2 said:**
> Well you have the makings of a beast of a machine, a ton of horsepower.

I like the Asus ROG series of boards.  A requirement of any board I get is it must have an Intel NIC.  I also look for no wifi, although it's not a deal breaker if it has it because I can disable them.  

Most of the AMD CPUs do support ECC ram now, and your does, BUT if using error correcting RAM is important to you, then check to be sure the mobo also support ECC.  However, if you've already bought the RAM and it's not ECC then probably not worth re-buying your RAM.  Most folks aren't looking for ECC RAM unless maybe if running ZFS, and even then it's not required, but also other OS's that natively run on ZFS like FreeBSD, and others.  ZFS likes ECC ram.
Hi,

Lot of thanks for your advice.

On further checking AMD Ryzen 9 7950X CPU
[https://www.amd.com/en/products/cpu/amd-ryzen-9-7950x](https://www.amd.com/en/products/cpu/amd-ryzen-9-7950x)

it requires Liquid cooler.

I'm not prepared installing Liquid cooler, considering to down-grade the CPU.  What will be your suggestion, next to 'AMD Ryzen 9 7950X Processor 16C 32T Socket AM5' ?

Thanks

---

### Post by aljames2 on 2023-11-03
> **satimis said:**
> 
it requires Liquid cooler.

And, it consumes 170w of power.

I think it comes down to what you want to do with your hardware. What will you be running on it?  Do you want it to be a 24/7 "always on" machine like for hosing servers.  Is it mostly for gaming, or video editing & rendering?  Are any of these important to you:  1) power consumption, 2) noise, 3) heat generated.  A lot of things to consider.

---

### Post by aljames2 on 2023-11-03
My latest build this past summer was:

Asus ROG Strix B550-A Gaming  (although I don't game on it)
Ryzen 5600x
A-Tech 32gb ddr4 ecc ram
NZXT C850 Gold PSW
Nvidia GT 1030  (low end but perfect for my use)

Overkill for even what I do but it runs all the time, quiet, and serves up 6 VMs for various things.  A lot of room to grow as well.

Don't go with what I did, but get what you want, considering what you want to do with your rig.

---

### Post by satimis on 2023-11-04
Hi aljames2,

Thanks for your advice.

I have following desktop PCs
1) AMD Ryzen 5 8-core PC with 32G RAM onboard (running for long time)

2) AMD Ryzen 7 8-core PC with 32G RAM onboard (built about 6 years ago)

I won't build another AMD Ryzen 5 or 7 desktop PC.  Neither I would run the new PC 24/7.  I'll run Oracle Virtualbox on this new PC with 40 websites serving only local network.

I don't game but I'll do graphic editing occasionally.

Now I'm considering to use an air cooler instead.  Following Thermalright coolers are available on local computer shops here;
1)
Thermalright Peerless Assassin 120 SE ARGB WHITE 
2)
Thermalright Phantom Spirit 120 SE
3)
Thermalright Peerless Assassin 120 PA120
4)
Thermalright Assassin X 120 Refined SE PLUS CPU Cooler AX120 R SE PLUS

etc.

Which model you'll recommend?

Thanks

Regards

---

### Post by aljames2 on 2023-11-04
There are a lot of choices in coolers I see.  Depending on the cpu you choose, if it will be happy with an air cooler, I would check sizes of each and see if any fitting issues within your case and other components.  I bought a cooler once that crowded my ram sockets more than I liked. I have had good luck with using cpu fans that come packages with some cpus.  I don&#8217;t choose RGB if I have other options, just my taste.  Did you decide on a different cpu, or are you going with the same one in you OP?

---

### Post by satimis on 2023-11-04
> **aljames2 said:**
> - snip -Did you decide on a different cpu, or are you going with the same one in you OP?
I'll stick on AMD Ryzen 9 7950X CPU

Regards

---

### Post by Yellow Pasque on 2023-11-04
Might as well move up to the 7950X3D (or drop back to the 7900X3D if you can live with "only" 12C/24T) if you're going to use air cooling. Those are newer revisions that have a 120W TDP instead of the 170W of the 7950X.

---

