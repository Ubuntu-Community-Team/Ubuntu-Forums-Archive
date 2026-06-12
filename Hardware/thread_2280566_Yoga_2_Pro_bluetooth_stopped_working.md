---
title: "Yoga 2 Pro bluetooth stopped working"
date: 2015-05-31
forum: Hardware
---

### Post by aylons on 2015-05-31
Hi!

I have a Yoga 2 Pro and have installed on it for quite some time now. Since the last install, everything worked just fine, but today bluetooth has stopped working. In the Bluetooth settings window, even if I try to turn bluetooth on, the message "Bluetooth is disable" still shows there, as if nothing happened.

Furthermore, "rfkill list" show bluetooth as not blocked. I also tried to compile and install the modules [as stated in another thread]("http://ubuntuforums.org/showthread.php?t=2280339&highlight=yoga+bluetooth"), but the problem remains the same.

The machine is a Windows 8.1 dual boot, and bluetooth works fine on Windows. I don't remember doing anything that could affect bluetooth recently, but I may possibly have installed usual Ubuntu updates in the last boot.

Some terminal outputs that may be useful:

rfkill list:
```
rfkill list
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

service bluetooth status
```

sudo service bluetooth status
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: inactive (dead)

```

If, after that, i try "service bluetooth start":

```

sudo service bluetooth status -l
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Sun 2015-05-31 21:15:23 BRT; 13s ago
 Main PID: 3033 (bluetoothd)
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;3033 /usr/sbin/bluetoothd -n

May 31 21:15:23 aylons-yoga2-ubuntu bluetoothd[3033]: bluetoothd[3033]: DIS cannot start: GATT is disabled
May 31 21:15:23 aylons-yoga2-ubuntu bluetoothd[3033]: bluetoothd[3033]: Failed to init deviceinfo plugin
May 31 21:15:23 aylons-yoga2-ubuntu bluetoothd[3033]: bluetoothd[3033]: Failed to init proximity plugin
May 31 21:15:23 aylons-yoga2-ubuntu bluetoothd[3033]: bluetoothd[3033]: Failed to init time plugin
May 31 21:15:23 aylons-yoga2-ubuntu bluetoothd[3033]: bluetoothd[3033]: Failed to init alert plugin
May 31 21:15:23 aylons-yoga2-ubuntu bluetoothd[3033]: bluetoothd[3033]: Failed to init thermometer plugin
May 31 21:15:23 aylons-yoga2-ubuntu bluetoothd[3033]: bluetoothd[3033]: Failed to init gatt_example plugin
May 31 21:15:23 aylons-yoga2-ubuntu bluetoothd[3033]: Failed to init gatt_example plugin
May 31 21:15:23 aylons-yoga2-ubuntu bluetoothd[3033]: Bluetooth Management interface initialized
May 31 21:15:23 aylons-yoga2-ubuntu bluetoothd[3033]: bluetoothd[3033]: Bluetooth Management interface initialized

```

sudo lsusb; uname -a; lsmod | grep bluetooth; dmesg | grep -i firmware
```

sudo lsusb; uname -a; lsmod | grep bluetooth; dmesg | grep -i firmware
Bus 003 Device 002: ID 8087:8000 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 010: ID 5986:0535 Acer, Inc 
Bus 001 Device 009: ID 04f3:016f Elan Microelectronics Corp. 
Bus 001 Device 008: ID 2047:0855 Texas Instruments 
Bus 001 Device 004: ID 045e:0780 Microsoft Corp. 
Bus 001 Device 011: ID 062a:3633 Creative Labs 
Bus 001 Device 002: ID 1a40:0201 Terminus Technology Inc. FE 2.1 7-port Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Linux aylons-yoga2-ubuntu 4.0.1-040001-generic #201504290935 SMP Wed Apr 29 09:36:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
[    2.129301] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    3.523595] iwlwifi 0000:01:00.0: loaded firmware version 25.17.12.0 op_mode iwlmvm

```

Sumarizing: bluetooth has suddenly stopped working on Yoga 2 Pro running Ubuntu 15.04, but it works fine in Windows. I have already tried installed new modules as describre in a similar post ([http://ubuntuforums.org/showthread.php?t=2280339&highlight=yoga+bluetooth](http://ubuntuforums.org/showthread.php?t=2280339&highlight=yoga+bluetooth)) and changing /etc/bluetooth/main.conf RememberPowered from true to false (and back again), as [ described in stack exchange]("http://askubuntu.com/questions/614800/bluetooth-worked-in-ubuntu-15-04-but-not-ubuntu-gnome-15-04"), to no avail.

---

### Post by jeremy31 on 2015-06-01
Does bluetooth work if you boot into a 3.19 kernel?  The other thread([http://ubuntuforums.org/showthread.php?t=2280339&highlight=yoga+bluetooth](http://ubuntuforums.org/showthread.php?t=2280339&highlight=yoga+bluetooth)) deals with a Realtek and you have Intel wifi, so you can uninstall those drivers with ```
cd rtlwifi_new
``````
sudo make uninstall
``````
cd ~/rtl8723au_bt
``````
sudo make uninstall
```

Include ```
lspci -nnk | grep -iA2 net; hciconfig -a
``` in your next post

---

### Post by aylons on 2015-06-03
First of all, thank you for your answers.

So, first, I tried going back to kernel 3.19 and indeed it worked. However, I must note that it didn't just stopped worked when I upgraded to the 4.0.1: bluetooth worked fine for the last several weeks since I updated the kernel, even through several reboots. I installed this version because it corrects a bug that prevented me to access my company's Juniper VPN. So, I wonder if there is any way to keep this kernel while using bluetooth.


After getting back to the 4.0.1 I uninstalled the uneeded modules. I should have noticed, I really didn't think this one through. Was just eager to find a solution before posting.

FInally, here goes the output for "lspci -nnk | grep -iA2 net; hciconfig -a":

```
lspci -nnk | grep -iA2 net; hciconfig -a
01:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b2] (rev 6b)
	Subsystem: Intel Corporation Wireless-N 7260 [8086:c262]
	Kernel driver in use: iwlwifi
```

EDIT:

I just realized Ubuntu's 3.19 kernel has been update and Jupiter VPN is working all right. Should have tested this before messing with modules. So now I have both bluetooth mouse AND Juniper VPN! Yay!

Thank you for helping! Now I just need to remove the 4.01 kernel and boot straight to the updated ubuntu standard kernels.

---

