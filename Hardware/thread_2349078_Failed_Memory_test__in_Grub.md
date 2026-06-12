---
title: "Failed Memory test  in Grub"
date: 2017-01-11
forum: Hardware
---

### Post by expatver on 2017-01-11
Asus z97  16gb ram  dual boot Ubuntu 16 LTS  and Windows10..... system fully updated. 3- 1TB spinning HD's. NVidia  graphics, yadayadayada......fairly typical.

Last week Ubuntu shutdown stopped on a memory message (I watch startup and shutdown, like things verbose) and I didnt pay much  attention to it.  Today I had a program error message in Windows 10 (Ninja Trader8-64) about a memory error. Tonight before booting into  Ubuntu I ran the memory test in GRUB. First run I received a test 7 error message, memory address 5443 MB. 57 instances.   Shut the machine down and swapped the sticks around thinking the error might move if in fact it was a hard error. Second run  failed test 10  at 5572MB. 169 instances. I figured ( not understanding well  how the memory test executes what it does even after a bit of reading) that the  failure address would at least be at a different location which it was but not by much (I probably am not supplying enough information here I imagine).  Machine is running fine with the exception of today's error message plus the on shutdown message about the memory error  earlier. I checked  BIOS to see if there had been some sort of change in memory  clock speed or timing (I dont over clock this one) and nothing had changed. . I imagine its time for some more memory, yes?  Question is this....is it something more serious i.e.  a motherboard problem given the address didnt move by much after swapping the stick location....of course if its dual channel memory (and I dont understand exactly how that works)  it might not have moved that much even with the swap...

Any  comments observations or  suggestions would be deeply appreciated. 

Regards and thanks
Expat

---

### Post by sudodus on 2017-01-11
One single error when running memtest a whole night is too much. It can cause many kinds of problems.

Run memtest with each memory stick alone and try to identify which of them is bad and replace it. If you can't identify which of them is bad, or if you cannot find a matching replacement, replace all memory sticks.

---

### Post by expatver on 2017-01-11
New memory earlier today. Unfortunately, considering its DDR3 (and pricey)  and considering where I live- in a small city in Ecuador......there was nothing available other than 4  4GB sticks, Kingston.  Before I had 2 sticks of 8GB each. Now all the memory slots are full. Passes Memtest86+  with absolutely no errors.

With this I have a probably stupid question. Given that I had the error I described in my first post...... and that I am spreading 16GB of memory across 4 slots instead of 2.....it seems like the machine is faster both in Windows and here in Ubuntu. I dont see how it is possible, maybe my imagination  but seems like boot time in both Windows and in Ubuntu is quicker.

Marking this one solved. And for information, I paid $154 for 4 sticks of 4 GB Kingston here.  One store wanted $200 for 2 8GB sticks with a 2 day wait.  

Expat

---

