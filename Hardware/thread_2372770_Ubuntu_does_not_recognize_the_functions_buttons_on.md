---
title: "Ubuntu does not recognize the functions buttons on keyboard"
date: 2017-09-28
forum: Hardware
---

### Post by kornroger on 2017-09-28
[COLOR=#111111][FONT=Ubuntu]Hi, all)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Doesn't work additional laptop (Acer TravelMate P645-S) [buttons]("https://imgur.com/a/l1K7C") - WiFi Switch On/Off, "P" button (programmable for custom actions), AudioMicMute button. Also, doesn't work Fn+F3 shortcut, which responsible for switching WiFi On/Off. Other Fn+F keys work fine. Wifi works fine, but the additional button always lights up.
[/FONT][/COLOR]
**[COLOR=#111111][FONT=Ubuntu]xev[/FONT][/COLOR]** [COLOR=#111111][FONT=Ubuntu]and **acpi_listen** doesn't show anything for that buttons.
[/FONT][/COLOR]
 **uname -a**
```
Linux evilmachine 4.10.0-35-generic #39~16.04.1-Ubuntu SMP Wed Sep 13 09:02:42 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

``` 
[B]
lspci[/B] 
```
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection (3) I218-LM (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)
00:1c.5 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #6 (rev e3)
00:1d.0 USB controller: Intel Corporation Wildcat Point-LP USB EHCI Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation Wildcat Point-LP Thermal Management Controller (rev 03)
02:00.0 Network controller: Intel Corporation Wireless 7265 (rev 48)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
```

[COLOR=#111111][FONT=Ubuntu]The **dmesg** shows an error that may be the cause:
[/FONT][/COLOR]acer_wmi: Enabling Launch Manager failed: 0xe4 - 0x0

[COLOR=#111111][FONT=Ubuntu]Output for [B]dmesg | grep acer_wmi:
[/B][/FONT][/COLOR]```

[ 6.551692] acer_wmi: Acer Laptop ACPI-WMI Extras
[ 6.551718] acer_wmi: Function bitmap for Communication Button: 0x4841
[ 6.556669] acer_wmi: Enabling Launch Manager failed: 0xe4 - 0x0
[ 6.568564] acer_wmi: Get Current Device Status failed: 0xe2 - 0x0
[ 6.600179] acer_wmi: Get Current Device Status failed: 0xe2 - 0x0
[ 6.606453] acer_wmi: Get Current Device Status failed: 0xe2 - 0x0
[ 6.609361] acer_wmi: Get Current Device Status failed: 0xe2 - 0x0
[ 17.011479] acer_wmi: Get Current Device Status failed: 0xe2 - 0x0
[ 17.014861] acer_wmi: Get Current Device Status failed: 0xe2 - 0x0
[ 1481.141666] acer_wmi: Get Current Device Status failed: 0xe2 - 0x0
[ 1481.146607] acer_wmi: Get Current Device Status failed: 0xe2 - 0x0
[ 1481.151606] acer_wmi: Get Current Device Status failed: 0xe2 - 0x0
[ 1524.198721] acer_wmi: Unknown function number - 6 - 1
```

[COLOR=#111111][FONT=Ubuntu]Also in **dmesg**:
[/FONT][/COLOR]
```
[ 67.987796] atkbd serio0: Unknown key pressed (translated set 2, code 0x8a on isa0060/serio0).
[ 67.987800] atkbd serio0: Use 'setkeycodes e00a <keycode>' to make it known.
```

[COLOR=#111111][FONT=Ubuntu]It appears when additional AudioMicMute button pressed. From **xmodmap**** -****pke** i found *keycode 198 = XF86AudioMicMute NoSymbol XF86AudioMicMute. *But after
 **sudo ****setkeycodes**[B] e00a 198 
[/B]nothing heppens.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]In addition, I tried many different solutions to the problem. I'm very good at Google. But a new one in Ubuntu. I will be grateful for the answers[/FONT][/COLOR]:D

---

### Post by alpsayin on 2018-08-22
Suffering from the same problem (Ubuntu 16.04 LTS). Anyone got anything yet?

---

### Post by oldos2er on 2018-08-22
alpsayin, please start a new thread for your problem.

Old thread closed.

---

