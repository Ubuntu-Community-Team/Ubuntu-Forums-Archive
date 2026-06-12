---
title: "Lenovo brightness problem. I want linux."
date: 2013-09-05
forum: Hardware
---

### Post by jeehyun on 2013-09-05
I tried ubuntu 1210, 1304, mint 15 and elementary os for lenovo m490s laptop(3rd intel hd graphics).
No issues on graphic driver but it's not fully bright. On windows 8, it's good.
White color seems to be grey.
I tried xcalib and xbacklight but i can't increse brightness or contrast because it is already 100%.

HELP!!!
I don't want to give up linux.

---

### Post by Toz on 2013-09-05
Can you provide some more information (run commands in terminal and post back results)?

1. Your current kernel boot parameter line:
```
cat /proc/cmdline
```

2. Your video card information:
```
lspci -k | grep -A3 VGA
```

3. Your backlight interfaces:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; cat $i/actual_brightness; done
```

4. Your Xorg log file:
```
pastebinit /var/log/Xorg.0.log
```
...and post back link that is generated.

---

### Post by jeehyun on 2013-09-08
Hey TOZ. Sorry too late.


me@M490s ~ $ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=d8f695a5-84a8-4c38-b622-0564a77a6a59 ro quiet splash vt.handoff=7
me@M490s ~ $ lspci -k | grep -A3 VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
	Subsystem: Lenovo Device 5014
	Kernel driver in use: i915
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
me@M490s ~ $ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; cat $i/actual_brightness; done
/sys/class/backlight/acpi_video0
100
100
100
/sys/class/backlight/intel_backlight
4437
4437
2958
me@M490s ~ $ pastebinit /var/log/Xorg.0.log
'pastebinit' &#54532;&#47196;&#44536;&#47016;&#51008; &#45796;&#51020; &#44984;&#47084;&#48120;&#46308;&#50640;&#49436; &#52286;&#51012; &#49688; &#51080;&#49845;&#45768;&#45796;:
 * pastebinit
 * pastebinit
&#45796;&#51020;&#51012; &#49892;&#54665;&#54644; &#48372;&#49901;&#49884;&#50724;: sudo apt-get install <&#49440;&#53469;&#54620; &#44984;&#47084;&#48120;>

---

### Post by Toz on 2013-09-08
> **jeehyun said:**
> me@M490s ~ $ pastebinit /var/log/Xorg.0.log
'pastebinit' &#54532;&#47196;&#44536;&#47016;&#51008; &#45796;&#51020; &#44984;&#47084;&#48120;&#46308;&#50640;&#49436; &#52286;&#51012; &#49688; &#51080;&#49845;&#45768;&#45796;:
 * pastebinit
 * pastebinit
&#45796;&#51020;&#51012; &#49892;&#54665;&#54644; &#48372;&#49901;&#49884;&#50724;: sudo apt-get install <&#49440;&#53469;&#54620; &#44984;&#47084;&#48120;>
Looks like pastebinit might not be installed. Install it by looking for it in the software centre or by command line like:
```
sudo apt-get install pastebinit
```
...then one more time:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

> me@M490s ~ $ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=d8f695a5-84a8-4c38-b622-0564a77a6a59 ro quiet splash vt.handoff=7
> me@M490s ~ $ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; cat $i/actual_brightness; done
/sys/class/backlight/acpi_video0
100
100
100
/sys/class/backlight/intel_backlight
4437
4437
2958

Lets try to get rid of one of your backlight interfaces to see if that works. Using the instructions from the "Temporarily Add a Kernel Boot Parameter for Testing" section of [this]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") page, add the **acpi_backlight=vendor** boot parameter. After you have done that and logged back in, see if its any better and one more time post back:
```
cat /proc/cmdline
```
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; cat $i/actual_brightness; done
```

---

### Post by jeehyun on 2013-09-08
TOZ! Thank you very much. I fixed problem. :D

acpi_backlight=vendor

---

### Post by Toz on 2013-09-09
> **jeehyun said:**
> TOZ! Thank you very much. I fixed problem. :D

acpi_backlight=vendor
Glad to hear. Can you please mark this thread Solved using the "Thread Tools" link towards the top of this page?

---

