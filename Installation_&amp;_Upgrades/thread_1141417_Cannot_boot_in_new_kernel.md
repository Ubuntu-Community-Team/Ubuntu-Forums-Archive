---
title: "Cannot boot in new kernel"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by apparle on 2009-04-28
When I put in live CD I get this error
```
Bug: Int 14: CR2 ffffb0f0
EDI 00000000 ESI 00000000 EBP c0731f3c ESP c0731f1c
EBX 00000046 EDX 0000000e ECX 00000000 EAX ffffb0f0
err 00000000 EIP c0119891 CS 00000060 flg 00010046
Stack: c011a26e 00000046 00000046 00000000 c0731f48 c0118a66 00eefd04 c0731f60
c05009ff c05fb24c c07e1a60 00eefd04 00000000 c0731fb8 c074144c c05f081c
007be000 00000000 00eefd04 00000000 c05f7b84 00100000 00000000 0087c52b
```

[https://bugs.launchpad.net/ubuntu/+bug/366587](https://bugs.launchpad.net/ubuntu/+bug/366587)
this is someone else's bug but I am getting the same problem while his problem seems to have been solved automatically.

Please check the site and help me plz..........
I want to install jaunty but if kernel does not boot then what can I do

---

### Post by apparle on 2009-04-29
Some one plz help me..........I want to try jaunty but I can't

---

### Post by apparle on 2009-04-30
I just used the option "Load Fail Safe values" in BIOS setup.
And I can now boot...................cheers

How to mark this thread as solved??

---

### Post by rMatey on 2009-05-07
Got mine working...  see this thread :[https://bugs.launchpad.net/ubuntu/+bug/366587](https://bugs.launchpad.net/ubuntu/+bug/366587).

  Before you start with the CMOS, write down any settings that you set  before, or like me I highlighted them in my manual. Safe settings will change the unexpected.  Took me all of four minutes to figure out why the keyboard and mouse were on vacation.
   This migh

this might work for you.

---

### Post by Blaze1024 on 2009-09-21
I may have the solution to this issue. 

You might not need to reset your bios 

Try simply Disabling the legacy bios setting "memory hole 15 to 16Mb" This setting should be disabled anyways! 

For some reason my new ASUS P5QC had it enabled.  I could not boot the  2.6.28-15-generic kernel on a Ubuntu  system just upgraded from 8.04LTS > 8.10 > 9.04  

 Disabling the "memory hole 15 to 16Mb" setting solved the problem on this system. Interestingly enough even through I could boot the older Kernel I could not use the CPU frequency adjustment tool until after I disabled the memory hole setting.   

Now all works fine..

---

### Post by apparle on 2009-09-21
I figured that out after sometime....but what is it?

---

### Post by apparle on 2009-09-21
I figured that out after sometime....but what is it?

---

### Post by Blaze1024 on 2009-09-21
> **apparle said:**
> I figured that out after sometime....but what is it?

Are you asking what the Memory hole setting does or is ? 

If so then, This is a legacy setting and I have no idea why its still being used in systems that don't have an ISA buss or expansion slots. 

  If I remember correctly ISA expansion cards use the memory addresses between 15 and 16Mb. Therefor if you have more then 15Mb of memory and use ISA expansion cards you need to enable this setting. 

 Since no modern computers have ISA expansion slots you don't need to enable it. In fact I think Linux has always required you disable it.

You should also make sure you disable all the shadow rom to ram features when using Linux.

---

