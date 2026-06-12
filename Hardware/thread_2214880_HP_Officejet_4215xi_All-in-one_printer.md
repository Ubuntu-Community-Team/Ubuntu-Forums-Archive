---
title: "HP Officejet 4215xi All-in-one printer"
date: 2014-04-03
forum: Hardware
---

### Post by pancho5 on 2014-04-03
According to HP, the HP Officejet 4215xi All-in-One printer is supported on Ubuntu. Unfortunately, I have a problem.  My Toshiba Laptop computer is a Non-PAE machine, and the Ubuntu distro will not work with my laptop.  Therefore, I must use Xubuntu 12.04.4.:(

Can anyone direct me in what steps I can do to solve my printing problem?  I will not be able to do anything until late next week, but if it is really technically involved, at least it will give me some time to do some added reading in preparation to see if I can get all the features to work (print, copy, scan, fax).  I know I could get on a Xubuntu forum and ask there, but I thought I would try Ubuntu forum first.

Any help would be much appreciated.

Newbie to Linux/Ubuntu,
Pancho

---

### Post by maglin2 on 2014-04-03
I don't use xubuntu, but I would guess that installing hplip, along with all its dependencies and recommends would be the start point.

---

### Post by ajgreeny on 2014-04-03
Yes, as maglin2 says install **hplip** if it's not already installed, and I also suggest **hplip-gui** to get a great gui control and configuration utility for the printer.

I assume it is attached by usb and not to a parallel port, as it looks as if the parallel port connection is not supported.

---

### Post by pancho5 on 2014-04-03
> **ajgreeny said:**
> Yes, as maglin2 says install **hplip** if it's not already installed, and I also suggest **hplip-gui** to get a great gui control and configuration utility for the printer.

I assume it is attached by usb and not to a parallel port, as it looks as if the parallel port connection is not supported.

Yes, my printer is attached by usb.  Question: Do I install hplip to "replace" the actual DL from the HP website or do both?:confused::confused:

---

### Post by rbmorse on 2014-04-03
HPLIP should be all you need.

---

### Post by tgalati4 on 2014-04-03
Use what you have from the repository.  The version from the HP website will be newer, but unless your printer was made last week, I would stick to the repository version.

You can also try installing from CUPS directly:  [http://localhost:631](http://localhost:631)

---

### Post by pancho5 on 2014-04-04
I have initially done some reading, but now I'm not sure what direction to take.  The 4215xi printer is supported on various distros.  It's supported on Ubuntu 12.04.4, but **I CANNOT** use this distro because my Laptop is Non-PAE.   Xubuntu 12.04.4 is what I would like to use because **my laptop** **is Non-PAE**.  Should I assume that the HPLIP Automatic Installer WILL NOT WORK with this distro and have to use the Manual Installation and DL the HPLIP Source Code Tarball?

If so....man...I will need some help with this!  Not that confident yet.  Please advise.

---

### Post by tgalati4 on 2014-04-04
There is a way to fake PAE for some installations.  Basically some processors support PAE, but it is not advertised or recompile the kernel without PAE and install that.  What is your specific model of laptop?  Open a terminal and post the output of:

```
cat /proc/cpuinfo
```

You should not have to recompile HPLIP (using the source code tarball).  Simply go to the CUPS server using the link I posted previously and click on Administration tab and click "Add Printer".  Go through the steps and see if it installs properly.

---

### Post by pancho5 on 2014-04-04
> **tgalati4 said:**
> There is a way to fake PAE for some installations.  Basically some processors support PAE, but it is not advertised or recompile the kernel without PAE and install that.  What is your specific model of laptop?  Open a terminal and post the output of:

```
cat /proc/cpuinfo
```

You should not have to recompile HPLIP (using the source code tarball).  Simply go to the CUPS server using the link I posted previously and click on Administration tab and click "Add Printer".  Go through the steps and see if it installs properly.

[B]The following is my CAT. But, just to let you know I am using the "Live" LXLE distro at this time.  Next week I will DL Xubuntu 12.04.4.  It's a long story...

...so from this CAT, what indicators tell me that my Laptop is PAE or Non-PAE?:confused:
[/B]
qwerty@qwerty:~$ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 13
model name    : Intel(R) Pentium(R) M processor 1.60GHz
stepping    : 6
microcode    : 0x18
cpu MHz        : 600.000
cache size    : 2048 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2
bogomips    : 1199.01
clflush size    : 64
cache_alignment    : 64
address sizes    : 32 bits physical, 32 bits virtual
power management:

qwerty@qwerty:~$

---

### Post by ajgreeny on 2014-04-04
It's the *flags* line that tells you about your CPU, and as you say, yours is not pae, as pae is not shown in that long list
> flags        : fpu vme de pse tsc msr mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts est tm2

Cups webmin should still manage to install the printer, so try that again.
[http://localhost:631/](http://localhost:631/)

---

### Post by mörgæs on 2014-04-04
The PAE problem has been thoroughly investigated in an eight page thread [here]("http://ubuntuforums.org/showthread.php?t=2211892").

---

### Post by tgalati4 on 2014-04-04
Pentium M's (a select few) don't advertise pae, but they support pae, they just need some kicking.

---

### Post by mörgæs on 2014-04-04
Correct, but let's keep that in the other thread. 
Printer talk here, please.

---

### Post by maglin2 on 2014-04-05
I have an HP Officejet 4315 all in one (not 4215).

I just booted from an xubuntu 12.04 live CD.

I turned on the printer, and it was imediately detected and configure automatically. 

HPLIP is already present in xubuntu default package set.

Good luck.

---

