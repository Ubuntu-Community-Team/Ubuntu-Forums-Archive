---
title: "Samsung NP550P7C"
date: 2012-07-20
forum: Hardware
---

### Post by jural on 2012-07-20
I've been struggling with some issues. First I will start off with a listing of my hardware.

00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation Device 0de9 (rev ff)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

I have an issue with over heating, the laptop is a week old, and no fans are cloged.

I've tried various solutions, pwmconfig errors with: /usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed, Jupiter seems to have no effects, and the samsung tools for laptops cannot start the fans.

Typically the system will run at 45 to 56 c on each cpu. The fans simply never kick in.

I have disabled acpi. This resulted in the Fans continuously running and the system locking up after 10 to 15 minutes. Temp was 55 to 57 c. By locked up I meen no gui control, and not able to switch to console (ctrl+alt+f1 - f6).

I've been through many form posts, and lots of google results but it seems no real solution.

Any help would be appreciated.

Just so you know my skill level, I ran Gentoo for years from stage 1 and hand rolled my kernel, I don't have enough time to maintain a gentoo build these days.

Last part, I have the system dual booting the original OS windows 7, it is stable and does not have any of the issues I am seeing in linux.

---

