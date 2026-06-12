---
title: "Is this a 64-bit processor?"
date: 2009-04-06
forum: Hardware
---

### Post by ubuntu27 on 2009-04-06
I am going to help install Ubuntu Linux to a friend.

Since I believe that Linux 64-it is ready. I want to know if her processor supports 64-bit. Yes, I did search on the web, but couldn't find anything relevant.


The microprocessor that she has is

**Intel Pentium 4 Possessor 525**

So, is that 32-bit or 64bit?

Oh, also, she has 512 MB of RAM. I wonder if it is still convenient to install 64-bit OS.

---

### Post by darkcrawler on 2009-04-06
IMHO since the system has just 512 MB of ram it's convenient to install 32-bit.

---

### Post by khelben1979 on 2009-04-06
Hmm... If your processor is 64 bit with 512MB of RAM, I strongly believe that you should be able to run the 64 bit version of Ubuntu Linux.

But I believe that your processor is 32 bit. Look for [this page]("http://en.wikipedia.org/wiki/Pentium_4") for further information about the Pentium 4 processor. I couldn't find anything about the code number that you specified.

---

### Post by RedSingularity on 2009-04-06
Yep sounds like a 32 bit.

---

### Post by ubuntu27 on 2009-04-06
Thank you guys. So it is 32-bit. 

I was getting confused since the Intel.com page on Intel Pentium 4 mentions
 "Intel EM64T also provides support for 64 bit computing to help handle the applications of tomorrow."

[http://www.intel.com/products/processor/pentium4/index.htm](http://www.intel.com/products/processor/pentium4/index.htm)

So, I deduce that it is talking about another processor. Thy make so confusing since the main title or heading is Intel® Pentium® 4 Processor.


Anyway, thank you guys!

---

### Post by jespdj on 2009-04-07
You can lookup your processor in the [Intel processorfinder](http://processorfinder.intel.com/List.aspx?ParentRadio=All&ProcFam=483&SearchKey=). I don't see the 525 there, however (the Processor Number field contains 521, 524, 530 but not 525).

Looking at the Pentium 4 524, I see two types, both at 3.06 GHz, and the spec pages say they **do** support EM64T, which means those do have 64-bit extensions.

Do you have more specifications of your processor (at what speed does it run, etc.)? Look in the Intel processorfinder if you can find your specific model there. As far as I know not all Pentium 4 processors have the 64-bit extensions, so if the 524 has it, it doesn't automatically mean that the 525 has it too.

*edit*: You should be able to find it out using this command:
```
sudo lshw -class processor
```
It will print some information about your processor. Look for a line starting with "width:". If it says "32 bits", then it's a 32-bit only processor; if it's "64 bits", you have a 64-bit capable processor.

---

### Post by hyper_ch on 2009-04-07
run
```

cat /proc/cpuinfo

```

if you ge
```

clflush size    : 64
cache_alignment : 64

```
then it's 64bit

---

### Post by jespdj on 2009-04-07
@hyper_ch: I'm not sure that that's correct; the Intel Atom N270 on my netbook, which is certainly 32-bit only, does report "clflush size: 64".

---

### Post by hyper_ch on 2009-04-07
and cache alignment?

---

### Post by Scubdup on 2009-04-07
[Here's some other info on the topic.]("http://ubuntuforums.org/showthread.php?p=6878068#post6878068")

The best way IMO to be certain is to download a 64-bit liveCD and try and run it on the machine.

---

