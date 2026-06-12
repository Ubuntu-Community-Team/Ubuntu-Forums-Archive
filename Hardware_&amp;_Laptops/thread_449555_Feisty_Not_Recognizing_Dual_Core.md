---
title: "Feisty Not Recognizing Dual Core"
date: 2007-05-20
forum: Hardware &amp; Laptops
---

### Post by taekwondodogoof on 2007-05-20
Hi,
      I've been trying to see if Feisty has been recognizing my dual core, and I've seen a post telling my how to find out if it using utilizing it. I ran in the terminal 
```
jared@MeinKampf:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
stepping        : 6
cpu MHz         : 1600.000
cache size      : 4096 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips        : 4803.21
clflush size    : 64

```

I'm pretty sure it's seeing my CPU as one core, even though it's a Core2Duo. Does anyone know how to enable two cores? THanks!

---

### Post by Rui Pais on 2007-05-20
weird! 
are you sure that you are running the -generic version of kernel? Or do you compiled your one kernel?

---

### Post by taekwondodogoof on 2007-05-20
I didn't compile my own kernel, I think I'm running the generic version. Do you know the command to check that?

---

### Post by Rui Pais on 2007-05-20
simple:
```
uname -a
```
:)

---

### Post by taekwondodogoof on 2007-05-20
Linux MeinKampf 2.6.20-15-386 #2 Sun Apr 15 07:34:00 UTC 2007 i686 GNU/Linux

---

### Post by Rui Pais on 2007-05-20
ok, try:
```
sudo apt-get install linux-generic linux-image-2.6.20-15-generic 
```
and reboot your machine with new kernel to see if it works.



Other theory says that is a conflict between your Ubuntu (Humanity to others) and your box name (No humanity for some) ;) ...:confused: :(

---

### Post by elfstone214 on 2007-05-20
The reason the CPU shows up as 1600MHz is because of speed stepping in the BIOS. The CPU automatically scales back the clock speed to save energy, etc. If you disable "C1E Speed stepping" on the BIOS it will show up as 2.4GHz which is the clock speed of your E6600 core2duo. I see this issue brought up at least 3 times a day in the CPU forums :)

Have you simply checked System Monitor to see if it is actually recognizing 2 cores? you should see two reading, one for each core.

---

### Post by taekwondodogoof on 2007-05-20
> **elfstone214 said:**
> The reason the CPU shows up as 1600MHz is because of speed stepping in the BIOS. The CPU automatically scales back the clock speed to save energy, etc. If you disable "C1E Speed stepping" on the BIOS it will show up as 2.4GHz which is the clock speed of your E6600 core2duo. I see this issue brought up at least 3 times a day in the CPU forums :)

Have you simply checked System Monitor to see if it is actually recognizing 2 cores? you should see two reading, one for each core.

The system monitor CPU History shows only one core. Also, I'll check to see if I have the C1E enabled in BIOS, thanks for the tip.

Also, I just installed the generic kernel, and set it to boot from the generic kernel, and it's still only reading one core. Any other suggestions? Thanks again!
(Even though I changed grub to boot to the -generic kernel, it still shows under uname -a as -386. Is this normal?)

---

### Post by Rui Pais on 2007-05-20
> **elfstone214 said:**
> The reason the CPU shows up as 1600MHz is because of speed stepping in the BIOS. The CPU automatically scales back the clock speed to save energy, etc. If you disable "C1E Speed stepping" on the BIOS it will show up as 2.4GHz which is the clock speed of your E6600 core2duo. I see this issue brought up at least 3 times a day in the CPU forums :)

Have you simply checked System Monitor to see if it is actually recognizing 2 cores? you should see two reading, one for each core.

the problem is that only one cpu is detected, not 2. 

> **taekwondodogoof said:**
> The system monitor CPU History shows only one core. Also, I'll check to see if I have the C1E enabled in BIOS, thanks for the tip.

Also, I just installed the generic kernel, and set it to boot from the generic kernel, and it's still only reading one core. Any other suggestions? Thanks again!
(Even though I changed grub to boot to the -generic kernel, it still shows under uname -a as -386. Is this normal?)

no. you are still booting from the old 386. 
How do you "set"? manually? install process should have change your menu.lst for you.

Anyway, you must have a grub entry like:
> title           Ubuntu, kernel 2.6.20-15-generic
root            (hdX,X)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=XXXXXXXXXXXXXXXXXXXX ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
boot
 

with XXXs replaced by your hardware specifications.

---

### Post by elfstone214 on 2007-05-20
try install 686-smp?

> sudo apt-get install linux-686-smp


EDIT: nevermind apparently this is now obsolete

---

### Post by Rui Pais on 2007-05-20
> **elfstone214 said:**
> Install the 686-smp kernel

-generic is now the 686-smp (deprecated nomenclature).

```
$ apt-cache show linux-686-smp
...
Description: Obsoleted by: linux-image-generic
 This package is for upgrades only.
...

```

---

### Post by taekwondodogoof on 2007-05-20
Ok... I forgot to change the last function in the menu.lst to -generic.. dumb error on my part sorry. Anyways.. I booted into generic, and it now recognizes two cores!!! (Still at a 1600 mhz clock though) Does the -386 not support dual core, and I turned off the C1E, but it still reduces the clock, any ideas on that? You guys have been a great help, thanks a ton!

---

### Post by Rui Pais on 2007-05-20
> **taekwondodogoof said:**
> Ok... I forgot to change the last function in the menu.lst to -generic.. dumb error on my part sorry. Anyways.. I booted into generic, and it now recognizes two cores!!! (Still at a 1600 mhz clock though) Does the -386 not support dual core, and I turned off the C1E, but it still reduces the clock, any ideas on that? You guys have been a great help, thanks a ton!

good :)

386 don't have SMP support, that enables the kernel to deal with process spread between cpus. So even if both  your cpus was detected kernel couldn't divide processes for them.

Your cpus are not 2.4Ghz ***each*** (that would made your box a 4.8 Ghz you wish ;))
Is 1.2+1.2 to 1.6+1.6. That mean 2.4 that under pressure can go to 3.2 (and if scaling is working go back to 1.2+1.2=2.4 as soon as the load is done).

glad its working.

---

### Post by elfstone214 on 2007-05-20
Sorry you have to disable EIST in the BIOS too but honestly I would set C1E and EIST back to "enabled" (unless you are overclocking which you are not) ... just because it shows up as 1600MHz at idle doesn't mean it is running any slower. It will ramp up when you give the CPU something to do. But if you feel like checking anyway then disable C1E and EIST in the BIOS. EIST is what lowers you CPU multiplier when not under load.

This is an example of my Core 2 Duo with EIST and C1E disabled which is overclocked to 3.1GHz and shows up correctly at ~3100.382MHz. Ignore the "1.80GHz" that is just the stock speed.

> processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz
stepping        : 2
**cpu MHz         : 3100.382**
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2


---

