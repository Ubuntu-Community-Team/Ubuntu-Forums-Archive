---
title: "APIC &amp; IO-APIC"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by Xgates on 2005-05-16
In /var/log/messages I get this info:

May 16 16:20:57 localhost kernel: PCI: Using ACPI for IRQ routing
May 16 16:20:57 localhost kernel: ** PCI interrupts are no longer routed automatically.  If this
May 16 16:20:57 localhost kernel: ** causes a device to stop working, it is probably because the
May 16 16:20:57 localhost kernel: ** driver failed to call pci_enable_device().  As a temporary
May 16 16:20:57 localhost kernel: ** workaround, the "pci=routeirq" argument restores the old
May 16 16:20:57 localhost kernel: ** behavior.  If this argument makes the device work again,
May 16 16:20:57 localhost kernel: ** please email the output of "lspci" to [email]bjorn.helgaas@hp.com[/email]
May 16 16:20:57 localhost kernel: ** so I can fix the driver.

I'm using a DFI NF11 400-AL mobo:
[http://www.dfi.com.tw/Product/xx_product_spec_details_r_us.jsp?PRODUCT_ID=1982&CATEGORY_TYPE=MB&SITE=NA](http://www.dfi.com.tw/Product/xx_product_spec_details_r_us.jsp?PRODUCT_ID=1982&CATEGORY_TYPE=MB&SITE=NA)

And a AMD 3000+XP, I'm not sure if these both have support for APIC & IO-APIC

Thanks

---

### Post by luca_linux on 2005-05-17
Don't worry, it's just a warning about the behaviour of the new kernel version.

---

