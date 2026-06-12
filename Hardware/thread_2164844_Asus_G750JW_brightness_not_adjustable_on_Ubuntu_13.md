---
title: "Asus G750JW brightness not adjustable on Ubuntu 13.04"
date: 2013-08-02
forum: Hardware
---

### Post by y0002 on 2013-08-02
First I tried to install 12.04LTS, succeded, but had some hard time getting the network to work. Finally decided to give a try to 13.04, and network run from first attempt (for wireless I had to install this driver: [http://people.canonical.com/~ypwong/drivers/broadcom/hybrid-v35_64-nodebug-pcoem-6_30_223_95.tar.gz](http://people.canonical.com/~ypwong/drivers/broadcom/hybrid-v35_64-nodebug-pcoem-6_30_223_95.tar.gz)). Also, right button from touchpad does not work, but I did not try to solve it as I use a mouse.

I would like to be able to adjust brightness too, as now it runs at max and is a little hard to the eyes.
When I press Fn+F5(F6), the value from /sys/class/backlight/acpi_video0/brightness is changed accordingly in the range 0..100, but with no effect on display brightness.
I'm using the nvidia driver.

Did someone solve this issue?
Thanks

---

### Post by Toz on 2013-08-02
Hello and welcome to the forums.

A little more information would help. Open a terminal window, type in the following commands and post back the results.

1. Your current kernel command line:
```
cat /proc/cmdline
```

2. Your video card and driver:
```
lspci -k | grep -A3 VGA
```

3. Your backlight interfaces (in case there are more than one):
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

If you are not using any kernel parameters, you might want to consider trying the following:
**- acpi_osi=\"!Windows 2012\"**
**- acpi_osi=Linux acpi_backlight=vendor**
Have a look at the "Kernel Boot Parameters" link in my signature for information on how to set kernel parameters.

---

### Post by y0002 on 2013-08-08
Hi Toz,
Thanks for your answer. Here is the output:

```
>cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.8.0-26-generic root=UUID=b15368c9-c44a-4d0e-abdb-9bb1eb1eb687 ro quiet splash vt.handoff=7
```

```
> lspci -k | grep -A3 VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GK106M [GeForce GTX 765M] (rev a1)
    Subsystem: ASUSTeK Computer Inc. Device 119d
    Kernel driver in use: nvidia
01:00.1 Audio device: NVIDIA Corporation Device 0e0b (rev a1)
```

```
> for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
6
100
/sys/class/backlight/acpi_video1
6
100
```

---

### Post by Toz on 2013-08-08
Frist off, can you try the **acpi_backlight=vendor** kernel parameter? To do this:

1. Edit the grub config file:
```
gksu gedit /etc/default/grub
```
...enter your password when prompted.

2. Change the line that reads:
> GRUB_CMDLINE_LINUX=""
...to read:
```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```

3. Save the file.

4. Commit the changes to grub:
```
sudo update-grub
```

5. When #4 completes, reboot your computer.

If, on reboot, the brightness still doesn't work, can you post back again:
```
cat /proc/cmdline
```
...and```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

I'm hoping this kernel parameter will return only one backlight interface and in turn enable the function keys to work against the correct backlight interface.

---

### Post by y0002 on 2013-08-09
Already tried adding "**acpi_osi=Linux acpi_backlight=vendor"** in GRUB_CMDLINE_LINUX_DEFAULT="quiet splash", as you suggested in your first post, with no result (the only result was that FnF5(F6) was not changing the brightness slider any more). Did not try **acpi_osi=\"!Windows 2012\".**
I will test also changing GRUB_CMDLINE_LINUX="acpi_backlight=vendor" and come back with some feedback.
Thank you

---

### Post by y0002 on 2013-08-09
Here is the result of commands after reboot:
```
> cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.8.0-26-generic root=UUID=b15368c9-c44a-4d0e-abdb-9bb1eb1eb687 ro acpi_backlight=vendor quiet splash vt.handoff=7
```

```
> for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/asus-nb-wmi
12
100
```
FnF5(F6) do not change the brightness slider any more. Tried to adjust it with the slider in SystemSettings, Brightness, but with no effect on actual brightness (but the brightness file adjusts value according to slider).

---

### Post by Toz on 2013-08-09
Can you also add:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```
...to the "Device" section of your /etc/X11/xorg.conf file? You'll need to log out and back in again to test.
When logged back in, if brightness still isn't working can you try:
```
echo 50 | sudo tee /sys/class/backlight/asus-nb-wmi/brightness
echo 75 | sudo tee /sys/class/backlight/asus-nb-wmi/brightness
```
...to see if manually manpulating the brightness file will change the actual brightness.

And if that still doesn't work, can you then try **acpi_osi="!Windows 2012"**? The relevant lines in /etc/default/grub should look like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet rw"
GRUB_CMDLINE_LINUX="acpi_osi=\!Windows 2012\""
```
...and after reboot post back again:
```
cat /proc/cmdline
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

---

### Post by y0002 on 2013-08-21
1. Was already there.
2. No change to actual brightness
3. I get the following error when trying to add those 2 lines (copy/paste):
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-27-generic
Found initrd image: /boot/initrd.img-3.8.0-27-generic
Found linux image: /boot/vmlinuz-3.8.0-26-generic
Found initrd image: /boot/initrd.img-3.8.0-26-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
Adding boot menu entry for EFI firmware configuration
error: out of memory.
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 289
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.done
```
4. NA


Ok, missing a quote. Managed to get it changed.
No change on brightness, though. Only the slider is adjusted directly from keyboard.

Here is the output:
```
>cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.8.0-27-generic root=UUID=b15368c9-c44a-4d0e-abdb-9bb1eb1eb687 ro "acpi_osi=!Windows 2012" quiet rw
> for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
4
10

```
Maybe is worth mentioning that I am using also another monitor, plugged inside the VGA slot of the laptop. The standalone monitor has a feature of autoadapting its brightness depending on ambient light strength.

---

### Post by Toz on 2013-08-21
> **y0002 said:**
> Maybe is worth mentioning that I am using also another monitor, plugged inside the VGA slot of the laptop. The standalone monitor has a feature of autoadapting its brightness depending on ambient light strength.
We should try to get brightness working on the laptop without the external monitor first, then add the monitor. 

I like the "acpi_osi=!Windows 2012" parameter because it leaves you with only one backlight interface - the acpi-managed backlight. With this parameter active:
1. Is "Option "RegistryDwords" "EnableBrightnessControl=1"" added to your xorg.conf file? Can you post back the file?
2. Does xbacklight work (you may have to install it if its not installed)?

Also, if anything relevant from these commands, can you post back?
```
cat /var/log/dmesg | grep -i backlight
cat /var/log/Xorg.0.log | grep -i backlight
```

---

### Post by y0002 on 2013-09-03
xbacklight was not installed. After I installed it, I managed to alter the brightness using it, but not using keyboard or brightness slider from System settings. So this is already an achievement, because I can lower brightness.
```
> cat /var/log/dmesg | grep -i backlight
[   11.458659] asus_wmi: Backlight controlled by ACPI video driver
```

The other command does not return anything. Also, maybe it is relevant: in modprobe.d/blacklist, there is an entry:
```
# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi
```

xorg.conf contents:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 325.08  (buildmeister@swio-display-x64-rhel04-12)  Wed Jun 26 18:41:44 PDT 2013

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option "registryDwords" "EnableBrightnessControl=1"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Toz on 2013-09-03
> Option "registryDwords" "EnableBrightnessControl=1"
Not sure if its relevant, but can you try capitalizing the "r" in registry:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```
...in case its case-sensitive. Save the file, log out and back in again to test.

---

### Post by y0002 on 2013-09-05
It seems to be case sensitive, but the correct one is registryDwords. After I change it ro "R", the brightness slider does not appear any more in System Settings. Anyway, xbacklight still works.

---

### Post by y0002 on 2013-10-03
Hi again,
While I did not manage to solve the issue, I found some errors when running dmesg. Here is a part of the output, maybe it is relevant for someone familiar with the correct output:
```
[    8.409558] lp: driver loaded but no devices found
[    8.806574] wmi: Mapper loaded
[    8.808054] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \GPIS 1 (20121018/utaddress-251)
[    8.808060] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \PMIO 2 (20121018/utaddress-251)
[    8.808063] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.808066] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    8.808068] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GP01 2 (20121018/utaddress-251)
[    8.808070] ACPI Warning: 0x0000000000001c30-0x0000000000001c3f SystemIO conflicts with Region \GPRL 3 (20121018/utaddress-251)
[    8.808073] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.808074] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPIO 1 (20121018/utaddress-251)
[    8.808077] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GP01 2 (20121018/utaddress-251)
[    8.808080] ACPI Warning: 0x0000000000001c00-0x0000000000001c2f SystemIO conflicts with Region \GPRL 3 (20121018/utaddress-251)
[    8.808082] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    8.808083] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    8.866518] ACPI Error: Current brightness invalid (20121018/video-384)
[    8.885100] mei 0000:00:16.0: setting latency timer to 64
[    8.885149] mei 0000:00:16.0: irq 44 for MSI/MSI-X
[    8.906530] acpi device:61: registered as cooling_device8
[    8.906553] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[    8.906588] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:5b/LNXVIDEO:00/input/input5
[    8.918871] microcode: CPU0 sig=0x306c3, pf=0x20, revision=0x8
[    8.980468] microcode: CPU1 sig=0x306c3, pf=0x20, revision=0x8
[    8.981377] microcode: CPU2 sig=0x306c3, pf=0x20, revision=0x8
[    8.982307] microcode: CPU3 sig=0x306c3, pf=0x20, revision=0x8
[    8.983157] microcode: CPU4 sig=0x306c3, pf=0x20, revision=0x8
[    8.983956] microcode: CPU5 sig=0x306c3, pf=0x20, revision=0x8
[    8.984721] microcode: CPU6 sig=0x306c3, pf=0x20, revision=0x8
[    8.985434] microcode: CPU7 sig=0x306c3, pf=0x20, revision=0x8
[    8.986099] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    8.998512] asus_wmi: ASUS WMI generic driver loaded
[    9.040134] asus_wmi: Initialization: 0x1asus_wmi: BIOS WMI version: 7.9
[    9.040173] asus_wmi: SFUN value: 0x4a0877<6>[    9.040651] input: Asus WMI hotkeys as /devices/platform/asus-nb-wmi/input/input6
[    9.077416] Qualcomm Atheros(R) AR816x/AR817x PCI-E Ethernet Network Driver
[    9.092420] asus_wmi: Backlight controlled by ACPI video driver
```

In /etc/default/grub I have now:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet rw"
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""
```

---

### Post by Toz on 2013-10-03
You might want to have a look at [nvidiabl]("https://github.com/guillaumezin/nvidiabl"). Unforunately, your system doesn't seem to be directly supported yet (see [https://github.com/guillaumezin/nvidiabl/blob/master/nvidiabl-laptops.h]("https://github.com/guillaumezin/nvidiabl/blob/master/nvidiabl-laptops.h")), so you may need to make some adjustments to the module parameters (see the "Driver Debug" section on that page) or source code. [This post]("http://rog.asus.com/forum/showthread.php?35105-Linux-compatibility&p=307439&viewfull=1#post307439"), for a similar system, indicates the same. You may wish to post in that thread and ask for the source code changes s/he used.

Ultimately, you should create a bug report against the **linux** package so that this can be fixed properly in the kernel.

---

