---
title: "Ubuntu brightness can't be changed after upgrading to 13.04"
date: 2013-09-04
forum: Hardware
---

### Post by 915086731 on 2013-09-04
[LEFT][COLOR=#000000][FONT=Arial]Today I upgrade my ubuntu to version 13.04 from 12.10, however , the brightness can't be adapted. I have tried the previous kernel which worked on version 12.10, brightness can't be changed too. My PC is Acer 4750G.[/FONT][/COLOR][COLOR=#000000][FONT=Arial]My boot parameter:[/FONT][/COLOR][/LEFT]
```
RAMDISK$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.8.0-29-generic root=UUID=0f905c49-affc-49b5-809b-4f7eea7dddbf ro quiet splash acpi_backlight=vendor vt.handoff=7
```
[LEFT][COLOR=#000000][FONT=Arial]My graphic card details:[/FONT][/COLOR]
[/LEFT]
    ```
RAMDISK$ sudo lspci -vnn | grep -A12 VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device [1025:0507]
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at f3400000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915

00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108M [GeForce GT 540M] [10de:0df4] (rev ff) (prog-if ff)
    !!! Unknown header type 7f

03:00.0 Network controller [0280]: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
    Subsystem: Foxconn International, Inc. Device [105b:e034]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f3900000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 3
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [60] Express Legacy Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-15-17-ff-ff-24-14-12
RAMDISK$
```
[LEFT][COLOR=#000000][FONT=Arial]My brightness interfaces and their values:[/FONT][/COLOR][/LEFT]
```
RAMDISK$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/acer-wmi
1
15
/sys/class/backlight/intel_backlight
509
976
```
Thanks

---

### Post by Toz on 2013-09-04
1. Which one of your backlight interfaces is the active one? Try echoing in values to see:
```
echo 7 | sudo tee /sys/class/backlight/acer-wmi/brightness
echo 15 | sudo tee /sys/class/backlight/acer-wmi/brightness
```
...or
```
echo 200 | sudo tee /sys/class/backlight/intel_backlight/brightness
echo 976 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

2. What happens if you blacklist the acer-wmi module? As root, add **blacklist acer-wmi** to **/etc/modprobe.d/blacklist** and reboot. See if you can get to the point where you have only one backlight interface.

3. Since this is an optimus-based system, have you installed bumblebee to manage the nvidia card or have you somehow disabled it?

---

### Post by 915086731 on 2013-09-04
Thanks!
The following commands works:
```
echo 200 | sudo tee /sys/class/backlight/intel_backlight/brightness
echo 976 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

However , the Fn shutcuts still does not work, and, the graphic brightness setting still not work.  It's confusing.
I haven't install any tools about optimus such as bumblebee.

---

### Post by 915086731 on 2013-09-04
I add **blacklist acer-wmi** to **/etc/modprobe.d/blacklist** and reboot.
The Fn shutcuts works, and graphic brightness setting also works. It's confusing!
Can you tell me why I have to blacklist acer-wmi? And How can you get the genius idea to give me so valuable solutions?

---

### Post by Toz on 2013-09-04
> **915086731 said:**
> I add **blacklist acer-wmi** to **/etc/modprobe.d/blacklist** and reboot.
The Fn shutcuts works, and graphic brightness setting also works.
Glad to hear it works.
> It's confusing!
It sure is.
> Can you tell me why I have to blacklist acer-wmi?
The ultimate goal, I think, is to have only one backlight interface. Then the system will know which one it is and which one to use. When you have more than one, the system gets confused as to which is the active one. When you found out the intel_backlight was the active one, the goal became to remove the inactive one. The acer-wmi module provides the acer-wmi interface, so naturally, blacklisting the module would prevent that interface from showing up.
> And How can you get the genius idea to give me so valuable solutions?
Lots of reading and trial and error. Access to a couple of flakey laptops also helps.

If you don't mind, can you please mark this thread as solved by using the "Thread Tools" link above so that others can more easily find the solution? Thanks.

---

### Post by 915086731 on 2013-09-04
Thanks very much!
To love Linux is not easy. It is so immature. Sometimes much time have to be spent to solve some confusing problem.

---

