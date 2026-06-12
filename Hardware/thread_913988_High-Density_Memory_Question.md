---
title: "High-Density Memory Question"
date: 2008-09-08
forum: Hardware
---

### Post by Jim_Rogers on 2008-09-08
Hello--

I recently upgraded the memory in my Thinkpad x31 to 2GB.

Due to my own confusion, I believe I bought high-density memory. After some study, I have found some debate over the merits of high density memory. This guy says it's bad, bad, bad:

[http://reviews.ebay.com/Myth-Low-Density-vs-High-Density-memory-modules_W0QQugidZ10000000001236178]("http://reviews.ebay.com/Myth-Low-Density-vs-High-Density-memory-modules_W0QQugidZ10000000001236178")


This guy says the first guy is wrong-- if your machine can use high-density, it's a great deal:

[http://reviews.ebay.com/MythBUSTED-Density-FACTS-Low-Density-vs-High-Density_W0QQugidZ10000000003939852]("http://reviews.ebay.com/MythBUSTED-Density-FACTS-Low-Density-vs-High-Density_W0QQugidZ10000000003939852")


Question 1: Apparently, one of the symptoms of a machine not being able to handle high density is that it will only recognize half of it. In my machine, top, dmidecode, lshw, and the system monitor all show a full 2GB. Is that a pretty good indicator that it can use high density? Is it possible these commands are fooled by high-density? Any other command to verify it's OK or not?

Question 2: Assuming the machine can handle high-density, is there a downside to it? In the links provided, there is debate about speed. I have another identical machine that I will likely upgrade. Should I take advantage of the low-price, high-density memory (based on the results from the first machine), or would I achieve better performance if I fork out for the low-density.

Thanks,

Jim

---

### Post by redoscar3 on 2008-09-08
Don't quote me on this, but my understanding of the compatibility of high density memory has a lot to do with the chipset used by your computer.  All my machines are old AMD Socket 462 based and I have never had any problems with high density DDR PC3200 memory modules.  However, computers with Intel chipsets that could use DDR PC2700/3200 memory, were usually not compatible with the high density variety.

I don't know the type of memory (DDR, DDR2) you are using, but this could be a hint as to why you may have compatibility issues.

Red

---

### Post by Jim_Rogers on 2008-09-08
> **redoscar3 said:**
> 

I don't know the type of memory (DDR, DDR2) you are using, but this could be a hint as to why you may have compatibility issues.

Red

I believe what I'm using is DDR.

However, my question is motivated by the fact that I think I'm *not* having compatibility issues as my machine appears to recognize all 2GB I installed.

I'm looking for 1.) confirmation (through personal response or suggestion of a test/command) that, if the machine recognizes all of the memory, all is well, 2.) opinions as to whether, even if it's compatible, high-denisity is the optimal way to go.

--Jim

---

### Post by ecsdrive on 2008-09-08
How much is reported by the BIOS, if it's 2Gig then in (probably) 99% of the cases it's alright
There is a boot option called memtest which does what it says: memory tests - it should not just report the memory you have installed but also check it throughly
Last userspace test, just run free -m you should see at Mem Total about 2000 (MB) more or less depeding on you video card

---

### Post by Jim_Rogers on 2008-09-09
> **ecsdrive said:**
> How much is reported by the BIOS, if it's 2Gig then in (probably) 99% of the cases it's alright

The BIOS does recognize all 2GB.

> **ecsdrive said:**
> There is a boot option called memtest which does what it says: memory tests - it should not just report the memory you have installed but also check it throughly

Thanks for that suggestion. I've seen that option a million time while booting up, and it never dawned on me to try it!

I've learned that memtest can take days to complete. I let mine go 17 hours, it completed 10 tests with no errors. Most consider that enough to mean there are no problems.

But, related to my original question, memtest does recognize all 2GB.


> **ecsdrive said:**
> Last userspace test, just run free -m you should see at Mem Total about 2000 (MB) more or less depeding on you video card

I forgot to include free in the original things I tried, but I did indeed try it and it saw 2GB.

To recap:

free, top, dmidecode, lshw, the system monitor, memtest and the BIOS all show the correct amount of 2GB. So unless high-density ram is super-tricky and able to fool all those tests, I'm going to conclude that my system can handle high-density memory just fine!

Still wondering if there's a down-side to it (e,g., any significant reduction in speed), but that's kind of an esoteric question that is perhaps not easily answerable.

Thanks for the help,

--Jim

---

### Post by ecsdrive on 2008-09-10
Jim, it's probably just marketing "mumbo-jumbo" so you don't have to worry for anything not going at full speed :popcorn:

---

