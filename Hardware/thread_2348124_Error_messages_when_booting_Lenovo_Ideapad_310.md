---
title: "Error messages when booting Lenovo Ideapad 310"
date: 2016-12-31
forum: Hardware
---

### Post by leozinho29_eu on 2016-12-31
Hello

I have recently bought a Lenovo Ideapad 310, have installed Xubuntu 16.04 on the side of Windows 10 and, for now, I am considering it a pretty good experience.

My experience with its ports and devices:

-Function keys works;
-Wi-Fi: works;
-Ethernet works;
-VGA works;
-HDMI works;
-SD Card reader works;
-Bluetooth works;
-Sound speakers works;
-Microphone works;
-Phone+Microphone jack works;
-Webcam works;
-DVD drive works;
-USB 2.0 ports works;
-USB 3.0 is problematic, it's not possible to eject devices, they are remounted immediately.

However, I have noticed it do not boot so smoothly. It has some error messages early in the boot, and the informations I have found when searching about this error messages says that these errors should not allow the computer to boot, although it successfully boots. The messages are: ```
[    0.217884] platform MSFT0101:00: failed to claim resource 1
[    0.217889] acpi MSFT0101:00: platform device creation failed: -16
[    0.956251] EFI: Problem loading in-kernel X.509 certificate (-74)
[    0.956488] EFI: Problem loading in-kernel X.509 certificate (-74)
[    0.956938] EFI: Problem loading in-kernel X.509 certificate (-74)
```

The notebook is a Lenovo Ideapad 310, the specifications are: 
-14"
-Intel Core i3-6100U;
-4 GB of RAM;
-1 TB HDD;
-Windows 10 and Xubuntu 16.04;
-Both systems in UEFI mode;
-Safe boot is enabled.

Maybe the errors are related with the failure of the USB 3.0 device ejection due to failure in energy management, and may be something more important.

Thank you.

---

