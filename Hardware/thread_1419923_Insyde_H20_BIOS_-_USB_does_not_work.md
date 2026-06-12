---
title: "Insyde H20 BIOS - USB does not work"
date: 2010-03-02
forum: Hardware
---

### Post by sirflyalot on 2010-03-02
I have a new Toshiba A505-S6030 laptop.  It has an Intel Core i7 processor.  I took an Ubuntu CD with me to Best Buy and tried booting the Toshiba Core i3 and i5 laptops.  They hang halfway through the bootup process.

[http://www.linlap.com/wiki/toshiba+satellite+a505](http://www.linlap.com/wiki/toshiba+satellite+a505)

It has Insyde H20 BIOS, and the USB ports do not work.  (Nor does the wifi, nvidia driver, etc, but first things first.)  Without USB, Ubuntu is unusable.  This laptop is very new, and there are no updates to the BIOS on the Toshiba support page.

I have been using all versions of Ubuntu with very few problems since 6.10.

I found this page talking about an iommu problem, but it does not exactly fit the problem:

[http://fedoraproject.org/wiki/Common_F12_bugs#Systems_fail_to_boot.2C_USB_is_not_functional.2C_network_adapter_fails_to_work_.28or_possibly_other_symptoms.29_due_to_imperfect_handling_of_BIOSes_with_broken_IOMMU_handling](http://fedoraproject.org/wiki/Common_F12_bugs#Systems_fail_to_boot.2C_USB_is_not_functional.2C_network_adapter_fails_to_work_.28or_possibly_other_symptoms.29_due_to_imperfect_handling_of_BIOSes_with_broken_IOMMU_handling)

I have attached my messages file for the most recent boot.

I know that this processor has issues also, and those will not be fixed until the 2.6.33 kernel, which will be Ubuntu 10.10.

Any ideas?  Thank you all for your time and most generous help.

If I need to provide more detail, please let me know.

---

### Post by rampage355 on 2010-04-20
I had to boot mine with noacpi and nomodeset in the F6 option

See post #26 by Simulator
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1400432&highlight=toshiba+a505&page=3]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1400432&highlight=toshiba+a505&page=3")

Only problem i found is on the wireless driver installation, if i installed as sudo the wireless would lock up my computer usually within about 15 min. So install with root and that does the trick.

---

