---
title: "Acer/Ivybridge vs Screen Brightness"
date: 2013-06-06
forum: Hardware
---

### Post by mykrob on 2013-06-06
Bought a new laptop today, an Acer Aspire V5-571P. Full specs as reported by lshw are attached.

Everything seems to be working fine (including the touchscreen), except for screen brightness. Wonder if I can get a little assistance on that, as turning down the brightness should yield a significant boost in battery life.

thanks,
-myk

---

### Post by mykrob on 2013-06-06
I tried this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backight=vendor"

Based on a bug report, and it did not work for me.

---

### Post by mykrob on 2013-06-06
I also tried updating the Intel graphics driver, still no luck :(

---

### Post by Toz on 2013-06-06
> **mykrob said:**
> I tried this:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backight=vendor"

Based on a bug report, and it did not work for me.

Can you give the following a try:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"!Windows 2012\""
```

Which version of Ubuntu are you installing?

---

### Post by mykrob on 2013-06-06
13.04 64 bit. Going to try that boot parameter.

---

### Post by mykrob on 2013-06-06
No luck, same results as before. The on screen display comes up that shows the keypresses are being received and are attempting to trigger the right response, but the screen does not get any brighter or dimmer.

---

### Post by Toz on 2013-06-06
Just to confirm, are you running "sudo update-grub" after editing the file?

Can you also try:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="
```

After reboot (with those parameters), can you post back:
```
cat /proc/cmdline
```
```
sudo lspci -vnn  |grep -A12 VGA
```
...and the link generated from:
```
pastebinit /var/log/dmesg
```

---

### Post by mykrob on 2013-06-06
Yes, I'm running the update command each time I edit grub. I will try your most recent suggestion(s) and post back shortly.
Thanks

---

### Post by mykrob on 2013-06-06
```
myk@myk-Aspire:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.8.0-23-generic.efi.signed root=UUID=3d62caab-2bac-40b9-891e-e79eb8afd3cb ro quiet splash acpi_osi= vt.handoff=7

```

```
myk@myk-Aspire:~$ sudo lspci -vnn |grep -A12 VGA
[sudo] password for myk: 
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device [1025:072d]
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 3000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Capabilities: [a4] PCI Advanced Features
	Kernel driver in use: i915

00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04) (prog-if 30 [XHCI])

```


[http://paste.ubuntu.com/5738997/](http://paste.ubuntu.com/5738997/)


thanks for all your assistance thus far.

---

### Post by Toz on 2013-06-06
Can you try a few other options? After each option, please post back:
1. The kernel boot line:
```
cat /proc/cmdline
```
2. Your backlight interfaces:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```
3. Your dmesg file:
```
pastebinit /var/log/dmesg
```
4. Whether the brightness function keys/brightness slider works.

The options to try are (some you've already tried, but please try again):
- GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"!Windows 2012\""                   
- GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force acpi_backlight=vendor"
- GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"    

I'd like to have a closer look at the dmesg files and the backlight interfaces.

---

### Post by mykrob on 2013-06-06
Will do, but may be a bit later tonight. Gotta finish up work, then band practice. Long day.

Thanks

---

### Post by mykrob on 2013-06-06
> **Toz said:**
> Can you try a few other options? After each option, please post back:
1. The kernel boot line:
```
cat /proc/cmdline
```
2. Your backlight interfaces:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```
3. Your dmesg file:
```
pastebinit /var/log/dmesg
```
4. Whether the brightness function keys/brightness slider works.

The options to try are (some you've already tried, but please try again):
- GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\"!Windows 2012\""                   
- GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force acpi_backlight=vendor"
- GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"    

I'd like to have a closer look at the dmesg files and the backlight interfaces.

First one out of the gate worked :)

The first one I tried was GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"    

That said, here is the other information you requested, maybe it will help you understand why it worked, so you can explain it to me :)

```
myk@myk-Aspire:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.8.0-23-generic.efi.signed root=UUID=3d62caab-2bac-40b9-891e-e79eb8afd3cb ro quiet splash acpi_osi=Linux acpi_backlight=vendor vt.handoff=7

```


```
myk@myk-Aspire:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/intel_backlight
96
976

```


```
myk@myk-Aspire:~$ pastebinit /var/log/dmesg
http://paste.ubuntu.com/5740645/

```

Brightness hotkeys and slider are working. Thank you so much.

---

### Post by Toz on 2013-06-06
Perfect. Glad to hear. 

I noticed, after the fact, that you had mispelled backlight in your post #2. That was the first option and it worked. So you were close.

**acpi_osi=Linux** tells the kernel to inform the bios that it is Linux so that it loads a certain set of acpi tables specific to Linux. **acpi_backlight=vendor** tells acpi to not use built in brightness management (acpi_video0), but to let the bios handle the brightness (in your case, intel_backlight).

---

### Post by mauricio288 on 2013-10-20
Could you both please help me?
I have the same laptop Model (except that my intel generation is the second one), and I have tried the GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor" but no luck. The other diference is that I use Kubuntu, I allready ask on their forums, but no luck :(
Please help

---

### Post by Toz on 2013-10-20
> **mauricio288 said:**
> Could you both please help me?
I have the same laptop Model (except that my intel generation is the second one), and I have tried the GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor" but no luck. The other diference is that I use Kubuntu, I allready ask on their forums, but no luck :(
Please help

Can you confirm some information:
1. The version of kubuntu you are using.

2. Your current kernel boot parameter line:
```
cat /proc/cmdline
```

3. Your video card and driver:
```
lspci -k | grep -A3 VGA
```

4. Your backlight interfaces and their values:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

5. Your dmesg log file:
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

6. Your Xorg log file:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

---

### Post by mauricio288 on 2013-10-20
> **Toz said:**
> Can you confirm some information:
1. The version of kubuntu you are using.

2. Your current kernel boot parameter line:
```
cat /proc/cmdline
```

3. Your video card and driver:
```
lspci -k | grep -A3 VGA
```

4. Your backlight interfaces and their values:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

5. Your dmesg log file:
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

6. Your Xorg log file:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

1. My version is Kubuntu 13.10 (same problem with 13.04) Kernel 3.11.0.12

2. cat /proc/cmdline
```
BOOT_IMAGE=/boot/vmlinuz-3.11.0-12-generic root=UUID=0b573e08-fee6-43ca-af4c-2a98a22f5952 ro quiet splash acpi_osi=Linux acpi_backlight=vendor vt.handoff=7
```

3. lspci -k | grep -A3 VGA
```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
        Subsystem: Acer Incorporated [ALI] Device 072a
        Kernel driver in use: i915
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
```

4. for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```
/sys/class/backlight/intel_backlight
488
488
976
```

5. pastebinit /var/log/dmesg
[http://paste.ubuntu.com/6274034/](http://paste.ubuntu.com/6274034/)

6. pastebinit /var/log/Xorg.0.log
[URL="http://paste.ubuntu.com/6274043/"]http://paste.ubuntu.com/6274043/

[/URL]Tanks for the reply

---

### Post by Toz on 2013-10-21
Can you try this:

1. Create the file /usr/share/X11/xorg.conf.d/20-intel.conf:
```
sudo -i kate /usr/share/X11/xorg.conf.d/20-intel.conf
```
...enter your password when prompted.

2. Copy/paste the following content:
```

Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection

```

3. Save the file.

4. Log out and back in again to see if it works.

If it still doesn't work, try removing the extra kernel parameters you added and trying again.

---

### Post by mauricio288 on 2013-10-21
> **Toz said:**
> Can you try this:

1. Create the file /usr/share/X11/xorg.conf.d/20-intel.conf:
```
sudo -i kate /usr/share/X11/xorg.conf.d/20-intel.conf
```
...enter your password when prompted.

2. Copy/paste the following content:
```

Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection

```

3. Save the file.

4. Log out and back in again to see if it works.

If it still doesn't work, try removing the extra kernel parameters you added and trying again.

It worked :D
it Worked!!!! :D :D :D :D :D :D 

I had to remove the kernel parameters for this to work

Thanks for the help, that thing was driving me crazy, but now it's solved.

I'll post it to my blog to help others, I'm not the only one with this problem

Thanks again :D

---

### Post by Toz on 2013-10-21
Glad to hear. Out of curiosity, did you remove the kernel parameters or are you still using them?

---

### Post by mauricio288 on 2013-10-21
Yep I remove the parameters.

---

