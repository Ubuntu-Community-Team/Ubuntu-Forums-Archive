---
title: "Using Both Cores in Fiesty, Turion X2"
date: 2007-06-05
forum: Hardware &amp; Laptops
---

### Post by jrmclaugh on 2007-06-05
I'm trying to make sure both of my cores are being used, but system monitor only shows one.  They are both activated in BIOS, because they show up under XP.

uname -a shows:
Linux jimbob-laptop 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686 GNU/Linux
so I have an SMP kernel.

all that shows up under "cat /proc/cpuinfo" is:
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 72
model name      : AMD Turion(tm) 64 X2 Mobile Technology TL-50
stepping        : 2
cpu MHz         : 1600.000
cache size      : 256 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up pni cx16 lahf_lm cmp_legacy svm cr8legacy ts fid vid ttp tm stc
bogomips        : 3217.79
clflush size    : 64

which leads me to believe it's only using one processor.

anyone have any advice? is it working and i'm just not realizing it?  any help is appreciated, thanks.

- James

---

### Post by jrmclaugh on 2007-06-05
Nothing?  I know this has been asked before, but I've tried the suggestions in all of the other posts I could find.  Any and all help is appreciated greatly.  Thanks.

- James

---

### Post by DagMan on 2007-06-05
Hi,
That suggests that you're install is only using one core.  I get this with a core duo
```
$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2050  @ 1.60GHz
stepping        : 8
cpu MHz         : 800.000
cache size      : 2048 KB
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor est tm2 xtpr
bogomips        : 3195.67
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2050  @ 1.60GHz
stepping        : 8
cpu MHz         : 800.000
cache size      : 2048 KB
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
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pni monitor est tm2 xtpr
bogomips        : 3193.71
clflush size    : 64
```

It spits out the info once for each one.  It does this on my desktop p4 with hyperthreading as well.  another thing to look at is if you have one or two processors being mapped in the system monitor.
```
gnome-system-monitor
```

---

### Post by jrmclaugh on 2007-06-05
Yeah, both of those tell me there's only one core.  Any suggestions at least for places for me to look into?  Thanks again.

- James

---

### Post by peanut butter on 2007-06-05
> **jrmclaugh said:**
> Yeah, both of those tell me there's only one core.  Any suggestions at least for places for me to look into?  Thanks again.

- James

you might have to install the smp version of your kernel. I cant remember how to tell the kernal version off hand.

---

### Post by jrmclaugh on 2007-06-05
As far as I can tell, the uname -a result of:

Linux jimbob-laptop 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686 GNU/Linux

tells me I have the SMP version.  I'll look more into it though.

- James

---

### Post by DagMan on 2007-06-06
try from here [http://ubuntuforums.org/showthread.php?t=373534](http://ubuntuforums.org/showthread.php?t=373534)
```
noapic acpi=noirq
```
or 
```
acpi=off
```

added to your boot option in grub.
```

sudo gedit /boot/grub/menu.list
```
and at the bottom of the file add one of them to the end of the line in the kernel you're going to boot into so for example below you can see the line where the first one is added to the end after the word splash, but don't just copy and paste because the UUID part will be differant:
```
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=8f132f8b-944a-45ec-8a43-d34b6c71933f ro quiet splash noapic acpi=noirq
```

If doing this makes your kernel unbootable then when you're at the grub menu hit the letter e for edit, use the arrow keys to go to the kernel line and hit e again and edit that part out, hit enter then the letter b for boot and once you get back in edit the /boot/grub/menu.lst file back to how it was.

---

### Post by jrmclaugh on 2007-06-07
I tried adding that, it didn't fix the two core problem, and it also disabled my wireless, heh.

I already have arguments similar to that in my boot options, I copied what was suggested under the Wiki for my laptop series.

The problem, however, was that one of the options was "nosmp".....I can't believe it.  Anyway, checking my boot options and removing that helped me fix it, thanks everyone for the input, I really appreciate it.

- James

---

### Post by Megatog615 on 2007-06-07
Also make sure it's not listed as a defoption for when you run update-grub ;).

---

