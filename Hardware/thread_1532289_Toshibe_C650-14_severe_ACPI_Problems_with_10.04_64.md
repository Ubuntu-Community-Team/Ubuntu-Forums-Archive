---
title: "Toshibe C650-14 severe ACPI Problems with 10.04 64bits"
date: 2010-07-16
forum: Hardware
---

### Post by SebX86 on 2010-07-16
Hi,

I bought a Toshiba Laptop Model C650-14. And like many of us,
I have severe ACPI issues with Ubuntu 10.04/64, no wireless,
no USB. Needless to say that Suspend to Ram and Suspend to Disk
crash the system...

First boot, system very slow, lots of IRQ conflicts; No USB and
no Wireless. 

Next try, used IRQPROBE in kernel parameters. I got USB working.
But still hyper slow. 

Tried with ACPI=off, It works perfectly (incl Wireless), but It's not very nice
as Fn keys don't work, no information about battery charge, screen dimming and so on.

Also tried with ACPI=noirq, ACPI=strict, It works (with Wireless too) and some
Hotkeys work too. In this case, when the kernel is running, 
I see some traces, and the system won't shutdown, restart.
After Halting, when trying to use ACPI, the kernel crashes...

I have several questions for you, how can I access ACPI info ?
I tried the omnibook driver but it doesn't work with this model.

How can I fix the Shutdown/Reboot problem ?

If you need something (lspci, lshw, kernel logs, etc), ask It I'll post it. 

Thank you very much...
Sébastien

---

### Post by SebX86 on 2010-07-17
Up, nobody has any idea ?

---

### Post by Linuxforall on 2010-07-24
I am picking this model next week with the i3 CPU, will see how it goes and keep you posted.

---

### Post by domagoj412 on 2010-07-24
Same problem here...
I tried with 32bit version - but it's the same...

I read somewhere that openSUSE would work, so I try that too - nothing! same problem!

I've seen that there where problems for other toshiba models... like this: [http://ubuntuforums.org/showthread.php?t=1534195](http://ubuntuforums.org/showthread.php?t=1534195)

That problem was solved by BIOS update (from 2 days ago) so maybe when update comes for this model - we will be able to use it...

---

### Post by domagoj412 on 2010-07-25
Now, I tried ubuntu 9.10 (64bit) and it works great!!
At least, I'm not stuck with windows anymore...

---

### Post by Linuxforall on 2010-08-01
Anyone got the LAN working on this, in my case the chip is detected but doesn't work.

---

### Post by phagem on 2010-08-06
I bought a Toshiba C650-15J yesterday preinstalled with Windows 7 64 bits. I made room for Linux and tried several distributions (Ubuntu 10.04, Mint 9, Fedora 13), they all gave similar problems with USB (mouse) and Wireless network (AR9285). After adding GRUB_CMDLINE_LINUX="noapic" to /etc/default/grub USB was working and my wireless network was recognized.

---

