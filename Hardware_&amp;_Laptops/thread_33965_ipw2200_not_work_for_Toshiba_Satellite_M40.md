---
title: "ipw2200 not work for Toshiba Satellite M40"
date: 2005-05-12
forum: Hardware &amp; Laptops
---

### Post by hshen on 2005-05-12
My laptop has dual boot: Windows XP and Ubuntu 5.04.

The Ubuntu boot hangs at hotplug installation. So I disabled the hotplug (by rename the hotplug start script from S40hotplug to s40hotplug). Now I have Ubuntu running nicely except I don't have network connection.

lspci shows that the wireless card is Intel PRP/Wireless 2915ABG. Its driver
(ipw2200) and firmware (firmware_class) are built into the kernel. After running modprobe ipw2200, lsmod shows that ipw2200 is alive. But I don't see anything related to the card when running iwlist. Checking /var/log/message, I got 

  ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19
  ipw2200: Copyright(c) 2003-2004 Intel Corporation
  ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
  ACPI: PCI interrupt 0000:06:04.0[A] -> GSI 11 (level, low) -> IRQ 11
  ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
  ipw2200: probe of 0000:06:04.0 failed with error -5

More detailed diagnose from dmesg shows that 

  ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19
  ipw2200: Copyright(c) 2003-2004 Intel Corporation
  ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
  ACPI: PCI interrupt 0000:06:04.0[A] -> GSI 11 (level, low) -> IRQ 11
  ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
  ipw2200: failed to send TX_POWER command
  ipw2200: failed to send TX_POWER command
  ipw2200: failed to send TX_POWER command
  ipw2200: failed to send TX_POWER command
  ipw2200: failed to send TX_POWER command
  ipw2200: Unable to initialize device after 5 attempts.
  ipw2200: failed to register network device
  ipw2200: probe of 0000:06:04.0 failed with error -5

What shoud I do to get around this problem? 

Thank!
hshen

---

### Post by luca_linux on 2005-05-13
You have to update your driver to the latest version that is 1.0.3: just follow this howto: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)

---

### Post by hshen on 2005-05-13
Thanks! I will try it.

---

