---
title: "airo module freezes kernel"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by G2_vincent on 2008-02-24
all,

after I upgraded my kernel to 2.6.24, the airo module seemed to freeze the boot for quite some time (few minutes) and would never be activated.

I suspect some kind of IRQ trouble, yet, after I tried all sorts of kernel booting options (lapic nolapic acpi on, off, force, pci=irqroute, having disabled some devices in the bios) I am STUCK.

if I disable the wifi card in my BIOS, it boots properly (without wifi support of course)
if I enable it, it freezes after saying "airo : PCI probe" 

please help :)

The laptop is an IBM X31 and the card a Cisco MP350

---

### Post by G2_vincent on 2008-02-28
all,

I found a quickfix here : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/189398)

"
Hi, I bypassed the problem in a crude way.
Since the problem comes from the padlock_aes module that of course does not find any hardware on my pc, I went in the /lib/modules/2.6.24-xxx/modules.alias and I commented out the first two occurrences of AES that link to padlock and geode hardware.
So, the airo driver works perfectly now and the boot process is smooth as usual. Somebody should modify the configuration in a way that aes_generic or something like that is used on normal hardware.

Hope it works for you too!
marco"

---

