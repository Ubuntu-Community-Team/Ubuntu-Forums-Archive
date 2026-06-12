---
title: "Cannot install ubuntu on Acer Aspire AMD Athlon dual core"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by spice_vs on 2009-09-06
Hi,
I bought a new laptop last week. Its Acer Aspire 6530, 
AMD Athlon X2 dual core.

I have Vista already running on it. I tried installing Ubuntu 9.04 from USBFlash made from Unetbootin. 

On boot i choose unbuntu and it starts the splash screen. But then gives some error about dual core bit not set ..
Just after it i get Busybox shell with the prompt

(initramfs)

I am not sure what should i do. I tested the usb for installation on other laptop and the live version booted fine.

Can anyone please tell me whats wrong with AMD dual core. Or am i guessing random.

Please reply soon. i need ubuntu very badly. I am not used to this Vista..

---

### Post by pastalavista on 2009-09-06
So you have already installed or are you trying to boot the live USB? I'm guessing you installed with Wubi (inside of Windows). Can you boot into linux recovery mode? I would try that and run fsck (file system check) and repair broken packages and reboot normally.

---

### Post by spice_vs on 2009-09-06
Hi i just noted the text displayed before the promt. 
> 
Firmware warn: MTRR:CPU 0 SYSCFG[mtrrfixdrammoden] not cleared by bios clearing this bit

modprobe:fatal:could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory

ata1 softreset failed. device not ready


If this helps..

---

### Post by spice_vs on 2009-09-06
I am trying to boot using ubuntu Live. I do not have any installation of ubuntu before. Its just plain vista i got with purchase..

> **pastalavista said:**
> So you have already installed or are you trying to boot the live USB? I'm guessing you installed with Wubi (inside of Windows). Can you boot into linux recovery mode? I would try that and run fsck (file system check) and repair broken packages and reboot normally.

---

### Post by pastalavista on 2009-09-06
I don't know why it won't boot. My g/f has the same processor and I installed it (8.10) on hers with a live USB no problem. Maybe it has been corrupted somehow by former usage. If you still have the iso file, you might want to try Unetbootin again.

(I gave her 8.10 instead of 9,04 because she has an older ATI graphics card)

---

### Post by spice_vs on 2009-09-06
Thats what the title says.. Cannot install or even run in live mode. :(

---

### Post by spice_vs on 2009-09-06
its a fresh USB setup i did by download ubuntu 9.04 just yesterday.

---

### Post by yomna98 on 2009-09-16
I have also the same exact problem except  i was installing ubuntu 9.04 from installation CD

---

### Post by oeyrvin on 2009-09-20
We have the same problem with Acer Aspire 7735ZG. It is "impossible" to get it to read our ubuntu 9.04 DVD :confused:

---

### Post by yomna98 on 2009-10-10
I found a solution that works for me at least
at the prompt initamfs> type the command retrun .... thats all and the boot process will continue

---

