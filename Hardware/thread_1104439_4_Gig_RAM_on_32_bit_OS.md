---
title: "4 Gig RAM on 32 bit OS"
date: 2009-03-23
forum: Hardware
---

### Post by Ravernomina on 2009-03-23
Hi.... i recently just bought and installed 4 gigs of DDR 2 memory on ubuntu 8.10 32 bit on my computer. When i go into system monitor it only says i have 3 gigs. Is this normal like What windows does? if so let me know cuz im a little worried..... 
TYVM!!!

      Ravernomina




Source: [http://in.answers.yahoo.com/question/index?qid=20090107041716AA6ce51](http://in.answers.yahoo.com/question/index?qid=20090107041716AA6ce51)

---

### Post by jordilin on 2009-03-23
cat /proc/meminfo and show what does it say.

---

### Post by .:Justus:. on 2009-03-23
32-bit OS´ no matter if linux or windows will only recognize a max of 3.2gigs of ram. Get the 64-bit version if you want to be able to use all of your ram.

---

### Post by Mehall on 2009-03-23
A 32-bit OS can only use between 3 and 3.5GB of RAM max, it's a limitation of the 32-bit Architecture.

It may only list 3GB, but it's probably seeing around 3.2 or something at best guess.

Unless you use a 64-bit OS, you will NOT be able to use the whole 4GB

---

### Post by Ravernomina on 2009-03-23
i cannot open the file this is what i get

The file /proc/meminfo changed on disk.

---

### Post by rocketflame on 2009-03-23
yes, thats normal. Last time I checked, 32 bit OS's could only address 3.3333 gigs of ram.  Since this is not windows, just download the 64 bit one (free? no way!!!)  :D

---

### Post by Ravernomina on 2009-03-23
i know its free lol but u can only use 64 bit software witch i don't wana deal with :(

---

### Post by jordilin on 2009-03-23
> **Ravernomina said:**
> i know its free lol but u can only use 64 bit software witch i don't wana deal with :(

I am using 64bit Ubuntu in a couple of laptops without any problem, if that helps.

---

### Post by Ravernomina on 2009-03-23
so your saying that i can use every Linux software out their on 32/64 bit?

---

### Post by qamelian on 2009-03-23
> **Ravernomina said:**
> so your saying that i can use every Linux software out their on 32/64 bit?
There are compatibility libraries that will let you run the odd program that doesn't have a 64-bit version yet. You won't need them for many apps though.

---

### Post by Ravernomina on 2009-03-23
so ur saying that it can run 32 apps on a 64 arch?

---

### Post by Tobis87 on 2009-03-23
Hello,

If you want to run a 32bit Linux.

You will need a kernel which is PAE aware:
[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

You could recompile your kernel with PAE enabled or install the server kernel.

But there shouldn't be any problems running a 64bit OS, anymore.

---

### Post by qamelian on 2009-03-23
> **Ravernomina said:**
> so ur saying that it can run 32 apps on a 64 arch?
Exactly. I can't remember the name of the libraries, and they are needed less and less. I'm sure someone else here must know the name.

---

### Post by Chemical Imbalance on 2009-03-23
> **qamelian said:**
> Exactly. I can't remember the name of the libraries, and they are needed less and less. I'm sure someone else here must know the name.

ia32-libs  I think is what you're talking about

---

### Post by qamelian on 2009-03-23
> **Chemical Imbalance said:**
> ia32-libs  I think is what you're talking about
That sounds familiar!:)

---

### Post by Ravernomina on 2009-03-23
yea that what its called i just looked it up and thats them.... i might do it but im a newbie at linux :P

---

### Post by Ravernomina on 2009-03-23
any benefits of 64 bit over 32 bit?

---

### Post by Tobis87 on 2009-03-23
> any benefits of 64 bit over 32 bit?

It will run programs a little bit faster, because it uses sse2 for any programs.

But you'll have to install Ubuntu from scratch again. Because you can't switch between i386 and x86_64. For the moment this will do:
```
sudo apt-get update && sudo apt-get install linux-headers-server linux-image-server linux-server
```

---

### Post by Chemical Imbalance on 2009-03-23
> **Ravernomina said:**
> any benefits of 64 bit over 32 bit?

It can be much faster with certain tasks like converting audio and other things. Plus, it utilizes over 3.3gb of RAM unlike 32bit.
 I recommend it.

---

### Post by Ravernomina on 2009-03-23
i might do it and i think my processor can do 64 bit witch is a bonus :) wow for a computer thats 5  years old its still really new XD

---

### Post by Chemical Imbalance on 2009-03-23
> **Ravernomina said:**
> i might do it and i think my processor can do 64 bit witch is a bonus :) wow for a computer thats 5  years old its still really new XD

What processor is it?

---

### Post by Ravernomina on 2009-03-23
pentium 4 hyper-threading 2.8 ghz each l2 catch of 2mb (2 cores)

---

### Post by Chemical Imbalance on 2009-03-23
> **Ravernomina said:**
> pentium 4 hyper-threading 2.8 ghz each l2 catch of 2mb (2 cores)

That should work great ;)

---

### Post by Ravernomina on 2009-03-23
good.... ugh for some reason im scared to go to a 64 bit o.o

---

### Post by Chemical Imbalance on 2009-03-23
If I were you I'd just wait until Jaunty comes out in April so that you have a good reason to reinstall ;)

---

### Post by Ravernomina on 2009-03-23
its a good idea but im wasting a gig of RAM :l

---

### Post by Chemical Imbalance on 2009-03-23
> **Ravernomina said:**
> its a good idea but im wasting a gig of RAM :l

You're only wasting .67 gb of RAM :)

3.3gb should be plenty though in the meantime :popcorn:

---

### Post by Tobis87 on 2009-03-23
Which Pentium 4 is it? If it is a Prescott, you will have to check which stepping it is, because 64bit was first enabled by stepping e0. ```
cat /proc/cpuinfo | grep stepping
```

---

### Post by Ravernomina on 2009-03-23
i got this:

Stepping:1
Stepping:1

---

### Post by Tobis87 on 2009-03-23
Could you please post the full output (cat /proc/cpuinfo) . Because there seem to be two Prescotts with 2.8ghz.

---

### Post by Ravernomina on 2009-03-23
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping	: 1
cpu MHz		: 2792.947
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 3
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl cid cx16 xtpr
bogomips	: 5585.89
clflush size	: 64
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping	: 1
cpu MHz		: 2792.947
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 3
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pebs bts pni monitor ds_cpl cid cx16 xtpr
bogomips	: 5586.00
clflush size	: 64
power management:

---

### Post by Tobis87 on 2009-03-23
Ok it is the first Prescott (SL7E3)
[http://en.wikipedia.org/wiki/List_of_Intel_Pentium_4_microprocessors#.22Prescott.22_.2890_nm.29_2](http://en.wikipedia.org/wiki/List_of_Intel_Pentium_4_microprocessors#.22Prescott.22_.2890_nm.29_2)

But I'm not sure if the stepping does support 64bit, you will have to test it. You could try to boot with a 64bit linux from cd. If it fails with a kernel panic. You will have to use the server kernel as I described a few posts earlier.

---

### Post by izizzle on 2009-03-23
Unless you have a 64-Bit OS, it will only recognize 3 gigs MAX of all the RAM you have installed.

---

### Post by Ravernomina on 2009-03-23
Aright thank you all for your help you guys all know a TON thanks you:)


Special thanks to: Tobis87 and Chemical Imbalance

---

### Post by Tobis87 on 2009-03-23
> Unless you have a 64-Bit OS, it will only recognize 3 gigs MAX of all the RAM you have installed.
Also if you have a kernel with pae enabled?

---

### Post by Chemical Imbalance on 2009-03-23
> **Tobis87 said:**
> Also if you have a kernel with pae enabled?

no, it wont be limited in that case. with pae you will address more than 3.3gbs
[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

---

### Post by Tobis87 on 2009-03-23
If he would use the server kernel, which has pae enabled, he would be able to use his full memory, even if the cpu doesn't support 64bit.
[http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/)

---

### Post by Ravernomina on 2009-03-24
It can run 64 bit :)

i chose to boot into ubuntu befor i installed and it worked i went into sytem monitor and it still says 3 gigs is this normal o.o

---

### Post by Chemical Imbalance on 2009-03-25
Are you sure you have 4gb's installed?

Make sure you go to the System tab in System Monitor and look at the * installed * size.

---

### Post by Ravernomina on 2009-03-25
i did, it says 300mb out of 3.0gb..... :(

---

### Post by Chemical Imbalance on 2009-03-25
Do you have a graphics card that shares your RAM?

And are you sure you have 4gb installed?

---

### Post by stchman on 2009-03-25
> **rocketflame said:**
> yes, thats normal. Last time I checked, 32 bit OS's could only address 3.3333 gigs of ram.  Since this is not windows, just download the 64 bit one (free? no way!!!)  :D

Actually 32 bit OS can theoretically recognize 2^32 bytes of RAM or 4294967296 bytes which is 4GB.  These are maximum theoreticals.

Problem is there is OS overhead and such with limits to around 3.2 - 3.5GB RAM.

---

### Post by Ravernomina on 2009-03-25
my graphics card is shared with my RAM but the thing is it only uses 128 MB and yes im positive i did the slot dance :l

---

