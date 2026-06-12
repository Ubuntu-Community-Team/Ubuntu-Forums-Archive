---
title: "google earth not working"
date: 2008-07-15
forum: General Help
---

### Post by clinux on 2008-07-15
I've installed Google Earth 4.3 according to this article [http://www.macewan.org/2006/06/12/how-to-install-google-earth-for-linux/]("http://www.macewan.org/2006/06/12/how-to-install-google-earth-for-linux/") and the installation was successful. But when i run google earth my screen turns blank, the system reboots and prompts me for username and pass. This happened when i tried both version 4.3 and version 4.2.
Anyone knows how to solve this?

---

### Post by overdrank on 2008-07-15
> **clinux said:**
> I've installed Google Earth 4.3 according to this article [http://www.macewan.org/2006/06/12/how-to-install-google-earth-for-linux/]("http://www.macewan.org/2006/06/12/how-to-install-google-earth-for-linux/") and the installation was successful. But when i run google earth my screen turns blank, the system reboots and prompts me for username and pass. This happened when i tried both version 4.3 and version 4.2.
Anyone knows how to solve this?

HI and welcome, Could you give us some system specs?
Also are you using compiz (desktop effects)?

---

### Post by clinux on 2008-07-15
No i don't use desktop effects.
here you go:
```
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Pentium(R) 4 CPU 2.00GHz
stepping	: 4
cpu MHz		: 2018.039
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm up pebs bts sync_rdtsc
bogomips	: 4040.73
clflush size	: 64

MemTotal:      1035420 kB
MemFree:        100892 kB
Buffers:         52880 kB
Cached:         525128 kB
SwapCached:       4684 kB
Active:         512268 kB
Inactive:       366384 kB
HighTotal:      131056 kB
HighFree:          240 kB
LowTotal:       904364 kB
LowFree:        100652 kB
SwapTotal:     4208904 kB
SwapFree:      4169296 kB
Dirty:             192 kB
Writeback:           0 kB
AnonPages:      295956 kB
Mapped:          71624 kB
Slab:            42192 kB
SReclaimable:    31296 kB
SUnreclaim:      10896 kB
PageTables:       2336 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
CommitLimit:   4726612 kB
Committed_AS:   777204 kB
VmallocTotal:   114680 kB
VmallocUsed:      5728 kB
VmallocChunk:   108628 kB

```

---

### Post by overdrank on 2008-07-15
Ok it appears you have enough memory but what is the model of the graphics card? 
You can use the command ```
lspci
``` in the terminal and look for VGA

---

### Post by clinux on 2008-07-15
```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO] (rev 10)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
00:0a.0 Communication controller: Intel Corporation 536EP Data Fax Modem
01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x] (rev a1)

```

---

### Post by overdrank on 2008-07-15
> **clinux said:**
> ```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO] (rev 10)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
00:0a.0 Communication controller: Intel Corporation 536EP Data Fax Modem
[COLOR="Red"]01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x] (rev a1)[/COLOR]

```

Ok have you enabled the drivers for the nvidia graphics card located under system, administration, hardware drivers?

---

### Post by clinux on 2008-07-15
ah, i was almost certain that this would be a problem.. i don't have them enabled because when i enable it i can only have a maximum resolution of 800x600. Now with them disabled it's 1024x768.
I'll test it now...

---

### Post by clinux on 2008-07-15
Ok just tried this, works with drivers enabled, however its 800x600. Now that i also tested Visual Effects, I NEED 1024x768! Why i'm unable to set 1024x768 with drivers enabled?!

---

### Post by overdrank on 2008-07-15
> **clinux said:**
> Ok just tried this, works with drivers enabled, however its 800x600. Now that i also tested Visual Effects, I NEED 1024x768! Why i'm unable to set 1024x768 with drivers enabled?!

Ok you can try and install nvidia settings from synaptic manager and then use the command ```
gksu nvidia-settings 
``` and adjust the resolution there.

---

### Post by clinux on 2008-07-15
Thanks that works, but there is another problem. When i use extra or normal visual effects, the title bar vanishes and the windows seem to not recognize the upper panel.

EDIT: problem solved: [http://www.pendrivelinux.com/2007/10/17/ubuntu-desktop-effects-fixing-the-missing-titlebar/](http://www.pendrivelinux.com/2007/10/17/ubuntu-desktop-effects-fixing-the-missing-titlebar/)

---

