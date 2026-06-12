---
title: "Computer starts with brightness set to zero"
date: 2013-10-12
forum: Hardware
---

### Post by tylerburtonca on 2013-10-12
I have a brand new Lenovo Y410P and it seems to have a problem with Ubuntu 13.04. When the computer starts up the brightness is set to the absolute minimum. Weirdly the live CD worked fine. I also tried installing KDE and when KDE begins to actually boot, i.e. the 4 icon loading screen after you log in, the brightness seems to correct itself. For reference Unity does not do this. I also thought this might be an issue with ldm but I also tried kdm and it didn't act any differently. 

Can anyone think of a way to make this work? Perhaps GRUB settings that I could apply? If needed I can post hardware printouts, just let me know which commands to type.

Thanks in advance!

---

### Post by Toz on 2013-10-12
Can you adjust the brightness manually to get it to the value that you want after the boot cycle or are you stuck with a blank screen?

Can you open a terminal window, type in the following commands, and post back the results:
1. Command line parameters:
```
cat /proc/cmdline
```

2. Video cards and drivers:
```
lspci -k | grep -A3 VGA
```

3. Backlight interfaces and values:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

---

### Post by mkmanifesto on 2013-10-12
Try this and reboot

```
sudo gedit /etc/rc.local
```

add this at the end of the file:

```
echo 75 > /sys/class/backlight/acpi_video0/brightness

exit 0
```

I had to do this for my ubuntu 12.04 install on my laptop. "75" is the brightness out of 100 for when my laptop boots.

---

### Post by tylerburtonca on 2013-10-12
> **Toz said:**
> Can you adjust the brightness manually to get it to the value that you want after the boot cycle or are you stuck with a blank screen?

Can you open a terminal window, type in the following commands, and post back the results:
1. Command line parameters:
```
cat /proc/cmdline
```

2. Video cards and drivers:
```
lspci -k | grep -A3 VGA
```

3. Backlight interfaces and values:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```

```
cat /proc/cmdline
```
BOOT_IMAGE=/boot/vmlinuz-3.8.0-31-generic root=UUID=869ec6af-a601-4a3d-bf75-81f3b13fd1ed ro quiet splash vt.handoff=7

```
lspci -k | grep -A3 VGA
```
00:02.0 VGA compatible controller: Intel Corporation Haswell Integrated Graphics Controller (rev 06)
    Subsystem: Lenovo Device 3801
    Kernel driver in use: i915
00:03.0 Audio device: Intel Corporation Haswell HD Audio Controller (rev 06)
--
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 750M] (rev a1)
    Subsystem: Lenovo Device 3801
08:00.0 Ethernet controller: Qualcomm Atheros QCA8171 Gigabit Ethernet (rev 10)
    Subsystem: Lenovo Device 3800

```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness;  cat $i/actual_brightness; cat $i/max_brightness; done
```
/sys/class/backlight/acpi_video0
100
100
100
/sys/class/backlight/intel_backlight
5273
5273
5273

---

### Post by tylerburtonca on 2013-10-12
> **mkmanifesto said:**
> Try this and reboot

```
sudo gedit /etc/rc.local
```

add this at the end of the file:

```
echo 75 > /sys/class/backlight/acpi_video0/brightness

exit 0
```

I had to do this for my ubuntu 12.04 install on my laptop. "75" is the brightness out of 100 for when my laptop boots.

I tried this as a work around before and it sometimes works but not always.

---

### Post by tylerburtonca on 2013-10-12
Sorry I should also point out that I can manually increase/decrease the brightness as well... if that makes a difference.

---

### Post by Toz on 2013-10-12
You have 2 active, possibly conflicting, backlight interfaces. Lets try removing one by using the **acpi_backlight=vendor** kernel parameter (this will tell acpi to release backlight control to the built-in device management facilities). Here is how:

1. With root privledges, open the grub config file for editing:
```
gksudo gedit /etc/default/grub
```

2. Change the line:
> GRUB_CMDLINE_LINUX=""
...to read:
```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```

3. Save the file.

4. Commit the change:
```
sudo update-grub
```

5. Reboot and test.

If it still doesn't work, re-run those commands again and post back your new results.

---

### Post by tylerburtonca on 2013-10-12
> **Toz said:**
> You have 2 active, possibly conflicting, backlight interfaces. Lets try removing one by using the **acpi_backlight=vendor** kernel parameter (this will tell acpi to release backlight control to the built-in device management facilities). Here is how:

1. With root privledges, open the grub config file for editing:
```
gksudo gedit /etc/default/grub
```

2. Change the line:

...to read:
```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```

3. Save the file.

4. Commit the change:
```
sudo update-grub
```

5. Reboot and test.

If it still doesn't work, re-run those commands again and post back your new results.

AWESOME! That worked perfectly! Thank you so much!

---

### Post by mkmanifesto on 2013-10-12
> **Toz said:**
> You have 2 active, possibly conflicting, backlight interfaces. Lets try removing one by using the **acpi_backlight=vendor** kernel parameter (this will tell acpi to release backlight control to the built-in device management facilities). Here is how:

1. With root privledges, open the grub config file for editing:
```
gksudo gedit /etc/default/grub
```

2. Change the line:

...to read:
```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```

3. Save the file.

4. Commit the change:
```
sudo update-grub
```

5. Reboot and test.

If it still doesn't work, re-run those commands again and post back your new results.

I just applied this suggestion to my laptop as well. Thank you for the tip.

---

### Post by alivin70 on 2013-12-08
It worked also on my HP notebook. Thank you!

Here is my  lspci:

00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
00:03.0 Audio device: Intel Corporation Device 0a0c (rev 09)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 1 (rev e4)
00:1c.1 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 2 (rev e4)
00:1c.2 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1c.4 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 5 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
08:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 08)
0a:00.0 3D controller: NVIDIA Corporation GK208M [GeForce GT 740M] (rev a1)

---

### Post by whitedp on 2013-12-18
Thanks Toz worked for me as well. :D

---

