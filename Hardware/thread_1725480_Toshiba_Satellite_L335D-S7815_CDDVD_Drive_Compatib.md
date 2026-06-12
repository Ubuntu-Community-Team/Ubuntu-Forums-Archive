---
title: "Toshiba Satellite L335D-S7815 CD/DVD Drive Compatibility"
date: 2011-04-09
forum: Hardware
---

### Post by arascii on 2011-04-09
Hi,
I have a Toshiba Satellite L335D-S7815 and it's unable to recognize anything inserted into the CD/DVD drive. I hear it spinning up and then stopping, and generally making strange noises, but refuses to do anything. Trying to access the drive from Computer yields no result. 
I've installed every driver I can and every package that even remotely has to do with DVD playback  =- the one thing I haven't done yet is install a newer BIOS. Could that be the problem?

Has anyone else had this problem?
Thanks,
arascii

---

### Post by Yellow Pasque on 2011-04-09
It could be the BIOS or even a defective drive. The first step is to see if the BIOS recognizes the drive. If it doesn't, then no OS is going to see it.

Looking at your BIOS changelog, I do see a couple changes related to optical drive:
```
Change History

    Version 1.80 - 2009-09-17
        Updated: SLP2.1 for Windows 7.
        Added a brightness table.
        Added support for the QL-65 CPU updates: 1) AGESA version: X4.4.0.0, 2) NB CMI-X version: .4.5.0, 3) SB CIM-X version: V4.4.0.
        Fixed: MPEG/Audio stutters or skips when turning the WLAN switch off.
        Added: 3 LCD panel IDs.
        Added support for the Win7 Container ID function.
        The CMOS Year/Month/Date default setting is changed to 2009/07/01 after a RTC battery failure.
        Modified: English "Yes" and "No" to French in the French BIOS Setup.
        Modified: BIOS Setup and F12 menu strings from "USB Memory" to "USB".
        Added support for the 2009 DMI 32 and DMI 64 utilities.
        Added support for the TVAP "Alarm power on" functions for the Win7 tool.
        BIOS workaround for Win7 64-bit brightness (interfaces) cannot be set properly.
        Modified: HPCP_ESP setting to fix internal HDDs and ODDs will become removable devices.
        Updated: New P/N for the Win7 OS.
        Updated COMPUTRACE OPROM 887 which default delay time is 3000ms.
        Updated: VBIOS to fix a Win7 DTM "Class driver Wave test" issue.
        Workaround for Win7 SB700 Performance Counter lag issue.
        Added support for the 75W AC adaptor and related BIOS interfaces.
        Added support 75W AC Adaptor with New Main Board.
        Added support for the AC Throttle function.
        Modified the critical battery wake up prevent value from 2% to 5%.
        Modified the battery low blinks, battery LED value from 2% to 10%.
        Modified the S3 Critical Battery wake up value from 5% to 8%.
    Version 1.50 - 2009-03-14
        Added: Sempron CPU logo.
        Added: Press the Power Button + 7 key to boot from CD.
    Version 1.40 - 2009-01-14
        Fixed: LAN disappears after enabled in HWSetup and rebooted for the first time.
        Updated: DMI type 2 Manufacturer and Product name string.
        [B]Increased the waiting time (40 seconds) for BSY bit clear for IDE DVD ROM.
        Removed an extra SATA port reset for a "PIONEER ODD cannot be recognized" issue.[/B]
        Fixed: PCIE card can not be detected after an S3 resume.
        Disabled an unused clock to reduce power consumption.
        Fixed: When the system is booted to a PXE-Linux Server, file downloads take a longer time.
        Updated: Agesa code to X4.3.9.0 for the QI-46 CPU.
        Fixed: Two 512Mb RAM modules will report an incorrect available memory size.
        Added: Additional BIOS interface for the flash utility.
    Version 1.20 - 2008-07-19
        Updated the SB CIM-X code to V3.1.3.
        undefined
        Updated the NB CIM-X code to V4.2.0.
        Added panel ID Support for the LP154WX4-TLD2 panel.
        Added a QL-60 CPU warm boot workaround to fix a hang issue.
        Added the LP154WX4-TLD2 brightness table.
        Corrected: The Internal keyboard repeat speed can not be changed
```

---

