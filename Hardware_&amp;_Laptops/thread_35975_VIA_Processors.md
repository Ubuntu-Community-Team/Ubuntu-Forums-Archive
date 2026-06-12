---
title: "VIA Processors"
date: 2005-05-21
forum: Hardware &amp; Laptops
---

### Post by royscott on 2005-05-21
I recently received my CDs, both the X86 and AMD64 versions. I have a PC that is run by the VIA CPU. Neither of the versions will work on it. I had thought that the VIA CPU family was fully X86 compatible, but apparently not for Ubuntu. Can you give me any info on this?

---

### Post by nad on 2005-05-21
There should be no issues with a via processor. Via chipsets often necessitate specific options as they do not play nicely with the current linux implementations of acpi and apic.

What are your specific problems?

---

### Post by royscott on 2005-05-21
The install fails during the hardware search and there is no way to recover. I also tried running the Live CD and got the same results.

---

### Post by ssam on 2005-05-21
i am running ubuntu fine on a via epia MII 6000

the installer run fine though i needed to put 

```
vga=771
``` 

as a boot argument.

sometimes it hang at hotplugging bit of booting. booting without the keyboard plugged in seems to help. sometimes unplugging the usb keybard when it hangs gets it going again.

sam

---

### Post by nick-f on 2006-02-08
thats weird, what via processor do you have? i have an m10000 nehemiah and everything  is fine, the only problem was a display problem on the first install screen which happened to be a bios setting gone awry.

---

### Post by ahh_dee on 2006-03-05
I just installed a 5000 and everything installed fine.  the only problem i have is the video buffering when i play video files.  can anyone help me with that?

---

### Post by az on 2006-03-05
Works fine on a Via C3.  They *are* x86 compatible.  They run the 386 kernel.

I suggest you have other hardware compatibility issues.

---

