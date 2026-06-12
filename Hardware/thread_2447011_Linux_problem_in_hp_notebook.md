---
title: "Linux problem in hp notebook"
date: 2020-07-10
forum: Hardware
---

### Post by arnav16 on 2020-07-10
[COLOR=#000000][FONT=HPSimplifiedLight]Hello everyone!!! I am being fed up due to this problem. I have tried everything i could do.  I have tried installing every linux in my notebook but each of them gave me the same error. At every bootup, it encounters  a warning saying ata2: COMRESET FAILED (errorno (-32)). And the boot load time is extremely slow. The login screen appears only after waiting 20-25 minutes from boot time. I am not able to get any solution. Please somebody help me with this. This have ruined my entire time. Please help me.

[/FONT][/COLOR][COLOR=#000000][FONT=HPSimplifiedLight]Look at this screenshot for error:[/FONT][/COLOR]
[COLOR=#000000][FONT=HPSimplifiedLight][https://prnt.sc/tfpeq2](https://prnt.sc/tfpeq2)[/FONT][/COLOR]
[COLOR=#000000][FONT=HPSimplifiedLight][https://prnt.sc/tfpex1](https://prnt.sc/tfpex1)[/FONT][/COLOR]
[COLOR=#000000][FONT=HPSimplifiedLight][https://cloud.sudiprijal.com.np/index.php/s/uW9abRu0dFpqKGj](https://cloud.sudiprijal.com.np/index.php/s/uW9abRu0dFpqKGj)

My laptop specs are:

Processor: Intel(R) Core(TM) i5-4200U CPU @ 1.60GHz 2.30 GHz
RAM: 8 GB
System Model: HP Pavilion 14 Notebook PC
Graphics: AMD Radeon (TM) HD 8670M[/FONT][/COLOR]

---

### Post by zebra2 on 2020-07-11
Don't know much about the configuration of the MB but you may want to check the boot order in your bios and point the boot at your boot drive. Turning off AHCPI may also help.
Worst case, it won't work.

---

### Post by arnav16 on 2020-07-12
Thanks for the reply. I have managed the boot order. But I don't have any option related to AHCPI in bios option.

---

### Post by zebra2 on 2020-07-12
So, did "managing the boot order" help the boot at all?

---

### Post by mastablasta on 2020-07-13
*** as pointed here: [https://askubuntu.com/questions/947126/how-to-fix-ata7-com-reset-failed-errno-32](https://askubuntu.com/questions/947126/how-to-fix-ata7-com-reset-failed-errno-32)

the issue and error is often related to bad disk drive or bad SATA connector / cable.  is the issue present when booting from USB? if not then drive needs a checkup.


> **arnav16 said:**
> Thanks for the reply. I have managed the boot order. But I don't have any option related to AHCPI in bios option.

You can change it on kernel (temporary first): [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

you could try acpi=off or noacpi
ubuntu boot options: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

since you have radeon card i would also try nomodeset.

---

