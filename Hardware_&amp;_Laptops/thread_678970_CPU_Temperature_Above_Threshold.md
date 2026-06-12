---
title: "CPU Temperature Above Threshold"
date: 2008-01-26
forum: Hardware &amp; Laptops
---

### Post by Majorix on 2008-01-26
Some Linux distros throttle the CPU when the temp goes above the threshold.

My CPU has the same problem, overheating. I regret having built it myself, I wish I had bought it pre-built. That way, I would have had a comp that would have been checked by computer engineers.

Anyways, with these Linux distros that slow down the CPU I have no rebooting problems. However I believe Ubuntu doesn't have this program (or the kernel option) pre-installed so it reboots pretty often. I hate this, so I am looking for a fix.

I cannot even install Xubuntu on the said comp, as it would reboot before the installation is complete.

Some example distros that have the fix are Arch and Gentoo. I don't know if they fix it via a kernel option or a program, so I decided to ask here.

Hope someone can help. Thanks.

---

### Post by shad0w_walker on 2008-01-26
Rather than work around the problem I would suggest trying to fix it. Make sure your CPU fan is clean of dust and running smoothly, make sure your case has enough ventilation, if all else fails check it actually has a decent coating of thermal paste on the heatsink and reapply it if needs be.

---

### Post by fearevilleet on 2008-01-26
> **shad0w_walker said:**
> Rather than work around the problem I would suggest trying to fix it. Make sure your CPU fan is clean of dust and running smoothly, make sure your case has enough ventilation, if all else fails check it actually has a decent coating of thermal paste on the heatsink and reapply it if needs be.

I agree, your computer is shutting down for a reason. If you don't fix the over heating issue you could fry your computer.

---

### Post by Majorix on 2008-01-26
Fry? Lol that annoying thing won't fry before frying me :lolflag:

However I don't know how I can check if the CPU is placed correctly etc, because it's fixed in its place and I can't move it an inch. So I am stuck.

---

### Post by Red Shift on 2008-01-26
I have a few questions.

1.  How are you measuring the temperature?  What is the temperature?

2.  Has this been a Ubuntu-only computer or have you run other OSs on it before?

3.  If you have run other OSs, did the computer overheat?

4.  What processor do you have?  You can find out by entering the following command in a terminal.  I only need the CPU part.

```
lshw
```

Ex.
```
*-cpu
          product: Genuine Intel(R) CPU            2160  @ 1.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx x86-64 constant_tsc pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm
```

5.  Did you use the CPU cooler that came with the CPU?

The solution may be as easy as A) removing dust from the CPU cooler, B) removing the CPU cooler and applying fresh thermal grease/pad, or C) buying and installing a better CPU cooler.  You're far from stuck because you have the skill to do all three. :)

---

### Post by Majorix on 2008-01-26
Hi Red Shift, thanks for your interest in the problem.

To answer your questions,
1. I don't measure the temperature actually. The OS gives an alert in the console that the CPU is overheated by printing the exact message in the topic of this thread.
2. I run various OS'es on my comp, reformatting very often and so on.
3. Yes it did. Like I said in the original post, Arch and Gentoo caught this. I think openSUSE did too, but it reseted 1 or 2 times so I can't be sure.
4. I am not on Ubuntu right now, so doing an lshw won't work, but I will tell you what I know. The CPU is a Pentium 4 3.0 GHz one, and an old one in that. I think I bought it 3 years ago or so.
5. Yes I am using the original cooler that came with the CPU.

I will clean the dust from the cooler, and also try to remove and replace it. Will post here.

Thanks again for caring.

---

