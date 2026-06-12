---
title: "SATA Not working v8.04 and v8.10"
date: 2008-11-30
forum: Hardware
---

### Post by skozzy on 2008-11-30
Since the release of v8.04 and also now with v8.10 I can not use my sata ports. In v8.04 the system boots but the sata drives do not apear, in v8.10 the system falls to a busybox.

If I unplug the sata drive v8.10 boots all the way to the OS Desktop.

The mainboard is a Asus A8V-MX with the latest available BIOS.

Can someone please offer advice how to get the SATA working for this lastest version of Ubuntu. It is very inconveniant to unplug the sata drive to boot ubuntu.

In XP and Vista everything works fine.

---

### Post by cariboo on 2008-11-30
Check your BIOS for an AHCI setting. Vista and Ubuntu will still work, and if you have an up-to-date XP install it should be OK to make the change. If your XP install is not up-to -date it may not boot.

Jim

---

### Post by skozzy on 2008-11-30
I have 3 options in bios around the ATA
1. SATA
2. RAID
3. AHCI
If I enable AHCI I get another option to enable a boot rom.

I tried the RAID and AHCI and AHCI+BOOTROM. Neither allow me to boot to Ubuntu Desktop. But both wait much longer before dropping to a busybox.

When AHCI+BOOTROM is enabled Windows XP and Vista never boot. I googled some info on AHCI and see drivers are needed to be installed before using the option in Windows. The explaination of making it work in Lunix was a little over my head at the moment.

I also killed my working Ubuntu 7.10 install somehow after tinkering with the bios settings. I am back to using bios set to SATA as it was when before changing settings, so Windows XP and Vista boots and runs.

I will attempt to install Ubuntu 7.10 again.

So is there something else to try.

---

### Post by satworld on 2011-06-04
sata does not work on 8.04 no matter what you do
sata hdd is not recognised and sata dvdrw is not recognused
its not possible to install it at all
i hope in 10.04 it will work

---

