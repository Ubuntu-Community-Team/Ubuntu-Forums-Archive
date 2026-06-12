---
title: "AMD A-10 4600m turbo core is not working"
date: 2013-02-22
forum: Hardware
---

### Post by evol4g on 2013-02-22
Ok so I have an hp envy m6 1105dx, with amd a10 4600m apu, it runs rather well on ubuntu and i love it and all but my turbo core is not working at all.. Now I compile roms for android (i know a laptop is not the ideal build enviroment but it's all i got right now :\) anyways I'd like to get turbo core working, I'm also experiencing HORRIBLE battery life with ubuntu even when i'm not compiling a full charge only gives me 3 hours... This laptop is brand-new and on windoze i get about 6-6.5hrs of battery life.. HDMI displays video when i plug it in to the tv.. but no audio, then if i plug in the powercord i get no audio and no sound.. I did try 2 different fixes for the HDMI issue with no luck.


Please telll me there's work arounds for these issues.. I'm rather new to ubuntu.. I just use it for my android compiles and such..

thank you for your time,
-evol4g

---

### Post by Yellow Pasque on 2013-02-22
I wouldn't assume turbo boost isn't working just because the turbo speed isn't reported. I'm not completely sure about AMD turbo boost, but cpufreq is unaware of Intel turbo boost (though it still works). One has to use a special tool (i7z) to actually get the Intel CPU to report turbo boost

---

### Post by evol4g on 2013-02-24
do you know how i can tell if it's workin or not?

---

### Post by evol4g on 2013-02-26
bump

---

### Post by titaniusanglesmith on 2013-02-27
> **evol4g said:**
> do you know how i can tell if it's workin or not?

cpufreq-aperf should be able to tell the actual frequency. 
[cpufreq-aperf manpage]("http://manpages.ubuntu.com/manpages/lucid/man1/cpufreq-aperf.1.html")

you need to run it in superuser mode. you may also need to install msr-tools and run modprobe msr before running cpufreq-aperf.


Another option is [turionpowercontrol]("http://code.google.com/p/turionpowercontrol/")

---

### Post by Rebelli0us on 2013-02-27
> **evol4g said:**
> Ok so I have an hp envy m6 1105dx, with **amd a10 4600m apu**, it runs rather well on ubuntu and i love it and all but my turbo core is not working at all.. Now I compile roms for android (i know a laptop is not the ideal build enviroment but it's all i got right now :\) anyways I'd like to get turbo core working, I'm also experiencing HORRIBLE battery life with ubuntu even when i'm not compiling a full charge only gives me 3 hours... This laptop is brand-new and on windoze i get about 6-6.5hrs of battery life.. HDMI displays video when i plug it in to the tv.. but no audio, then if i plug in the powercord i get no audio and no sound.. I did try 2 different fixes for the HDMI issue with no luck.


Please telll me there's work arounds for these issues.. I'm rather new to ubuntu.. I just use it for my android compiles and such..

thank you for your time,
-evol4g

What makes you think turbo boost is not working? I have a laptop with an AMD A8-4500M APU and turbo cores are working fine with kernel 3.5

Here's a short blast of prime95:

```
sudo cpufreq-aperf
CPU	Average freq(KHz)	Time in C0	Time in Cx	C0 percentage
000	2166000			00 sec 997 ms	00 sec 002 ms	99
001	2166000			00 sec 997 ms	00 sec 002 ms	99
002	2166000			00 sec 997 ms	00 sec 002 ms	99
003	2166000			00 sec 997 ms	00 sec 002 ms	99

000	2128000			00 sec 996 ms	00 sec 003 ms	99
001	2128000			00 sec 996 ms	00 sec 003 ms	99
002	2128000			00 sec 996 ms	00 sec 003 ms	99
003	2128000			00 sec 996 ms	00 sec 003 ms	99

000	2109000			00 sec 996 ms	00 sec 003 ms	99
001	2109000			00 sec 996 ms	00 sec 003 ms	99
002	2109000			00 sec 996 ms	00 sec 003 ms	99
003	2109000			00 sec 996 ms	00 sec 003 ms	99

000	2090000			00 sec 943 ms	00 sec 056 ms	94
001	2090000			00 sec 925 ms	00 sec 074 ms	92
002	2090000			00 sec 931 ms	00 sec 068 ms	93
003	2090000			00 sec 932 ms	00 sec 067 ms	93

000	1368000			00 sec 063 ms	00 sec 936 ms	06
001	1368000			00 sec 037 ms	00 sec 962 ms	03
002	1368000			00 sec 049 ms	00 sec 950 ms	04
003	1406000			00 sec 014 ms	00 sec 985 ms	01

000	1368000			00 sec 080 ms	00 sec 919 ms	08
001	1368000			00 sec 050 ms	00 sec 949 ms	05
002	1368000			00 sec 083 ms	00 sec 916 ms	08
003	1368000			00 sec 033 ms	00 sec 966 ms	03

000	1691000			00 sec 111 ms	00 sec 888 ms	11
001	1653000			00 sec 050 ms	00 sec 949 ms	05
002	1368000			00 sec 079 ms	00 sec 920 ms	07
003	1349000			00 sec 015 ms	00 sec 984 ms	01

```

---

### Post by Rebelli0us on 2013-02-27
And another one, it shows 2.3 GHz on all 4 cores even though I thought that only 1 or 2 cores do the boost thing...

```
sudo cpufreq-aperf
CPU	Average freq(KHz)	Time in C0	Time in Cx	C0 percentage
000	2299000			00 sec 998 ms	00 sec 001 ms	99
001	2299000			00 sec 998 ms	00 sec 001 ms	99
002	2299000			00 sec 998 ms	00 sec 001 ms	99
003	2299000			00 sec 998 ms	00 sec 001 ms	99

000	2299000			00 sec 998 ms	00 sec 001 ms	99
001	2299000			00 sec 998 ms	00 sec 001 ms	99
002	2299000			00 sec 998 ms	00 sec 001 ms	99
003	2299000			00 sec 998 ms	00 sec 001 ms	99

000	2299000			00 sec 998 ms	00 sec 001 ms	99
001	2299000			00 sec 998 ms	00 sec 001 ms	99
002	2299000			00 sec 998 ms	00 sec 001 ms	99
003	2299000			00 sec 998 ms	00 sec 001 ms	99
```

---

