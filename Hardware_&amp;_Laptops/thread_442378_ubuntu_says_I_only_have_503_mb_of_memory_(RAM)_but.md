---
title: "ubuntu says I only have 503 mb of memory (RAM) but I really have 512 mb"
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by TheRingmaster on 2007-05-13
See the screenshot to know what I mean. I recently removed both my memory chips while I was replacing a cpu fan. I removed because I wanted to blow the dust off. I don't know if this knocked the memory specs down. The one is a centon brand and the other is a Kensington and they are supposed to add up to 512. The screenshot shows that ubuntu only recognizes 503 mb of memory. Maybe this is normal, I don't know.

---

### Post by Spartan.II.117 on 2007-05-13
is your graphics card built into your motherboard?

---

### Post by Kal9001 on 2007-05-13
Its common to see a laptops GPU use system memory as its own cache. although 8MB is a pretty abismal amout. It can sometimes be alterd in your video settings how much exactly it uses. Tho ofcource the lower the value the lower your graphics praformance and there will most likely be a minimum.
If its not this try the sticks in the opposite slots, RAM is a funny old dog and things like that can acctualy make a deiiference. Only other thing after that id if your unhappy witht the low RAM buy annother 512 stick and get 768 (or 760 in your case :P)

---

### Post by TheRingmaster on 2007-05-13
No my graphics card is separate from the motherboard. FYI: This is a custom desktop I am talking about, not a laptop. I will try to remove and reinsert them to see if that makes any difference.

one question: Is is good to mix different brands of memory together. Like I said above, I have a centon and Kensington mix.

---

### Post by jjordan on 2007-05-14
This is not a problem, and while it is unlikely that removing and reinstalling your RAM (again) will casue damage it is possible.  Most likely explanation is something is being cached into RAM befor the operating system is loaded.  You may be able to gain a few MB's by disabiling every type of cahing you can find in the BIOS setup screens but at the cost of a much greater performance impact than the loss of 9MB of RAM.  

You will not be able to detect any diffrence in the performance of 503MB vs. 512MB of RAM.

Different MFRs chips usually work together or if that don't, you will not be able to boot.  It is entirely possible that both memory boards rolled off the same assembly line.

-j

---

### Post by pingvin on 2007-05-14
I found [this]("http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html?sid=619cda6e4dae2a0651c474f9f5e4dfcf") explanation of Linux memory management, mine says I have 1011.5 when I have 1024 really.
Mike

---

### Post by engla on 2007-05-14
Cutting out from the link posted above:
> Notice that I have 512 MB of memory in my machine, but only 503 is listed as available by free. This is mainly because the kernel can't be swapped out, so the memory it occupies could never be freed. There may also be regions of memory reserved for/by the hardware for other purposes as well, depending on the system architecture. 

This means that the "missing RAM" is allocated and reserved by the kernel.

---

### Post by TheRingmaster on 2007-05-14
heres what mine says. So I guess this isn't a problem then. That takes a big monkey off my back. I will still take them out just to see what kind of memory they really are (DDR, DDR2, SDRAM...etc)

> desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           503        497          6          0         61        239
-/+ buffers/cache:        196        307
Swap:         1474          0       1474


---

### Post by TheRingmaster on 2007-05-14
Has anyone had any luck with [this memory]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1779570&Sku=U93-6014")? It is on sale now!

---

