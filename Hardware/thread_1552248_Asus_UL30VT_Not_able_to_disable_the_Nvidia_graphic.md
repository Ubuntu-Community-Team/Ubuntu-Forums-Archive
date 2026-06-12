---
title: "Asus UL30VT Not able to disable the Nvidia graphic card"
date: 2010-08-13
forum: Hardware
---

### Post by rdjse on 2010-08-13
Hi!

I just bought an Asus UL30JT, it contains two graphic cards, one Intel and one Nvidia. I understand there is no easy way to switch between them, so what I want to do is to disable the Nvidia card and just use the Intel card (for power saving reasons)

I found this thread with a suggestion on how to disable the Nvidia card: [http://ubuntuforums.org/showthread.php?t=1366605]("http://ubuntuforums.org/showthread.php?t=1366605")

I installed the .deb package without any problem and when I try to modprobe the module I get this error message:
```

FATAL: Error inserting nvidia_g210m_acpi (/lib/modules/2.6.32-21-generic/updates/dkms/nvidia-g210m_acpi.ko): Kernel does not have module support

```

I then tried and unload a bluetooth module and then loading it again, and that worked, so apparently I have some kind of module support. So why am I not able to modprobe this module that I actually need?
Do I really need to download the kernel source and manually compile a new kernel for this "fix" to work or is it possible to enable module support in an easy way?

If you guys have any info on what I should do to disable the nvidia card in my laptop, you have info on how to load this module or want more info please reply. :)

Thanks in advance!

---

### Post by dswissmiss on 2010-08-16
I just got the UL30JT a few days ago myself. 
Do you know for sure that you can't switch between the two cards? I'm doing some research on this myself over the next week, will let you know if I come up with anything - but let me know if you have any good resources.

I assume you have gone through this thread? [http://ubuntuforums.org/showthread.php?t=1300562](http://ubuntuforums.org/showthread.php?t=1300562)

---

