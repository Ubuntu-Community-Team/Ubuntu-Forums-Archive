---
title: "Upgrade to 8.04: power turns off after login"
date: 2008-06-22
forum: Hardware
---

### Post by madscientist on 2008-06-22
So, I just upgraded my father's Toshiba Satellite M35X laptop from Ubuntu 6.06 to 8.04.  Everything seems to work fine (wireless network, video, etc.) except that after he logs in, the laptop simply turns off.  I don't think it's hibernating: the power LED is off and when I press it again, the system boots normally from scratch.

The login seems to go fine: I get the panels, I see the wireless connection, etc. and I even have a few seconds to click a menu or something if I want.  Then, it just goes off.  No warning, no error, no panic: just ... off.

I booted using the old 6.06 kernel (2.6.15 something) at the grub menu and it does work with this kernel (doesn't turn off--I'm using it now).  I've checked all the /var/log files and the last message in them is related to power; for example from messages:```
Jun 22 11:28:52 psmith-laptop kernel: [   57.348336] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jun 22 11:28:56 psmith-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.host_name
Jun 22 11:28:56 psmith-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Jun 22 11:28:56 psmith-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Jun 22 11:28:56 psmith-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.interface_mtu
Jun 22 11:29:23 psmith-laptop kernel: [  146.638718] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 22 11:30:13 psmith-laptop syslogd 1.5.0#1ubuntu1: restart.

```
The last line is the first line from the restart.  Here's more info, from syslog:```
Jun 22 11:29:14 psmith-laptop kernel: [  183.787297] eth1: no IPv6 routers present
Jun 22 11:29:23 psmith-laptop kernel: [  146.638718] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 22 11:29:23 psmith-laptop NetworkManager: <debug> [1214148563.107496] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT1'). 
Jun 22 11:30:13 psmith-laptop syslogd 1.5.0#1ubuntu1: restart.
```
It seems that the problem is related to the battery or power (the laptop is currently plugged in, not running on battery).  Maybe the kernel or NetworkManager gets confused and tries to disable the power supply that the laptop is actually using?

Help... anyone have any thoughts?

---

### Post by madscientist on 2008-06-23
I tried to do a little triaging by working backwards to find which kernels failed and which worked.  I installed the original Hardy kernel (linux-image-2.6.24-16-386_2.6.24-16.30), the latest Gutsy kernel (linux-image-2.6.22-14-386_2.6.22-14.52_i386), and the latest Feisty kernel (linux-image-2.6.20-15-386_2.6.20-15.27_i386).  As I mentioned, the latest Hardy kernel (2.6.24-19) fails and the latest Dapper kernel (2.6.15-52.67) works.

Experimentation shows that the Hardy and Gutsy kernels both fail, while the Dapper and Feisty kernels work.

One weird thing: when the Feisty kernel boots it gives me an odd popup warning on the status bar that says the system has been unplugged from AC power, even though it has NOT been unplugged.  However, the system doesn't shut down and I do see the "plug" icon in the notification area and if I hover over it, it says "Computer is running on AC power" which is correct.

---

### Post by iSKUNK! on 2009-11-12
The problem is a buggy ACPI implementation in the BIOS, that somehow didn't cause trouble until 8.04 (as gleaned from various secondhand reports). Upgrading the BIOS to the latest version should make the sudden-shutoff behavior go away.

See [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/242400") for more details.

---

