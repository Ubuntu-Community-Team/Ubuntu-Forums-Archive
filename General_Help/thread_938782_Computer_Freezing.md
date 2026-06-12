---
title: "Computer Freezing"
date: 2008-10-05
forum: General Help
---

### Post by jesuisbenjamin on 2008-10-05
Hello there,

I am using Hardy on a laptop. 
This one often freezes. This means nothing responds, including keyboard and mouse. The Caps and Num Lock flash.
It apparently happens randomly, but i am not sure. It can happen at startup. 
This issue is really causing a lot of trouble, it happens at least 4 times a day. 
Is there anyone to help troubleshooting this problem?

Thanks a lot.
Benjamin

---

### Post by concord on 2008-10-05
> **jesuisbenjamin said:**
> 
This one often freezes. This means nothing responds, including keyboard and mouse. The Caps and Num Lock flash.


This sounds like a kernel panic.  They are usually caused by hardware problems.  Boot the live CD and choose the memory test option.  Test the system memory first.

Good luck!

---

### Post by iponeverything on 2008-10-05
Also post the output "lspci" we might be able to spot hardware with a known problematic driver.

---

### Post by jesuisbenjamin on 2008-10-05
First of all thank you for your reply.

> Test the system memory first.
There was no alternative as to what had to be tested, it just did the test.

> Also post the output "lspci"
When i put an end to the test there was nothing indicating an output or any lspci, nor was there any lspci mentioned in the options. Should i have found this in Memtest?

The test went through 3 pass and no error was found. However since your description differs from what i have seen, i am wondering whether i did the right thing.
What i did was: booting with install CD of Hardy. Then chose Memory Test option and it did the test. It seemed to keep on doing the same test for ever and ever so after the 3rd pass i chose Reboot. And here i am.

What i could notice (maybe it is relevant) is that there was information about the microprocessor, about L1 cache and L2 cache and memory, but in front of chipset there was no info.

What to do next?
What is lspci?

Thanks

---

### Post by iponeverything on 2008-10-05
Boot into ubuntu open a terminal and run lspci -- post the output 

:)

---

### Post by jesuisbenjamin on 2008-10-05
Ha that was simple: 

> 00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:03.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:04.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:0a.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
00:0a.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
00:0b.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M


What's the verdict?

:)

---

### Post by iponeverything on 2008-10-05
I don't see anything there that sticks out.

Next it locks up, make a note of system time. After you get back into the system, 

cd /var/log

use the command "less" to scroll through the logs and find the time of crash. See if anything shows up a around that time. Some the logs you might look at are: messages, syslog, daemon.log, kernel.log

---

### Post by jesuisbenjamin on 2008-10-06
OK thanks again.

Computer froze two times in a row, time noted 19:26 and again 19:29, and i checked the logs as you said.

Messages.log
> Oct  6 19:18:00 mati kernel: [   40.319427] Bluetooth: Core ver 2.11
Oct  6 19:18:00 mati kernel: [   40.321048] NET: Registered protocol family 31
Oct  6 19:18:00 mati kernel: [   40.321059] Bluetooth: HCI device and connection manager initialized
Oct  6 19:18:00 mati kernel: [   40.321066] Bluetooth: HCI socket layer initialized
Oct  6 19:18:00 mati kernel: [   40.352645] Bluetooth: L2CAP ver 2.9
Oct  6 19:18:00 mati kernel: [   40.352657] Bluetooth: L2CAP socket layer initialized
Oct  6 19:18:00 mati kernel: [   40.446029] Bluetooth: RFCOMM socket layer initialized
Oct  6 19:18:00 mati kernel: [   40.446537] Bluetooth: RFCOMM TTY layer initialized
Oct  6 19:18:00 mati kernel: [   40.446544] Bluetooth: RFCOMM ver 1.8
Oct  6 19:18:00 mati dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct  6 19:18:01 mati kernel: [   62.112141] Marking TSC unstable due to: cpufreq changes.
Oct  6 19:18:02 mati kernel: [   42.606975] [drm] Initialized drm 1.1.0 20060810
Oct  6 19:18:03 mati kernel: [   42.672209] ACPI: PCI Interrupt Link [LNK0] enabled at IRQ 11
Oct  6 19:18:03 mati kernel: [   42.672226] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNK0] -> GSI 11 (level, low) -> IRQ 11
Oct  6 19:18:03 mati kernel: [   42.672648] [drm] Initialized radeon 1.28.0 20060524 on minor 0
Oct  6 19:18:03 mati kernel: [   43.065039] NET: Registered protocol family 17
Oct  6 19:18:04 mati kernel: [   65.754286] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Oct  6 19:18:04 mati kernel: [   65.754932] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Oct  6 19:18:04 mati kernel: [   65.755390] agpgart: Putting AGP V2 device at 0000:01:05.0 into 4x mode
Oct  6 19:18:05 mati kernel: [   67.136053] [drm] Setting GART location based on new memory map
Oct  6 19:18:05 mati kernel: [   67.136134] [drm] writeback test succeeded in 1 usecs
Oct  6 19:18:09 mati dhcdbd: dhco_parse_option_settings: bad option setting: old_server_name =  
Oct  6 19:18:09 mati dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct  6 19:18:09 mati dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct  6 19:18:09 mati dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Oct  6 19:18:10 mati kernel: [   72.354472] NET: Registered protocol family 10
Oct  6 19:18:10 mati kernel: [   72.355754] lo: Disabled Privacy Extensions
Oct  6 19:27:49 mati syslogd 1.5.0#1ubuntu1: restart.

> Oct  6 19:27:50 mati kernel: [   33.693600] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2061: AC'97 1 does not respond - RESET
Oct  6 19:27:50 mati kernel: [   34.688512] cs: IO port probe 0x100-0x3af: excluding 0x220-0x22f 0x330-0x337 0x388-0x38f
Oct  6 19:27:50 mati kernel: [   34.690106] cs: IO port probe 0x3e0-0x4ff: clean.
Oct  6 19:27:50 mati kernel: [   34.690742] cs: IO port probe 0x820-0x8ff: clean.
Oct  6 19:27:50 mati kernel: [   34.691338] cs: IO port probe 0xc00-0xcf7: clean.
Oct  6 19:27:50 mati kernel: [   34.692169] cs: IO port probe 0xa00-0xaff: clean.
Oct  6 19:27:50 mati kernel: [   34.702286] cs: IO port probe 0x100-0x3af: excluding 0x220-0x22f 0x330-0x337 0x388-0x38f
Oct  6 19:27:50 mati kernel: [   34.703914] cs: IO port probe 0x3e0-0x4ff: clean.
Oct  6 19:27:50 mati kernel: [   34.704554] cs: IO port probe 0x820-0x8ff: clean.
Oct  6 19:27:50 mati kernel: [   34.705151] cs: IO port probe 0xc00-0xcf7: clean.
Oct  6 19:27:50 mati kernel: [   34.706009] cs: IO port probe 0xa00-0xaff: clean.
Oct  6 19:27:50 mati kernel: [   35.911593] lp0: using parport0 (interrupt-driven).
Oct  6 19:27:50 mati kernel: [   36.050882] Adding 1413680k swap on /dev/hda5.  Priority:-1 extents:1 across:1413680k
Oct  6 19:27:50 mati kernel: [   36.101858] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
Oct  6 19:27:50 mati kernel: [   36.102144] EXT3 FS on hda1, internal journal
Oct  6 19:27:50 mati kernel: [   36.881213] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct  6 19:27:50 mati kernel: [   37.524195] No dock devices found.
Oct  6 19:27:50 mati kernel: [   39.317050] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Oct  6 19:27:50 mati kernel: [   39.317063] apm: overridden by ACPI.
Oct  6 19:27:50 mati kernel: [   39.468787] ppdev: user-space parallel port driver
Oct  6 19:27:51 mati kernel: [   39.676346] audit(1223314071.097:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4822 profile="/usr/sbin/cupsd" namespace="default"
Oct  6 19:27:51 mati dhcdbd: Started up.
Oct  6 19:27:51 mati kernel: [   60.234625] Marking TSC unstable due to: cpufreq changes.
Oct  6 19:27:52 mati kernel: [   40.848208] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Oct  6 19:27:52 mati kernel: [   41.011943] Bluetooth: Core ver 2.11
Oct  6 19:27:52 mati kernel: [   41.013490] NET: Registered protocol family 31
Oct  6 19:27:52 mati kernel: [   41.013503] Bluetooth: HCI device and connection manager initialized
Oct  6 19:27:52 mati kernel: [   41.013511] Bluetooth: HCI socket layer initialized
Oct  6 19:27:52 mati kernel: [   41.046090] Bluetooth: L2CAP ver 2.9
Oct  6 19:27:52 mati kernel: [   41.046101] Bluetooth: L2CAP socket layer initialized
Oct  6 19:27:52 mati kernel: [   41.150085] Bluetooth: RFCOMM socket layer initialized
Oct  6 19:27:52 mati kernel: [   41.150562] Bluetooth: RFCOMM TTY layer initialized
Oct  6 19:27:52 mati kernel: [   41.150570] Bluetooth: RFCOMM ver 1.8
Oct  6 19:27:53 mati dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct  6 19:27:55 mati kernel: [   43.219740] [drm] Initialized drm 1.1.0 20060810
Oct  6 19:27:55 mati kernel: [   43.285221] ACPI: PCI Interrupt Link [LNK0] enabled at IRQ 11
Oct  6 19:27:55 mati kernel: [   43.285240] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNK0] -> GSI 11 (level, low) -> IRQ 11
Oct  6 19:27:55 mati kernel: [   43.285661] [drm] Initialized radeon 1.28.0 20060524 on minor 0
Oct  6 19:27:55 mati kernel: [   43.755475] NET: Registered protocol family 17
Oct  6 19:27:56 mati kernel: [   66.663284] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Oct  6 19:27:56 mati kernel: [   66.663929] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Oct  6 19:27:56 mati kernel: [   66.664394] agpgart: Putting AGP V2 device at 0000:01:05.0 into 4x mode
Oct  6 19:27:58 mati kernel: [   68.045317] [drm] Setting GART location based on new memory map
Oct  6 19:27:58 mati kernel: [   68.045396] [drm] writeback test succeeded in 1 usecs
Oct  6 19:27:58 mati dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct  6 19:27:58 mati dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct  6 19:27:58 mati dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Oct  6 19:27:59 mati kernel: [   69.519395] NET: Registered protocol family 10
Oct  6 19:27:59 mati kernel: [   69.520644] lo: Disabled Privacy Extensions
Oct  6 19:30:13 mati syslogd 1.5.0#1ubuntu1: restart.

As you know the log is huge, so i post the others in another reply.

---

### Post by jesuisbenjamin on 2008-10-06
Now Syslog.log

> Oct  6 19:18:02 mati kernel: [   42.606975] [drm] Initialized drm 1.1.0 20060810
Oct  6 19:18:03 mati kernel: [   42.672209] ACPI: PCI Interrupt Link [LNK0] enabled at IRQ 11
Oct  6 19:18:03 mati kernel: [   42.672226] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNK0] -> GSI 11 (level, low) -> IRQ 11
Oct  6 19:18:03 mati kernel: [   42.672648] [drm] Initialized radeon 1.28.0 20060524 on minor 0
Oct  6 19:18:03 mati NetworkManager: <debug> [1223313483.014598] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_4337_drm_radeon_card0'). 
Oct  6 19:18:03 mati /usr/sbin/cron[5194]: (CRON) INFO (pidfile fd = 3)
Oct  6 19:18:03 mati /usr/sbin/cron[5195]: (CRON) STARTUP (fork ok)
Oct  6 19:18:03 mati /usr/sbin/cron[5195]: (CRON) INFO (Running @reboot jobs)
Oct  6 19:18:03 mati NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Oct  6 19:18:03 mati kernel: [   43.065039] NET: Registered protocol family 17
Oct  6 19:18:04 mati dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Oct  6 19:18:04 mati kernel: [   65.754286] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Oct  6 19:18:04 mati kernel: [   65.754932] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Oct  6 19:18:04 mati kernel: [   65.755390] agpgart: Putting AGP V2 device at 0000:01:05.0 into 4x mode
Oct  6 19:18:05 mati kernel: [   67.136053] [drm] Setting GART location based on new memory map
Oct  6 19:18:05 mati kernel: [   67.136134] [drm] writeback test succeeded in 1 usecs
Oct  6 19:18:09 mati dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Oct  6 19:18:09 mati dhclient: DHCPOFFER of 192.168.1.33 from 192.168.1.254
Oct  6 19:18:09 mati dhclient: DHCPREQUEST of 192.168.1.33 on eth0 to 255.255.255.255 port 67
Oct  6 19:18:09 mati dhclient: DHCPACK of 192.168.1.33 from 192.168.1.254
Oct  6 19:18:09 mati avahi-daemon[4777]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.33.
Oct  6 19:18:09 mati avahi-daemon[4777]: New relevant interface eth0.IPv4 for mDNS.
Oct  6 19:18:09 mati avahi-daemon[4777]: Registering new address record for 192.168.1.33 on eth0.IPv4.
Oct  6 19:18:09 mati dhcdbd: dhco_parse_option_settings: bad option setting: old_server_name =  
Oct  6 19:18:09 mati NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Oct  6 19:18:09 mati NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct  6 19:18:09 mati NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Oct  6 19:18:09 mati dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct  6 19:18:09 mati dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct  6 19:18:09 mati NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct  6 19:18:09 mati NetworkManager: <info>    address 192.168.1.33 
Oct  6 19:18:09 mati NetworkManager: <info>    netmask 255.255.255.0 
Oct  6 19:18:09 mati NetworkManager: <info>    broadcast 192.168.1.255 
Oct  6 19:18:09 mati NetworkManager: <info>    gateway 192.168.1.254 
Oct  6 19:18:09 mati NetworkManager: <info>    nameserver 192.168.1.254 
Oct  6 19:18:09 mati NetworkManager: <info>    nameserver 195.241.77.55 
Oct  6 19:18:09 mati NetworkManager: <info>    nameserver 195.241.77.58 
Oct  6 19:18:09 mati NetworkManager: <info>    hostname 'dhcppc0' 
Oct  6 19:18:09 mati NetworkManager: <info>    domain name 'lokaal' 
Oct  6 19:18:09 mati dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Oct  6 19:18:09 mati NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct  6 19:18:09 mati NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Oct  6 19:18:09 mati NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Oct  6 19:18:09 mati dhclient: bound to 192.168.1.33 -- renewal in 13568 seconds.
Oct  6 19:18:09 mati avahi-daemon[4777]: Withdrawing address record for 192.168.1.33 on eth0.
Oct  6 19:18:09 mati avahi-daemon[4777]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.33.
Oct  6 19:18:09 mati avahi-daemon[4777]: Interface eth0.IPv4 no longer relevant for mDNS.
Oct  6 19:18:09 mati avahi-daemon[4777]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.33.
Oct  6 19:18:09 mati avahi-daemon[4777]: New relevant interface eth0.IPv4 for mDNS.
Oct  6 19:18:09 mati avahi-daemon[4777]: Registering new address record for 192.168.1.33 on eth0.IPv4.
Oct  6 19:18:10 mati NetworkManager: <info>  Clearing nscd hosts cache. 
Oct  6 19:18:10 mati NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct  6 19:18:10 mati NetworkManager: <info>  Activation (eth0) successful, device activated. 
Oct  6 19:18:10 mati NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Oct  6 19:18:10 mati NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Oct  6 19:18:10 mati kernel: [   72.354472] NET: Registered protocol family 10
Oct  6 19:18:10 mati kernel: [   72.355754] lo: Disabled Privacy Extensions
Oct  6 19:18:11 mati ntpdate[5344]: adjust time server 91.189.94.4 offset -0.047069 sec
Oct  6 19:18:12 mati avahi-daemon[4777]: Registering new address record for fe80::230:13ff:feb5:d865 on eth0.*.
Oct  6 19:18:21 mati kernel: [   83.918859] eth0: no IPv6 routers present
Oct  6 19:18:48 mati hcid[5046]: Default passkey agent (:1.22, /org/bluez/passkey) registered
Oct  6 19:18:48 mati hcid[5046]: Default authorization agent (:1.22, /org/bluez/auth) registered
Oct  6 19:18:57 mati NetworkManager: <info>  Updating allowed wireless network lists. 
Oct  6 19:18:57 mati NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Oct  6 19:27:49 mati syslogd 1.5.0#1ubuntu1: restart.

And again:

> ct  6 19:27:50 mati kernel: [   39.317050] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Oct  6 19:27:50 mati kernel: [   39.317063] apm: overridden by ACPI.
Oct  6 19:27:50 mati kernel: [   39.468787] ppdev: user-space parallel port driver
Oct  6 19:27:51 mati kernel: [   39.676346] audit(1223314071.097:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4822 profile="/usr/sbin/cupsd" namespace="default"
Oct  6 19:27:51 mati dhcdbd: Started up.
Oct  6 19:27:51 mati kernel: [   60.234625] Marking TSC unstable due to: cpufreq changes.
Oct  6 19:27:52 mati kernel: [   40.848208] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Oct  6 19:27:52 mati NetworkManager: <info>  eth0: Device is fully-supported using driver '8139too'. 
Oct  6 19:27:52 mati NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct  6 19:27:52 mati NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct  6 19:27:52 mati NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct  6 19:27:52 mati NetworkManager: <info>  Deactivating device eth0. 
Oct  6 19:27:52 mati NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Oct  6 19:27:52 mati NetworkManager: <debug> [1223314072.381200] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_QSI_CD_RW/DVD_ROM_SBW_242'). 
Oct  6 19:27:52 mati NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Oct  6 19:27:52 mati hcid[5052]: Bluetooth HCI daemon
Oct  6 19:27:52 mati kernel: [   41.011943] Bluetooth: Core ver 2.11
Oct  6 19:27:52 mati kernel: [   41.013490] NET: Registered protocol family 31
Oct  6 19:27:52 mati kernel: [   41.013503] Bluetooth: HCI device and connection manager initialized
Oct  6 19:27:52 mati kernel: [   41.013511] Bluetooth: HCI socket layer initialized
Oct  6 19:27:52 mati hcid[5052]: Starting SDP server
Oct  6 19:27:52 mati kernel: [   41.046090] Bluetooth: L2CAP ver 2.9
Oct  6 19:27:52 mati kernel: [   41.046101] Bluetooth: L2CAP socket layer initialized
Oct  6 19:27:52 mati hcid[5052]: Created local server at unix:abstract=/var/run/dbus-6t1pGb3alx,guid=86e3127d12a0af1cfc8b163948ea4a98
Oct  6 19:27:52 mati audio[5065]: Bluetooth Audio daemon
Oct  6 19:27:52 mati input[5071]: Bluetooth Input daemon
Oct  6 19:27:52 mati audio[5065]: Unix socket created: 5
Oct  6 19:27:52 mati audio[5065]: audio.conf: Key file does not have key 'Enable'
Oct  6 19:27:52 mati audio[5065]: audio.conf: Key file does not have key 'Disable'
Oct  6 19:27:52 mati input[5071]: Registered input manager path:/org/bluez/input
Oct  6 19:27:52 mati kernel: [   41.150085] Bluetooth: RFCOMM socket layer initialized
Oct  6 19:27:52 mati kernel: [   41.150562] Bluetooth: RFCOMM TTY layer initialized
Oct  6 19:27:52 mati kernel: [   41.150570] Bluetooth: RFCOMM ver 1.8
Oct  6 19:27:52 mati audio[5065]: add_service_record: got record id 0x10000
Oct  6 19:27:52 mati audio[5065]: audio.conf: Key file does not have key 'Disable'
Oct  6 19:27:52 mati audio[5065]: audio.conf: Key file does not have group 'A2DP'
Oct  6 19:27:52 mati last message repeated 3 times
Oct  6 19:27:52 mati audio[5065]: SEP 0x806d6d0 registered: type:0 codec:0 seid:1
Oct  6 19:27:52 mati audio[5065]: add_service_record: got record id 0x10001
Oct  6 19:27:52 mati audio[5065]: add_service_record: got record id 0x10002
Oct  6 19:27:52 mati audio[5065]: add_service_record: got record id 0x10003
Oct  6 19:27:52 mati audio[5065]: Registered manager path:/org/bluez/audio
Oct  6 19:27:53 mati dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Oct  6 19:27:53 mati NetworkManager: <info>  Will activate connection 'eth0'. 
Oct  6 19:27:53 mati NetworkManager: <info>  Device eth0 activation scheduled... 
Oct  6 19:27:53 mati NetworkManager: <debug> [1223314073.394647] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Oct  6 19:27:53 mati NetworkManager: <info>  Activation (eth0) started... 
Oct  6 19:27:53 mati NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct  6 19:27:53 mati NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Oct  6 19:27:53 mati NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Oct  6 19:27:53 mati NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Oct  6 19:27:53 mati NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Oct  6 19:27:53 mati NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Oct  6 19:27:53 mati NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct  6 19:27:53 mati NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Oct  6 19:27:53 mati NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Oct  6 19:27:54 mati NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Oct  6 19:27:54 mati NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Oct  6 19:27:54 mati NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Oct  6 19:27:55 mati kernel: [   43.219740] [drm] Initialized drm 1.1.0 20060810
Oct  6 19:27:55 mati kernel: [   43.285221] ACPI: PCI Interrupt Link [LNK0] enabled at IRQ 11
Oct  6 19:27:55 mati kernel: [   43.285240] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNK0] -> GSI 11 (level, low) -> IRQ 11
Oct  6 19:27:55 mati kernel: [   43.285661] [drm] Initialized radeon 1.28.0 20060524 on minor 0
Oct  6 19:27:55 mati NetworkManager: <debug> [1223314075.293116] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_4337_drm_radeon_card0'). 
Oct  6 19:27:55 mati /usr/sbin/cron[5200]: (CRON) INFO (pidfile fd = 3)
Oct  6 19:27:55 mati /usr/sbin/cron[5201]: (CRON) STARTUP (fork ok)
Oct  6 19:27:55 mati /usr/sbin/cron[5201]: (CRON) INFO (Running @reboot jobs)
Oct  6 19:27:55 mati NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Oct  6 19:27:55 mati kernel: [   43.755475] NET: Registered protocol family 17
Oct  6 19:27:56 mati kernel: [   66.663284] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Oct  6 19:27:56 mati kernel: [   66.663929] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Oct  6 19:27:56 mati kernel: [   66.664394] agpgart: Putting AGP V2 device at 0000:01:05.0 into 4x mode
Oct  6 19:27:58 mati dhclient: DHCPREQUEST of 192.168.1.33 on eth0 to 255.255.255.255 port 67
Oct  6 19:27:58 mati dhclient: DHCPACK of 192.168.1.33 from 192.168.1.254
Oct  6 19:27:58 mati kernel: [   68.045317] [drm] Setting GART location based on new memory map
Oct  6 19:27:58 mati kernel: [   68.045396] [drm] writeback test succeeded in 1 usecs
Oct  6 19:27:58 mati avahi-daemon[4783]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.33.
Oct  6 19:27:58 mati avahi-daemon[4783]: New relevant interface eth0.IPv4 for mDNS.
Oct  6 19:27:58 mati avahi-daemon[4783]: Registering new address record for 192.168.1.33 on eth0.IPv4.
Oct  6 19:27:58 mati NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth0 
Oct  6 19:27:58 mati NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct  6 19:27:58 mati NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Oct  6 19:27:58 mati dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Oct  6 19:27:58 mati dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Oct  6 19:27:58 mati NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct  6 19:27:58 mati NetworkManager: <info>    address 192.168.1.33 
Oct  6 19:27:58 mati NetworkManager: <info>    netmask 255.255.255.0 
Oct  6 19:27:58 mati NetworkManager: <info>    broadcast 192.168.1.255 
Oct  6 19:27:58 mati NetworkManager: <info>    gateway 192.168.1.254 
Oct  6 19:27:58 mati NetworkManager: <info>    nameserver 192.168.1.254 
Oct  6 19:27:58 mati NetworkManager: <info>    nameserver 195.241.77.55 
Oct  6 19:27:58 mati NetworkManager: <info>    nameserver 195.241.77.58 
Oct  6 19:27:58 mati NetworkManager: <info>    hostname 'dhcppc0' 
Oct  6 19:27:58 mati NetworkManager: <info>    domain name 'lokaal' 
Oct  6 19:27:58 mati dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Oct  6 19:27:58 mati NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct  6 19:27:58 mati NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Oct  6 19:27:58 mati NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Oct  6 19:27:58 mati dhclient: bound to 192.168.1.33 -- renewal in 11339 seconds.
Oct  6 19:27:58 mati avahi-daemon[4783]: Withdrawing address record for 192.168.1.33 on eth0.
Oct  6 19:27:58 mati avahi-daemon[4783]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.33.
Oct  6 19:27:58 mati avahi-daemon[4783]: Interface eth0.IPv4 no longer relevant for mDNS.
Oct  6 19:27:58 mati avahi-daemon[4783]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.33.
Oct  6 19:27:58 mati avahi-daemon[4783]: New relevant interface eth0.IPv4 for mDNS.
Oct  6 19:27:58 mati avahi-daemon[4783]: Registering new address record for 192.168.1.33 on eth0.IPv4.
Oct  6 19:27:59 mati NetworkManager: <info>  Clearing nscd hosts cache. 
Oct  6 19:27:59 mati NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct  6 19:27:59 mati NetworkManager: <info>  Activation (eth0) successful, device activated. 
Oct  6 19:27:59 mati NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Oct  6 19:27:59 mati NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Oct  6 19:27:59 mati kernel: [   69.519395] NET: Registered protocol family 10
Oct  6 19:27:59 mati kernel: [   69.520644] lo: Disabled Privacy Extensions
Oct  6 19:27:59 mati ntpdate[5350]: adjust time server 91.189.94.4 offset -0.044575 sec
Oct  6 19:28:00 mati avahi-daemon[4783]: Registering new address record for fe80::230:13ff:feb5:d865 on eth0.*.
Oct  6 19:28:09 mati kernel: [   80.642457] eth0: no IPv6 routers present
Oct  6 19:28:32 mati hcid[5052]: Default passkey agent (:1.22, /org/bluez/passkey) registered
Oct  6 19:28:32 mati hcid[5052]: Default authorization agent (:1.22, /org/bluez/auth) registered
Oct  6 19:28:43 mati NetworkManager: <info>  Updating allowed wireless network lists. 
Oct  6 19:28:43 mati NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Oct  6 19:30:13 mati syslogd 1.5.0#1ubuntu1: restart.

---

### Post by jesuisbenjamin on 2008-10-06
Deamon.log :)

> Oct  6 19:18:00 mati audio[5059]: Bluetooth Audio daemon
Oct  6 19:18:00 mati input[5065]: Bluetooth Input daemon
Oct  6 19:18:00 mati audio[5059]: Unix socket created: 5
Oct  6 19:18:00 mati audio[5059]: audio.conf: Key file does not have key 'Enable'
Oct  6 19:18:00 mati audio[5059]: audio.conf: Key file does not have key 'Disable'
Oct  6 19:18:00 mati input[5065]: Registered input manager path:/org/bluez/input
Oct  6 19:18:00 mati audio[5059]: add_service_record: got record id 0x10000
Oct  6 19:18:00 mati audio[5059]: audio.conf: Key file does not have key 'Disable'
Oct  6 19:18:00 mati audio[5059]: audio.conf: Key file does not have group 'A2DP'
Oct  6 19:18:00 mati last message repeated 3 times
Oct  6 19:18:00 mati audio[5059]: SEP 0x806d6d0 registered: type:0 codec:0 seid:1
Oct  6 19:18:00 mati audio[5059]: add_service_record: got record id 0x10001
Oct  6 19:18:00 mati audio[5059]: add_service_record: got record id 0x10002
Oct  6 19:18:00 mati audio[5059]: add_service_record: got record id 0x10003
Oct  6 19:18:00 mati audio[5059]: Registered manager path:/org/bluez/audio
Oct  6 19:18:00 mati NetworkManager: <info>  Will activate connection 'eth0'. 
Oct  6 19:18:00 mati NetworkManager: <info>  Device eth0 activation scheduled... 
Oct  6 19:18:00 mati NetworkManager: <debug> [1223313480.947657] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Oct  6 19:18:00 mati NetworkManager: <info>  Activation (eth0) started... 
Oct  6 19:18:00 mati NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct  6 19:18:00 mati NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Oct  6 19:18:00 mati NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Oct  6 19:18:00 mati NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Oct  6 19:18:00 mati NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Oct  6 19:18:00 mati NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Oct  6 19:18:00 mati NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct  6 19:18:00 mati NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Oct  6 19:18:00 mati NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Oct  6 19:18:01 mati NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Oct  6 19:18:01 mati NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Oct  6 19:18:01 mati NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Oct  6 19:18:03 mati NetworkManager: <debug> [1223313483.014598] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_4337_drm_radeon_card0'). 
Oct  6 19:18:03 mati NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Oct  6 19:18:04 mati dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Oct  6 19:18:09 mati dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Oct  6 19:18:09 mati dhclient: DHCPOFFER of 192.168.1.33 from 192.168.1.254
Oct  6 19:18:09 mati dhclient: DHCPREQUEST of 192.168.1.33 on eth0 to 255.255.255.255 port 67
Oct  6 19:18:09 mati dhclient: DHCPACK of 192.168.1.33 from 192.168.1.254
Oct  6 19:18:09 mati avahi-daemon[4777]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.33.
Oct  6 19:18:09 mati avahi-daemon[4777]: New relevant interface eth0.IPv4 for mDNS.
Oct  6 19:18:09 mati avahi-daemon[4777]: Registering new address record for 192.168.1.33 on eth0.IPv4.
Oct  6 19:18:09 mati NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface eth0 
Oct  6 19:18:09 mati NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct  6 19:18:09 mati NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Oct  6 19:18:09 mati NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct  6 19:18:09 mati NetworkManager: <info>    address 192.168.1.33 
Oct  6 19:18:09 mati NetworkManager: <info>    netmask 255.255.255.0 
Oct  6 19:18:09 mati NetworkManager: <info>    broadcast 192.168.1.255 
Oct  6 19:18:09 mati NetworkManager: <info>    gateway 192.168.1.254 
Oct  6 19:18:09 mati NetworkManager: <info>    nameserver 192.168.1.254 
Oct  6 19:18:09 mati NetworkManager: <info>    nameserver 195.241.77.55 
Oct  6 19:18:09 mati NetworkManager: <info>    nameserver 195.241.77.58 
Oct  6 19:18:09 mati NetworkManager: <info>    hostname 'dhcppc0' 
Oct  6 19:18:09 mati NetworkManager: <info>    domain name 'lokaal' 
Oct  6 19:18:09 mati NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct  6 19:18:09 mati NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Oct  6 19:18:09 mati NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Oct  6 19:18:09 mati dhclient: bound to 192.168.1.33 -- renewal in 13568 seconds.
Oct  6 19:18:09 mati avahi-daemon[4777]: Withdrawing address record for 192.168.1.33 on eth0.
Oct  6 19:18:09 mati avahi-daemon[4777]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.33.
Oct  6 19:18:09 mati avahi-daemon[4777]: Interface eth0.IPv4 no longer relevant for mDNS.
Oct  6 19:18:09 mati avahi-daemon[4777]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.33.
Oct  6 19:18:09 mati avahi-daemon[4777]: New relevant interface eth0.IPv4 for mDNS.
Oct  6 19:18:09 mati avahi-daemon[4777]: Registering new address record for 192.168.1.33 on eth0.IPv4.
Oct  6 19:18:10 mati NetworkManager: <info>  Clearing nscd hosts cache. 
Oct  6 19:18:10 mati NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct  6 19:18:10 mati NetworkManager: <info>  Activation (eth0) successful, device activated. 
Oct  6 19:18:10 mati NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Oct  6 19:18:10 mati NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Oct  6 19:18:11 mati ntpdate[5344]: adjust time server 91.189.94.4 offset -0.047069 sec
Oct  6 19:18:12 mati avahi-daemon[4777]: Registering new address record for fe80::230:13ff:feb5:d865 on eth0.*.
Oct  6 19:18:48 mati hcid[5046]: Default passkey agent (:1.22, /org/bluez/passkey) registered
Oct  6 19:18:48 mati hcid[5046]: Default authorization agent (:1.22, /org/bluez/auth) registered
Oct  6 19:18:57 mati NetworkManager: <info>  Updating allowed wireless network lists. 
Oct  6 19:18:57 mati NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Oct  6 19:27:50 mati NetworkManager: <info>  starting... 

And then:

> Oct  6 19:27:50 mati NetworkManager: <info>  starting... 
Oct  6 19:27:50 mati avahi-daemon[4783]: Found user 'avahi' (UID 109) and group 'avahi' (GID 120).
Oct  6 19:27:50 mati avahi-daemon[4783]: Successfully dropped root privileges.
Oct  6 19:27:50 mati avahi-daemon[4783]: avahi-daemon 0.6.22 starting up.
Oct  6 19:27:50 mati avahi-daemon[4783]: Successfully called chroot().
Oct  6 19:27:50 mati avahi-daemon[4783]: Successfully dropped remaining capabilities.
Oct  6 19:27:50 mati avahi-daemon[4783]: No service file found in /etc/avahi/services.
Oct  6 19:27:50 mati avahi-daemon[4783]: Network interface enumeration completed.
Oct  6 19:27:50 mati avahi-daemon[4783]: Registering HINFO record with values 'I686'/'LINUX'.
Oct  6 19:27:50 mati avahi-daemon[4783]: Server startup complete. Host name is mati.local. Local service cookie is 390551562.
Oct  6 19:27:52 mati NetworkManager: <info>  eth0: Device is fully-supported using driver '8139too'. 
Oct  6 19:27:52 mati NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct  6 19:27:52 mati NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct  6 19:27:52 mati NetworkManager: <info>  Now managing wired Ethernet (802.3) device 'eth0'. 
Oct  6 19:27:52 mati NetworkManager: <info>  Deactivating device eth0. 
Oct  6 19:27:52 mati NetworkManager: <info>  Will activate wired connection 'eth0' because it now has a link. 
Oct  6 19:27:52 mati NetworkManager: <debug> [1223314072.381200] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_QSI_CD_RW/DVD_ROM_SBW_242'). 
Oct  6 19:27:52 mati NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'. 
Oct  6 19:27:52 mati hcid[5052]: Bluetooth HCI daemon
Oct  6 19:27:52 mati hcid[5052]: Starting SDP server
Oct  6 19:27:52 mati hcid[5052]: Created local server at unix:abstract=/var/run/dbus-6t1pGb3alx,guid=86e3127d12a0af1cfc8b163948ea4a98
Oct  6 19:27:52 mati audio[5065]: Bluetooth Audio daemon
Oct  6 19:27:52 mati input[5071]: Bluetooth Input daemon
Oct  6 19:27:52 mati audio[5065]: Unix socket created: 5
Oct  6 19:27:52 mati audio[5065]: audio.conf: Key file does not have key 'Enable'
Oct  6 19:27:52 mati audio[5065]: audio.conf: Key file does not have key 'Disable'
Oct  6 19:27:52 mati input[5071]: Registered input manager path:/org/bluez/input
Oct  6 19:27:52 mati audio[5065]: add_service_record: got record id 0x10000
Oct  6 19:27:52 mati audio[5065]: audio.conf: Key file does not have key 'Disable'
Oct  6 19:27:52 mati audio[5065]: audio.conf: Key file does not have group 'A2DP'
Oct  6 19:27:52 mati last message repeated 3 times
Oct  6 19:27:52 mati audio[5065]: SEP 0x806d6d0 registered: type:0 codec:0 seid:1
Oct  6 19:27:52 mati audio[5065]: add_service_record: got record id 0x10001
Oct  6 19:27:52 mati audio[5065]: add_service_record: got record id 0x10002
Oct  6 19:27:52 mati audio[5065]: add_service_record: got record id 0x10003
Oct  6 19:27:52 mati audio[5065]: Registered manager path:/org/bluez/audio
Oct  6 19:27:53 mati NetworkManager: <info>  Will activate connection 'eth0'. 
Oct  6 19:27:53 mati NetworkManager: <info>  Device eth0 activation scheduled... 
Oct  6 19:27:53 mati NetworkManager: <debug> [1223314073.394647] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
Oct  6 19:27:53 mati NetworkManager: <info>  Activation (eth0) started... 
Oct  6 19:27:53 mati NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct  6 19:27:53 mati NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Oct  6 19:27:53 mati NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Oct  6 19:27:53 mati NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Oct  6 19:27:53 mati NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Oct  6 19:27:53 mati NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Oct  6 19:27:53 mati NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Oct  6 19:27:53 mati NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Oct  6 19:27:53 mati NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Oct  6 19:27:54 mati NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Oct  6 19:27:54 mati NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Oct  6 19:27:54 mati NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth0 
Oct  6 19:27:55 mati NetworkManager: <debug> [1223314075.293116] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/pci_1002_4337_drm_radeon_card0'). 
Oct  6 19:27:55 mati NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth0 
Oct  6 19:27:58 mati dhclient: DHCPREQUEST of 192.168.1.33 on eth0 to 255.255.255.255 port 67
Oct  6 19:27:58 mati dhclient: DHCPACK of 192.168.1.33 from 192.168.1.254
Oct  6 19:27:58 mati avahi-daemon[4783]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.33.
Oct  6 19:27:58 mati avahi-daemon[4783]: New relevant interface eth0.IPv4 for mDNS.
Oct  6 19:27:58 mati avahi-daemon[4783]: Registering new address record for 192.168.1.33 on eth0.IPv4.
Oct  6 19:27:58 mati NetworkManager: <info>  DHCP daemon state is now 4 (reboot) for interface eth0 
Oct  6 19:27:58 mati NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled... 
Oct  6 19:27:58 mati NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started... 
Oct  6 19:27:58 mati NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
Oct  6 19:27:58 mati NetworkManager: <info>    address 192.168.1.33 
Oct  6 19:27:58 mati NetworkManager: <info>    netmask 255.255.255.0 
Oct  6 19:27:58 mati NetworkManager: <info>    broadcast 192.168.1.255 
Oct  6 19:27:58 mati NetworkManager: <info>    gateway 192.168.1.254 
Oct  6 19:27:58 mati NetworkManager: <info>    nameserver 192.168.1.254 
Oct  6 19:27:58 mati NetworkManager: <info>    nameserver 195.241.77.55 
Oct  6 19:27:58 mati NetworkManager: <info>    nameserver 195.241.77.58 
Oct  6 19:27:58 mati NetworkManager: <info>    hostname 'dhcppc0' 
Oct  6 19:27:58 mati NetworkManager: <info>    domain name 'lokaal' 
Oct  6 19:27:58 mati NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct  6 19:27:58 mati NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete. 
Oct  6 19:27:58 mati NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started... 
Oct  6 19:27:58 mati dhclient: bound to 192.168.1.33 -- renewal in 11339 seconds.
Oct  6 19:27:58 mati avahi-daemon[4783]: Withdrawing address record for 192.168.1.33 on eth0.
Oct  6 19:27:58 mati avahi-daemon[4783]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.1.33.
Oct  6 19:27:58 mati avahi-daemon[4783]: Interface eth0.IPv4 no longer relevant for mDNS.
Oct  6 19:27:58 mati avahi-daemon[4783]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.33.
Oct  6 19:27:58 mati avahi-daemon[4783]: New relevant interface eth0.IPv4 for mDNS.
Oct  6 19:27:58 mati avahi-daemon[4783]: Registering new address record for 192.168.1.33 on eth0.IPv4.
Oct  6 19:27:59 mati NetworkManager: <info>  Clearing nscd hosts cache. 
Oct  6 19:27:59 mati NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
Oct  6 19:27:59 mati NetworkManager: <info>  Activation (eth0) successful, device activated. 
Oct  6 19:27:59 mati NetworkManager: <info>  Activation (eth0) Finish handler scheduled. 
Oct  6 19:27:59 mati NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete. 
Oct  6 19:27:59 mati ntpdate[5350]: adjust time server 91.189.94.4 offset -0.044575 sec
Oct  6 19:28:00 mati avahi-daemon[4783]: Registering new address record for fe80::230:13ff:feb5:d865 on eth0.*.
Oct  6 19:28:32 mati hcid[5052]: Default passkey agent (:1.22, /org/bluez/passkey) registered
Oct  6 19:28:32 mati hcid[5052]: Default authorization agent (:1.22, /org/bluez/auth) registered
Oct  6 19:28:43 mati NetworkManager: <info>  Updating allowed wireless network lists. 
Oct  6 19:28:43 mati NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Oct  6 19:30:14 mati NetworkManager: <info>  starting... 

---

### Post by jesuisbenjamin on 2008-10-06
As for Kern.log

> Oct  6 19:18:00 mati kernel: [   40.319427] Bluetooth: Core ver 2.11
Oct  6 19:18:00 mati kernel: [   40.321048] NET: Registered protocol family 31
Oct  6 19:18:00 mati kernel: [   40.321059] Bluetooth: HCI device and connection manager initialized
Oct  6 19:18:00 mati kernel: [   40.321066] Bluetooth: HCI socket layer initialized
Oct  6 19:18:00 mati kernel: [   40.352645] Bluetooth: L2CAP ver 2.9
Oct  6 19:18:00 mati kernel: [   40.352657] Bluetooth: L2CAP socket layer initialized
Oct  6 19:18:00 mati kernel: [   40.446029] Bluetooth: RFCOMM socket layer initialized
Oct  6 19:18:00 mati kernel: [   40.446537] Bluetooth: RFCOMM TTY layer initialized
Oct  6 19:18:00 mati kernel: [   40.446544] Bluetooth: RFCOMM ver 1.8
Oct  6 19:18:01 mati kernel: [   62.112141] Marking TSC unstable due to: cpufreq changes.
Oct  6 19:18:02 mati kernel: [   42.606975] [drm] Initialized drm 1.1.0 20060810
Oct  6 19:18:03 mati kernel: [   42.672209] ACPI: PCI Interrupt Link [LNK0] enabled at IRQ 11
Oct  6 19:18:03 mati kernel: [   42.672226] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNK0] -> GSI 11 (level, low) -> IRQ 11
Oct  6 19:18:03 mati kernel: [   42.672648] [drm] Initialized radeon 1.28.0 20060524 on minor 0
Oct  6 19:18:03 mati kernel: [   43.065039] NET: Registered protocol family 17
Oct  6 19:18:04 mati kernel: [   65.754286] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Oct  6 19:18:04 mati kernel: [   65.754932] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Oct  6 19:18:04 mati kernel: [   65.755390] agpgart: Putting AGP V2 device at 0000:01:05.0 into 4x mode
Oct  6 19:18:05 mati kernel: [   67.136053] [drm] Setting GART location based on new memory map
Oct  6 19:18:05 mati kernel: [   67.136134] [drm] writeback test succeeded in 1 usecs
Oct  6 19:18:10 mati kernel: [   72.354472] NET: Registered protocol family 10
Oct  6 19:18:10 mati kernel: [   72.355754] lo: Disabled Privacy Extensions
Oct  6 19:18:21 mati kernel: [   83.918859] eth0: no IPv6 routers present
Oct  6 19:27:49 mati kernel: Inspecting /boot/System.map-2.6.24-19-generic

And finally:
> Oct  6 19:27:50 mati kernel: [   29.011594] input: Power Button (CM) as /devices/virtual/input/input5
Oct  6 19:27:50 mati kernel: [   29.024699] ACPI: Power Button (CM) [PWRB]
Oct  6 19:27:50 mati kernel: [   29.024887] input: Lid Switch as /devices/virtual/input/input6
Oct  6 19:27:50 mati kernel: [   29.025027] ACPI: Lid Switch [LID]
Oct  6 19:27:50 mati kernel: [   29.050967] ACPI: AC Adapter [ACAD] (off-line)
Oct  6 19:27:50 mati kernel: [   29.108573] ACPI: Battery Slot [BAT1] (battery absent)
Oct  6 19:27:50 mati kernel: [   29.727878] input: PS/2 Mouse as /devices/virtual/input/input7
Oct  6 19:27:50 mati kernel: [   29.746857] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
Oct  6 19:27:50 mati kernel: [   30.077295] parport_pc 00:0a: reported by Plug and Play ACPI
Oct  6 19:27:50 mati kernel: [   30.077327] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
Oct  6 19:27:50 mati kernel: [   30.543308] ACPI: PCI Interrupt Link [LNK7] enabled at IRQ 11
Oct  6 19:27:50 mati kernel: [   30.543317] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNK7] -> GSI 11 (level, low) -> IRQ 11
Oct  6 19:27:50 mati kernel: [   33.693600] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2061: AC'97 1 does not respond - RESET
Oct  6 19:27:50 mati kernel: [   33.704172] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ac97/ac97_codec.c:2070: AC'97 1 access is not valid [0xffffffff], removing mixer.
Oct  6 19:27:50 mati kernel: [   33.704190] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/ali5451/ali5451.c:1927: ali mixer 1 creating error.
Oct  6 19:27:50 mati kernel: [   34.688512] cs: IO port probe 0x100-0x3af: excluding 0x220-0x22f 0x330-0x337 0x388-0x38f
Oct  6 19:27:50 mati kernel: [   34.690106] cs: IO port probe 0x3e0-0x4ff: clean.
Oct  6 19:27:50 mati kernel: [   34.690742] cs: IO port probe 0x820-0x8ff: clean.
Oct  6 19:27:50 mati kernel: [   34.691338] cs: IO port probe 0xc00-0xcf7: clean.
Oct  6 19:27:50 mati kernel: [   34.692169] cs: IO port probe 0xa00-0xaff: clean.
Oct  6 19:27:50 mati kernel: [   34.702286] cs: IO port probe 0x100-0x3af: excluding 0x220-0x22f 0x330-0x337 0x388-0x38f
Oct  6 19:27:50 mati kernel: [   34.703914] cs: IO port probe 0x3e0-0x4ff: clean.
Oct  6 19:27:50 mati kernel: [   34.704554] cs: IO port probe 0x820-0x8ff: clean.
Oct  6 19:27:50 mati kernel: [   34.705151] cs: IO port probe 0xc00-0xcf7: clean.
Oct  6 19:27:50 mati kernel: [   34.706009] cs: IO port probe 0xa00-0xaff: clean.
Oct  6 19:27:50 mati kernel: [   35.911593] lp0: using parport0 (interrupt-driven).
Oct  6 19:27:50 mati kernel: [   36.050882] Adding 1413680k swap on /dev/hda5.  Priority:-1 extents:1 across:1413680k
Oct  6 19:27:50 mati kernel: [   36.101858] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
Oct  6 19:27:50 mati kernel: [   36.102144] EXT3 FS on hda1, internal journal
Oct  6 19:27:50 mati kernel: [   36.881213] ip_tables: (C) 2000-2006 Netfilter Core Team
Oct  6 19:27:50 mati kernel: [   37.524195] No dock devices found.
Oct  6 19:27:50 mati kernel: [   39.317050] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Oct  6 19:27:50 mati kernel: [   39.317063] apm: overridden by ACPI.
Oct  6 19:27:50 mati kernel: [   39.468787] ppdev: user-space parallel port driver
Oct  6 19:27:51 mati kernel: [   39.676346] audit(1223314071.097:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4822 profile="/usr/sbin/cupsd" namespace="default"
Oct  6 19:27:51 mati kernel: [   60.234625] Marking TSC unstable due to: cpufreq changes.
Oct  6 19:27:52 mati kernel: [   40.848208] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Oct  6 19:27:52 mati kernel: [   41.011943] Bluetooth: Core ver 2.11
Oct  6 19:27:52 mati kernel: [   41.013490] NET: Registered protocol family 31
Oct  6 19:27:52 mati kernel: [   41.013503] Bluetooth: HCI device and connection manager initialized
Oct  6 19:27:52 mati kernel: [   41.013511] Bluetooth: HCI socket layer initialized
Oct  6 19:27:52 mati kernel: [   41.046090] Bluetooth: L2CAP ver 2.9
Oct  6 19:27:52 mati kernel: [   41.046101] Bluetooth: L2CAP socket layer initialized
Oct  6 19:27:52 mati kernel: [   41.150085] Bluetooth: RFCOMM socket layer initialized
Oct  6 19:27:52 mati kernel: [   41.150562] Bluetooth: RFCOMM TTY layer initialized
Oct  6 19:27:52 mati kernel: [   41.150570] Bluetooth: RFCOMM ver 1.8
Oct  6 19:27:55 mati kernel: [   43.219740] [drm] Initialized drm 1.1.0 20060810
Oct  6 19:27:55 mati kernel: [   43.285221] ACPI: PCI Interrupt Link [LNK0] enabled at IRQ 11
Oct  6 19:27:55 mati kernel: [   43.285240] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNK0] -> GSI 11 (level, low) -> IRQ 11
Oct  6 19:27:55 mati kernel: [   43.285661] [drm] Initialized radeon 1.28.0 20060524 on minor 0
Oct  6 19:27:55 mati kernel: [   43.755475] NET: Registered protocol family 17
Oct  6 19:27:56 mati kernel: [   66.663284] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Oct  6 19:27:56 mati kernel: [   66.663929] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Oct  6 19:27:56 mati kernel: [   66.664394] agpgart: Putting AGP V2 device at 0000:01:05.0 into 4x mode
Oct  6 19:27:58 mati kernel: [   68.045317] [drm] Setting GART location based on new memory map
Oct  6 19:27:58 mati kernel: [   68.045396] [drm] writeback test succeeded in 1 usecs
Oct  6 19:27:59 mati kernel: [   69.519395] NET: Registered protocol family 10
Oct  6 19:27:59 mati kernel: [   69.520644] lo: Disabled Privacy Extensions
Oct  6 19:28:09 mati kernel: [   80.642457] eth0: no IPv6 routers present
Oct  6 19:30:13 mati kernel: Inspecting /boot/System.map-2.6.24-19-generic

---

### Post by DrMega on 2008-10-06
I had Dapper and then Gutsy on one of my machines for ages with no problems. I installed Hardy and got random freeze-ups. No hardware had changed, only the version of Ubuntu, so I went back to Gutsy.

---

### Post by jesuisbenjamin on 2008-10-06
Had freezes under Gusty AND my computer was a lot slower. Now it's freezing, but faster, so i can do more between freezes :)

---

### Post by DrMega on 2008-10-07
> **jesuisbenjamin said:**
> Had freezes under Gusty AND my computer was a lot slower. Now it's freezing, but faster, so i can do more between freezes :)

Can you list your hardware spec? I had freezups on one of my machines and it turned out to be an issue with the graphics drivers when I was using a particular card.

---

### Post by jesuisbenjamin on 2008-10-08
OK guyes this is it. My computer died yesterday morning. 

I don't know what the hell happened but intuitively knew it would end this way. It froze as usual and then when starting up again it beeped several times and didn't even start anything, not even a cursor on the screen. 
It eventually restarted after a while, then froze and that was the end, the last breath...

It's real crap, i lost all my data blabla, you know the story i am not here to complain, just to point at the fact it happened and that Ubuntu potentially is responsible for the case. It would be nice if some qualified people could investigate the case, with the data provided above. I am afraid i won't be able to provide any more information about late computer.

I am going to buy a new laptop with my saving piglet tomorrow, it might just as well be a good thing before the fiancial crisis turns my money into rupies :)

I've heard Dell Vostro 1510 is quite friend with Ubuntu. Comments and suggestions are welcome.

Thanks for your attention.

\

---

### Post by linux2.6.24-19-generic on 2008-10-08
The ATI graphics card is a potential problem.  I had an ATI in my desktop and ubuntu crashed on a daily basis.  I replaced it with an nvidia and my system is now stable...after a complete reinstall of the OS.  Ubuntu didn't handle a graphics card upgrade very well.

In any case, none of this probably matters to you.  Except, if you plan on using linux on any future computer I would avoid ATI and target nvidia.

---

### Post by jesuisbenjamin on 2008-10-09
Cool thanks,
This computer has Intel Integrated GMA X3100 and it works fine so far.

Thanks.

---

