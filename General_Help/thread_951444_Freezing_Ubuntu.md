---
title: "Freezing Ubuntu"
date: 2008-10-18
forum: General Help
---

### Post by pumex1990 on 2008-10-18
Hi,
first of all, sorry for my bad English, but I'm doing my best :)

I have problem with my Ubuntu 8.04. It's freezing very often. It happens when I'm doing normal things, like using Firefoks, Kadu, Or Nautilus. Sometimes it's also freezing during logging in.

I don't think that it's hardware fault, because Windows and Ubuntu Live CD is working properly.

I've tried to format disk (including /home partition), but it didn't help.

What's more I think, that it's freezing only when I'm doing something - I mean using keyboard or mouse - computer is able to work all night with an open torrent without a freeze.

Some logs from syslog:

```
Oct 17 19:02:01 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
 Oct 17 19:02:01 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
 Oct 17 19:02:01 pumex-desktop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
 Oct 17 19:02:01 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 31 seconds.
 Oct 17 19:02:32 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
 Oct 17 19:02:32 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
 Oct 17 19:02:32 pumex-desktop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
 Oct 17 19:02:32 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 26 seconds.
 Oct 17 19:02:58 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
 Oct 17 19:02:58 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
 Oct 17 19:02:58 pumex-desktop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
 Oct 17 19:02:58 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 27 seconds.
 Oct 17 19:03:25 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
 Oct 17 19:03:25 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
 Oct 17 19:03:25 pumex-desktop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
 Oct 17 19:03:25 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 26 seconds.
 Oct 17 19:03:51 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
 Oct 17 19:03:51 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
 Oct 17 19:03:51 pumex-desktop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
 Oct 17 19:03:51 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 30 seconds.
 Oct 17 19:04:21 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
 Oct 17 19:04:21 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
 Oct 17 19:04:21 pumex-desktop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
 Oct 17 19:04:21 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 28 seconds.
 Oct 17 19:04:49 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
 Oct 17 19:04:49 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
 Oct 17 19:04:49 pumex-desktop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
 Oct 17 19:04:49 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 30 seconds.
 Oct 17 19:05:19 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
 Oct 17 19:05:19 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
 Oct 17 19:05:19 pumex-desktop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
 Oct 17 19:05:19 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 26 seconds.
 Oct 17 19:05:45 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
 Oct 17 19:05:45 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
 Oct 17 19:05:45 pumex-desktop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
 Oct 17 19:05:45 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 25 seconds.
 Oct 17 19:06:10 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
 Oct 17 19:06:10 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
 Oct 17 19:06:10 pumex-desktop NetworkManager: <info>  DHCP daemon state is now 3 (renew) for interface eth0 
 Oct 17 19:06:10 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 32 seconds.
 Oct 17 19:07:17 pumex-desktop syslogd 1.5.0#1ubuntu1: restart.
```

And the second one:

```


ct 17 22:30:45 pumex-desktop kernel: [  196.891304] Bluetooth: RFCOMM socket layer initialized
Oct 17 22:30:45 pumex-desktop kernel: [  196.891328] Bluetooth: RFCOMM TTY layer initialized
Oct 17 22:30:45 pumex-desktop kernel: [  196.891331] Bluetooth: RFCOMM ver 1.8
Oct 17 22:30:45 pumex-desktop audio[6337]: add_service_record: got record id 0x10000
Oct 17 22:30:45 pumex-desktop audio[6337]: audio.conf: Key file does not have key 'Disable'
Oct 17 22:30:45 pumex-desktop audio[6337]: audio.conf: Key file does not have group 'A2DP'
Oct 17 22:30:45 pumex-desktop last message repeated 3 times
Oct 17 22:30:45 pumex-desktop audio[6337]: SEP 0x806d648 registered: type:0 codec:0 seid:1
Oct 17 22:30:45 pumex-desktop audio[6337]: add_service_record: got record id 0x10001
Oct 17 22:30:45 pumex-desktop audio[6337]: add_service_record: got record id 0x10002
Oct 17 22:30:45 pumex-desktop audio[6337]: add_service_record: got record id 0x10003
Oct 17 22:30:45 pumex-desktop audio[6337]: Registered manager path:/org/bluez/audio
Oct 17 22:30:46 pumex-desktop anacron[6393]: Anacron 2.3 started on 2008-10-17
Oct 17 22:30:46 pumex-desktop anacron[6393]: Normal exit (0 jobs run)
Oct 17 22:30:46 pumex-desktop /usr/sbin/cron[6420]: (CRON) INFO (pidfile fd = 3)
Oct 17 22:30:46 pumex-desktop /usr/sbin/cron[6421]: (CRON) STARTUP (fork ok)
Oct 17 22:30:46 pumex-desktop /usr/sbin/cron[6421]: (CRON) INFO (Running @reboot jobs)
Oct 17 22:31:00 pumex-desktop kernel: [  212.359271] NET: Registered protocol family 10
Oct 17 22:31:00 pumex-desktop kernel: [  212.360143] lo: Disabled Privacy Extensions
Oct 17 22:31:01 pumex-desktop avahi-daemon[5976]: Registering new address record for fe80::20f:eaff:fe5a:c1e7 on eth0.*.
Oct 17 22:31:03 pumex-desktop hcid[6315]: Default passkey agent (:1.20, /org/bluez/passkey) registered
Oct 17 22:31:03 pumex-desktop hcid[6315]: Default authorization agent (:1.20, /org/bluez/auth) registered
Oct 17 22:31:08 pumex-desktop kernel: [  123.743318] UDF-fs: No VRS found
Oct 17 22:31:08 pumex-desktop kernel: [  123.769086] ISO 9660 Extensions: Microsoft Joliet Level 3
Oct 17 22:31:08 pumex-desktop kernel: [  123.770061] ISOFS: changing to secondary root
Oct 17 22:31:11 pumex-desktop kernel: [  225.375340] eth0: no IPv6 routers present
Oct 17 22:31:14 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
Oct 17 22:31:14 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Oct 17 22:31:14 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 26 seconds.
Oct 17 22:31:40 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
Oct 17 22:31:40 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Oct 17 22:31:40 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 25 seconds.
Oct 17 22:32:05 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
Oct 17 22:32:05 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Oct 17 22:32:05 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 26 seconds.
Oct 17 22:32:31 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
Oct 17 22:32:31 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Oct 17 22:32:31 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 25 seconds.
Oct 17 22:32:56 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
Oct 17 22:32:56 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Oct 17 22:32:56 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 32 seconds.
Oct 17 22:33:28 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
Oct 17 22:33:28 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Oct 17 22:33:28 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 25 seconds.
Oct 17 22:33:53 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
Oct 17 22:33:53 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Oct 17 22:33:53 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 24 seconds.
Oct 17 22:34:17 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
Oct 17 22:34:17 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Oct 17 22:34:17 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 31 seconds.
Oct 17 22:34:48 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
Oct 17 22:34:48 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Oct 17 22:34:48 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 30 seconds.
Oct 17 22:35:18 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
Oct 17 22:35:18 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Oct 17 22:35:18 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 30 seconds.
Oct 17 22:35:48 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
Oct 17 22:35:48 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Oct 17 22:35:48 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 26 seconds.
Oct 17 22:36:14 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
Oct 17 22:36:14 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Oct 17 22:36:14 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 26 seconds.
Oct 17 22:36:40 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
Oct 17 22:36:40 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Oct 17 22:36:40 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 25 seconds.
Oct 17 22:37:05 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
Oct 17 22:37:05 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Oct 17 22:37:05 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 26 seconds.
Oct 17 22:37:31 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
Oct 17 22:37:31 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Oct 17 22:37:31 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 26 seconds.
Oct 17 22:37:57 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
Oct 17 22:37:57 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Oct 17 22:37:57 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 28 seconds.
Oct 17 22:38:25 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
Oct 17 22:38:25 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Oct 17 22:38:25 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 29 seconds.
Oct 17 22:38:54 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
Oct 17 22:38:54 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Oct 17 22:38:54 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 25 seconds.
Oct 17 22:39:19 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
Oct 17 22:39:19 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Oct 17 22:39:19 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 31 seconds.
Oct 17 22:39:50 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
Oct 17 22:39:50 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Oct 17 22:39:50 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 27 seconds.
Oct 17 22:40:17 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
Oct 17 22:40:17 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Oct 17 22:40:17 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 28 seconds.
Oct 17 22:40:45 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
Oct 17 22:40:45 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Oct 17 22:40:45 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 26 seconds.
Oct 17 22:41:11 pumex-desktop dhclient: DHCPREQUEST of <null address> on eth0 to 192.168.1.1 port 67
Oct 17 22:41:11 pumex-desktop dhclient: DHCPACK of 192.168.1.101 from 192.168.1.1
Oct 17 22:41:11 pumex-desktop dhclient: bound to 192.168.1.101 -- renewal in 28 seconds.
Oct 17 22:42:33 pumex-desktop syslogd 1.5.0#1ubuntu1: restart.
```

On polish forum people blamed for that:

- pulseaudio - so i removed it completly (by typing sudo apt-get remove pulseaudio*)
- graphic card drivers - I was using close drivers for NVidia, but i turned them off and it didn't help.
- network menager - but I completly removed it and installed WICD instead of it, and it didn't help.

Any ideas? :)

---

### Post by geirha on 2008-10-18
Could you explain "freezing" a bit more. Does it freeze totally, forcing you to shut it off using the power button, or does it freeze for a while, then starts working again for a while?

Output of the dmesg command would also be helpful.

---

### Post by pumex1990 on 2008-10-18
I have to force restart by using the restart button. It's not responding for anything else, like ctrl+alt+backspace, I can't use a mouse. If I'm listening to the music, when it freeze, the music stops. I can hear, that the hard drive is working for a while when it freeze, and after a few seconds it stops working.

Now I have logged in a 'Gnome emergency session' (i hope it's a good translation) - i picked up this option on the welcome screen, and it's not freezing.

Dmesg shows:

```
[   26.498611] ACPI: bus type pci registered
[   26.512144] PCI: PCI BIOS revision 3.00 entry at 0xfb060, last bus=2
[   26.512211] PCI: Using configuration type 1
[   26.512277] Setting up standard PCI resources
[   26.515940] ACPI: EC: Look up EC in DSDT
[   26.522104] ACPI: Interpreter enabled
[   26.522169] ACPI: (supports S0 S1 S4 S5)
[   26.522453] ACPI: Using IOAPIC for interrupt routing
[   26.531514] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   26.533153] PCI: Transparent bridge - 0000:00:10.0
[   26.533240] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   26.533531] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   26.608402] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   26.609223] ACPI: PCI Interrupt Link [LNK2] (IRQs *5 7 9 10 11 14 15)
[   26.609934] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 *11 14 15)
[   26.610643] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   26.611460] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 *11 14 15)
[   26.612163] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   26.612980] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   26.613800] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   26.614622] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 *10 11 14 15)
[   26.615326] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   26.616144] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[   26.616848] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   26.617669] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
[   26.618373] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   26.619194] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   26.620013] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 *11 14 15)
[   26.620718] ACPI: PCI Interrupt Link [LUB2] (IRQs *5 7 9 10 11 14 15)
[   26.621429] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   26.622247] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[   26.622960] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
[   26.623703] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   26.624230] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[   26.624702] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   26.625173] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   26.625701] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
[   26.626173] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   26.626703] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   26.627228] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   26.627753] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   26.628383] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   26.629067] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   26.629700] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[   26.630386] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[   26.631074] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[   26.631704] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   26.632388] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   26.633018] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   26.633651] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   26.634335] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   26.635022] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   26.635653] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   26.636205] Linux Plug and Play Support v0.97 (c) Adam Belay
[   26.636295] pnp: PnP ACPI init
[   26.636364] ACPI: bus type pnp registered
[   26.640968] pnp: PnP ACPI: found 13 devices
[   26.641034] ACPI: ACPI bus type pnp unregistered
[   26.641101] PnPBIOS: Disabled by ACPI PNP
[   26.641356] PCI: Using ACPI for IRQ routing
[   26.641424] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   26.729244] NET: Registered protocol family 8
[   26.729310] NET: Registered protocol family 20
[   26.729432] AppArmor: AppArmor Filesystem Enabled
[   26.733235] Time: tsc clocksource has been installed.
[   26.741262] system 00:01: ioport range 0x1000-0x107f has been reserved
[   26.741330] system 00:01: ioport range 0x1080-0x10ff has been reserved
[   26.741398] system 00:01: ioport range 0x1400-0x147f has been reserved
[   26.741465] system 00:01: ioport range 0x1480-0x14ff has been reserved
[   26.741533] system 00:01: ioport range 0x1800-0x187f has been reserved
[   26.741600] system 00:01: ioport range 0x1880-0x18ff has been reserved
[   26.741667] system 00:01: ioport range 0x2000-0x207f has been reserved
[   26.741735] system 00:01: ioport range 0x2080-0x20ff has been reserved
[   26.741803] system 00:01: iomem range 0xfefe0000-0xfefe01ff could not be reserved
[   26.741878] system 00:01: iomem range 0x0-0x0 could not be reserved
[   26.742826] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   26.742893] system 00:02: ioport range 0x800-0x87f has been reserved
[   26.742961] system 00:02: ioport range 0x295-0x314 has been reserved
[   26.743028] system 00:02: ioport range 0x290-0x294 has been reserved
[   26.743101] system 00:0b: iomem range 0xf0000000-0xf1ffffff could not be reserved
[   26.743180] system 00:0c: iomem range 0xcec00-0xcffff has been reserved
[   26.743247] system 00:0c: iomem range 0xf0000-0xf7fff could not be reserved
[   26.743315] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[   26.743383] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[   26.743451] system 00:0c: iomem range 0x3fff0000-0x3fffffff could not be reserved
[   26.743527] system 00:0c: iomem range 0xffff0000-0xffffffff could not be reserved
[   26.743602] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   26.743670] system 00:0c: iomem range 0x100000-0x3ffeffff could not be reserved
[   26.743745] system 00:0c: iomem range 0x0-0x0 could not be reserved
[   26.743812] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[   26.743888] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[   26.774307] PCI: Bridge: 0000:00:04.0
[   26.774373]   IO window: a000-afff
[   26.774438]   MEM window: f2000000-f4ffffff
[   26.774508]   PREFETCH window: e0000000-efffffff
[   26.774574] PCI: Bridge: 0000:00:10.0
[   26.774638]   IO window: disabled.
[   26.774705]   MEM window: f5000000-f50fffff
[   26.774772]   PREFETCH window: disabled.
[   26.774850] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   26.774864] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   26.774875] NET: Registered protocol family 2
[   26.813268] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   26.813618] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   26.814532] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   26.815024] TCP: Hash tables configured (established 131072 bind 65536)
[   26.815092] TCP reno registered
[   26.825322] checking if image is initramfs... it is
[   27.276987] Switched to high resolution mode on CPU 0
[   27.476517] Freeing initrd memory: 7330k freed
[   27.477120] audit: initializing netlink socket (disabled)
[   27.477197] audit(1224325763.468:1): initialized
[   27.477387] highmem bounce pool size: 64 pages
[   27.479021] VFS: Disk quotas dquot_6.5.1
[   27.479145] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   27.479333] io scheduler noop registered
[   27.479397] io scheduler anticipatory registered
[   27.479462] io scheduler deadline registered
[   27.479535] io scheduler cfq registered (default)
[   27.479613] pci 0000:00:00.0: Enabling HT MSI Mapping
[   27.479709] pci 0000:00:04.0: Enabling HT MSI Mapping
[   27.479802] pci 0000:00:09.0: Enabling HT MSI Mapping
[   27.479950] pci 0000:00:0e.0: Enabling HT MSI Mapping
[   27.480032] pci 0000:00:0f.0: Enabling HT MSI Mapping
[   27.480111] pci 0000:00:10.0: Enabling HT MSI Mapping
[   27.480194] pci 0000:00:10.1: Enabling HT MSI Mapping
[   27.480282] Boot video device is 0000:02:00.0
[   27.480375] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   27.480401] assign_interrupt_mode Found MSI capability
[   27.480486] Allocate Port Service[0000:00:04.0:pcie00]
[   27.480675] isapnp: Scanning for PnP cards...
[   27.835049] isapnp: No Plug & Play device found
[   27.859720] Real Time Clock Driver v1.12ac
[   27.859880] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   27.860109] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.860796] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   27.861497] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   27.861631] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   27.861778] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   27.861845] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   27.862018] serio: i8042 KBD port at 0x60,0x64 irq 1
[   27.864823] mice: PS/2 mouse device common for all mice
[   27.864990] EISA: Probing bus 0 at eisa.0
[   27.865060] Cannot allocate resource for EISA slot 1
[   27.865125] Cannot allocate resource for EISA slot 2
[   27.865216] EISA: Detected 0 cards.
[   27.865281] cpuidle: using governor ladder
[   27.865346] cpuidle: using governor menu
[   27.865488] NET: Registered protocol family 1
[   27.865573] Using IPI No-Shortcut mode
[   27.865662] registered taskstats version 1
[   27.865838]   Magic number: 12:362:477
[   27.866074] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   27.866140] EDD information not available.
[   27.866427] Freeing unused kernel memory: 368k freed
[   27.892602] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   28.095302] fuse init (API version 7.9)
[   28.117861] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   29.175925] usbcore: registered new interface driver usbfs
[   29.176022] usbcore: registered new interface driver hub
[   29.186964] usbcore: registered new device driver usb
[   29.200012] SCSI subsystem initialized
[   29.235872] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   29.236268] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   29.236342] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
[   29.236534] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   29.236538] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   29.236877] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   29.236968] ohci_hcd 0000:00:0b.0: irq 16, io mem 0xf5105000
[   29.271830] libata version 3.00 loaded.
[   29.293917] usb usb1: configuration #1 chosen from 1 choice
[   29.294009] hub 1-0:1.0: USB hub found
[   29.294081] hub 1-0:1.0: 8 ports detected
[   29.396298] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   29.396374] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 17
[   29.396564] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   29.396568] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   29.396654] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   29.396765] ehci_hcd 0000:00:0b.1: debug port 1
[   29.396834] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   29.396845] ehci_hcd 0000:00:0b.1: irq 17, io mem 0xf5106000
[   29.407713] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   29.407904] usb usb2: configuration #1 chosen from 1 choice
[   29.407990] hub 2-0:1.0: USB hub found
[   29.408058] hub 2-0:1.0: 8 ports detected
[   29.450926] Floppy drive(s): fd0 is 1.44M
[   29.473284] FDC 0 is a post-1991 82077
[   29.511829] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   29.512275] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[   29.512346] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 21 (level, low) -> IRQ 18
[   29.512531] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   30.031799] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:0f:ea:5a:c1:e7
[   30.031880] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
[   30.034855] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   30.034929] ACPI: PCI Interrupt 0000:01:0e.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 19
[   30.084893] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f5004000-f50047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   30.086548] pata_amd 0000:00:0d.0: version 0.3.10
[   30.086613] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   30.090825] scsi0 : pata_amd
[   30.093795] scsi1 : pata_amd
[   30.094605] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   30.094674] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   30.443120] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   30.575525] ata1.00: ATAPI: LG       DVD-ROM DRD-8160B, 1.01, max UDMA/33
[   30.575610] ata1.01: ATAPI: PIONEER DVD-RW  DVR-110D, 1.17, max UDMA/66
[   30.659170] usb 1-1: configuration #1 chosen from 1 choice
[   30.747372] ata1.00: configured for UDMA/33
[   30.919427] ata1.01: configured for UDMA/66
[   30.962825] usb 1-7: new full speed USB device using ohci_hcd and address 3
[   31.115201] ata2.00: HPA unlocked: 117229295 -> 117231408, native 117231408
[   31.115272] ata2.00: ATA-5: WDC WD600AB-00CBA1, 04.07B04, max UDMA/100
[   31.115339] ata2.00: 117231408 sectors, multi 16: LBA 
[   31.115695] ata2.01: ATA-5: ST340016A, 3.75, max UDMA/100
[   31.115761] ata2.01: 78165360 sectors, multi 16: LBA 
[   31.132040] ata2.00: configured for UDMA/100
[   31.147314] ata2.01: configured for UDMA/100
[   31.147851] scsi 0:0:0:0: CD-ROM            LG       DVD-ROM DRD8160B 1.01 PQ: 0 ANSI: 5
[   31.154785] scsi 0:0:1:0: CD-ROM            PIONEER  DVD-RW  DVR-110D 1.17 PQ: 0 ANSI: 5
[   31.155149] scsi 1:0:0:0: Direct-Access     ATA      WDC WD600AB-00CB 04.0 PQ: 0 ANSI: 5
[   31.155485] scsi 1:0:1:0: Direct-Access     ATA      ST340016A        3.75 PQ: 0 ANSI: 5
[   31.157997] sata_nv 0000:00:0e.0: version 3.5
[   31.158352] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[   31.158425] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 20
[   31.158645] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   31.160389] scsi2 : sata_nv
[   31.160689] scsi3 : sata_nv
[   31.160930] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd400 irq 20
[   31.160999] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd408 irq 20
[   31.269847] usb 1-7: configuration #3 chosen from 1 choice
[   31.323795] usbcore: registered new interface driver hiddev
[   31.336060] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /devices/pci0000:00/0000:00:0b.0/usb1/1-1/1-1:1.0/input/input2
[   31.346688] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:0b.0-1
[   31.347873] usbcore: registered new interface driver usbhid
[   31.347941] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   31.366723] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000fea00005ae8d2]
[   31.470544] ata3: SATA link down (SStatus 0 SControl 300)
[   31.790360] ata4: SATA link down (SStatus 0 SControl 300)
[   31.801957] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
[   31.802025] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 16
[   31.802246] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   31.802310] scsi4 : sata_nv
[   31.802617] scsi5 : sata_nv
[   31.802817] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc000 irq 16
[   31.802886] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc008 irq 16
[   32.114178] ata5: SATA link down (SStatus 0 SControl 300)
[   32.433997] ata6: SATA link down (SStatus 0 SControl 300)
[   32.460965] Driver 'sr' needs updating - please use bus_type methods
[   32.464773] sr0: scsi3-mmc drive: 0x/48x cd/rw xa/form2 cdda tray
[   32.464845] Uniform CD-ROM driver Revision: 3.20
[   32.464945] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   32.468425] Driver 'sd' needs updating - please use bus_type methods
[   32.495607] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   32.495729] sr 0:0:1:0: Attached scsi CD-ROM sr1
[   32.502999] sd 1:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[   32.503081] sd 1:0:0:0: [sda] Write Protect is off
[   32.503147] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   32.503162] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.503286] sd 1:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[   32.503360] sd 1:0:0:0: [sda] Write Protect is off
[   32.503426] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   32.503439] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.503516]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[   32.504695] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   32.504774] sd 1:0:0:0: Attached scsi generic sg2 type 0
[   32.504852] scsi 1:0:1:0: Attached scsi generic sg3 type 0
[   32.520655]  sda1 sda2 sda3
[   32.540247] sd 1:0:0:0: [sda] Attached SCSI disk
[   32.540373] sd 1:0:1:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
[   32.540449] sd 1:0:1:0: [sdb] Write Protect is off
[   32.540515] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   32.540530] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.540641] sd 1:0:1:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
[   32.540715] sd 1:0:1:0: [sdb] Write Protect is off
[   32.540780] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   32.540794] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   32.540871]  sdb: sdb1
[   32.555876] sd 1:0:1:0: [sdb] Attached SCSI disk
[   32.976642] Attempting manual resume
[   32.976708] swsusp: Resume From Partition 8:2
[   32.976710] PM: Checking swsusp image.
[   32.976880] PM: Resume from disk failed.
[   33.008583] kjournald starting.  Commit interval 5 seconds
[   33.008662] EXT3-fs: mounted filesystem with ordered data mode.
[   44.023507] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   44.143721] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   44.203399] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   44.203481] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c80
[   44.580153] input: Power Button (FF) as /devices/virtual/input/input3
[   44.595099] ACPI: Power Button (FF) [PWRF]
[   44.595275] input: Power Button (CM) as /devices/virtual/input/input4
[   44.611096] ACPI: Power Button (CM) [PWRB]
[   44.874956] Linux agpgart interface v0.102
[   45.702482] Linux video capture interface: v2.00
[   46.103427] saa7130/34: v4l2 driver version 0.2.14 loaded
[   46.103919] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   46.103989] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 21
[   46.104177] saa7130[0]: found at 0000:01:07.0, rev: 1, irq: 21, latency: 32, mmio: 0xf5005000
[   46.104258] saa7134: <rant>
[   46.104259] saa7134:  Congratulations!  Your TV card vendor saved a few
[   46.104260] saa7134:  cents for a eeprom, thus your pci board has no
[   46.104262] saa7134:  subsystem ID and I can't identify it automatically
[   46.104263] saa7134: </rant>
[   46.104264] saa7134: I feel better now.  Ok, here are the good news:
[   46.104265] saa7134: You can use the card=<nr> insmod option to specify
[   46.104266] saa7134: which board do you have.  The list:
[   46.104780] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[   46.104900] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   46.105135] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   46.105369] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   46.105603] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   46.105784] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   46.105964] saa7134:   card=6 -> Tevion MD 9717                          
[   46.106084] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[   46.106324] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[   46.106504] saa7134:   card=9 -> Medion 5044                             
[   46.106624] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[   46.106744] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[   46.106925] saa7134:   card=12 -> Medion 7134                              16be:0003
[   46.107106] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[   46.107226] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[   46.107406] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[   46.107587] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[   46.107874] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[   46.108055] saa7134:   card=18 -> BMK MPEX No Tuner                       
[   46.108175] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[   46.108355] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[   46.108536] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[   46.108717] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   46.108897] saa7134:   card=23 -> BMK MPEX Tuner                          
[   46.109017] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[   46.109198] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[   46.109379] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[   46.109559] saa7134:   card=27 -> Manli MuchTV M-TV002/Behold TV 403 FM   
[   46.109679] saa7134:   card=28 -> Manli MuchTV M-TV001/Behold TV 401      
[   46.109799] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[   46.109980] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[   46.110160] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[   46.110344] saa7134:   card=32 -> AVACS SmartTV                           
[   46.110464] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[   46.110644] saa7134:   card=34 -> Noval Prime TV 7133                     
[   46.110764] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[   46.110945] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[   46.111125] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[   46.111245] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[   46.111426] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212
[   46.111660] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[   46.111841] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[   46.112021] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[   46.112141] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[   46.112261] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[   46.112381] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[   46.112562] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[   46.112742] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[   46.112923] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[   46.113104] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[   46.113285] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[   46.113465] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[   46.113646] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[   46.114701] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[   46.114882] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[   46.115223] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[   46.115457] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[   46.115638] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[   46.115819] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[   46.116159] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[   46.116279] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[   46.116567] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[   46.116748] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[   46.116867] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[   46.116987] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[   46.117168] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[   46.117288] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[   46.117408] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[   46.117588] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[   46.117769] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[   46.117950] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[   46.118130] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[   46.118313] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[   46.118494] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[   46.118675] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[   46.118855] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[   46.119036] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[   46.119217] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   46.119397] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862 1043:4857
[   46.119631] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[   46.119751] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[   46.119932] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[   46.120113] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231
[   46.120293] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[   46.120474] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[   46.120655] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[   46.120889] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[   46.121123] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[   46.121304] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[   46.121485] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[   46.121666] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
[   46.121900] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[   46.122080] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[   46.122263] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[   46.122444] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 4e42:3502
[   46.122732] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[   46.122913] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008
[   46.123147] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[   46.123381] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[   46.123562] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[   46.123742] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[   46.123923] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[   46.124104] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[   46.124285] saa7134:   card=103 -> Compro Videomate DVB-T200A              
[   46.124405] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6701
[   46.124586] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[   46.124766] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[   46.125054] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[   46.125235] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[   46.125415] saa7134:   card=109 -> Philips Tiger - S Reference design      
[   46.125536] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[   46.125716] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[   46.125897] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[   46.126078] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[   46.126261] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[   46.126442] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[   46.126622] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
[   46.126803] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
[   46.126985] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   46.127069] saa7130[0]: board init: gpio is 13000
[   46.230784] saa7130[0]: Huh, no eeprom present (err=-5)?
[   46.230921] saa7130[0]: registered device video0 [v4l2]
[   46.231013] saa7130[0]: registered device vbi0
[   46.897800] saa7134 ALSA driver for DMA sound loaded
[   46.897895] saa7130[0]/alsa: saa7130[0] at 0xf5005000 irq 21 registered as card -2
[   47.661784] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   47.661857] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [AAZA] -> GSI 22 (level, low) -> IRQ 17
[   47.662058] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   48.576929] cdc_acm 1-7:3.1: ttyACM0: USB ACM device
[   48.592985] cdc_acm 1-7:3.3: ttyACM1: USB ACM device
[   48.600930] usbcore: registered new interface driver cdc_acm
[   48.601002] /build/buildd/linux-2.6.24/drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
[   48.820744] usb0: register 'cdc_ether' at usb-0000:00:0b.0-7, CDC Ethernet Device, 02:80:37:11:03:00
[   48.820836] usbcore: registered new interface driver cdc_ether
[   49.126623] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   49.681528] parport_pc 00:09: reported by Plug and Play ACPI
[   49.681668] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   51.807383] lp0: using parport0 (interrupt-driven).
[   51.893357] Adding 498004k swap on /dev/sda2.  Priority:-1 extents:1 across:498004k
[   52.304136] EXT3 FS on sda3, internal journal
[   54.142652] kjournald starting.  Commit interval 5 seconds
[   54.142814] EXT3 FS on sda1, internal journal
[   54.142818] EXT3-fs: mounted filesystem with ordered data mode.
[   54.181252] kjournald starting.  Commit interval 5 seconds
[   54.185855] EXT3 FS on sdb1, internal journal
[   54.185858] EXT3-fs: mounted filesystem with ordered data mode.
[   66.417864] No dock devices found.
[   66.826318] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (1 cpu cores) (version 2.20.00)
[   66.826350] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
[   66.826352] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
[   67.792970] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   67.792976] apm: overridden by ACPI.
[   67.919987] ppdev: user-space parallel port driver
[   68.233445] audit(1224325804.539:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5369 profile="/usr/sbin/cupsd" namespace="default"
[  124.313137] Marking TSC unstable due to: cpufreq changes.
[  124.320120] Time: acpi_pm clocksource has been installed.
[  124.516081] Clocksource tsc unstable (delta = -90287782 ns)
[  125.807634] NET: Registered protocol family 17
[   70.834479] Bluetooth: Core ver 2.11
[   70.846511] NET: Registered protocol family 31
[   70.846517] Bluetooth: HCI device and connection manager initialized
[   70.846521] Bluetooth: HCI socket layer initialized
[   70.886753] Bluetooth: L2CAP ver 2.9
[   70.886758] Bluetooth: L2CAP socket layer initialized
[   70.951426] Bluetooth: RFCOMM socket layer initialized
[   70.951443] Bluetooth: RFCOMM TTY layer initialized
[   70.951445] Bluetooth: RFCOMM ver 1.8
[  152.949672] NET: Registered protocol family 10
[  152.950479] lo: Disabled Privacy Extensions
[   92.554128] eth0: no IPv6 routers present
[  924.511758] usb 2-8: new high speed USB device using ehci_hcd and address 4
[  924.655045] usb 2-8: configuration #1 chosen from 1 choice
[  924.816625] usbcore: registered new interface driver libusual
[  924.878421] Initializing USB Mass Storage driver...
[  924.881052] scsi6 : SCSI emulation for USB Mass Storage devices
[  924.887759] usbcore: registered new interface driver usb-storage
[  924.888281] USB Mass Storage support registered.
[  924.888785] usb-storage: device found at 4
[  924.888790] usb-storage: waiting for device to settle before scanning
[  929.885925] usb-storage: device scan complete
[  929.888151] scsi 6:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[  932.009434] sd 6:0:0:0: [sdc] 15646720 512-byte hardware sectors (8011 MB)
[  932.012305] sd 6:0:0:0: [sdc] Write Protect is off
[  932.012312] sd 6:0:0:0: [sdc] Mode Sense: 23 00 00 00
[  932.012317] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[  932.023431] sd 6:0:0:0: [sdc] 15646720 512-byte hardware sectors (8011 MB)
[  932.026301] sd 6:0:0:0: [sdc] Write Protect is off
[  932.026308] sd 6:0:0:0: [sdc] Mode Sense: 23 00 00 00
[  932.026311] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[  932.026321]  sdc: sdc1
[  932.028563] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[  932.028660] sd 6:0:0:0: Attached scsi generic sg4 type 0
[  978.837893] cdrom: This disc doesn't have any tracks I recognize!
pumex@pumex-desktop:~$ 

```

---

### Post by geirha on 2008-10-18
You have a tv-card. My instincts tell me it may be related. Let's try disabling it and see if you still experience freezing. Add "blacklist saa7134" to /etc/modprobe.d/blacklist.

The following command will add it to the end of the file. Don't forget the -a option, or the file will be truncated. You may of course edit it manually by using your favourite editor too.
```
echo "blacklist saa7134" | sudo tee -a /etc/modprobe.d/blacklist
```

Reboot and check that the saa7134 module doesn't get loaded by looking at the output of dmesg, then see if it freezes like before.

---

### Post by pumex1990 on 2008-10-18
Unfortunatelly, it didn't help.
I first added it to the blacklist, just like you told me, and it freezed. Than, just to be sure, I removed the TVCard completly out of my computer, and it also freezed. What's more, now it freezed also in the 'GNOME emergency mode'

My new dmesg:

```
000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 260081
[    0.000000] Kernel command line: root=UUID=d2cf16d6-fbdc-42ef-8b21-6b300652e81e ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1808.384 MHz processor.
[   26.789752] spurious 8259A interrupt: IRQ7.
[   26.791417] Console: colour VGA+ 80x25
[   26.791421] console [tty0] enabled
[   26.791767] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   26.792157] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   26.815875] Memory: 1027344k/1048512k available (2177k kernel code, 20464k reserved, 1006k data, 368k init, 131008k highmem)
[   26.815884] virtual kernel memory layout:
[   26.815885]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   26.815886]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   26.815887]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   26.815888]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   26.815890]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   26.815891]       .data : 0xc0320514 - 0xc041bdc4   (1006 kB)
[   26.815892]       .text : 0xc0100000 - 0xc0320514   (2177 kB)
[   26.815895] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   26.815931] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   26.895924] Calibrating delay using timer specific routine.. 3621.35 BogoMIPS (lpj=7242706)
[   26.895950] Security Framework initialized
[   26.895956] SELinux:  Disabled at boot.
[   26.895971] AppArmor: AppArmor initialized
[   26.895975] Failure registering capabilities with primary security module.
[   26.895982] Mount-cache hash table entries: 512
[   26.896094] Initializing cgroup subsys ns
[   26.896097] Initializing cgroup subsys cpuacct
[   26.896107] CPU: After generic identify, caps: 078bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000001d 00000000
[   26.896116] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   26.896118] CPU: L2 Cache: 512K (64 bytes/line)
[   26.896121] CPU: After all inits, caps: 078bfbff ebd3fbff 00000000 00020410 00002001 00000000 0000001d 00000000
[   26.896131] Compat vDSO mapped to ffffe000.
[   26.896141] Checking 'hlt' instruction... OK.
[   26.912192] SMP alternatives: switching to UP code
[   26.913282] Freeing SMP alternatives: 11k freed
[   26.913392] Early unpacking initramfs... done
[   27.251389] ACPI: Core revision 20070126
[   27.251452] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   27.255846] CPU0: AMD Athlon(tm) 64 Processor 3000+ stepping 02
[   27.255858] Total of 1 processors activated (3621.35 BogoMIPS).
[   27.256193] ENABLING IO-APIC IRQs
[   27.256433] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   27.403741] Brought up 1 CPUs
[   27.403767] CPU0 attaching sched-domain:
[   27.403769]  domain 0: span 01
[   27.403771]   groups: 01
[   27.403912] net_namespace: 64 bytes
[   27.403917] Booting paravirtualized kernel on bare hardware
[   27.404378] Time: 11:19:20  Date: 10/18/08
[   27.404397] NET: Registered protocol family 16
[   27.404555] EISA bus registered
[   27.404590] ACPI: bus type pci registered
[   27.418127] PCI: PCI BIOS revision 3.00 entry at 0xfb060, last bus=2
[   27.418129] PCI: Using configuration type 1
[   27.418133] Setting up standard PCI resources
[   27.422936] ACPI: EC: Look up EC in DSDT
[   27.429175] ACPI: Interpreter enabled
[   27.429177] ACPI: (supports S0 S1 S4 S5)
[   27.429189] ACPI: Using IOAPIC for interrupt routing
[   27.438187] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   27.439720] PCI: Transparent bridge - 0000:00:10.0
[   27.439743] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   27.440009] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   27.514973] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   27.515145] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   27.515317] ACPI: PCI Interrupt Link [LNK3] (IRQs *5 7 9 10 11 14 15)
[   27.515486] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   27.515661] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 *11 14 15)
[   27.515831] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   27.516000] ACPI: PCI Interrupt Link [LNK7] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   27.516170] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   27.516341] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 *11 14 15)
[   27.516511] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   27.516686] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 9 10 11 14 15)
[   27.516856] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   27.517027] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 *10 11 14 15)
[   27.517196] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   27.517367] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   27.517538] ACPI: PCI Interrupt Link [LSMB] (IRQs *5 7 9 10 11 14 15)
[   27.517713] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 *10 11 14 15)
[   27.517882] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[   27.518053] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 10 *11 14 15)
[   27.518227] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 *10 11 14 15)
[   27.518436] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   27.518637] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   27.518836] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   27.519035] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   27.519234] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0
[   27.519433] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[   27.519633] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0, disabled.
[   27.519836] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[   27.520036] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   27.520236] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   27.520436] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   27.520641] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[   27.520842] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[   27.521042] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[   27.521243] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   27.521444] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   27.521645] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   27.521847] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[   27.522050] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   27.522252] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   27.522453] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   27.522575] Linux Plug and Play Support v0.97 (c) Adam Belay
[   27.522602] pnp: PnP ACPI init
[   27.522609] ACPI: bus type pnp registered
[   27.527136] pnp: PnP ACPI: found 13 devices
[   27.527138] ACPI: ACPI bus type pnp unregistered
[   27.527142] PnPBIOS: Disabled by ACPI PNP
[   27.527326] PCI: Using ACPI for IRQ routing
[   27.527330] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   27.607633] NET: Registered protocol family 8
[   27.607635] NET: Registered protocol family 20
[   27.607694] AppArmor: AppArmor Filesystem Enabled
[   27.611605] Time: tsc clocksource has been installed.
[   27.619631] system 00:01: ioport range 0x1000-0x107f has been reserved
[   27.619634] system 00:01: ioport range 0x1080-0x10ff has been reserved
[   27.619637] system 00:01: ioport range 0x1400-0x147f has been reserved
[   27.619640] system 00:01: ioport range 0x1480-0x14ff has been reserved
[   27.619642] system 00:01: ioport range 0x1800-0x187f has been reserved
[   27.619645] system 00:01: ioport range 0x1880-0x18ff has been reserved
[   27.619648] system 00:01: ioport range 0x2000-0x207f has been reserved
[   27.619651] system 00:01: ioport range 0x2080-0x20ff has been reserved
[   27.619654] system 00:01: iomem range 0xfefe0000-0xfefe01ff could not be reserved
[   27.619657] system 00:01: iomem range 0x0-0x0 could not be reserved
[   27.619662] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   27.619665] system 00:02: ioport range 0x800-0x87f has been reserved
[   27.619668] system 00:02: ioport range 0x295-0x314 has been reserved
[   27.619670] system 00:02: ioport range 0x290-0x294 has been reserved
[   27.619678] system 00:0b: iomem range 0xf0000000-0xf1ffffff could not be reserved
[   27.619684] system 00:0c: iomem range 0xf0000-0xf3fff could not be reserved
[   27.619687] system 00:0c: iomem range 0xf4000-0xf7fff could not be reserved
[   27.619690] system 00:0c: iomem range 0xf8000-0xfbfff could not be reserved
[   27.619692] system 00:0c: iomem range 0xfc000-0xfffff could not be reserved
[   27.619695] system 00:0c: iomem range 0x3fff0000-0x3fffffff could not be reserved
[   27.619698] system 00:0c: iomem range 0xffff0000-0xffffffff could not be reserved
[   27.619701] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   27.619704] system 00:0c: iomem range 0x100000-0x3ffeffff could not be reserved
[   27.619707] system 00:0c: iomem range 0x0-0x0 could not be reserved
[   27.619709] system 00:0c: iomem range 0xfec00000-0xfec00fff could not be reserved
[   27.619712] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[   27.650063] PCI: Bridge: 0000:00:04.0
[   27.650066]   IO window: a000-afff
[   27.650069]   MEM window: f2000000-f4ffffff
[   27.650072]   PREFETCH window: e0000000-efffffff
[   27.650074] PCI: Bridge: 0000:00:10.0
[   27.650076]   IO window: disabled.
[   27.650081]   MEM window: f5000000-f50fffff
[   27.650085]   PREFETCH window: disabled.
[   27.650101] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   27.650115] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   27.650126] NET: Registered protocol family 2
[   27.687638] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   27.687921] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   27.688758] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   27.689178] TCP: Hash tables configured (established 131072 bind 65536)
[   27.689180] TCP reno registered
[   27.699691] checking if image is initramfs... it is
[   28.151360] Switched to high resolution mode on CPU 0
[   28.349320] Freeing initrd memory: 7330k freed
[   28.349850] audit: initializing netlink socket (disabled)
[   28.349862] audit(1224328760.432:1): initialized
[   28.349989] highmem bounce pool size: 64 pages
[   28.351555] VFS: Disk quotas dquot_6.5.1
[   28.351619] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   28.351742] io scheduler noop registered
[   28.351744] io scheduler anticipatory registered
[   28.351746] io scheduler deadline registered
[   28.351755] io scheduler cfq registered (default)
[   28.351770] pci 0000:00:00.0: Enabling HT MSI Mapping
[   28.351803] pci 0000:00:04.0: Enabling HT MSI Mapping
[   28.351833] pci 0000:00:09.0: Enabling HT MSI Mapping
[   28.367264] pci 0000:00:0e.0: Enabling HT MSI Mapping
[   28.367283] pci 0000:00:0f.0: Enabling HT MSI Mapping
[   28.367299] pci 0000:00:10.0: Enabling HT MSI Mapping
[   28.367318] pci 0000:00:10.1: Enabling HT MSI Mapping
[   28.367342] Boot video device is 0000:02:00.0
[   28.367436] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   28.367462] assign_interrupt_mode Found MSI capability
[   28.367483] Allocate Port Service[0000:00:04.0:pcie00]
[   28.367674] isapnp: Scanning for PnP cards...
[   28.722016] isapnp: No Plug & Play device found
[   28.746410] Real Time Clock Driver v1.12ac
[   28.746505] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   28.746662] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.747521] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   28.748171] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   28.748228] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   28.748304] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   28.748307] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   28.748409] serio: i8042 KBD port at 0x60,0x64 irq 1
[   28.759089] mice: PS/2 mouse device common for all mice
[   28.759183] EISA: Probing bus 0 at eisa.0
[   28.759191] Cannot allocate resource for EISA slot 1
[   28.759193] Cannot allocate resource for EISA slot 2
[   28.759221] EISA: Detected 0 cards.
[   28.759224] cpuidle: using governor ladder
[   28.759225] cpuidle: using governor menu
[   28.759304] NET: Registered protocol family 1
[   28.759324] Using IPI No-Shortcut mode
[   28.759350] registered taskstats version 1
[   28.759461]   Magic number: 12:812:327
[   28.759634] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   28.759636] EDD information not available.
[   28.759862] Freeing unused kernel memory: 368k freed
[   28.787023] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   30.024302] fuse init (API version 7.9)
[   30.047581] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   31.133061] usbcore: registered new interface driver usbfs
[   31.133087] usbcore: registered new interface driver hub
[   31.140719] usbcore: registered new device driver usb
[   31.154024] SCSI subsystem initialized
[   31.189776] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   31.190177] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   31.190184] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
[   31.190198] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   31.190202] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[   31.190471] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[   31.190490] ohci_hcd 0000:00:0b.0: irq 16, io mem 0xf5105000
[   31.229792] libata version 3.00 loaded.
[   31.247924] usb usb1: configuration #1 chosen from 1 choice
[   31.247951] hub 1-0:1.0: USB hub found
[   31.247960] hub 1-0:1.0: 8 ports detected
[   31.350275] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   31.350283] ACPI: PCI Interrupt 0000:00:0b.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 17
[   31.350296] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   31.350300] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[   31.350322] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[   31.350359] ehci_hcd 0000:00:0b.1: debug port 1
[   31.350366] PCI: cache line size of 64 is not supported by device 0000:00:0b.1
[   31.350376] ehci_hcd 0000:00:0b.1: irq 17, io mem 0xf5106000
[   31.361741] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   31.361880] usb usb2: configuration #1 chosen from 1 choice
[   31.361902] hub 2-0:1.0: USB hub found
[   31.361907] hub 2-0:1.0: 8 ports detected
[   31.385793] Floppy drive(s): fd0 is 1.44M
[   31.407855] FDC 0 is a post-1991 82077
[   31.465849] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   31.466216] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[   31.466222] ACPI: PCI Interrupt 0000:00:14.0[A] -> Link [APCH] -> GSI 21 (level, low) -> IRQ 18
[   31.466230] PCI: Setting latency timer of device 0000:00:14.0 to 64
[   31.985851] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:0f:ea:5a:c1:e7
[   31.985857] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
[   31.988761] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   31.988769] ACPI: PCI Interrupt 0000:01:0e.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 19
[   32.038553] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[f5004000-f50047ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   32.040953] pata_amd 0000:00:0d.0: version 0.3.10
[   32.041018] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   32.045407] scsi0 : pata_amd
[   32.047849] scsi1 : pata_amd
[   32.048594] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   32.048597] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   32.365219] usb 2-2: new high speed USB device using ehci_hcd and address 3
[   32.499624] usb 2-2: configuration #1 chosen from 1 choice
[   32.529628] ata1.00: ATAPI: LG       DVD-ROM DRD-8160B, 1.01, max UDMA/33
[   32.529649] ata1.01: ATAPI: PIONEER DVD-RW  DVR-110D, 1.17, max UDMA/66
[   32.701467] ata1.00: configured for UDMA/33
[   32.873425] ata1.01: configured for UDMA/66
[   32.976912] usb 2-8: new high speed USB device using ehci_hcd and address 5
[   33.053335] ata2.00: HPA unlocked: 117229295 -> 117231408, native 117231408
[   33.053339] ata2.00: ATA-5: WDC WD600AB-00CBA1, 04.07B04, max UDMA/100
[   33.053342] ata2.00: 117231408 sectors, multi 16: LBA 
[   33.053692] ata2.01: ATA-5: ST340016A, 3.75, max UDMA/100
[   33.053694] ata2.01: 78165360 sectors, multi 16: LBA 
[   33.070201] ata2.00: configured for UDMA/100
[   33.085428] ata2.01: configured for UDMA/100
[   33.085896] scsi 0:0:0:0: CD-ROM            LG       DVD-ROM DRD8160B 1.01 PQ: 0 ANSI: 5
[   33.092363] scsi 0:0:1:0: CD-ROM            PIONEER  DVD-RW  DVR-110D 1.17 PQ: 0 ANSI: 5
[   33.092657] scsi 1:0:0:0: Direct-Access     ATA      WDC WD600AB-00CB 04.0 PQ: 0 ANSI: 5
[   33.092943] scsi 1:0:1:0: Direct-Access     ATA      ST340016A        3.75 PQ: 0 ANSI: 5
[   33.095345] sata_nv 0000:00:0e.0: version 3.5
[   33.095698] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[   33.095705] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 20
[   33.095747] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   33.097384] scsi2 : sata_nv
[   33.097617] scsi3 : sata_nv
[   33.097780] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd400 irq 20
[   33.097784] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd408 irq 20
[   33.118664] usb 2-8: configuration #1 chosen from 1 choice
[   33.320823] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000fea00005ae8d2]
[   33.408700] ata3: SATA link down (SStatus 0 SControl 300)
[   33.420685] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   33.638639] usb 1-1: configuration #1 chosen from 1 choice
[   33.728541] ata4: SATA link down (SStatus 0 SControl 300)
[   33.740099] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
[   33.740103] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 16
[   33.740148] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   33.740214] scsi4 : sata_nv
[   33.740471] scsi5 : sata_nv
[   33.740623] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc000 irq 16
[   33.740626] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc008 irq 16
[   33.944426] usb 1-7: new full speed USB device using ohci_hcd and address 3
[   34.052377] ata5: SATA link down (SStatus 0 SControl 300)
[   34.248324] usb 1-7: configuration #3 chosen from 1 choice
[   34.308195] usbcore: registered new interface driver libusual
[   34.308291] usbcore: registered new interface driver hiddev
[   34.314845] Initializing USB Mass Storage driver...
[   34.316044] scsi6 : SCSI emulation for USB Mass Storage devices
[   34.317348] usb-storage: device found at 5
[   34.317350] usb-storage: waiting for device to settle before scanning
[   34.324526] input: Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00 as /devices/pci0000:00/0000:00:0b.0/usb1/1-1/1-1:1.0/input/input2
[   34.340315] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse&#65533; 1.00] on usb-0000:00:0b.0-1
[   34.340344] usbcore: registered new interface driver usbhid
[   34.340348] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   34.340478] usbcore: registered new interface driver usb-storage
[   34.340481] USB Mass Storage support registered.
[   34.372231] ata6: SATA link down (SStatus 0 SControl 300)
[   34.405278] Driver 'sr' needs updating - please use bus_type methods
[   34.409161] sr0: scsi3-mmc drive: 0x/48x cd/rw xa/form2 cdda tray
[   34.409167] Uniform CD-ROM driver Revision: 3.20
[   34.409212] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   34.412809] Driver 'sd' needs updating - please use bus_type methods
[   34.440222] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   34.440272] sr 0:0:1:0: Attached scsi CD-ROM sr1
[   34.440667] sd 1:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[   34.444793] sd 1:0:0:0: [sda] Write Protect is off
[   34.444797] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.447602] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.447655] sd 1:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[   34.447665] sd 1:0:0:0: [sda] Write Protect is off
[   34.447668] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   34.447681] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.447685]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[   34.450641] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   34.450656] sd 1:0:0:0: Attached scsi generic sg2 type 0
[   34.450671] scsi 1:0:1:0: Attached scsi generic sg3 type 0
[   34.463756]  sda1 sda2 sda3
[   34.483341] sd 1:0:0:0: [sda] Attached SCSI disk
[   34.483407] sd 1:0:1:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
[   34.483419] sd 1:0:1:0: [sdb] Write Protect is off
[   34.483421] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   34.483436] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.483473] sd 1:0:1:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
[   34.483482] sd 1:0:1:0: [sdb] Write Protect is off
[   34.483484] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   34.483497] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   34.483501]  sdb: sdb1
[   34.493360] sd 1:0:1:0: [sdb] Attached SCSI disk
[   34.862661] Attempting manual resume
[   34.862665] swsusp: Resume From Partition 8:2
[   34.862667] PM: Checking swsusp image.
[   34.862834] PM: Resume from disk failed.
[   34.878171] EXT3-fs: INFO: recovery required on readonly filesystem.
[   34.878176] EXT3-fs: write access will be enabled during recovery.
[   34.990874] kjournald starting.  Commit interval 5 seconds
[   34.990889] EXT3-fs: sda3: orphan cleanup on readonly fs
[   34.990895] ext3_orphan_cleanup: deleting unreferenced inode 131084
[   34.990920] EXT3-fs: sda3: 1 orphan inode deleted
[   34.990922] EXT3-fs: recovery complete.
[   34.992138] EXT3-fs: mounted filesystem with ordered data mode.
[   39.313989] usb-storage: device scan complete
[   39.315106] scsi 6:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[   39.319461] sd 6:0:0:0: [sdc] 15646720 512-byte hardware sectors (8011 MB)
[   39.322336] sd 6:0:0:0: [sdc] Write Protect is off
[   39.322339] sd 6:0:0:0: [sdc] Mode Sense: 23 00 00 00
[   39.322341] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   39.332454] sd 6:0:0:0: [sdc] 15646720 512-byte hardware sectors (8011 MB)
[   39.335329] sd 6:0:0:0: [sdc] Write Protect is off
[   39.335331] sd 6:0:0:0: [sdc] Mode Sense: 23 00 00 00
[   39.335333] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[   39.335336]  sdc: sdc1
[   39.337879] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[   39.337906] sd 6:0:0:0: Attached scsi generic sg4 type 0
[   46.342255] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   46.374483] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   46.682160] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   46.682177] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c80
[   46.746176] input: Power Button (FF) as /devices/virtual/input/input3
[   46.758017] ACPI: Power Button (FF) [PWRF]
[   46.758091] input: Power Button (CM) as /devices/virtual/input/input4
[   46.774000] ACPI: Power Button (CM) [PWRB]
[   47.057892] Linux agpgart interface v0.102
[   49.788212] cdc_acm 1-7:3.1: ttyACM0: USB ACM device
[   49.796212] cdc_acm 1-7:3.3: ttyACM1: USB ACM device
[   49.808630] usbcore: registered new interface driver cdc_acm
[   49.808635] /build/buildd/linux-2.6.24/drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
[   50.106130] usb0: register 'cdc_ether' at usb-0000:00:0b.0-7, CDC Ethernet Device, 02:80:37:11:03:00
[   50.106147] usbcore: registered new interface driver cdc_ether
[   50.170660] usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x03F0 pid 0x3D17
[   50.170682] usbcore: registered new interface driver usblp
[   51.723662] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   52.161183] parport_pc 00:09: reported by Plug and Play ACPI
[   52.161257] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   52.510113] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   52.510118] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [AAZA] -> GSI 22 (level, low) -> IRQ 17
[   52.510140] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   54.250755] lp0: using parport0 (interrupt-driven).
[   54.335850] Adding 498004k swap on /dev/sda2.  Priority:-1 extents:1 across:498004k
[   54.622966] usblp0: removed
[   54.904968] EXT3 FS on sda3, internal journal
[   56.375246] kjournald starting.  Commit interval 5 seconds
[   56.375404] EXT3 FS on sda1, internal journal
[   56.375409] EXT3-fs: mounted filesystem with ordered data mode.
[   56.410349] kjournald starting.  Commit interval 5 seconds
[   56.417377] EXT3 FS on sdb1, internal journal
[   56.417380] EXT3-fs: mounted filesystem with ordered data mode.
[   57.085967] No dock devices found.
[   57.484047] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (1 cpu cores) (version 2.20.00)
[   57.484080] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
[   57.484082] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
[   58.250058] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   58.250064] apm: overridden by ACPI.
[   58.366992] ppdev: user-space parallel port driver
[   58.650566] audit(1224328791.518:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5263 profile="/usr/sbin/cupsd" namespace="default"
[   59.755508] NET: Registered protocol family 17
[   60.662695] Bluetooth: Core ver 2.11
[   60.663248] NET: Registered protocol family 31
[   60.663253] Bluetooth: HCI device and connection manager initialized
[   60.663257] Bluetooth: HCI socket layer initialized
[   60.686525] Bluetooth: L2CAP ver 2.9
[   60.686530] Bluetooth: L2CAP socket layer initialized
[   60.740351] Bluetooth: RFCOMM socket layer initialized
[   60.740367] Bluetooth: RFCOMM TTY layer initialized
[   60.740369] Bluetooth: RFCOMM ver 1.8
[  110.460312] Marking TSC unstable due to: cpufreq changes.
[  110.469398] Time: acpi_pm clocksource has been installed.
[  110.740163] Clocksource tsc unstable (delta = -124508559 ns)
[  139.877184] NET: Registered protocol family 10
[  139.877875] lo: Disabled Privacy Extensions
[   86.409170] eth0: no IPv6 routers present
pumex@pumex-desktop:~$ 

```

---

### Post by pumex1990 on 2008-10-18
I've noticed a new thing; if i am using firefox and click the scroll of the mouse to rewind the page (not scrollig, but click and turn mouse down to do it fast) - it freeze, almost always.

I hope it will be helpful :)

---

### Post by geirha on 2008-10-18
Have you run a memtest btw? There should be a grub boot option called memtest86+.

Also check xorgs previous log file, /var/log/Xorg.0.log.old it may contain some clues as well.

I'm fairly clueless as to what's causing this. It sounds odd.

---

### Post by pumex1990 on 2008-10-18
I run memtest and it showed no errors. But while I was logging in after running memtes, my computer freezed, and after reebot I didn't see a welcome screen, but a white letters on black screen:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter help for  alist of built-in command.

(initramfs) [       38.785562] sd 4:0:0:0: [sdc] Assuming drive cache: write through [    38.798554] sd 4:0ming drive :0:0: [sdc] Assuming drive cache: write through.


So now I can't even log in my Ubuntu.

What should I do? :)

---

### Post by pumex1990 on 2008-10-18
And one more question: do you think, that installing Ubuntu 8.10 Beta can solve my problem? Should I try to do this?

---

### Post by cicatrix1 on 2008-10-18
Do you have an ATI video card?

I ask because you mentioned the firefox scroll bar, which used to crash my Thinkpad T60 (with ATI Mobile Radeon X1300), before I turned off compiz.  Mine wouldn't freeze but crash my X, so it might not be the same thing.

The crashing still happens without compiz, by the way, it just doesn't seem to happen as frequently.

---

### Post by pumex1990 on 2008-10-18
Hm, now computer froze while I was using LiveCD... so it must be harware's fault. It's strange, because it never froze on LiveCD or Windows before...

What should I check, and how now?

---

### Post by pumex1990 on 2008-10-18
Hm, I checked, and I have still got warranty on my computer, so I'll just take it to service, and let the find out what's wrong :)Probably it's motherboard fault, because ram and hard drive are ok.

Thanks to everyone for your help!

---

### Post by geirha on 2008-10-18
Searching for "freeze" at these forums gives alot of results. There's way too many posts to read, but it seems like it's related to some drivers in the 2.6.24-kernels. [This](http://ubuntuforums.org/showthread.php?t=765510&page=48) 48 page long thread seems somewhat related, and on the last post there, a user says blacklisting pcspkr makes the system stop freezing. It doesn't sound like the exact same problem as you have, but worth a try in my opinion.

Other threads mentioned network drivers as the cause of the problems, so it's probably some driver that is causing this, and not a hardware fault, since windows is still working well..?

Also, it is possible that it's fixed in a newer kernel, so at least trying the 8.10 beta live CD to see if it freezes is worth a shot.

---

### Post by pumex1990 on 2008-10-20
> **geirha said:**
> 
Other threads mentioned network drivers as the cause of the problems, so it's probably some driver that is causing this, and not a hardware fault, since windows is still working well..?


But Windows also started to freeze, so it must be hardware fault :) I'll take my computer to the service today, and I'll let you know what they said ;]

---

### Post by mariuszkopec on 2008-10-20
I also have observed symptoms of freezing (or at least not responding) Ubuntu (8.04.01) but it seems it has something to do with graphics. Eg. when the screensaver runs for a longer time (over a weekend) the computer stops respondnig. The screensaver apparently runs, but I can't stop it neither by mouse nor by keyboard. The combinations Ctrl-Alt-F[1-7] as well as Ctrl-Alt-Del and Ctrl-Alt-Backspace doesn't work. As the remote login is also not possible (no response to ssh) the only solution is the reset button. I didn't have such problems with the previous versions of Ubuntu (6 and 7).

---

