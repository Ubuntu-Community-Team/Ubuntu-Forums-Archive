---
title: "Missing System Memory"
date: 2008-12-14
forum: Hardware
---

### Post by AuronGrande on 2008-12-14
I was just browsing round Ubuntu 8.10 system information, more specifically "System Monitor" in Gnome when I noticed something that shouldn't be.

I have installed in my motherboard 4GB of memory, however, System Monitor is only showing 3.0 GiB.

The memory is physically fine, and so is the motherboard. Does anyone know what's happened to the other 1GiB?

My system on the very page where the above info is provided is as follows;

**Ubuntu**
   Release 8.10 (intrepid)
   Kernel Linux 2.6.27-9-generic
   Gnome 2.24.1

**Hardware**
   Memory: 3.0 GiB
   Processor 0: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+
   Processor 1: AMD Athlon(tm) 64 X2 Dual Core Processor 6000+

**System Status**
   Available disk space: 161.9 GiB

---

### Post by taurus on 2008-12-14
If you are running x86, then that is what you would see, 3.2GB of RAM, even if you have more than that.  If you want to use all 4GB of RAM, you need to install the x86_64 version.

Applications -> Accessories -> Terminal
```
uname -a
```

---

### Post by nick09 on 2008-12-14
Your computer could have onboard graphics(integrated into the motherboard) that uses that missing bit of memory.

---

### Post by AuronGrande on 2008-12-15
I am using the none 64bit version because for some reason the fglrx drivers for my Radeon X1950Pro 512mb PCIe card doesn't like the 64bit Ubuntu.

Also, the motherboard doesn't have built in graphics. Built in sound, but no graphics.

Why does the none 64bit version only see 3.2GB of system memory??

---

### Post by sdennie on 2008-12-15
This thread explains it a bit and provides possible solutions: [ Ubuntu with 4GB+ of memory]("http://ubuntuforums.org/showthread.php?t=855511")

---

### Post by AuronGrande on 2008-12-15
Well, I'm downloading the 64bit version of Ubuntu now. So I will see what happens.

Cheers

---

### Post by AuronGrande on 2008-12-16
I installed the 64bit version of Ubuntu. Sadly, it didn't go well. As I figured, the fglrx drivers for my graphics card were a no go from the start, and half my programs didn't work. Then to top it off, upon updating software, the darn thing went belly up.

I've returned to the 32bit version and am currently in the process of reinstalling everything.

---

### Post by cb951303 on 2008-12-16
> **AuronGrande said:**
> I installed the 64bit version of Ubuntu. Sadly, it didn't go well. As I figured, the fglrx drivers for my graphics card were a no go from the start, and half my programs didn't work. Then to top it off, upon updating software, the darn thing went belly up.

I've returned to the 32bit version and am currently in the process of reinstalling everything.

one thing not mentioned on that thread to use 4gig ram on a 32bit operating system is "memory hole remapping" which may be done from BIOS *if only* your motherboard supports it. mine doesn't so I'm stuck with 32bit and 3gig :(

---

### Post by AuronGrande on 2008-12-16
Sadly, my motherboard doesn't allow that as well.

---

