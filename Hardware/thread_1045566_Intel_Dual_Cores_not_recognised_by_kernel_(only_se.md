---
title: "Intel Dual Cores not recognised by kernel (only sees one core)"
date: 2009-01-20
forum: Hardware
---

### Post by zongpog on 2009-01-20
Dear everyone,

  I just realised that my Intel 2.18Ghz dual core laptop was not running with two cores, but only one.  I tried an apt-get of the generic kernel but it told me it was already up to date.  System monitor only shows one CPU.  Does anyone know how to get this to work?  

Cheers, z.

-----------------

uname -a
Linux fred 2.6.24-23-generic #1 SMP Thu Nov 27 18:44:42 UTC 2008 i686 GNU/Linux
eet@fred:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Genuine Intel(R) CPU           T2600  @ 2.16GHz
stepping	: 8
cpu MHz		: 1000.000
cache size	: 2048 KB
physical id	: 0
siblings	: 1
core id		: 0
cpu cores	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc up arch_perfmon bts pni monitor vmx est tm2 xtpr
bogomips	: 4338.82
clflush size	: 64

eet@fred:~$ su -
Password: 
root@fred:~# uname -a
Linux fred 2.6.24-23-generic #1 SMP Thu Nov 27 18:44:42 UTC 2008 i686 GNU/Linux
root@fred:~# apt-get install linux-generic linux-image-2.6.24-23-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-generic is already the newest version.
linux-image-2.6.24-23-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  googleearth-4.2 libnfnetlink0 libamrnb3 libamrwb3 googleearth-4.2-data libnetfilter-queue1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 30 not upgraded.

---

### Post by zongpog on 2009-01-21
PS. This is in the laptop/hw section because its on a Sony Vaio SZ notebook.

---

### Post by zongpog on 2009-09-15
noticed that Ubuntu has this in the dmesg:

SMP alternatives: switching to UP

It really does not like Intel Core Duos.  Has someone put some bright code into the kernel? ^^

---

### Post by bartman on 2009-09-15
Strange problem... Just for kicks see what this command returns:
```
$ grep CONFIG_SMP /boot/config-2.6.24-23-generic
```

BTW, which release of Ubuntu are you using? That kernel version was released last January so I guess you're using 8.04 LTS?

---

### Post by zongpog on 2009-09-15
Ubuntu 9.04 installed

# grep CONFIG_SMP /boot/config-2.6.28-25-generic
CONFIG_SMP=y

Current kernel is 2.6.28-25-generic #49-Ubuntu SMP

---

