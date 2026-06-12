---
title: "Core 2 Duo and Edgy"
date: 2006-10-28
forum: Hardware &amp; Laptops
---

### Post by jinx099 on 2006-10-28
I have a seemingly well-running Ubuntu edgy running, and everyhting is running fine, even the IDE CD-rom drive.  However, I have 1 concern.  I loaded up the CPU frequency monitor and it says my cores are running at only 600 MHz at idle, and 700 at load.  I looked in my /proc/cpuinfo file and it shows the same frequency info.  

In dapper, the scaling did not work, however the frequency monitor did show my CPU speed correctly even though it did not scale.  Now I'm wondering, is this just an error in the speed detection, or is there something wrong with the compatibility of the kernel and the C2D or motherboard.

I'm running an e6300 Core 2 Duo overclocked to 2.8 GHz (400x7) with a Gigabyte P965-DS3 motherboard and am using the 2.6.17-10-generic kernel.  Will other Core 2 Duo users please share their output of "cat /proc/cpuinfo".

---

### Post by z00100 on 2006-10-28
Hi,

I do not have a C2D, I have an Athlon 64 3000+ (1.8Ghz).

On Edgy, it clocks down to 1.0Ghz, and under load it goes back to 1.8Ghz.

I have set up CnQ (Cool n Quiet) in my BIOS and hence it works properly.  

So as far as I'm concerned there is no issue with my setup.  

However, lets go to your problem.....

Can you please let me know how you are "stressing" the CPU?  

Regards,

p.s. Can you please dump the /proc/cpuinfo for me?  I would like to see that.

---

### Post by jinx099 on 2006-10-28
Well weird, it is now working after the reboot after I posted this.  It is just like it was in dapper, no scaling but detects the right frequency.  And yes, I did try rebooting before, and I did not change any options in BIOS.  Weird...

z00100, I also have an A64 3000+ and I can confirm it scales from 1 GHz to 1.8.  When I was stessing the CPU before, I was using prime95 on each core at a time and on both with the same results.

---

### Post by jinx099 on 2006-10-29
And of course my problem came back as soon as it was "fixed".  I'm thinking that before when all was working fine that I might have accidentally been booted in the 386 kernel, but now I'm definitley booted in the generic kernel.  Here is my /proc/cpuinfo:

```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping        : 6
cpu MHz         : 600.000
cache size      : 2048 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 5605.82

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping        : 6
cpu MHz         : 600.000
cache size      : 2048 KB
physical id     : 1
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 5600.43

```

---

### Post by jinx099 on 2006-10-29
Bump, I know I'm not the only Ubuntu edgy user with a core 2 duo.

---

### Post by nardusg on 2006-10-30
> **jinx099 said:**
> Bump, I know I'm not the only Ubuntu edgy user with a core 2 duo.

Hi K/Ubuntu'ers

Same problem here :( Got an Dell D620, same problem.

Any ideas ?

nardusg

---

### Post by zgornel on 2006-10-30
kill powernowd daemon and see if the frequency goes up. If it does, there were some nice posts on the forum on how to change the speed of the cpu.

---

### Post by jinx099 on 2006-10-30
Thank you for the reply.  It seems as though the powernowd daemon is not running though because "ps aux | grep powernowd" returns nothing.  Any more ideas?

---

### Post by zgornel on 2006-10-30
Hmm ... Add the cpu frequency scaling monitor to the gnome taskbar, take a peek and see what's the highest frequecy available.

---

### Post by jinx099 on 2006-10-30
> **zgornel said:**
> Hmm ... Add the cpu frequency scaling monitor to the gnome taskbar, take a peek and see what's the highest frequecy available.

It peaks at 700 MHz while running prime95

---

### Post by zgornel on 2006-10-30
No No, click on it and see what is the maximum freqency you can select, don't just look at it.

---

### Post by jinx099 on 2006-10-30
> **zgornel said:**
> No No, click on it and see what is the maximum freqency you can select, don't just look at it.

I can't select any frequencies.

---

### Post by jinx099 on 2006-10-30
Update:  I fixed the frequency problem by uninstalling powernowd.  Even thought I couldn't find the process, it was installed and apparently causing the problems.  However, CPU scaling does not work anymore (stuck at full speed all the time), but thats okay for my desktop.  Thank you all for the help!

---

### Post by yachoo on 2006-11-21
I know that you don't see any problem with it, but if you would read this, try to write:
```
sudo dpkg-reconfigure gnome-applets
```
on the console
you will be able then to control the speed of your CPU's in CPU Frequency Scaling Monitor

---

### Post by zgornel on 2006-11-24
> **yachoo said:**
> I know that you don't see any problem with it, but if you would read this, try to write:
```
sudo dpkg-reconfigure gnome-applets
```
on the console
you will be able then to control the speed of your CPU's in CPU Frequency Scaling Monitor
Forgot to mention that :rolleyes:

---

