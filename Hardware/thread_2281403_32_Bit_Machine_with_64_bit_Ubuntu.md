---
title: "32 Bit Machine with 64 bit Ubuntu"
date: 2015-06-06
forum: Hardware
---

### Post by Shayaan_Mustafa on 2015-06-06
Hello everyone!

As Ubuntu official website says, "If you have RAM less than 2GB then install Ubuntu 32 bit otherwise install 64 bit"

My machine is 32 bit. Can I install 64 bit Ubuntu on my system? And will it work efficiently.

PS: I have 3 GB RAM

Best Regards,
Shayaan Mustafa

---

### Post by howefield on 2015-06-06
Yes, you can assuming that your machine is 64 bit capable but if as your title says your machine is 32 bit, you can't.

---

### Post by tgalati4 on 2015-06-06
If your processor supports PAE--physical address extension, then you will see all 3 GB using 32-bit linux.

Open a terminal:

```
cat /proc/cpuinfo
```

and

```
grep pae /proc/cpuinfo
```

Welcome to the forums.

---

### Post by lisati on 2015-06-06
> **Shayaan_Mustafa said:**
> 
My machine is 32 bit. Can I install 64 bit Ubuntu on my system?

What sort of computer are you using? 

If your machine is really 32-bit, you're unlikely to get a 64-bit OS to work. On the other hand, it is often possible to run a 32-bit OS on a 64-bit computer.

I have seen 64-bit computers come with a 32-bit OS installed. If we know the make and model, perhaps some of the hardware gurus will be able to give you a better idea.

---

### Post by yancek on 2015-06-06
64-bit software will not work on hardware that is 32-bit but the reverse will work so, if you know your hardware is 32-bit, download a 32-bit OS.  You can determine if the hardware is 64-bit with the command:  grep flags /proc/cpuinfo

If you see 'lm' in the output as shown in red below, that means the hardware is 64-bit

flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp [COLOR=#ff0000]lm[/COLOR] 3dnowext 3dnow up extd_apicid pni cx16 lahf_ svm extapic cr8_legacy 3dnowprefetch lbrv

---

