---
title: "upgrade 9.04 - system locked, x-server ruined"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by stephan0h on 2009-05-04
hi group

this is bad: after upgrading to kubuntu 9.04 only garbage is displayed on my screen - i can'T login anymore. i even can't open a text-mode session with <ctrl><Fn> - in fact the keyboard does not react. i tried to use recovery-mode - but unfortunately it does not let me in as root with my sudo-password. i guess something went wrong with x-windows. (is it a problem, i have an old ati-card?) but without being able to login, how can i repair it?

thanks,
stephan

---

### Post by stephan0h on 2009-05-04
ok, luckily i could login via ssh (despite the fact this is really bad) :(

here's the last portion of my sys.log:
(it says something about x-server dying.)

```

mily 10
May  4 15:41:42 rechenmonster kernel: [   17.333226] lo: Disabled Privacy Extensions
May  4 15:41:42 rechenmonster kernel: [   17.903291] ACPI: WMI: Mapper loaded
May  4 15:41:47 rechenmonster exportfs[5312]: /etc/exports [2]: Neither 'subtree_check' or 'no_subtree_check' specified for export "*:/opt/ltsp".   Assuming default behaviour ('no_subtree_check').   NOTE: this default has changed since nfs-utils version 1.0.x
May  4 15:41:47 rechenmonster kernel: [   24.028089] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
May  4 15:41:47 rechenmonster kernel: [   24.043370] NFSD: starting 90-second grace period
May  4 15:41:49 rechenmonster xinetd[5439]: Reading included configuration file: /etc/xinetd.d/chargen [file=/etc/xinetd.conf] [line=14]
May  4 15:41:49 rechenmonster xinetd[5439]: Reading included configuration file: /etc/xinetd.d/daytime [file=/etc/xinetd.d/daytime] [line=28]
May  4 15:41:49 rechenmonster xinetd[5439]: Reading included configuration file: /etc/xinetd.d/discard [file=/etc/xinetd.d/discard] [line=26]
May  4 15:41:49 rechenmonster xinetd[5439]: Reading included configuration file: /etc/xinetd.d/echo [file=/etc/xinetd.d/echo] [line=25]
May  4 15:41:49 rechenmonster xinetd[5439]: Reading included configuration file: /etc/xinetd.d/swat [file=/etc/xinetd.d/swat] [line=26]
May  4 15:41:49 rechenmonster xinetd[5439]: Server /usr/sbin/swat is not executable [file=/etc/xinetd.d/swat] [line=12]
May  4 15:41:49 rechenmonster xinetd[5439]: Error parsing attribute server - DISABLING SERVICE [file=/etc/xinetd.d/swat] [line=12]
May  4 15:41:49 rechenmonster xinetd[5439]: Reading included configuration file: /etc/xinetd.d/time [file=/etc/xinetd.d/time] [line=17]
May  4 15:41:49 rechenmonster xinetd[5439]: removing chargen
May  4 15:41:49 rechenmonster xinetd[5439]: removing chargen
May  4 15:41:49 rechenmonster xinetd[5439]: removing daytime
May  4 15:41:49 rechenmonster xinetd[5439]: removing daytime
May  4 15:41:49 rechenmonster xinetd[5439]: removing discard
May  4 15:41:49 rechenmonster xinetd[5439]: removing discard
May  4 15:41:49 rechenmonster xinetd[5439]: removing echo
May  4 15:41:49 rechenmonster xinetd[5439]: removing echo
May  4 15:41:49 rechenmonster xinetd[5439]: removing time
May  4 15:41:49 rechenmonster xinetd[5439]: removing time
May  4 15:41:49 rechenmonster xinetd[5439]: Must specify a server in swat
May  4 15:41:49 rechenmonster xinetd[5439]: xinetd Version 2.3.14 started with libwrap loadavg options compiled in.
May  4 15:41:49 rechenmonster xinetd[5439]: Started working: 0 available services
May  4 15:41:49 rechenmonster acpid: client connected from 5602[106:110]
May  4 15:41:50 rechenmonster bluetoothd[5621]: Bluetooth daemon
May  4 15:41:50 rechenmonster kernel: [   26.643052] Bluetooth: Core ver 2.13
May  4 15:41:50 rechenmonster kernel: [   26.644123] NET: Registered protocol family 31
May  4 15:41:50 rechenmonster kernel: [   26.644129] Bluetooth: HCI device and connection manager initialized
May  4 15:41:50 rechenmonster kernel: [   26.644134] Bluetooth: HCI socket layer initialized
May  4 15:41:50 rechenmonster bluetoothd[5621]: Starting SDP server
May  4 15:41:50 rechenmonster kernel: [   26.669325] Bluetooth: L2CAP ver 2.11
May  4 15:41:50 rechenmonster kernel: [   26.669332] Bluetooth: L2CAP socket layer initialized
May  4 15:41:50 rechenmonster bluetoothd[5621]: Starting experimental netlink support
May  4 15:41:50 rechenmonster bluetoothd[5621]: Failed to find Bluetooth netlink family
May  4 15:41:50 rechenmonster kernel: [   26.686538] Bluetooth: SCO (Voice Link) ver 0.6
May  4 15:41:50 rechenmonster kernel: [   26.686544] Bluetooth: SCO socket layer initialized
May  4 15:41:50 rechenmonster kernel: [   26.722239] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
May  4 15:41:50 rechenmonster kernel: [   26.722246] Bluetooth: BNEP filters: protocol multicast
May  4 15:41:50 rechenmonster bluetoothd[5621]: bridge pan0 created
May  4 15:41:50 rechenmonster bluetoothd[5621]: Registered interface org.bluez.Service on path /org/bluez/5621/any
May  4 15:41:50 rechenmonster kernel: [   26.796129] Bridge firewalling registered
May  4 15:41:50 rechenmonster kernel: [   26.845465] Bluetooth: RFCOMM socket layer initialized
May  4 15:41:50 rechenmonster kernel: [   26.845481] Bluetooth: RFCOMM TTY layer initialized
May  4 15:41:50 rechenmonster kernel: [   26.845484] Bluetooth: RFCOMM ver 1.10
May  4 15:41:50 rechenmonster atieventsd[5705]: ATI External Events Daemon started...
May  4 15:41:50 rechenmonster atieventsd[5705]: Event daemon control socket created
May  4 15:41:50 rechenmonster atieventsd[5705]: acpid connection established
May  4 15:41:50 rechenmonster acpid: client connected from 5705[0:0]
May  4 15:41:51 rechenmonster acpid: client connected from 5709[0:0]
May  4 15:41:51 rechenmonster kernel: [   27.940008] eth0: no IPv6 routers present
May  4 15:41:51 rechenmonster kernel: [   27.968651] warning: `dhcpd3' uses 32-bit capabilities (legacy support in use)
May  4 15:41:51 rechenmonster dhcpd: Internet Systems Consortium DHCP Server V3.1.1
May  4 15:41:51 rechenmonster dhcpd: Copyright 2004-2008 Internet Systems Consortium.
May  4 15:41:51 rechenmonster dhcpd: All rights reserved.
May  4 15:41:51 rechenmonster dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
May  4 15:41:51 rechenmonster dhcpd: WARNING: Host declarations are global.  They are not limited to the scope you declared them in.
May  4 15:41:51 rechenmonster dhcpd: Internet Systems Consortium DHCP Server V3.1.1
May  4 15:41:51 rechenmonster dhcpd: Copyright 2004-2008 Internet Systems Consortium.
May  4 15:41:51 rechenmonster dhcpd: All rights reserved.
May  4 15:41:51 rechenmonster dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
May  4 15:41:51 rechenmonster dhcpd: WARNING: Host declarations are global.  They are not limited to the scope you declared them in.
May  4 15:41:51 rechenmonster dhcpd: Internet Systems Consortium DHCP Server V3.1.1
May  4 15:41:51 rechenmonster dhcpd: Copyright 2004-2008 Internet Systems Consortium.
May  4 15:41:51 rechenmonster dhcpd: All rights reserved.
May  4 15:41:51 rechenmonster dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
May  4 15:41:51 rechenmonster kernel: [   28.030728] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
May  4 15:41:51 rechenmonster dhcpd: Wrote 0 deleted host decls to leases file.
May  4 15:41:51 rechenmonster dhcpd: Wrote 0 new dynamic host decls to leases file.
May  4 15:41:51 rechenmonster dhcpd: Wrote 2 leases to leases file.
May  4 15:41:51 rechenmonster kernel: [   28.122850] NET: Registered protocol family 17
May  4 15:41:52 rechenmonster kdm[5691]: X server died during startup
May  4 15:41:52 rechenmonster kdm[5691]: Failed to start X server. Starting failsafe X server.
May  4 15:41:53 rechenmonster acpid: client 5709[0:0] has disconnected
May  4 15:41:53 rechenmonster acpid: client connected from 5820[0:0]
May  4 15:41:53 rechenmonster NetworkManager: <info>  starting...
May  4 15:41:53 rechenmonster NetworkManager: <info>  (eth0): new Ethernet device (driver: 'e100')
May  4 15:41:53 rechenmonster NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_16_76_cb_c3_8f
May  4 15:41:53 rechenmonster NetworkManager: <info>  (ttyS0): ignoring due to lack of mobile broadband capabilties
May  4 15:41:53 rechenmonster NetworkManager: <info>  Trying to start the supplicant...
May  4 15:41:53 rechenmonster NetworkManager: <info>  Trying to start the system settings daemon...
May  4 15:41:53 rechenmonster NetworkManager: <info>  (eth0): carrier now ON (device state 1)
May  4 15:41:53 rechenmonster avahi-daemon[5870]: Found user 'avahi' (UID 104) and group 'avahi' (GID 108).
May  4 15:41:53 rechenmonster avahi-daemon[5870]: Successfully dropped root privileges.
May  4 15:41:53 rechenmonster avahi-daemon[5870]: avahi-daemon 0.6.23 starting up.
May  4 15:41:53 rechenmonster avahi-daemon[5870]: Successfully called chroot().
May  4 15:41:53 rechenmonster avahi-daemon[5870]: Successfully dropped remaining capabilities.
May  4 15:41:53 rechenmonster avahi-daemon[5870]: No service file found in /etc/avahi/services.
May  4 15:41:53 rechenmonster avahi-daemon[5870]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.170.
May  4 15:41:53 rechenmonster avahi-daemon[5870]: New relevant interface eth0.IPv4 for mDNS.
May  4 15:41:53 rechenmonster avahi-daemon[5870]: Network interface enumeration completed.
May  4 15:41:53 rechenmonster avahi-daemon[5870]: Registering new address record for fe80::216:76ff:fecb:c38f on eth0.*.
May  4 15:41:53 rechenmonster avahi-daemon[5870]: Registering new address record for 192.168.1.170 on eth0.IPv4.
May  4 15:41:53 rechenmonster avahi-daemon[5870]: Registering HINFO record with values 'I686'/'LINUX'.
May  4 15:41:53 rechenmonster nm-system-settings:    SCPlugin-Ifupdown: init!
May  4 15:41:53 rechenmonster nm-system-settings:    SCPlugin-Ifupdown: update_system_hostname
May  4 15:41:53 rechenmonster nm-system-settings:    SCPluginIfupdown: guessed connection type (eth0) = 802-3-ethernet
May  4 15:41:54 rechenmonster nm-system-settings:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:eth0, type:802-3-ethernet, autoconnect:0, id:Ifupdown (eth0), uuid: 681b428f-0000-0000-0000-000039000000
May  4 15:41:54 rechenmonster nm-system-settings:    SCPlugin-Ifupdown: addresses count: 1
May  4 15:41:54 rechenmonster nm-system-settings:    SCPlugin-Ifupdown: No dns-nameserver configured in /etc/network/interfaces
May  4 15:41:54 rechenmonster nm-system-settings:    SCPlugin-Ifupdown: autoconnect
May  4 15:41:54 rechenmonster nm-system-settings:    SCPluginIfupdown: management mode: unmanaged
May  4 15:41:54 rechenmonster nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_00_16_76_cb_c3_8f, iface: eth0): well known
May  4 15:41:54 rechenmonster nm-system-settings:    Ifupdown: get unmanaged devices count: 1
May  4 15:41:54 rechenmonster nm-system-settings:    SCPlugin-Ifupdown: (146965760) ... get_connections.
May  4 15:41:54 rechenmonster nm-system-settings:    SCPlugin-Ifupdown: (146965760) ... get_connections (managed=false): return empty list.
May  4 15:41:54 rechenmonster nm-system-settings:    Ifupdown: get unmanaged devices count: 1
May  4 15:41:54 rechenmonster nm-system-settings:    SCPlugin-Ifupdown: end _init.
May  4 15:41:54 rechenmonster nm-system-settings: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May  4 15:41:54 rechenmonster nm-system-settings: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May  4 15:41:54 rechenmonster NetworkManager: <info>  (eth0): now unmanaged
May  4 15:41:54 rechenmonster anacron[5977]: Anacron 2.3 started on 2009-05-04
May  4 15:41:54 rechenmonster anacron[5977]: Normal exit (0 jobs run)
May  4 15:41:54 rechenmonster /usr/sbin/cron[6020]: (CRON) INFO (pidfile fd = 3)
May  4 15:41:54 rechenmonster /usr/sbin/cron[6021]: (CRON) STARTUP (fork ok)
May  4 15:41:54 rechenmonster avahi-daemon[5870]: Server startup complete. Host name is rechenmonster.local. Local service cookie is 2461668096.
May  4 15:41:54 rechenmonster /usr/sbin/cron[6021]: (CRON) INFO (Running @reboot jobs)
May  4 15:41:56 rechenmonster init: tty1 main process ended, respawning
May  4 15:42:07 rechenmonster kdm[5691]: X server died during startup
May  4 15:42:07 rechenmonster kdm[5691]: Failed to start X server. Starting failsafe X server.
May  4 15:42:22 rechenmonster acpid: client 5820[0:0] has disconnected
May  4 15:42:22 rechenmonster acpid: client connected from 6687[0:0]
May  4 15:42:23 rechenmonster kdm[5691]: X server died during startup
May  4 15:42:23 rechenmonster kdm[5691]: X server for display :0 cannot be started, session disabled
May  4 15:42:43 rechenmonster console-kit-daemon[5461]: WARNING: Couldn't read /proc/5460/environ: Failed to open file '/proc/5460/environ': No such file or directory
May  4 15:44:08 rechenmonster NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May  4 15:44:08 rechenmonster NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May  4 15:50:01 rechenmonster CRON[8165]: Fehler bei Authentifizierung
stephan@rechenmonster:/var/log$

```

---

### Post by stephan0h on 2009-05-04
i did the following now:

sudo dpkg --remove fglrx-amdcccle
sudo dpkg --remove xorg-driver-fglrx

and it seems xorg is up and running again. hurray!


but this error is a real showstopper - it shows that ubuntu is still way from recommending it to my mother ... :(

---

### Post by stephan0h on 2009-05-04
oh god, this is not over yet.

i can login now, but my machine is slow as hell. kded4 eats up all my resources. help please!!

(i'm starting to hate this ubuntu stuff ...)

i mean, wouldn't it be a good idea to tell people not to upgrade because of certain problems????!!!! what kind of people are programming and testing this? i think next i'm thing is getting a mac - it's expensive, but at least it's working ... :((((

---

### Post by markbuntu on 2009-05-04
It is usually a really good idea to remove proprietary drivers before upgrading.

---

### Post by stephan0h on 2009-05-06
sorry for being a bit rude - but i was a bit pissed off because i wanted to work and not repair things.

you're right, it's a good idea and i learned this now the hard way - BUT if it's such a good idea, why can't the system inform me about the fact? Also, why can't the release notes be displayed right after clicking on the upgrade button? maybe i'm a little lazy bacause i didn't check the release notes in detail before - but i expect the system to support me here. after all, ubuntu claims not to be a pure expert-system - it should also be useable for the average use - and the average user surely is lazy!

---

### Post by DitchingMS on 2009-06-10
Hi,

I'm having a similar nightmare. I can't get into the command prompt as the keyboard doesn't react and I can't seem to enter a password. Please check out my thread at [http://ubuntuforums.org/showthread.php?t=1181268](http://ubuntuforums.org/showthread.php?t=1181268).

Thanks!

---

