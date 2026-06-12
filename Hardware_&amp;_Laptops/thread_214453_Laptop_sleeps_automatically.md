---
title: "Laptop sleeps automatically"
date: 2006-07-12
forum: Hardware &amp; Laptops
---

### Post by vitorsouza on 2006-07-12
Hi,

Just installed Kubuntu 6.06 on my new Toshiba Satellite M45-S269. Everything is working fine so far (haven't tested everything yet), but there is an annoyance and maybe someone can point me some directions.

The laptop is sleeping automatically, out of the blue, while I'm working! It takes 5s to sleep, then I press the power button and it takes another 5s to wake up, so it's no biggie, except when it's running on batteries, because instead of sleeping, it hibernates (takes a lot more than 10s).

I searched the forum but found nothing like this. It hasn't happened when I'm using Windows (although I don't use it too often) and it didn't happen when I ran Ubuntu's memtest86 (it ran all morning).

Any directions, please? Thanks in advance.

Vitor Souza

---

### Post by vitorsouza on 2006-07-18
Hi there,

No clue yet of what's going on. Can anyone help, please?

Below I pasted some messages that might be related to the event.

Thanks in advance,

Vitor Souza

/var/log/acpid:
```
[Tue Jul 18 16:12:46 2006] received event "button/power PWRF 00000080 00000001"
[Tue Jul 18 16:12:46 2006] notifying client 4461[108:108]
[Tue Jul 18 16:12:46 2006] completed event "button/power PWRF 00000080 00000001"
[Tue Jul 18 16:12:46 2006] received event "battery BAT1 00000081 00000001"
[Tue Jul 18 16:12:46 2006] notifying client 4461[108:108]
[Tue Jul 18 16:12:46 2006] completed event "battery BAT1 00000081 00000001"

```

/var/log/kern.log:
```
Jul 18 16:12:34 seattle kernel: [17187382.240000] eth1: no IPv6 routers present
Jul 18 16:12:35 seattle kernel: [17187383.936000] eth0: no IPv6 routers present
Jul 18 16:12:37 seattle kernel: [17187385.856000]     ACPI-0240: *** Error: Cannot release Mutex [MUT1], not acquired
Jul 18 16:12:38 seattle kernel: [17187386.232000] sky2 eth0: disabling interface
Jul 18 16:12:38 seattle kernel: [17187386.648000] ACPI: PCI interrupt for device 0000:01:00.0 disabled
Jul 18 16:12:38 seattle kernel: [17187386.704000] ACPI: PCI interrupt for device 0000:05:04.0 disabled
Jul 18 16:12:38 seattle kernel: [17187386.708000] ieee80211_crypt: unregistered algorithm 'NULL'
Jul 18 16:12:38 seattle kernel: [17187386.712000] ieee80211_1_1_13_crypt: unregistered algorithm 'NULL'
Jul 18 16:12:46 seattle kernel: [17187389.728000] Freezing cpus ...
Jul 18 16:12:46 seattle kernel: [17187389.728000] Stopping tasks: =================================================================================================================
==|
Jul 18 16:12:46 seattle kernel: [17187389.772000] ata2: suspend device
Jul 18 16:12:46 seattle kernel: [17187389.772000] ata1: suspend device
Jul 18 16:12:46 seattle kernel: [17187390.224000] ACPI: PCI interrupt for device 0000:05:06.0 disabled
Jul 18 16:12:46 seattle kernel: [17187390.224000] ata_piix 0000:00:1f.2: suspend PCI device
Jul 18 16:12:46 seattle kernel: [17187390.224000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
Jul 18 16:12:46 seattle kernel: [17187390.240000] ACPI: PCI interrupt for device 0000:00:1e.2 disabled
Jul 18 16:12:46 seattle kernel: [17187390.240000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
Jul 18 16:12:46 seattle kernel: [17187390.256000] ACPI: PCI interrupt for device 0000:00:1d.3 disabled
Jul 18 16:12:46 seattle kernel: [17187390.256000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
Jul 18 16:12:46 seattle kernel: [17187390.256000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
Jul 18 16:12:46 seattle kernel: [17187390.256000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
Jul 18 16:12:46 seattle kernel: [17187390.256000] cpufreq: suspend failed to assert current frequency is what timing core thinks it is.
Jul 18 16:12:46 seattle kernel: [17187390.256000] Back to C!
Jul 18 16:12:46 seattle kernel: [17187390.256000] cpufreq: resume failed to assert current frequency is what timing core thinks it is.
Jul 18 16:12:46 seattle kernel: [17187393.256000] **** SET: Misaligned resource pointer: c1d27b42 Type 07 Len 0
Jul 18 16:12:46 seattle last message repeated 6 times
Jul 18 16:12:46 seattle kernel: [17187393.276000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul 18 16:12:46 seattle kernel: [17187393.276000] ACPI: PCI Interrupt 0000:00:1c.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
Jul 18 16:12:46 seattle kernel: [17187393.276000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Jul 18 16:12:46 seattle kernel: [17187393.276000] ACPI: PCI Interrupt 0000:00:1c.1[B] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul 18 16:12:46 seattle kernel: [17187393.276000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Jul 18 16:12:46 seattle kernel: [17187393.276000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
Jul 18 16:12:46 seattle kernel: [17187393.276000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Jul 18 16:12:46 seattle kernel: [17187393.276000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Jul 18 16:12:46 seattle kernel: [17187393.276000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Jul 18 16:12:46 seattle kernel: [17187393.276000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Jul 18 16:12:46 seattle kernel: [17187393.276000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Jul 18 16:12:46 seattle kernel: [17187393.276000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul 18 16:12:46 seattle kernel: [17187393.276000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Jul 18 16:12:46 seattle kernel: [17187393.292000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
Jul 18 16:12:46 seattle kernel: [17187393.292000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
Jul 18 16:12:46 seattle kernel: [17187393.292000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Jul 18 16:12:46 seattle kernel: [17187393.292000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Jul 18 16:12:46 seattle kernel: [17187393.292000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
Jul 18 16:12:46 seattle kernel: [17187393.292000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
Jul 18 16:12:46 seattle kernel: [17187393.544000] ata_piix 0000:00:1f.2: resume PCI device
Jul 18 16:12:46 seattle kernel: [17187393.560000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
Jul 18 16:12:46 seattle kernel: [17187393.560000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Jul 18 16:12:46 seattle kernel: [17187393.560000] ACPI: PCI Interrupt 0000:05:06.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Jul 18 16:12:46 seattle kernel: [17187393.560000] PCI: Enabling device 0000:05:06.2 (0000 -> 0002)
Jul 18 16:12:46 seattle kernel: [17187393.560000] ACPI: PCI Interrupt 0000:05:06.2[C] -> Link [LNKG] -> GSI 6 (level, low) -> IRQ 6
Jul 18 16:12:46 seattle kernel: [17187393.560000] ACPI: PCI Interrupt 0000:05:06.4[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
Jul 18 16:12:46 seattle kernel: [17187394.264000] ata1: resume device
Jul 18 16:12:46 seattle kernel: [17187394.420000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
Jul 18 16:12:46 seattle kernel: [17187394.420000] pata_get_dev_handle: dev_handle: 0xdffe0f20, parent_handle: 0xdffe79c0
Jul 18 16:12:46 seattle kernel: [17187394.420000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff62a00, *handle=0xdffe0f20
Jul 18 16:12:46 seattle kernel: [17187394.432000] ata1: dev 0 configured for UDMA/100
Jul 18 16:12:46 seattle kernel: [17187394.432000] ata2: resume device
Jul 18 16:12:46 seattle kernel: [17187394.588000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
Jul 18 16:12:46 seattle kernel: [17187394.588000] pata_get_dev_handle: dev_handle: 0xdffe0f20, parent_handle: 0xdffe79c0
Jul 18 16:12:46 seattle kernel: [17187394.588000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff62a00, *handle=0xdffe0f20
Jul 18 16:12:46 seattle kernel: [17187394.588000] ata2: dev 0 configured for UDMA/33
Jul 18 16:12:46 seattle kernel: [17187394.812000] Restarting tasks...<6>usb 1-1: USB disconnect, address 7
Jul 18 16:12:46 seattle kernel: [17187394.876000]  done
Jul 18 16:12:46 seattle kernel: [17187394.876000] Thawing cpus ...
Jul 18 16:12:46 seattle kernel: [17187395.068000] usb 1-1: new low speed USB device using uhci_hcd and address 8
Jul 18 16:12:46 seattle kernel: [17187395.188000]     ACPI-0240: *** Error: Cannot release Mutex [MUT1], not acquired
Jul 18 16:12:47 seattle kernel: [17187395.260000] input: Logitech USB Receiver as /class/input/input7
Jul 18 16:12:47 seattle kernel: [17187395.260000] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-1
Jul 18 16:12:48 seattle kernel: [17187396.304000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul 18 16:12:48 seattle kernel: [17187396.304000] PCI: Setting latency timer of device 0000:01:00.0 to 64
Jul 18 16:12:48 seattle kernel: [17187396.304000] sky2 v1.4 addr 0xcc000000 irq 11 Yukon-FE (0xb7) rev 1
Jul 18 16:12:48 seattle kernel: [17187396.304000] sky2 eth0: addr 00:a0:d1:25:ea:31
Jul 18 16:12:48 seattle kernel: [17187396.368000] sky2 eth0: enabling interface
Jul 18 16:12:48 seattle kernel: [17187396.376000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul 18 16:12:48 seattle kernel: [17187396.404000] sky2 0000:01:00.0: No interrupt was generated using MSI, switching to INTx mode. Please report this failure to the PCI maintainer
 and include system chipset information.
Jul 18 16:12:48 seattle kernel: [17187396.412000] ieee80211_1_1_13_crypt: registered algorithm 'NULL'
Jul 18 16:12:48 seattle kernel: [17187396.412000] ieee80211_1_1_13: 802.11 data/management/control stack, 1.1.13
Jul 18 16:12:48 seattle kernel: [17187396.412000] ieee80211_1_1_13: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Jul 18 16:12:48 seattle kernel: [17187396.412000] ieee80211_crypt: registered algorithm 'NULL'
Jul 18 16:12:48 seattle kernel: [17187396.416000] ieee80211: 802.11 data/management/control stack, git-1.1.7
Jul 18 16:12:48 seattle kernel: [17187396.416000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Jul 18 16:12:48 seattle kernel: [17187396.416000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
Jul 18 16:12:48 seattle kernel: [17187396.416000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
Jul 18 16:12:48 seattle kernel: [17187396.416000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
Jul 18 16:12:48 seattle kernel: [17187396.416000] ACPI: PCI Interrupt 0000:05:04.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Jul 18 16:12:48 seattle kernel: [17187396.416000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
Jul 18 16:12:48 seattle kernel: [17187396.548000] ipw2200: Radio Frequency Kill Switch is On:
Jul 18 16:12:48 seattle kernel: [17187396.548000] Kill switch must be turned off for wireless networking to work.
Jul 18 16:12:48 seattle kernel: [17187396.548000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
Jul 18 16:12:48 seattle kernel: [17187396.616000] eth1: NETDEV_TX_BUSY returned; driver should report queue full via ieee_device->is_queue_full.
Jul 18 16:12:51 seattle kernel: [17187397.936000] ACPI: Power Button (FF) [PWRF]
Jul 18 16:12:51 seattle kernel: [17187397.936000] ACPI: Lid Switch [LID0]
Jul 18 16:12:51 seattle kernel: [17187397.936000] ACPI: Power Button (CM) [PWRB]
Jul 18 16:12:51 seattle kernel: [17187397.976000] ACPI: Fan [FAN1] (off)
Jul 18 16:12:51 seattle kernel: [17187398.016000] ACPI: Thermal Zone [TZCR] (49 C)
Jul 18 16:12:51 seattle kernel: [17187398.024000] ACPI: Thermal Zone [TZCL] (43 C)
Jul 18 16:12:51 seattle kernel: [17187398.080000] ACPI: AC Adapter [AC] (on-line)
Jul 18 16:12:51 seattle kernel: [17187398.104000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control none
Jul 18 16:12:51 seattle kernel: [17187398.136000] ACPI: Battery Slot [BAT1] (battery present)
Jul 18 16:12:52 seattle kernel: [17187398.304000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jul 18 16:12:59 seattle kernel: [17187406.616000] eth1: no IPv6 routers present
Jul 18 16:13:02 seattle kernel: [17187409.140000] eth0: no IPv6 routers present
Jul 18 16:13:31 seattle kernel: [17187437.812000]     ACPI-0258: *** Error: Thread 147D cannot release Mutex [MUT1] acquired by thread 1468
Jul 18 16:13:31 seattle kernel: [17187437.812000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.RDEC] (Node dffdf700), AE_AML_NOT_OWNER
Jul 18 16:13:31 seattle kernel: [17187437.812000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.LID0._LID] (Node dffe7a40), AE_AML_NOT_OWNER
Jul 18 16:14:31 seattle kernel: [17187497.780000]     ACPI-0258: *** Error: Thread 147D cannot release Mutex [MUT1] acquired by thread 1468
Jul 18 16:14:31 seattle kernel: [17187497.780000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.RDEC] (Node dffdf700), AE_AML_NOT_OWNER
Jul 18 16:14:31 seattle kernel: [17187497.780000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.LID0._LID] (Node dffe7a40), AE_AML_NOT_OWNER

```

/var/log/debug:
```
Jul 18 16:12:34 seattle kernel: [17187382.240000] eth1: no IPv6 routers present
Jul 18 16:12:35 seattle kernel: [17187383.936000] eth0: no IPv6 routers present
Jul 18 16:12:38 seattle kernel: [17187386.708000] ieee80211_crypt: unregistered algorithm 'NULL'
Jul 18 16:12:38 seattle kernel: [17187386.712000] ieee80211_1_1_13_crypt: unregistered algorithm 'NULL'
Jul 18 16:12:46 seattle kernel: [17187389.772000] ata2: suspend device
Jul 18 16:12:46 seattle kernel: [17187389.772000] ata1: suspend device
Jul 18 16:12:46 seattle kernel: [17187390.224000] ata_piix 0000:00:1f.2: suspend PCI device
Jul 18 16:12:46 seattle kernel: [17187390.256000] Back to C!
Jul 18 16:12:46 seattle kernel: [17187393.276000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
Jul 18 16:12:46 seattle kernel: [17187393.276000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
Jul 18 16:12:46 seattle kernel: [17187393.276000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
Jul 18 16:12:46 seattle kernel: [17187393.276000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
Jul 18 16:12:46 seattle kernel: [17187393.276000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
Jul 18 16:12:46 seattle kernel: [17187393.276000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
Jul 18 16:12:46 seattle kernel: [17187393.292000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
Jul 18 16:12:46 seattle kernel: [17187393.292000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
Jul 18 16:12:46 seattle kernel: [17187393.292000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
Jul 18 16:12:46 seattle kernel: [17187393.544000] ata_piix 0000:00:1f.2: resume PCI device
Jul 18 16:12:46 seattle kernel: [17187393.560000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Jul 18 16:12:46 seattle kernel: [17187394.264000] ata1: resume device
Jul 18 16:12:46 seattle kernel: [17187394.420000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
Jul 18 16:12:46 seattle kernel: [17187394.420000] pata_get_dev_handle: dev_handle: 0xdffe0f20, parent_handle: 0xdffe79c0
Jul 18 16:12:46 seattle kernel: [17187394.420000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff62a00, *handle=0xdffe0f20
Jul 18 16:12:46 seattle kernel: [17187394.432000] ata2: resume device
Jul 18 16:12:46 seattle kernel: [17187394.588000] pata_get_dev_handle: ENTER: dev->bus_id='0000:00:1f.2'
Jul 18 16:12:46 seattle kernel: [17187394.588000] pata_get_dev_handle: dev_handle: 0xdffe0f20, parent_handle: 0xdffe79c0
Jul 18 16:12:46 seattle kernel: [17187394.588000] pata_get_dev_handle: for dev=0x1f.2, addr=0x1f0002, parent=0xdff62a00, *handle=0xdffe0f20
Jul 18 16:12:48 seattle kernel: [17187396.304000] PCI: Setting latency timer of device 0000:01:00.0 to 64
Jul 18 16:12:48 seattle kernel: [17187396.412000] ieee80211_1_1_13_crypt: registered algorithm 'NULL'
Jul 18 16:12:48 seattle kernel: [17187396.412000] ieee80211_crypt: registered algorithm 'NULL'
Jul 18 16:12:59 seattle kernel: [17187406.616000] eth1: no IPv6 routers present
Jul 18 16:13:02 seattle kernel: [17187409.140000] eth0: no IPv6 routers present

```

---

### Post by vitorsouza on 2006-08-01
Hello again, I'm enjoying this monologue... It's almos like this is my personal blog! :)

Anyways, I discovered that Kubuntu was sleeping because it thought that I was closing the lid of the laptop. I configured KLaptop to log off instead of sleeping when the laptop lid is closed, and it started doing that out of nowhere, instead of sleeping.

So, I turned the feature off (do nothing on lid close) and circumvented the problem. It's still not fixed, because it would be nice to have the lid close feature enabled to make the laptop sleep when I close it. But I'm satisfied as it is. Better than using Windows, I guess.

Still, if anybody has any thoughts on this, I'd still like to hear them.

Vitor Souza

---

### Post by kronepils on 2006-08-10
Hello!

It would be interesting to know if it's KDE, or the system, that thinks your lid is closed.
Try looking in your /var/log/acpid when it happens. It would state that it recieved a event like LID CLOSED or something like that.
Or if you have ubuntu-desktop or xbuntu-desktop installed, try running gnome or xfce for a while and see if it happens. You would have to instruct gnome-power-manager to do something on lid closing.

Good luck!

---

