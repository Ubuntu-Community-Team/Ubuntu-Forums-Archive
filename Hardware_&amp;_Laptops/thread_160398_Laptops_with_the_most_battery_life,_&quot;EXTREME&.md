---
title: "Laptops with the most battery life, &quot;EXTREME&quot; batt life"
date: 2006-04-14
forum: Hardware &amp; Laptops
---

### Post by Knowledge2012 on 2006-04-14
Hi, im interested in getting a laptop, i dont realy care by who, how big, or what ever else, i am just in the market for a laptop that get an EXTREME amount of battey life, or a laptop that supports multiple battery's.

---

### Post by dermotti on 2006-04-14
[This thing has a huge battery]("http://www.livedigitally.com/theldb/Very Old.jpg")

---

### Post by Knowledge2012 on 2006-04-15
Funny, haha. But seriously, anything over 6 hours would be awesome. Im thinking about getting a micro laptop or something of the sort to get great batt life. But i would like to get a some what full size laptop if possible.

---

### Post by David Corrales on 2006-04-15
A friend got an Inspiron 630m. About 4-5 hours with extended battery in Windows.

---

### Post by Peacepunk on 2006-04-17
Well, your problem here is UBUNTU then, as under Windows my Sony Vaio VGN-T16 is returning 5 proved hours of  Office work, or 1 plain DVD + One hour of Civilisation Gaming on one battery, while under UBUNTU, we top at 3.5 max...

this VAIO was our choice because of Weight, Size and Battery. UBUNTU / Linux fails to scale the power consumption of the Centrino as effectively as MS does, and these Vaio are fragile (my first one only lasted for 14 months), got bad AfterSales Support records, and Sony does not support Linux At ALL.

Think of "Lightweight" + spare Battery Cost if you reallly want to move around linux-ed. Consider yourself happy above 4 hours, and only credit your target machine of 80% of what's advertised.



Cheers

.

---

### Post by razahel on 2006-04-17
I myself have an Asus M67 and can add another battery into my multibay with both batteries and conservative cpu governor i can watch films or play games under linux with an battery time of 5-6 hours.
when i only use Openoffice i have a battery time around 7-8 hours.

---

### Post by mips on 2006-04-17
IBM/Lenovo have claims of up to 10.5 hours of battery life.
[http://www.pc.ibm.com/europe/thinkpad/why/en/tseries.html?uk&cc=uk](http://www.pc.ibm.com/europe/thinkpad/why/en/tseries.html?uk&cc=uk)
[http://www.pc.ibm.com/europe/thinkpad/why/en/xseries.html?uk&cc=uk#computing](http://www.pc.ibm.com/europe/thinkpad/why/en/xseries.html?uk&cc=uk#computing)

Look at the section for "All-day computing"

Can take two batteries or they have the bigger extended batteries that connect to the rear.

---

### Post by Tom Tiger on 2006-04-21
Toshiba Portege R100 and its successor R200

normal battery 2.0 hours to 2.5 hours but equipped with the secondary battery
6 to 7 hours of battery life  

The R stands for Revolutionary 8-)

---

### Post by akniss on 2006-04-21
I've got a Dell Insprion 600m and get >6 hours with the dual battery while in windows... in Ubuntu I get ~3 hours if I turn my wireless off and turn the brightness  down to where I can barely see the screen.

---

### Post by Egalus on 2006-04-23
I get about 4 to 5 hours on XP on my Inspiron 600 with 83Wh battery on normal work (no gaming, no large compiling stuff but surfing, programming and wordprocessing) with undervolting for my P-M.

With ubuntu dapper, a patched kernel for undervolting I get 4-4,5 hours.
With breezy it was more like 3,5-4 hours, which is the main reason I still use windows sometimes ;)

---

### Post by NiceGuy on 2006-04-23
Just to add my 2 pence (cents). I'm running an aopen 1551-AG1 (barebones) with a 1.7GHz pentium m and 512MB of ram (its basically the same as a dell 700m). The battery life is approx. 2-3 hours on the standard 4 cell battery (I could get an 8 cell battery which should double the running time but I can't be bothered). Anyway, in windows the battery life is normally shorter than in linux. This is probably because when I'm in linux I use a program/applet called EmiFreq to control the speedstepping and I usually have it on 'power saving' ie. 600Mhz. There are probably programs which do the same in windows but as I rarely use it I haven't really looked in to it. Hope this helps someone.

---

### Post by YuHoo on 2006-04-23
I was interested in a similar type of laptop. I've found that the Dell XPS m140 works very well. The standard 6 cell battery gets about 6 hours of battery life, the 9 cell, about 9 hours. Everything works out of the box, but the wireless needs updates in breezy. You can check out their outlet store to buy a refurbished one and save around $300 and they're always going on sale for another $200-$400 off.

---

### Post by leshkin on 2006-04-27
Hi guys,

I'm using a Sony Vaio VGN-T2XP. This isn't the cheapest laptop out there, but in some magazine review (I think it was PC Pro) it came up a as top battery performer. I normally get about 4-5 hours on the standard battery (nothing too CPU intensive), which I am very happy with. There is an option for an extended battery, which takes this laptop into 6+ hours territory. The built-in Dual Layer DVD Writter and a very nice screen is a bonus also.

Sony have released an updated version of this laptop, which is even better on battery than my model.

Anyway, Ubuntu runs pretty well on it out of the box, appart from the screen resolution detection, which is easily fixed.

Good luck in your search.

Leshkin

---

### Post by Dominican on 2008-02-07
I was also in the search for the laptop with the most battery life. took six months of good research, but I found the perfect laptop. the X60s, or the X61s. both extremely lightweight, both extremely fast when on A/C power, and both great on battery life. I own an X61S with the ultralight screen (great luminosity) and the 8 cell battery. Running XP, I got 9-11 hours of battery life. On Ubuntu, I get 4-6 hours of battery life. I can actually an extra battery wedge for another 2-3 hours of battery life. This is great.

now if I can only figure out how to fix Ubuntu for more battery life...

---

### Post by Yellow Pasque on 2008-02-07
I'm guessing Ubuntu is using more CPU or CPU scaling isn't working if the difference is that drastic. The GPU might not idle as well as it does on Windows too. What kind of CPU do you have in there? Run this for us please:
```
cat /proc/cpuinfo
sudo update-pciids; lspci | grep VGA
```

---

### Post by Dominican on 2008-02-07
Here's the info for my laptop. I also have 2 gigs of ram, 12.1 inch screen, no CD/DVD drive, and an 8 cell battery.

hope this explains something...

////////////////////////////////////////\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\\
dominican@jet:~$ cat /proc/cpuinfo

processor       : 0

vendor_id       : GenuineIntel

cpu family      : 6

model           : 15

model name      : Intel(R) Core(TM)2 Duo CPU     L7500  @ 1.60GHz

stepping        : 10

cpu MHz         : 800.000

cache size      : 4096 KB

physical id     : 0

siblings        : 2

core id         : 0

cpu cores       : 2

fdiv_bug        : no

hlt_bug         : no

f00f_bug        : no

coma_bug        : no

fpu             : yes

fpu_exception   : yes

cpuid level     : 10

wp              : yes

flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm

bogomips        : 3198.44

clflush size    : 64



processor       : 1

vendor_id       : GenuineIntel

cpu family      : 6

model           : 15

model name      : Intel(R) Core(TM)2 Duo CPU     L7500  @ 1.60GHz

stepping        : 10

cpu MHz         : 800.000

cache size      : 4096 KB

physical id     : 0

siblings        : 2

core id         : 1

cpu cores       : 2

fdiv_bug        : no

hlt_bug         : no

f00f_bug        : no

coma_bug        : no

fpu             : yes

fpu_exception   : yes

cpuid level     : 10

wp              : yes

flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm

bogomips        : 3191.94

clflush size    : 64



00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

---

