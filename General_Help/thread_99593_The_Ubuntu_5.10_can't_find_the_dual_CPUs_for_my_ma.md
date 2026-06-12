---
title: "The Ubuntu 5.10 can't find the dual CPUs for my machine."
date: 2005-12-05
forum: General Help
---

### Post by trytrytry on 2005-12-05
Hi All,

I just installed the Ubuntu 5.10 (Breezy Badger) (downloaded ubuntu-5.10-install-i386.iso from [http://www.ubuntulinux.org/download/)](http://www.ubuntulinux.org/download/)). Everything is working fine except one big problem. My dual processors can't be recognized by the system. So the machine becomes very slow when I run a big program (100% CPU used). (Under my Windows Xp Pro, however I can find four processors under the device manager -> processor. When I run a problem there, only 25% CPU is taken.) 

I am a newbie to Linux and below is my ubuntu problem.  Any suggestions? Thanks ahead.


1. When I lauch System Monitor, there is only one CPU in CPH History.

2. I then run "top" in a console and here are the top lines:

Tasks:  78 total,   1 running,  77 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.7% us,  1.0% sy,  0.0% ni, 89.3% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:   2075596k total,   443996k used,  1631600k free,    16436k buffers
Swap:  3903752k total,        0k used,  3903752k free,   280036k cached

3.  Next, I run "cat /proc/cpuinfo" and also found only one processor. Here is the result.

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Xeon(TM) CPU 3.40GHz
stepping        : 3
cpu MHz         : 3391.959
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 3
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm pni monitor ds_c pl est cid cx16 xtpr
bogomips        : 6733.82

4. The command "dmesg" gives too much information and I don't know where related to the CPU.

---

### Post by l3lackEyedAngels on 2005-12-05
I haven't tried it, but this post might help: [http://www.ubuntuforums.org/showthread.php?t=85917&highlight=kernel+performance]("http://www.ubuntuforums.org/showthread.php?t=85917&highlight=kernel+performance")

Good luck.

---

### Post by -DarkMind- on 2005-12-05
```
sudo apt-get install linux-686-smp
```

this install the kernel for 2+ cpus


reboot with the kernel and enjoy :)

---

### Post by trytrytry on 2005-12-05
Done! Thanks a lot!

[QUOTE=-DarkMind-]```
sudo apt-get install linux-686-smp
```

this install the kernel for 2+ cpus


reboot with the kernel and enjoy :)[/QUOTE]

---

### Post by -DarkMind- on 2005-12-05
[QUOTE=trytrytry]Done! Thanks a lot![/QUOTE]

you're welcome  :)

---

### Post by kugel on 2005-12-05
[QUOTE=-DarkMind-]```
sudo apt-get install linux-686-smp
```

this install the kernel for 2+ cpus


reboot with the kernel and enjoy :)[/QUOTE]


Can I use this same kernel on my dual 64bit, 3.00 Ghz Dell poweredge server? 
Or what could I use besides the Kubuntu 2.6.12-9-amd64-generic?

---

### Post by kugel on 2005-12-06
[QUOTE=trytrytry]Done! Thanks a lot![/QUOTE]


oh, btw when I just attempted  sudo apt-get install linux-686-smp
I received: E: Couldn't find package linux-686-smp

What should I do next?

---

### Post by funkydan2 on 2005-12-06
Have you got the Universe and Multiverse repositories enabled?  And updated your package listing?

[http://packages.ubuntu.com/breezy/base/linux-686-smp](http://packages.ubuntu.com/breezy/base/linux-686-smp)

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

