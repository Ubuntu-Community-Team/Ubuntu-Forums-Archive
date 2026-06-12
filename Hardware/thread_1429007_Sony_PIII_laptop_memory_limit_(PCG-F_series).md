---
title: "Sony PIII laptop memory limit (PCG-F series)"
date: 2010-03-13
forum: Hardware
---

### Post by chris1379 on 2010-03-13
Hello all. I know there are quite a few people out there who will be considering Ubuntu on these older Sony Vaio notebooks. They were designed for Windows 98 or Windows 2000 which are being phased out. Other newer operating systems require newer hardware and won't run well on these. Ubuntu can bring them back to life. You may have one of these already or may be considering picking one up cheap because someone else no longer wants it. Some of the models are
[FONT=Arial]Sony VAIO PCG-F520
Sony VAIO PCG-F540
Sony VAIO PCG-F540K
Sony VAIO PCG-F560
Sony VAIO PCG-F560K
Sony VAIO PCG-F570
Sony VAIO PCG-F580
Sony VAIO PCG-F580K
Sony VAIO PCG-F590
Sony VAIO PCG-F590K

Some others that this should apply to are
[/FONT][FONT=Arial]Sony VAIO PCG-F420
Sony VAIO PCG-F430
Sony VAIO PCG-F450
Sony VAIO PCG-F480
Sony VAIO PCG-F480K
Sony VAIO PCG-F490
Sony VAIO PCG-F490K[/FONT]

Sony states that the max memory on these is 256MB, which is 128MB in each of 2 slots. This is probably due to the fact that Sony didn't sell the proper modules to upgrade any further or they weren't available when this was printed. Other laptops like IBM Thinkpads with similar hardware list much higher supported RAM limits. This prompted me to do some research. Since I couldn't find any documented cases of these laptops with more than 256MB of RAM, I decided to try it following the Thinkpad guidelines. The one requirement is that 256MB modules used with the 440BX chipset must be low density. These are usually easily recognized by their 8 chips on each side for a total of 16 chips. Armed with this new revelation, I purchased one Kingston KTM-TP390X/256 from ebay. As expected, it works and I now have 384MB of RAM in my PCG-F580K. When I get a chance, I'll try replacing the other 128MB module with 256MB but I'm almost certain it will work just fine. If anyone else surpasses this alleged 256MB RAM limit, please post it here.

Chris

---

### Post by chris1379 on 2010-05-15
I see this thread has a few views. Is anyone else using more than 256MB on one of these? Can someone verify that 512MB will work?

---

### Post by p_code on 2010-10-25
[FONT=Arial]I have a Sony VAIO PCG-F480 running perfectly with 2 x 256Meg PC100 Low Density SO-DIMMs for a total of 512 Megs. 

This is twice this models originally specified maximum of 256 Megs.

As stated above, I think the original Max 256 Meg specification was more about the maximum size SO-DIMM SDRAM modules that Sony had available when these models were introduced, rather than the maximum capabilities of the 440 BX chip set.

The 256 Meg SO-DIMM modules I am using are the so-called 'Low Density' type with 16 chip (8 chips per side) in a 32Meg x 64bits wide architecture created using a total of 16 each 8 bit wide chips.  

The other alternative 'High Density' modules with 4 bit wide chips or with only 4 chips per side may not work though, so you should try to stay with the 8 bit chip 'Low Density' type RAM modules.

Hope this helps.  [/FONT]:smile:

---

### Post by chris1379 on 2010-10-25
I almost forgot about this thread. I did add another 256MB module and 512MB works just fine. The second one is a Samsung M464S3323BN0-L1L. It is also a 16 chip low-density module.

---

### Post by p_code on 2010-10-25
> **chris1379 said:**
> I almost forgot about this thread. I did add another 256MB module and 512MB works just fine. The second one is a Samsung M464S3323BN0-L1L. It is also a 16 chip low-density module.

I am using the exact same Samsung SO-DIMM part except that the P/N on mine ends with "L1H" instead of "L1L".  

Samsung M464S3323BN0-L1H

Fortunately, in this case that "H" at the end doesn't make them the dreaded 'High Density' type, but simply referes to the fact that they are slightly higher speed CL2 (CAS latency 2 cycles) instead of CL3 parts.

Found them on EBay for 10 bucks each plus 5 dollars in shipping, which made this a fairly inexpensive upgrade.

With the RAM upgrade, [FONT=Arial]the F480 is still not quite up to the demands of streaming HD video, but is more than adequate for word processing, net surfing, email, instant messaging, etc.[/FONT]

---

