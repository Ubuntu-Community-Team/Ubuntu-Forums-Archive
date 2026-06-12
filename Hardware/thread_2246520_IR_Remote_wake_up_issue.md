---
title: "IR Remote wake up issue"
date: 2014-10-01
forum: Hardware
---

### Post by raimis_d on 2014-10-01
Recently I've decided to replace Windows with Linux on my HTPC. 

[list]
[*]I installed Ubuntu 14.04 and configured remote
[*]All remote functions are working. Suspend and resume with remote is working. Resume with wireless keyboard also works
[*]I turned PC off and unplugged power cable
[*]Unplugged and plugged back ir receiver
[*]Turned PC on
[*]All remote functions are working. Suspend with remote and resume with keyboard is working, but resume with remote doesn't work anymore
[*]I did clean install of Ubuntu 14.04 and configured remote
[*]All remote functions are working. Suspend with remote and resume with keyboard work is working, but resume wtih remote still doesn't work
[*]Several time reinstalled linux - tried ubuntu 14.04 and XBMCbuntu
[*]Resume with remote still doesn't work
[*]So I installed Windows and then installed Ubuntu 14.04 again and configured remote
[*]Resume with remote starts working again
[*]But if I unplug ir receiver, resume with remote stops working and I need to install windows and then linux again
[/list]

I believe it's might related to BIOS settings, but can't figure out what settings I need to change.

My hardware is:
[list]
[*]MB: Gigabyte GA-H77N-WIFI
[*]CPU: Intel Core i3-3225
[*]IR Receiver: Lenovo branded, produced by SMK
[*]Remote: One For All URC7960
[*]OS: tried with Ubuntu14.04 and XBMCbuntu 13.0
[*]Tried with Lirc and ir-keytable
[/list]

Anyone has any idea how would be possible to resolve this issue?

---

### Post by tgalati4 on 2014-10-01
Install *acpitool* and post the output of:

```
sudo apt-get install acpitool
acpitool -w
```

You need to figure out which USB port the IR receiver is connected to:

```
lsusb -vvv
```

Then make sure that port has power ("enabled") during S3 sleep.  No power to the receiver, then no wakey.

And yes, there may be a BIOS setting to achieve this:  "Allow USB devices to Wake".

---

### Post by raimis_d on 2014-10-01
```
xbmc@htpc-pc:~$ acpitool -w
   Device       S-state   Status   Sysfs node
  ---------------------------------------
  1. P0P1         S4    *disabled
  2. USB1         S3    *disabled
  3. USB2         S3    *disabled
  4. USB3         S3    *disabled
  5. USB4         S3    *disabled
  6. USB5         S3    *disabled
  7. USB6         S3    *disabled
  8. USB7         S3    *disabled
  9. RP01         S4    *disabled  pci:0000:00:1c.0
  10. RP02        S4    *disabled
  11. PXSX        S4    *disabled
  12. RP03        S4    *disabled
  13. PXSX        S4    *disabled
  14. RP04        S4    *disabled
  15. PXSX        S4    *disabled
  16. RP05        S4    *disabled  pci:0000:00:1c.4
  17. PXSX        S4    *enabled   pci:0000:02:00.0
  18. RP06        S4    *disabled  pci:0000:00:1c.5
  19. PXSX        S4    *enabled   pci:0000:03:00.0
  20. RP07        S4    *disabled  pci:0000:00:1c.6
  21. PXSX        S4    *disabled  pci:0000:04:00.0
  22. RP08        S4    *disabled
  23. PXSX        S4    *disabled
  24. PEG0        S4    *disabled
  25. PEGP        S4    *disabled
  26. PEG1        S4    *disabled
  27. PEG2        S4    *disabled
  28. PEG3        S4    *disabled
  29. GLAN        S4    *disabled
  30. EHC1        S4    *enabled   pci:0000:00:1d.0
  31. EHC2        S4    *enabled   pci:0000:00:1a.0
  32. XHC         S4    *enabled   pci:0000:00:14.0
  33. HDEF        S4    *disabled  pci:0000:00:1b.0
  34. PWRB        S3    *enabled
```

I know that my ir receiver is connected to 1-1.1 port and it has power during sleep
```
xbmc@htpc-pc:~$ cat /sys/bus/usb/devices/1-1.1/power/wakeup
enabled
```

I enabled power for ir receiver and wireless keyboard with such script
```
echo "SUBSYSTEM==\"usb\", ATTRS{idVendor}==\"046d\", ATTRS{idProduct}==\"c52b\" RUN+=\"/bin/sh -c 'echo enabled > /sys\$env{DEVPATH}/../power/wakeup'\"" > /etc/udev/rules.d/90-keyboardup.rules
echo "SUBSYSTEM==\"usb\", ATTRS{idVendor}==\"0609\", ATTRS{idProduct}==\"0357\" RUN+=\"/bin/sh -c 'echo enabled > /sys\$env{DEVPATH}/../power/wakeup'\"" > /etc/udev/rules.d/90-mcewakeup.rules

```

And if wakeup with USB is disabled in the BIOS then it's very strange why I'm still able to wakeup PC with keyboard but not with remote.

---

### Post by tgalati4 on 2014-10-01
Your wakeup script simply overrides the BIOS setting.  If you didn't run your script to put "enabled" in the appropriate device files, then you would not be able to wake with the keyboard.

What is the output of:

```
lsusb
```

All 7 of your USB ports are "disabled" which means they do not have power when in S3 (sleep-RAM-has-power) state.  So regardless of your device settings, at least one USB port needs power.  Preferably the USB port that the IR receiver is connected to.  You can charge your cell phone on the other ports by activating power for those other ports.

I don't know what USB device is "1-1.1", but on my system that is USB1:

> tgalati4@Mint14-Extensa /sys/bus/usb/devices $ ls -la
total 0
drwxr-xr-x 2 root root 0 Sep 25 16:27 .
drwxr-xr-x 4 root root 0 Sep 18 06:53 ..
lrwxrwxrwx 1 root root 0 Sep 25 16:27 1-0:1.0 -> ../../../devices/pci0000:00/0000:00:1a.7/usb1/1-0:1.0
lrwxrwxrwx 1 root root 0 Sep 25 16:27 1-1 -> ../../../devices/pci0000:00/0000:00:1a.7/usb1/1-1
lrwxrwxrwx 1 root root 0 Sep 25 16:27 1-1:1.0 -> ../../../devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.0
lrwxrwxrwx 1 root root 0 Sep 25 16:27 **1-1:1.1 -> ../../../devices/pci0000:00/0000:00:1a.7/usb1/1-1/1-1:1.1**
lrwxrwxrwx 1 root root 0 Sep 25 16:27 2-0:1.0 -> ../../../devices/pci0000:00/0000:00:1d.7/usb2/2-0:1.0
lrwxrwxrwx 1 root root 0 Sep 25 16:27 3-0:1.0 -> ../../../devices/pci0000:00/0000:00:1a.0/usb3/3-0:1.0
lrwxrwxrwx 1 root root 0 Sep 25 16:27 4-0:1.0 -> ../../../devices/pci0000:00/0000:00:1a.1/usb4/4-0:1.0
lrwxrwxrwx 1 root root 0 Sep 25 16:27 5-0:1.0 -> ../../../devices/pci0000:00/0000:00:1d.0/usb5/5-0:1.0
lrwxrwxrwx 1 root root 0 Sep 25 16:27 6-0:1.0 -> ../../../devices/pci0000:00/0000:00:1d.1/usb6/6-0:1.0
lrwxrwxrwx 1 root root 0 Sep 25 16:27 7-0:1.0 -> ../../../devices/pci0000:00/0000:00:1d.2/usb7/7-0:1.0
lrwxrwxrwx 1 root root 0 Sep 25 16:27 **usb1 -> ../../../devices/pci0000:00/0000:00:1a.7/usb1**
lrwxrwxrwx 1 root root 0 Sep 25 16:27 usb2 -> ../../../devices/pci0000:00/0000:00:1d.7/usb2
lrwxrwxrwx 1 root root 0 Sep 25 16:27 usb3 -> ../../../devices/pci0000:00/0000:00:1a.0/usb3
lrwxrwxrwx 1 root root 0 Sep 25 16:27 usb4 -> ../../../devices/pci0000:00/0000:00:1a.1/usb4
lrwxrwxrwx 1 root root 0 Sep 25 16:27 usb5 -> ../../../devices/pci0000:00/0000:00:1d.0/usb5
lrwxrwxrwx 1 root root 0 Sep 25 16:27 usb6 -> ../../../devices/pci0000:00/0000:00:1d.1/usb6
lrwxrwxrwx 1 root root 0 Sep 25 16:27 usb7 -> ../../../devices/pci0000:00/0000:00:1d.2/usb7


According to *acpitool*, USB1 has no power during S3 sleep.  Try turning it on with -W switch.

---

