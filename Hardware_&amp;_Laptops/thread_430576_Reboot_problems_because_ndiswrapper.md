---
title: "Reboot problems because ndiswrapper"
date: 2007-05-02
forum: Hardware &amp; Laptops
---

### Post by adrian.urgyan on 2007-05-02
Hello,

I hope I'm posting in the right forum.

I was looking forward to the final Feisty badly, and when it came out I downloaded and installed it right after, so I could use it as my primary OS.
After the smooth install I sadly realized that my built-in WiFi card not working (used to work in the 6.10). It's a Gemtek ... card based on Intersil ISL3886 chipset (computer is: FuSi Amilo L1300).

Ok, no problems at all, we have ndiswrapper. Installed it, working fine, but I got some issues with the ndiswrapper. Every (and I really mean it) reboot (no matter that I choose Windows or Ubuntu in grub) freezes on boot. Both Windows XP and Ubuntu. (the XP freezing coming after a little noise from speakers, probably hardware detect part). And it's very, very annoying. If I'm doing shutdown instead of reboot, its all working fine. If I remove the Gemtek driver, it's all fine.

Is there any way to solve this, so I could use Feisty as soon as possible? :)
I'm interested in any solutions.

Thanks in advance,
Adrian Urgyan

---

### Post by adrian.urgyan on 2007-05-02
Can't get my Windows to bootlog, only logging the successfull boots...
But I catched some part from the freezed linux boot.

Last lines that I saw on the debug mode boot were:

May  3 02:13:48 fusi kernel: [   21.228000] ndiswrapper: driver prisma00 (Conexant,07/20/2004, 2.1.25.0) loaded
May  3 02:13:48 fusi kernel: [   21.228000] ACPI: PCI Interrupt 0000:01:01.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
May  3 02:13:48 fusi kernel: [   21.228000] ndiswrapper: using IRQ 11

---

### Post by sae.area on 2008-07-22
Hi,

did you ever solve the problem? I have the same issue and created a workaround. I am interested in how you solved it.

Best wishes...

---

