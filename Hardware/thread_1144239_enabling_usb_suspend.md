---
title: "enabling usb suspend"
date: 2009-04-30
forum: Hardware
---

### Post by surfdoc on 2009-04-30
I have a new install of jaunty (kubuntu 64bit version). Its on a ASUS f5 laptop.

I'm trying to maximize battery usage and I recently found powertop. It keeps suggesting that I enable usb suspend as "A USB device is active 100.0% of the time:"


Here's the full output

```
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (14.6%)         1.83 Ghz     0.0%
polling           0.0ms ( 0.0%)         1328 Mhz     0.0%
C1 halt           0.0ms ( 0.0%)          996 Mhz   100.0%
C2                2.0ms ( 3.3%)
C3                1.7ms (82.1%)

Wakeups-from-idle per second : 492.3    interval: 5.0s
Power usage (ACPI estimate): 27.7W (0.2 hours)

Top causes for wakeups:
  23.3% (138.6)       <interrupt> : PS/2 keyboard/mouse/touchpad
  21.8% (129.6)      npviewer.bin : schedule_hrtimeout_range (hrtimer_wakeup)
  16.9% (100.4)       <interrupt> : extra timer interrupt
  12.6% ( 74.8)      <kernel IPI> : Rescheduling interrupts
  10.1% ( 60.0)       <interrupt> : fglrx[0]@PCI:1:0:0
   3.4% ( 20.2)            ggl-qt : schedule_hrtimeout_range (hrtimer_wakeup)
   3.1% ( 18.6)       <interrupt> : ath
   3.0% ( 18.0)           firefox : futex_wait (hrtimer_wakeup)
   1.2% (  7.4)             prism : futex_wait (hrtimer_wakeup)
   1.0% (  6.0)              Xorg : schedule_hrtimeout_range (hrtimer_wakeup)
   0.7% (  4.0)        cairo-dock : schedule_hrtimeout_range (hrtimer_wakeup)
   0.5% (  3.0)          knotify4 : schedule_hrtimeout_range (hrtimer_wakeup)

A USB device is active 100.0% of the time:
USB device  1-8 : USB2.0-CRW (Generic)

 Q - Quit   R - Refresh   U - Enable USB suspend

```

(Is this good or bad power usage?)

It offers to enable it for me, but it doesn't seem to have an effect as the message keeps reappearing.

I was wondering if anyone knew how to either check if usb suspend is enabled or how to manually enable usb suspend.

The only usb devices attached are built in  (camera and card reader). There is also built in bluetooth. I'm not sure if this is usb?
I rarely use any of these.

```

joe@laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0116 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 002: ID 174f:5a31 Syntek
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
```

joe@laptop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```
I don't think the bluetooth is working anyway

```
joe@laptop:~$ cat /var/log/syslog | grep blue             
Apr 29 12:05:28 laptop bluetoothd[2621]: Bluetooth daemon   
Apr 29 12:05:28 laptop bluetoothd[2621]: Starting SDP server
Apr 29 12:05:28 laptop bluetoothd[2621]: bridge pan0 created
Apr 29 12:05:28 laptop bluetoothd[2621]: Starting experimental netlink support
Apr 29 12:05:28 laptop bluetoothd[2621]: Failed to find Bluetooth netlink family
Apr 29 12:05:28 laptop bluetoothd[2621]: Registered interface org.bluez.Service on path /org/bluez/2621/any
Apr 29 12:14:36 laptop bluetoothd[2621]: bridge pan0 removed                                               
Apr 29 12:14:36 laptop bluetoothd[2621]: Stopping SDP server                                               
Apr 29 12:14:36 laptop bluetoothd[2621]: Exit                      
```

---

### Post by sdennie on 2009-04-30
27.7W is very high for most laptops (it of course depends on the laptop though).  It's probably due to the fact that you have flash running in your browser.

As for the powertop message, powertop is not always correct.  Usually if it keeps giving you the same option, it's either mistaken or the device doesn't support what it tries to do to it.  Regardless, check:

```

cat /sys/bus/usb/drivers/usb/1-8/power/autosuspend

```

If that is set to 0 or higher, it's set to suspend.

---

### Post by surfdoc on 2009-04-30
Thanks for that. The command returns 0 - so I take it that powertop is wrong.

With nothing running I get 24.5W. What would be a good value? Any other tips for saving more power?

Regards

---

### Post by sdennie on 2009-04-30
It depends on a lot on the hardware in the laptop.  I've written a guide with links, implementation for a specific laptop and tricks here: [http://ubuntuforums.org/showthread.php?t=847773](http://ubuntuforums.org/showthread.php?t=847773)

---

### Post by surfdoc on 2009-05-06
Thanks for the info! I played around with the settings in your scripts, but couldn't see any appreciable difference under powertop (and to be honest it was a little scary). I think that perhaps I might just have a thirsty laptop (it's not expensive so I'm not surprised). I might compare kubuntu with vista when I can next be bothered to boot up vista - I suppose that will tell me if kubuntu has the power settings set up reasonably?

Cheers!

---

