---
title: "Enable wireless hardware switch by command"
date: 2011-04-05
forum: Hardware
---

### Post by yosque on 2011-04-05
How can I enable wireless hardware switch by comamnd or script? Usually, I push Fn+F3 hotkey, but I need to toggle in shell.

I use Ubuntu 10.10 on Acer Aspire 1830z. I found the following command in other threads, but it doesn't work in my environment.

$ cat /sys/class/net/*/device/rf_kill
cat: /sys/class/net/*/device/rf_kill: No such file or directory

I also cannot find rf_kill under /sys/bus/pci/drivers/iwlagn/0000\:02\:00.0.

Here is the result of rfkill command.

$ rfkill list
0: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: i2400m-usb:2-1.4:1.0: WiMAX
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

