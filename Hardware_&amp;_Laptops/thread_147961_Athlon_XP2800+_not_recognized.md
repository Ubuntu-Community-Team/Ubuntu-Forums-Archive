---
title: "Athlon XP2800+ not recognized"
date: 2006-03-21
forum: Hardware &amp; Laptops
---

### Post by renq on 2006-03-21
the problem is that ubuntu does not recognize my xp2800+ barton- the system is running really slow. all updates have been installed..the conf of my pc is 2800+ barton, 1gb ddr400, 200gb sata (11.8gb partition for linux), msi nf2u400 k7n2delta ilsr, radeon 9800pro. all help is welcome as i am a total beginner in linux.

---

### Post by tseliot on 2006-03-21
1) Open Terminal or Konsole (i.e. the command line) and type this:
```
cat /proc/cpuinfo
```

Post the ouput (i.e. the result)

2) Open gnome-system-monitor (aka System monitor)

and tell me the percentage of use of your cpu.

EDIT: of course I think that this guide of mine can help you: [HOWTO: Double Clock Speed Problem]("http://www.ubuntuforums.org/showthread.php?t=75281")

---

### Post by renq on 2006-03-21
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 10
model name      : AMD Athlon(tm) XP 2800+
stepping        : 0
cpu MHz         : 2079.840
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
bogomips        : 4120.57

this is from cpuinfo, but Device manager doesnt recognize the cpu, should i be worried? and the pc is not suffering from the double speed bug.

---

### Post by tseliot on 2006-03-21
[QUOTE=renq]this is from cpuinfo, but Device manager doesnt recognize the cpu, should i be worried? and the pc is not suffering from the double speed bug.[/QUOTE]
Don't care about what Device manager reports (this is not Windows).

You CPU is well detected.

1) Have you tried to play an mp3? How does it go?

2) type this command so as to know if DMA is enabled:
sudo hdparm -d /dev/hda

OR sudo hdparm -d /dev/hdx (replace "x" with the letter of your partition)

and post the output

---

### Post by taurus on 2006-03-21
What version of kernel do you use right now?  Perhaps you need to get the "k7" version!!!

---

