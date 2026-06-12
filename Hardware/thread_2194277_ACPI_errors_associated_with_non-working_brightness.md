---
title: "ACPI errors associated with non-working brightness keys on new HP Spectre 13 x2"
date: 2013-12-17
forum: Hardware
---

### Post by pgratz on 2013-12-17
This isn't a huge problem but I thought I'd make a note of it.  I've got most of my "special" keys working with the "hp_wmi" module on this laptop ([See my comments about getting this laptop running linux here]("http://cesg.tamu.edu/faculty/paul-gratz/personal/linux-on-the-hp-spectre-13-x2/")), the exception being the brightness keys which do not seem to be visible to X (xev does not notice their key presses).  I recently noticed that when I press those keys I see the following messages in dmesg:

```

[ 3324.617378] ACPI Error: [^^^PEG0.PEGP.DD02] Namespace lookup failure, AE_NOT_FOUND (20130725/psargs-359)
[ 3324.617386] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._Q1D] (Node ffff8801592fc730), AE_NOT_FOUND (20130725/psparse-536)
[ 3325.604163] ACPI Error: [^^^PEG0.PEGP.DD02] Namespace lookup failure, AE_NOT_FOUND (20130725/psargs-359)
[ 3325.604171] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._Q1C] (Node ffff8801592fc708), AE_NOT_FOUND (20130725/psparse-536)



```

the two "nodes" correspond to one press of each of the two keys.  Can anyone point me in the right direction to getting these two keys working?
Thanks!
Paul

---

### Post by Toz on 2013-12-17
Are you able to change the brightness on your device?

Try using the:
```
acpi_osi= acpi_backlight=vendor
```
..._OR_
```
acpi_osi=\"!Windows 2012\"
```
...kernel parameters to see if they force the bios to load a different set of tables that allow them to be properly recognized by the kernel. 

More info on kernel boot parameters can be found by following the "Kernel Boot Parameters" link in my signature.

---

### Post by pgratz on 2013-12-17
Hi Toz,
After a good deal of trails and tribulations ([documented here]("http://cesg.tamu.edu/faculty/paul-gratz/personal/linux-on-the-hp-spectre-13-x2/")) I was able to get brightness working somewhat correctly using xbacklight which I mapped to a hotkey (cntrl-f2 and cntrl-f3).
In a nutshell, I added this to the linux kernel options in grub:
```
i915.invert_brightness=1 acpi_osi='' 
```

To get it working.  The remaining problem being that the ubuntu system/KDE seems to have the brightness reversed still.  So in my battery manager if I set brightness to 10% it is very bright while 90% is quite dark.
Pau

---

### Post by Toz on 2013-12-17
If you're still willing to investigate, can you give the **acpi_osi=\"!Windows 2012\"** kernel parameter a try? It might solve these issues. The relevant lines in your /etc/default/grub file should look like:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet rw"
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""
```
(note that the escaping and quoting looks weird but needs to be done like that)

---

### Post by pgratz on 2013-12-17
Giving it a shot...

---

### Post by pgratz on 2013-12-17
Ah, great that fixed part of the problem.  With the acpi_osi command you gave, now I don't have the inverted brightness problem so now KDE properly dims the screen and brightens the screen. 

This did not appear to do anything for the brightness keys themselves but I can live with mapping CTRL-F2/F3 for brightness up and down.
Thanks!
Paul

---

### Post by Toz on 2013-12-17
> This did not appear to do anything for the brightness keys themselves but I can live with mapping CTRL-F2/F3 for brightness up and down.
Do you want to dig a little deeper to see if we can fix this as well? If so, can you post back the results to the following commands:
```
cat /proc/cmdline
lspci -k | grep -iA2 VGA
for i in /sys/class/backlight/*; do echo $i;cat $i/brightness;cat $i/max_brightness;done
```

And also, run this command:
```
xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'
```
...press the Function key combination for brightness up followed by the key combination for brightness down and post back any codes that appear in the terminal window.

---

### Post by pgratz on 2013-12-17
Sure, here is the output of those commands:
```
pgratz@pgratz-HP-Spectre-13-x2:~$ cat /proc/cmdline BOOT_IMAGE=/boot/vmlinuz-3.12.5-031205-generic root=UUID=48580585-f540-425c-8328-f2aa0e70767c ro "acpi_osi=!Windows 2012" quiet splash rw vt.handoff=7
pgratz@pgratz-HP-Spectre-13-x2:~$ lspci -k | grep -iA2 VGA
00:02.0 VGA compatible controller: Intel Corporation Device 0a1e (rev 0b)
        Subsystem: Hewlett-Packard Company Device 2152
        Kernel driver in use: i915
pgratz@pgratz-HP-Spectre-13-x2:~$ for i in /sys/class/backlight/*; do echo $i;cat $i/brightness;cat $i/max_brightness;done
/sys/class/backlight/acpi_video0
86
100
/sys/class/backlight/intel_backlight
657
937



```

On the xev line, I got no output at all (only more lines in the dmesg like I posted before).

Paul

---

### Post by Toz on 2013-12-17
You have 2 backlight interfaces (acpi_video0 & intel_backlight). I would try to get rid of one of them in case the two are confusing the system. There are two ways to do this:

1. Add the **acpi_backlight=vendor** kernel parameter to your parameter list:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet rw"
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\" acpi_backlight=vendor"
```
...this should remove the acpi_video0 interface.

2. Direct X to use the intel_backlight interface by creating the file **/usr/share/X11/xorg.conf.d/20-intel.conf** with the following content:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```
...this will force X to use the intel_backlight interface as the primary one.

Once the interface issue is cleared up, try the function keys again to see if they make a difference.

---

### Post by pgratz on 2013-12-18
Hi Toz,
OK I did the steps above and this seems to have removed the other interface from /sys/ but it did not get those two keys working (to be clear, brightness does work with my configured hotkeys and KDE's powermanager is handling it correctly and can change brightness, just those two keys aren't doing anything but spewing ACPI errors in dmesg).
Paul

---

### Post by Toz on 2013-12-18
Okay, just wanted to see if those kernel parameters would help. I would suggest either looking to see if a bios update is available, or creating a bug report so that it can be fixed in the kernel. To create a bug report:
```
ubuntu-bug linux
```

---

### Post by pgratz on 2013-12-18
OK I'll file the bug on linux (I'm on the latest BIOS).
Thanks!
Paul

---

