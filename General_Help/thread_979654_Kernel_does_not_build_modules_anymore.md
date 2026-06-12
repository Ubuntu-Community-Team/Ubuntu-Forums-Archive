---
title: "Kernel does not build modules anymore"
date: 2008-11-12
forum: General Help
---

### Post by Hausi on 2008-11-12
Hi,
 since a few weeks kernel compilation completes with a few section mismatches (mostly trampoline, whatever that is) and gives me the MODPOST 0 modules message: 

<snip>
  OBJCOPY arch/x86/boot/setup.bin
  OBJCOPY arch/x86/boot/vmlinux.bin
  BUILD   arch/x86/boot/bzImage
Root device is (8, 1)
Setup is 11324 bytes (padded to 11776 bytes).
System is 2633 kB
CRC fd64ae04
Kernel: arch/x86/boot/bzImage is ready  (#10)
  Building modules, stage 2.
  MODPOST 0 modules
<snip>

This happens for Kubuntu and Ubuntu 8.10
I have looked for answers, but found nothing which could solve this problem...

thanks _Hans

---

