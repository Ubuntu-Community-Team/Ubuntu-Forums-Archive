---
title: "Ubuntu 9.04 on a Macbook, Close Lid id not recognised"
date: 2009-07-10
forum: Hardware
---

### Post by divot_powell on 2009-07-10
Hi,

I recently install Ubuntu on a Macbook 1,1 for a friend. Unfortunately it seems that opening and closing her laptop lid is not being recognized by the acpi. 

$ dmesg | grep Lid
[    1.895370] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.895423] ACPI: Lid Switch [LID0]

Monitoring /proc/acpi/button/lid/LID0/state shows that it never thinks that the lid is closed. Anyone have any ideas how to fix this?

I want to be able to turn on suspend on lid close for her but it's not working and I'm having to resort to suspend on timeout instead.

---

