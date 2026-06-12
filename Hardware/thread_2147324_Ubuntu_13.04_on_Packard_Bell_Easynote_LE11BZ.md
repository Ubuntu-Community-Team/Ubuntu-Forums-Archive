---
title: "Ubuntu 13.04 on Packard Bell Easynote LE11BZ"
date: 2013-05-21
forum: Hardware
---

### Post by narcisgarcia on 2013-05-21
Raring Ringtail

After disabling UEFI in BIOS, I've booted Ubuntu GNU/Linux 13.04 Live-CD (tried with Gnome and LXDE editions). All works fine except the keyboard and touchpad.
I can only move pointer with an external mouse (USB), and write with an external keyboard (USB).

What can I look for, to find the problem?

---

### Post by narcisgarcia on 2013-05-22
I've tested now with these other Live-CD versions:
[LIST]
[*]Lubuntu 11.10: Both onboard keyboard and touchpad work.
[*]Lubuntu 12.04: Both onboard keyboard and touchpad work.
[*]Lubuntu 12.10: Don't work (only work external devices through USB)
[*]Lubuntu 13.04: Don't work (only work external devices through USB)
[*]
[/LIST]
For all the cases, integrated keyboard works in GRUB stage

Following [this page]("http://www.upubuntu.com/2012/10/fix-laptops-touchpadtrackpad-not.html"), I've checked input devices:
```
$ xinput -list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Power Button                            	id=10	[slave  keyboard (3)]
    &#8627; HD WebCam                               	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                        	id=13	[slave  keyboard (3)]

$ xinput --list-props 12
Device 'AT Translated Set 2 keyboard':
	Device Enabled (137):	1
	Coordinate Transformation Matrix (139):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Product ID (254):	1, 1
	Device Node (255):	"/dev/input/event5"

```
(doesn't appear any touchpad, and integrated keyboard seems to be activated)
```
$ gsettings get org.gnome.settings-daemon.peripherals.touchpad touchpad-enabled
true
```

---

### Post by narcisgarcia on 2013-05-22
Surprisingly, all the devices work perfectly if I boot with an additional USB pendrive plugged (need to be FAT formatted). Tried booting Ubuntu-gnome 13.04 Live-USB:

```
$ xinput -list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                	id=13	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Power Button                            	id=10	[slave  keyboard (3)]
    &#8627; HD WebCam                               	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                        	id=14	[slave  keyboard (3)]

```
```
$ dmesg | grep -ie "i8042"
[   11.462336] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   11.464955] i8042: Detected active multiplexing controller, rev 1.1
[   11.467068] serio: i8042 KBD port at 0x60,0x64 irq 1
[   11.467084] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   11.467144] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   11.467185] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   11.467226] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   11.484090] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[   41.032440] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio2/input/input7
```
```
$ sudo lshw -short
H/W path       Device      Class       Description
==================================================
                           system      ENLE11BZ (ENLE11BZ_073D_2.10)
/0                         bus         EG70_BZ
/0/0                       memory      128KiB BIOS
/0/4                       processor   AMD E1-1200 APU with Radeon(tm) HD Graphics
/0/4/8                     memory      64KiB L1 cache
/0/4/9                     memory      512KiB L2 cache
/0/13                      memory      4GiB System Memory
/0/13/0                    memory      4GiB SODIMM DDR3 Synchronous 667 MHz (1.5 ns)
/0/13/1                    memory      [empty]
/0/100                     bridge      Family 14h Processor Root Complex
/0/100/1                   display     Wrestler [Radeon HD 7310]
/0/100/1.1                 multimedia  Wrestler HDMI Audio [Radeon HD 6250/6310]
/0/100/10                  bus         FCH USB XHCI Controller
/0/100/11                  storage     FCH SATA Controller [AHCI mode]
/0/100/12                  bus         FCH USB OHCI Controller
/0/100/12.2                bus         FCH USB EHCI Controller
/0/100/13                  bus         FCH USB OHCI Controller
/0/100/13.2                bus         FCH USB EHCI Controller
/0/100/14                  bus         FCH SMBus Controller
/0/100/14.2                multimedia  FCH Azalia Controller
/0/100/14.3                bridge      FCH LPC Bridge
/0/100/14.4                bridge      FCH PCI Bridge
/0/100/14.5                bus         FCH USB OHCI Controller
/0/100/15                  bridge      Hudson PCI to PCI bridge (PCIE port 0)
/0/100/15.1                bridge      Hudson PCI to PCI bridge (PCIE port 1)
/0/100/15.1/0  wlan0       network     Centrino Wireless-N 105
/0/100/15.2                bridge      Hudson PCI to PCI bridge (PCIE port 2)
/0/100/15.2/0  eth0        network     AR8151 v2.0 Gigabit Ethernet
/0/100/15.3                bridge      Hudson PCI to PCI bridge (PCIE port 3)
/0/101                     bridge      Family 12h/14h Processor Function 0
/0/102                     bridge      Family 12h/14h Processor Function 1
/0/103                     bridge      Family 12h/14h Processor Function 2
/0/104                     bridge      Family 12h/14h Processor Function 3
/0/105                     bridge      Family 12h/14h Processor Function 4
/0/106                     bridge      Family 12h/14h Processor Function 6
/0/107                     bridge      Family 12h/14h Processor Function 5
/0/108                     bridge      Family 12h/14h Processor Function 7
/0/1           scsi1       storage     
/0/1/0.0.0     /dev/sda    disk        500GB WDC WD5000LPVT-2
/0/1/0.0.0/1   /dev/sda1   volume      399MiB Windows NTFS volume
/0/1/0.0.0/2   /dev/sda2   volume      299MiB Windows FAT volume
/0/1/0.0.0/3   /dev/sda3   volume      127MiB reserved partition
/0/1/0.0.0/4   /dev/sda4   volume      441GiB Windows NTFS volume
/0/1/0.0.0/5   /dev/sda5   volume      23GiB Windows NTFS volume
/0/2           scsi2       storage     
/0/2/0.0.0     /dev/cdrom  disk        DVD-RW DVRTD11RS
/0/3           scsi0       storage     
/0/3/0.0.0     /dev/sdb    disk        32GB SCSI Disk
/0/3/0.0.0/1   /dev/sdb1   volume      29GiB Windows FAT volume
/0/5           scsi3       storage     
/0/5/0.0.0     /dev/sdc    disk        32GB SCSI Disk
/0/5/0.0.0/1   /dev/sdc1   volume      28GiB Linux filesystem partition
/0/5/0.0.0/2   /dev/sdc2   volume      1019MiB Linux filesystem partition
```

---

### Post by narcisgarcia on 2013-05-22
Here I've fount the solution, thanks to Javier Aragones (javara2305):
[http://www.taringa.net/posts/linux/5497150/Solucion-a-Touchpad-en-netbooks-Commodore.html](http://www.taringa.net/posts/linux/5497150/Solucion-a-Touchpad-en-netbooks-Commodore.html)

Simply adding this parameter to kernel on boot entry (GRUB):
```
i8042.nomux
```

* I don't know how to mark this thread as [SOLVED]

---

