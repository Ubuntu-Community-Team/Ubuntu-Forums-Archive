---
title: "Laptop fan always spinning"
date: 2006-11-26
forum: Hardware &amp; Laptops
---

### Post by csadowski on 2006-11-26
I have a Gateway 4535GZ laptop, and when I run ubuntu, the fan is always spinning.  I was wondering if there was some fix to this issue at all?

I was considering trying to use powersaved, but was wondering if thats safe to do and if it will have a positive or negative effect on battery life or if it'll have any effect on the fans that are always spinning.

Any thoughts?

---

### Post by bernied on 2006-11-26
This might be about CPU frequency staying at the maximum, instead of slowing down when usage is low. Look for something like cpufreq (cpufreq-utils?) in your package manager.

In KDE you can use KDE System Guard to watch your clock frequency - there must be something similar in Gnome.

---

### Post by bernied on 2006-11-26
...and, look in /proc/cpuinfo
```
$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 8
model name      : AMD Sempron(tm)   2600+
stepping        : 1
cpu MHz         : 1836.123

```That bit that says stepping should be greater than one, if you can change your CPU's speed.

---

### Post by csadowski on 2006-11-26
i get this output: 

sadowski@Euclid:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.70GHz
stepping        : 6
cpu MHz         : 600.000
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up est tm2
bogomips        : 1197.19




im a bit of a newb, what exactly should i do?

---

### Post by csadowski on 2006-11-26
i also got that cpufrequtils package...what should I do with it?

---

### Post by bernied on 2006-11-27
ok, so it looks like your cpu is scaling down:> model name : Intel(R) Pentium(R) M processor 1.70GHz
stepping : 6
cpu MHz : 600.000...the first line above says you have a 1.7GHz processot, the second says that it can go at 6 different speeds, and the third is the speed it was going when you asked the question. 600 is like idling for for a 1.7GHz chip - I think.

So, forget my theory, the problem seems to be with the fans themselves.

---

### Post by sloggerkhan on 2006-11-27
I have an acer with an AMD chip, but the fan is always running, though very slowly, and it does it on windows, too. I think some laptops always run their fan these days. I wouldn't worry about it.

---

### Post by bernied on 2006-11-27
> ...and when I run ubuntu, the fan is always spinning....I inferred from this that this was unusual, like the fan does not always spin when a different operating system was used. Is this right, csadowski?

---

### Post by torb. on 2006-11-28
I got the same problem with my Intel(R) Pentium(R) M processor 1.70GHz. In OpenSuse, Fedora, Mandriva, Ubuntu 5.04 and 5.10 the fan is running slow. In Ubuntu 6.10 and 6.06 the fan is spinning like crazy.

---

### Post by bernied on 2006-11-28
Sorry, I don't think I can be of any more use here, except to say this now sounds to me like an ACPI (Advanced Configuration and Power Interface) issue. This is power management magic that is part of the linux kernel, though some of it may be in modules.

And, you might want to have at look at dmesg, for anything that looks like it might be a problem:```
sudo dmesg
```(sudo might not be necessary there)

---

