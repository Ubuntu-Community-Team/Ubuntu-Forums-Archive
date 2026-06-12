---
title: "Using x64 OS on an older machine"
date: 2010-06-09
forum: Hardware
---

### Post by cj66 on 2010-06-09
Hello guys
  This is my first post here at Ubuntu Forums. Been using Ubuntu since Hardy Heron.
  I want to run the Ubuntu 10.04 Lucid Lynx x64 on my almost 2 yr old laptop. It’s a Intel® Core™2 Duo Mobile Processor P8400 3 MB Level 2 cache, 3GB RAM. [These are my complete specs if it would help]("http://is.gd/cJ7dc") 
  This page has details about my [processor]("http://processorfinder.intel.com/details.aspx?sSpec=SLB3R") 
  I cant find any information anywhere which would tell me if it would work fine or not. I don’t wanna install and damage my processor and motherboard if it does indeed not support it. 
  I would really appreciate any help and facts which can lead me in the right direction.
Thank you!
Cheers!

---

### Post by pytheas22 on 2010-06-09
[According to Intel]("http://ark.intel.com/Product.aspx?id=35569"), your Core 2 Duo Processor P8400 is 64-bit, so no problem.  You can install 64-bit Ubuntu 10.04.

Also, there's no need to worry about damaging anything.  If you tried to run a 64-bit operating system on a 32-bit processor, you'd just get an error message saying you can't do it; nothing would be damaged at all.

---

### Post by Sam Fallow on 2010-06-09
My laptop is about the same age\spec, and runs 64bit ubuntu with no issues. 

Just make sure you install the correct 64bit flash player (if you need flash)it's well documented on here.

---

### Post by cascade9 on 2010-06-10
> **cj66 said:**
> I cant find any information anywhere which would tell me if it would work fine or not. I don’t wanna install and damage my processor and motherboard if it does indeed not support it. 

Dont worry, if you try to run a 64bit CD/DVD on a 32bit only system, it will refuse to run, and there will be no damage. 

BTW, from inside linux, you can run the command- 

lshw

Then check the output. What you are looking for is this- 

```
*-cpu
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 1
          bus info: cpu@0
          size: 2500MHz
          capacity: 2500MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv cpufreq

```

If there is 'lm' or 'x86-64' in 'capabilities' then you have a 64bit capable systme ;)

---

### Post by cj66 on 2010-06-11
Wow. The replies really helped. :D 
Thank you guys! :D 
Now Ill be using Ubuntu x64! "D

---

