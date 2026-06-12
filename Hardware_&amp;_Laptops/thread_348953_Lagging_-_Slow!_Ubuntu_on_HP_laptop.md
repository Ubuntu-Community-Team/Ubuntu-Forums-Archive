---
title: "Lagging - Slow! Ubuntu on HP laptop"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by mmjau on 2007-01-29
Hi!

When I installed ubuntu it was a VERY slow installation. Took some hours, since when i clicked somewhere it didn't respond until like 10 minutes passed. 
Same with all live-cds no matter what version I tried and how much i reinstalled and installed ubuntu. 

My laptop specs ([http://www.inet.se/artikel/1968029](http://www.inet.se/artikel/1968029)) - ATI Radeon Xpress 1150, AMD Sempron 3500+ (1,8GHz) 

It takes like 5 minutes for ubuntu to start and when the login screen is loading it lags! When I'm finally in it also takes like 5 minutes to open the terminal and glxgears is SOO slow. 

When using glxgears -printfps it shows:
181 frames in 15.4 seconds = 11.716 FPS
114 frames in 14.9 seconds = 7.639 FPS

etc..

I tried doing this:
[https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy](https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy)
but it is not helping!!

What should I do?

---

### Post by Paerez on 2007-01-29
what is the output of:
```
sudo hdparm -d /dev/hda
```

---

### Post by K.Mandla on 2007-01-29
Are you using the native ATI driver, or the default Ubuntu video driver?

Try changing the driver to *vesa* in your xorg.conf file, and see if that helps. It'll probably make things worse, but at least you'll have an idea if your problem is video-related or something else.

---

### Post by mmjau on 2007-01-29
> **Paerez said:**
> what is the output of:
```
sudo hdparm -d /dev/hda
```


it's 
using_dma     = 1 (on) 

is that good? :)

---

### Post by mmjau on 2007-01-29
> **K.Mandla said:**
> Are you using the native ATI driver, or the default Ubuntu video driver?

Try changing the driver to *vesa* in your xorg.conf file, and see if that helps. It'll probably make things worse, but at least you'll have an idea if your problem is video-related or something else.

it sais in section device in the file:
Driver "ati"
ill try to change it then, brb!

---

### Post by Paerez on 2007-01-29
dma should be on. So I guess that's good (unless good=problem solved).

It's weird that it took a while to install.

whats the output of:
```
cat /proc/cpuinfo
```

---

### Post by mmjau on 2007-01-29
> **K.Mandla said:**
> Are you using the native ATI driver, or the default Ubuntu video driver?

Try changing the driver to *vesa* in your xorg.conf file, and see if that helps. It'll probably make things worse, but at least you'll have an idea if your problem is video-related or something else.

didn't change anything ;/ just got a weird blackscreen once, but still same lag ;/

---

### Post by mmjau on 2007-01-29
> **Paerez said:**
> dma should be on. So I guess that's good (unless good=problem solved).

It's weird that it took a while to install.

whats the output of:
```
cat /proc/cpuinfo
```

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 76
model name	: Mobile AMD Sempron (tm) Processor 3500+
stepping	: 2
cpu Mhz		: 798.101
cache size	: 512 Kb
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni cx16 lahf_lm
bogomips	: 1598.56

---

### Post by mmjau on 2007-01-30
do u see anything wrong? should I post something more? Using reiserfs, could that be the problem?

---

### Post by Paerez on 2007-01-30
Your cpu is running at 800mhz, which is weird.

Run this and paste the output:
```
sudo /etc/init.d/powernowd restart
```

---

### Post by mmjau on 2007-01-30
> **Paerez said:**
> Your cpu is running at 800mhz, which is weird.

Run this and paste the output:
```
sudo /etc/init.d/powernowd restart
```

oh, yes.. that's odd. maybe it isnt the graphics card then?

it said:
* Stopping powernowd:                    [ ok ]
* Starting powernowd...                   [ ok ]

how do I make it go in 1,8 ghz like it is supposed too?

thanks for your time btw

---

### Post by petri on 2007-01-30
Nope, those new CPUs should have some kind of variation in speed - don't run fast when you don't have to.


I'm prety sure you need to install ATI drivers. Try these ATI installation howtos

Edgy: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
Dapper: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)


First Method 1 and if it didn't help then Method 2.

---

### Post by mmjau on 2007-01-31
> **petri said:**
> Nope, those new CPUs should have some kind of variation in speed - don't run fast when you don't have to.


I'm prety sure you need to install ATI drivers. Try these ATI installation howtos

Edgy: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
Dapper: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)


First Method 1 and if it didn't help then Method 2.


didnt work with nr 1 ;/ ill try 2 tomorrow!

---

