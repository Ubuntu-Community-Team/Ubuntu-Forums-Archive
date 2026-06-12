---
title: "[SOLVED] Intel Wireless card stopped getting deteced"
date: 2008-04-05
forum: Hardware &amp; Laptops
---

### Post by sameeer_s on 2008-04-05
Hi

My HP dv9000 laptop used to always detect my wireless card automatically, from install. I never had to install any drivers etc.

Then since one fine day, everytime I boot into Ubuntu, the wireless card is not detected.

dmesg gives following which may be helpful:

[   16.937049] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.962555] NET: Registered protocol family 8
[   16.962557] NET: Registered protocol family 20
[   16.962587] pnp: 00:00: iomem range 0xe0000000-0xefffffff could not be reserved
[   16.962592] pnp: 00:02: iomem range 0xe0000000-0xefffffff could not be reserved
[   16.962595] pnp: 00:02: iomem range 0xfed14000-0xfed17fff could not be reserved
[   16.962597] pnp: 00:02: iomem range 0xfed18000-0xfed18fff could not be reserved
[   16.962599] pnp: 00:02: iomem range 0xfed19000-0xfed19fff could not be reserved
[   16.962604] pnp: 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   16.962609] pnp: 00:07: ioport range 0x6a0-0x6af has been reserved
[   16.962611] pnp: 00:07: ioport range 0x6b0-0x6ff has been reserved
[   16.965789] Time: tsc clocksource has been installed.
[   16.981790] Switched to high resolution mode on CPU 0
[   16.992805] PCI: Failed to allocate mem resource #6:20000@d0000000 for 0000:01:00.0
....

Everything else in dmesg looks okay, except for the webcam error I used to get earlier.

The card I have is the Intel 3945ABG. I don't know what I did to make it stop working, but the laptop had been up for a few weeks without rebooting, hence there might have been at least one kernel update.

As far as my guess goes, there appears to be some PCI resource conflict, but I have no clue what to do about it, if indeed that is the problem.

Please help!

---

### Post by riven0 on 2008-04-06
Since you think it's kernel related, have you tried booting into one of the older kernel version in your grub? That usually fixes my problems when something breaks.

---

### Post by sameeer_s on 2008-04-06
I booted into an older version of the kernel, but that didn't work. Incidentally, booting into the older version did not even detect the nvidia driver.

Is there a way to have a more verbose dmesg to see exactly what's going on, or to sort of look at where the wireless adapter is connected so that we can see the messages only relevant to that.

I'm being a bit vague, just thinking aloud. Any help will be appreciated.

Thanks

---

### Post by sameeer_s on 2008-04-06
In case it helps, here's lspci output:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

and lshw output, just the relevant section, i.e. the PCI ports:

        *-pci:1
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: 82801G (ICH7 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver

Hope that helps!
Thanks a lot!

---

### Post by riven0 on 2008-04-07
Unless I'm missing something, I doesn't look like your card is even detected. :confused:

In either case, try running this command and see what it brings back: **iwconfig**


Then try to load some of the modules one by one:

**modprobe mac80211**

**modprobe iwl3945**
[B]
modprobe iwl4965[/B]

Also, this may sound stupid, but make sure your wireless switch is on and your wireless card is not disabled in the BIOS.

If it still doesn't work, it may be that you need to re-install the drivers at: [http://intellinuxwireless.org/]("http://intellinuxwireless.org/")

Post back if it doesn't work...

---

### Post by sameeer_s on 2008-04-07
It turns out it was stupid.

The wireless card had been disabled in the BIOS.

Really sorry for wasting your time.

Thanks a lot.

---

### Post by riven0 on 2008-04-07
Good to know it was a simple problem. :KS

---

