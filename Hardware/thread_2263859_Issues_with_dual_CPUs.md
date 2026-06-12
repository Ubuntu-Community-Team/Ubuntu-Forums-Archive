---
title: "Issues with dual CPUs"
date: 2015-02-03
forum: Hardware
---

### Post by Ludwigzz on 2015-02-03
As the title says, i'm having issues with my HP ProLiant DL380 G4 server. It's running Ubuntu Server 14.04. I've done some basic research, only coming up with the solution of unplugging usb devices before booting. That didn't work. It has two of these CPUs. [http://ark.intel.com/products/28017/64-bit-Intel-Xeon-Processor-3_20-GHz-2M-Cache-800-MHz-FSB](http://ark.intel.com/products/28017/64-bit-Intel-Xeon-Processor-3_20-GHz-2M-Cache-800-MHz-FSB)

Any help would be appreciated.

---

### Post by mastablasta on 2015-02-04
and the issue is what exactly ? it doesn't boot? what about CentOS?

---

### Post by Ludwigzz on 2015-02-04
The cpu isn't listed as active, only one is listed when I type lscpu.

---

### Post by tgalati4 on 2015-02-04
I assume you have installed a 64-bit operating system:

```
uname -a
```

Boot into BIOS and check for any settings that would disable multiple CPU's--like custom clock or memory settings.  Start with factory default BIOS settings.

Compare your BIOS version with the latest that is available from HP.  Upgrade your BIOS if necessary.

---

### Post by SeijiSensei on 2015-02-04
Run the "top" command and press the "1" key.  How many "CPUs" does it report?

I maintain a dual-Xeon Dell server running CentOS 6.5 x86_64.  It configured itself to use both CPUs during installation without any extra intervention on my part.  Top reports:
```

top - 12:26:12 up 63 days, 21:51,  2 users,  load average: 1.53, 1.43, 1.37
Tasks: 384 total,   3 running, 381 sleeping,   0 stopped,   0 zombie
Cpu0  :  0.9%us,  0.5%sy,  0.0%ni, 98.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu1  :  0.9%us,  0.5%sy,  0.0%ni, 98.1%id,  0.0%wa,  0.0%hi,  0.5%si,  0.0%st
Cpu2  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu3  :  0.5%us,  0.0%sy,  0.0%ni, 99.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu4  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu5  : 13.3%us,  0.9%sy,  0.0%ni, 73.9%id, 11.8%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu6  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu7  :  0.5%us,  0.0%sy,  0.0%ni, 99.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu8  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu9  : 89.5%us,  0.0%sy,  0.0%ni, 10.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu10 : 35.5%us,  2.8%sy,  0.0%ni, 61.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu11 :  0.0%us,  0.5%sy,  0.0%ni, 99.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu12 :  0.5%us,  0.0%sy,  0.0%ni, 99.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu13 :  0.0%us,  0.0%sy,  0.0%ni, 99.1%id,  0.9%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu14 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu15 :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st

```

---

### Post by Ludwigzz on 2015-02-04
Installing CentOS has solved my issue. I would assume it's either my CPUs being outdated, no driver support, etc. 
In the bios, both CPUs were enabled.


```
 
top - 15:23:11 up  8:33,  1 user,  load average: 0.11, 0.25, 0.39Tasks: 149 total,   1 running, 148 sleeping,   0 stopped,   0 zombie
%Cpu0  : 12.8 us,  0.7 sy,  0.0 ni, 86.6 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu1  :  3.7 us,  0.7 sy,  0.0 ni, 95.3 id,  0.3 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu2  :  4.6 us,  1.0 sy,  0.0 ni, 94.4 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
%Cpu3  :  8.3 us,  0.3 sy,  0.0 ni, 91.3 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st

```

---

