---
title: "Monitor connected through DP to VGA Adapter only allows resolution of 1024x768"
date: 2016-02-29
forum: Hardware
---

### Post by abhijitb on 2016-02-29
I am using Lenovo Tiny m73 having **1 VGA** port and** 1 Display Port**.
Currently I have the following configuration:
[LIST]
[*]ThinkVision E1922s (1366x768) is connected to VGA Port. 
[*]DELL S2240L (1920x1080) is connected to Display Port (but through a Display Port to VGA adapter) 
[/LIST]
OS: Ubuntu 14.04 LTS (64 Bit)
Processor: Intel i5-4590T
RAM: 12 GB
Graphics: Intel Integrated Graphics

When I launch **Displays** to setup dual monitors I find that Ubuntu is unable to determine the display connected to Display Port (via DP to VGA adapter). When I switch the monitors (i.e., connect ThinkVision to Display Port and DELL to VGA Port) the results are identical. The monitor connected to the Display Port to VGA adapter always come as **Unknown Display** with only two allowed resolutions 1024x768 and 800x600

The monitor connected to VGA port never gets any issue.

Any help in this regard is highly appreciated.

---

### Post by gordintoronto on 2016-02-29
That is typical of DisplayPort to VGA adapters. DisplayPort to HDMI might work better, since both methods are digital. But no guarantees.

---

### Post by abhijitb on 2016-03-02
Are there any work arounds? Tried to use xrandr but -addmode did not work :(

---

### Post by buzzingrobot on 2016-03-02
The monitor's documentation/specifications will usually contain the maximum resolution available for each connection method allowed by the device. VGA is something of a fallback these days.

---

