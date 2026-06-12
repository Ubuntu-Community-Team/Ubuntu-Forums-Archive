---
title: "Toshiba Portege Z930 Power Consumption"
date: 2012-12-11
forum: Hardware
---

### Post by andradx on 2012-12-11
Here's a few things to start with. I've recently installed ubuntu 12.04 on a Toshiba Portege Z930 and performed a series of modifications to my grub ad fstab settings so that I could optimize the SSD, power settings etc.

I've added the options:

discard,noatime,nodiratime to the ubuntu partition in /etc/fstab,

and:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force i915.i915_enable_rc6=1 i915.lvds_downclock=1 acpi_osi=Linux acpi_backlight=vendor elevator=noop"
GRUB_CMDLINE_LINUX="quiet splash pcie_aspm=force i915.i915_enable_rc6=1 i915.lvds_downclock=1 acpi_osi=Linux acpi_backlight=vendor elevator=noop",


which enables a series of power optimizations to enhance my battery life.


On Windows 7, in Eco Mode I get at 100% battery (mainly browsing) ~7h. However, the laptop power consumption statistics is reporting a close to 10W dischage rate of the battery.


In Ubuntu, I've installed the PowerTool from [here]("https://01.org/powertop/") and I get a 8W discharge rate. However, this gives me an expected 4h battery.

Question 1: How can I truly let my battery last as long as it does running Windows but running Ubuntu.

Question 2: Are the options apropriate for SSD optimization and for power consumption optimization?

Question 3: Can I thank you in advance?

---

