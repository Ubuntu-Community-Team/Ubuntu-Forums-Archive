---
title: "new cpu lost a GH"
date: 2006-12-07
forum: Hardware &amp; Laptops
---

### Post by tophatandy on 2006-12-07
Recently installed a hardware monitor and realized that I am missing 1 ghz on my frequency for my processor.

it is and amdx64 3200+ at ~2Ghz

not over clocking it

also am running it on 32bit 6.06.. 


any explainations.. or even better a fix..

actually any help would be appriciated.. even guesses

---

### Post by PurplePenguin on 2006-12-07
The AMD 64 3200 runs at 2GHz.  What's it showing up as?  Or are you expecting that it's supposed to run at 3.2 GHz?  The numbers that AMD uses aren't MHz... they're traditionally more or less an indication of how they'd compare to Intel's chips.  That is, Intel chips usually clock faster, but due to design differences, AMD chips that are clocked at lower MHz still keep up.

---

### Post by tophatandy on 2006-12-07
I know that AMD chips are clocked different.. 
it is supposed to run at 2Ghz.. 
only running at 1Ghz.. 
thats half of my processing that went..

---

### Post by ~LoKe on 2006-12-07
What are you using to read your clock speed?  Have you checked what the BIOS is showing?

---

### Post by po0f on 2006-12-07
tophatandy,

Are you sure it's not throttled back from being idle?  Which hardware monitor are you using to gather this information?  What's the output of:
```
[FONT="Courier New"]$ cat /proc/cpuinfo[/FONT]
```

---

### Post by tophatandy on 2006-12-08
I am using a sys info that I got from the repos.

My bios shows that I should be going 2000Mhz

this is what i got from your command you gave me to run in terminal:

~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 39
model name      : AMD Athlon(tm) 64 Processor 3200+
stepping        : 1
cpu MHz         : 1000.099
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow pni lahf_lm
bogomips        : 2002.35

---

### Post by po0f on 2006-12-08
tophatandy,

Is CPU throttling activated?  If it is, it would throttle back your CPU to a slower frequency when idle to save power.

---

### Post by tophatandy on 2006-12-08
I do not know how to check that or turn it off..

it would make sense though.

---

### Post by dmartinsca on 2006-12-08
Here's a simple test:
Right click on a panel, and choose "Add to Panel". In the window that opens, scroll down and choose "Cpu Frequency Scaling Monitor". Now, take note of what the new monitor currently reads. Next, open a terminal and type, or paste this:
```
while true; do echo -n;  done
```

Press enter, and watch the cpu frequency scaling monitor you just added to the panel, if things are working properly, it should jump up to your maximum cpu speed. To stop the command running in the terminal, either press Ctrl+C or close the window.

What this command does is create a loop which runs until you stop it, it should put full load on the cpu so that if frequency scaling is working the processor speed should increase automatically.

---

### Post by tophatandy on 2006-12-08
wow.

jumped up to full speed, and yes I was only running at 50% usage

thank you all very much

---

