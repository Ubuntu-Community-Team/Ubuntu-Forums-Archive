---
title: "Processor Upgrade"
date: 2009-12-09
forum: Hardware
---

### Post by trudisill on 2009-12-09
I have a Ubuntu box set up that's main purpose is hosting vmware.  I am considering upgrading the processor form an amd athlon ii x2 6000 to an amd phenom II x4 940.  With this change will there need be a major.  I have done this kind of upgrade a couple times in windows and once it was smooth with no issue, the other i had to reinstall windows.  How does linux/ubuntu handle this?  Will i need to reinstall unbuntu?  I am running x64 version of v9.04.

Thanks

---

### Post by Fafler on 2009-12-09
No. Linux is very easy to move across different hardware platforms, as it probes for hardware on every boot and has (almost) all drivers readily available.

Shutdown, change the hardware, and boot back up.

---

### Post by zgornel on 2009-12-09
> **trudisill said:**
> I have a Ubuntu box set up that's main purpose is hosting vmware.  I am considering upgrading the processor form an amd athlon ii x2 6000 to an amd phenom II x4 940.  With this change will there need be a major.  I have done this kind of upgrade a couple times in windows and once it was smooth with no issue, the other i had to reinstall windows.  How does linux/ubuntu handle this?  Will i need to reinstall unbuntu?  I am running x64 version of v9.04.

Thanks

It should work flawlessly however, it might just give a kernel segmentation fault and a reinstall would be required.

---

### Post by gradinaruvasile on 2009-12-09
Ubuntu auto configures new hardware by default at every boot and loads the necessary modules. So, if the hardware is supported, it should work. And the processor should not be the issue, but the motherboard.

---

### Post by trudisill on 2009-12-09
Thanks folks, i appreciate it.

---

