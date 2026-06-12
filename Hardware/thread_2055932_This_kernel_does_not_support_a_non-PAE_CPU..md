---
title: "This kernel does not support a non-PAE CPU."
date: 2012-09-10
forum: Hardware
---

### Post by hasardeur on 2012-09-10
Hello.

I have just updated lubuntu to 12.10 beta and during that process I found out that a PAE kernel seems to be mandatory these days. Kernel version "3.2.0-30-generic" was kept so I can work with this machine.

What can I do? Is there a ppa with another kernel flavor available? Is this the end of the line?

```
cat /proc/cpuinfo 
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 13
model name	: Intel(R) Celeron(R) M processor         1.30GHz
stepping	: 6
microcode	: 0x18
cpu MHz		: 1296.792
cache size	: 1024 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts
bogomips	: 2593.58
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 32 bits virtual
power management:
```

---

### Post by lukeiamyourfather on 2012-09-10
> **hasardeur said:**
> Is this the end of the line?


Ubuntu and some of the official spins are dropping non-PAE support for 32-bit. If you want to use current software there are other distributions like Debian will likely continue supporting older hardware for longer than Ubuntu. Alternatively you could stick with 12.04 LTS until April of 2017.

---

### Post by hasardeur on 2012-09-10
So I guess a third party ppa for a non PAE kernel is unlikely? Sticking with the LTS is an option. 
Hm, seems so un-linux like that this happens anyway...

---

### Post by lukeiamyourfather on 2012-09-10
> **hasardeur said:**
> So I guess a third party ppa for a non PAE kernel is unlikely? Sticking with the LTS is an option. 
Hm, seems so un-linux like that this happens anyway...

If someone volunteers and creates/maintains a PPA there will be. You can always build your own kernel if you want.

---

### Post by marinara on 2012-09-10
install 12.04 and do a dist-upgrade

---

### Post by hasardeur on 2012-09-12
Unfortunately that is not an option.  I already switched to Arch, so this matter is more or less solved. Thanks for the input everybody.

---

### Post by bhuvneshdave on 2012-09-12
just add pae kernel by sudo apt-get install "name type of kernel you want or simply type your current kernel name with suffix -pae" then run grub update

---

### Post by lukeiamyourfather on 2012-09-12
> **bhuvneshdave said:**
> just add pae kernel by sudo apt-get install "name type of kernel you want or simply type your current kernel name with suffix -pae" then run grub update

The original poster is using a processor that doesn't support PAE. Ubuntu is dropping support for processors that are not at least PAE capable. I wouldn't be surprised to see the next LTS drop support for 32-bit completely. Its hard to find a new computer that doesn't have at least 4 GB of memory and I haven't had a computer without 64-bit support for nine years (Athlon 64 3000+ was my first and everything since has had it too).

---

### Post by raw2 on 2013-03-20
I just tried to install the 12.04.2 LTS CD on a 2003 vintage Dell Inspiron 9200 with 1 GB RAM. The install also insisted on PAE compatible hardware, which the 9200 does not have.

Will the "alternate" install CD also insist on PAE hardware/kernel?
I yes, then I won't bother to waste more time.

---

### Post by mörgæs on 2013-03-23
It does not matter if you use the regular or the alternate ISO. 
Your best option is Xubuntu 12.04, which is supported two years from now and does not require PAE.

---

### Post by martywd on 2013-06-06
I realize this thread is marked 'SOLVED' so this is a FWIW...

I ran into a similar issue on an old HP Compaq (w/Celeron cpu) laptop with almost identical spec as the OP's Celeron laptop.  This HP laptop I type of is running 32-bit LM13, (i.e. Ubuntu 12.04 LTS) and I was attempting to upgrade the kernel to linux-image-generic-lts-quantal 3.5 but as posted above installs failed with the 'non-PAE CPU' error.  Then I found the solution for my issue here:

[http://askubuntu.com/questions/203984/lubuntu-12-10-this-kernel-does-not-support-a-non-pae-cpu/256037#256037](http://askubuntu.com/questions/203984/lubuntu-12-10-this-kernel-does-not-support-a-non-pae-cpu/256037#256037)

Install the 'fake-pae' repository, install 'fake-pae' package, then do another install/re-install of the 3.5 kernel packages, reboot.
.

---

