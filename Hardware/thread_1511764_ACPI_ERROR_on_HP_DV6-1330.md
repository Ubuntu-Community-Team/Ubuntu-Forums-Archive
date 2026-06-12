---
title: "ACPI ERROR on HP DV6-1330"
date: 2010-06-17
forum: Hardware
---

### Post by kahnoie on 2010-06-17
I see the following error on /var/log/messages

Jun 12 01:23:37 amit-laptop kernel: [    0.323401] ACPI Error (psargs-0359): [\_PR_.CPU0._PPC] Namespace lookup failure, AE_NOT_FOUND
Jun 12 01:23:37 amit-laptop kernel: [    0.323401] ACPI Error (psparse-0537): Method parse/execution failed [\CPUL] (Node f7015b70), AE_NOT_FOUND
Jun 12 01:23:37 amit-laptop kernel: [    0.323401] ACPI Error (psparse-0537): Method parse/execution failed [\PSSC] (Node f7015b88), AE_NOT_FOUND
Jun 12 01:23:37 amit-laptop kernel: [    0.324022] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPC_.EC0_._REG] (Node f701ca38), AE_NOT_FOUND

Please let me know for additional logs.

---

### Post by kahnoie on 2010-06-17
Jun 12 01:23:37 amit-laptop kernel: [    6.119721] ACPI Error (dswload-0781): [_T_1] Namespace lookup failure, AE_ALREADY_EXISTS
Jun 12 01:23:37 amit-laptop kernel: [    6.119727] ACPI Exception: AE_ALREADY_EXISTS, During name lookup/catalog (20090903/psloop-230)
Jun 12 01:23:37 amit-laptop kernel: [    6.119733] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.PEGP.VGA_.LCD_.GBQC] (Node f7013408), AE_ALREADY_EXISTS
Jun 12 01:23:37 amit-laptop kernel: [    6.119743] ACPI: Marking method GBQC as Serialized because of AE_ALREADY_EXISTS error
Jun 12 01:23:37 amit-laptop kernel: [    6.119778] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.PEGP.VGA_.LCD_._BQC] (Node f70133f0), AE_ALREADY_EXISTS
Jun 12 01:23:37 amit-laptop kernel: [    6.119787] ACPI: Marking method _BQC as Serialized because of AE_ALREADY_EXISTS error
Jun 12 01:23:37 amit-laptop kernel: [    6.119824] ACPI Warning: Evaluating _BQC failed (20090903/video-641)
Jun 12 01:23:37 amit-laptop kernel: [    6.122228] acpi device:07: registered as cooling_device2
Jun 12 01:23:37 amit-laptop kernel: [    6.122798] ACPI Error (dswload-0781): [_T_1] Namespace lookup failure, AE_ALREADY_EXISTS
Jun 12 01:23:37 amit-laptop kernel: [    6.122804] ACPI Exception: AE_ALREADY_EXISTS, During name lookup/catalog (20090903/psloop-230)
Jun 12 01:23:37 amit-laptop kernel: [    6.122809] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.PEGP.VGA_.LCD1.GBQC] (Node f7013588), AE_ALREADY_EXISTS
Jun 12 01:23:37 amit-laptop kernel: [    6.122819] ACPI: Marking method GBQC as Serialized because of AE_ALREADY_EXISTS error
Jun 12 01:23:37 amit-laptop kernel: [    6.122854] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.PEGP.VGA_.LCD1._BQC] (Node f7013570), AE_ALREADY_EXISTS
Jun 12 01:23:37 amit-laptop kernel: [    6.122863] ACPI: Marking method _BQC as Serialized because of AE_ALREADY_EXISTS error
Jun 12 01:23:37 amit-laptop kernel: [    6.122901] ACPI Warning: Evaluating _BQC failed (20090903/video-641)

---

### Post by lidex on 2010-06-17
Have a look here:
[http://linux.aldeby.org/bios-dst.html]("http://linux.aldeby.org/bios-dst.html")
[http://forums.opensuse.org/information-new-users/unreviewed-how-faq/386054-how-fix-your-buggy-dsdt.html]("http://forums.opensuse.org/information-new-users/unreviewed-how-faq/386054-how-fix-your-buggy-dsdt.html")

---

