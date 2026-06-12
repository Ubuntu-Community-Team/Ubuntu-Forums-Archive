---
title: "Bluetooth keyboard dock not working on 16.04 LTS"
date: 2016-05-09
forum: Hardware
---

### Post by Peter_Willemsen on 2016-05-09
Hi guys,


I have an Asus Transformer Book t300 chi, which has a separated bluetooth keyboard dock and trackpad. It works out of the box with Ubuntu 14.04. I tried the version after that, I think 14.10, and the bluetooth keyboard stopped working :(
I asked this on the forums too, but decided to wait for the next LTS to see if the problem would be solved.

Now I tried the 16.04 live usb and they bluetooth still doesnt work! :( This is really strange as this used to work very well.

I'm prepared to supply any details needed to fix this, thanks!

---

### Post by jeremy31 on 2016-05-09
I assume your hardware hasn't changed from your other posts but I will ask for them anyhow.  Please post ```
lsusb; dmesg | grep -i blue
```

Not familiar with the keyboard dock but after putting it in pairing mode does ```
hcitool scan
``` show any results or does the Bluetooth manager find it when you try to add devices?

Also post the result for ```
hciconfig -a; rfkill list all
```

And the very last question I wanted to ask, how are the batteries?

---

### Post by Peter_Willemsen on 2016-05-10
Thanks,

I'll do that today, will edit this post when going into live usb again. Hardware hasn't changed (the laptop is like a macbook air it's completely 1 piece of aluminum and the whole pc is soldered on 1 piece)

---

### Post by Peter_Willemsen on 2016-05-11
> **jeremy31 said:**
> I assume your hardware hasn't changed from your other posts but I will ask for them anyhow.  Please post ```
lsusb; dmesg | grep -i blue
```

Not familiar with the keyboard dock but after putting it in pairing mode does ```
hcitool scan
``` show any results or does the Bluetooth manager find it when you try to add devices?

Also post the result for ```
hciconfig -a; rfkill list all
```

And the very last question I wanted to ask, how are the batteries?

Hi there,

It was a bit clumsy to do (1 usb port, where the 16.04 live usb was in) but I did it using touch screen keyboard + posted the results on pastebin so I can drop it here later.

Here is the results for each command:

```

ubuntu@ubuntu:~$ lsusb; dmesg | grep -i blue
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 06cb:11ef Synaptics, Inc. 
Bus 001 Device 004: ID 0bda:57d2 Realtek Semiconductor Corp. 
Bus 001 Device 006: ID 8087:0a2a Intel Corp. 
Bus 001 Device 002: ID 13fe:1e00 Kingston Technology Company Inc. Flash Drive 2 GB [ICIDU 2 GB]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[   16.921292] Bluetooth: Core ver 2.21
[   16.921308] Bluetooth: HCI device and connection manager initialized
[   16.921312] Bluetooth: HCI socket layer initialized
[   16.921314] Bluetooth: L2CAP socket layer initialized
[   16.921323] Bluetooth: SCO socket layer initialized
[   17.009795] Bluetooth: hci0: read Intel version: 370810011003110e00
[   17.034324] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-1.10.3.11.e.bseq
[   17.369807] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
[   18.321038] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.321042] Bluetooth: BNEP filters: protocol multicast
[   18.321048] Bluetooth: BNEP socket layer initialized
[   26.285343] Bluetooth: RFCOMM TTY layer initialized
[   26.285352] Bluetooth: RFCOMM socket layer initialized
[   26.285359] Bluetooth: RFCOMM ver 1.11
[   64.230557] Bluetooth: hci0: read Intel version: 370810011003110e00
[   64.230600] Bluetooth: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-1.10.3.11.e.bseq
[   64.527795] Bluetooth: hci0: Intel Bluetooth firmware patch completed and activated
ubuntu@ubuntu:~$ 
```

```

ubuntu@ubuntu:~$ hcitool scan
Scanning ...
	1C:B7:2C:27:FF:DF	ASUS T300CHI DOCKING
```

```

ubuntu@ubuntu:~$ hciconfig -a; rfkill list all
hci0:	Type: BR/EDR  Bus: USB
	BD Address: 34:02:86:83:8D:2A  ACL MTU: 1021:5  SCO MTU: 96:6
	UP RUNNING PSCAN 
	RX bytes:4371 acl:9 sco:0 events:321 errors:0
	TX bytes:39972 acl:12 sco:0 commands:235 errors:0
	Features: 0xff 0xfe 0x0f 0xfe 0xdb 0xff 0x7b 0x87
	Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
	Link policy: RSWITCH HOLD SNIFF 
	Link mode: SLAVE ACCEPT 
	Name: 'ubuntu'
	Class: 0x0c010c
	Service Classes: Rendering, Capturing
	Device Class: Computer, Laptop
	HCI Version: 4.2 (0x8)  Revision: 0x1000
	LMP Version: 4.2 (0x8)  Subversion: 0x1000
	Manufacturer: Intel Corp. (2)

1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
4: hci0: Bluetooth
	Soft blocked: no
```

About the batteries, what do you mean exactly? The battery life of this laptop is pretty good considering the whole pc is behind the screen (I think I can get like 6 hours out of this thing)

---

### Post by jeremy31 on 2016-05-11
Looks like a working bluetooth to my eyes.  With the docking station/keyboard in pairing mode, in terminal
```
bluetoothctl
pair 1C:B7:2C:27:FF:DF
trust 1C:B7:2C:27:FF:DF
connect 1C:B7:2C:27:FF:DF

```
Hopefully it works after that or gives an error that can be fixed

---

### Post by Peter_Willemsen on 2016-05-11
Thanks will try that soon. What happened when I tried in the GUI was that the bluetooth 'new device' screen did recognize the keyboard, and when I connect it stays on connecting for like 1 minute and then says failed.
I haven't tested yet with command line, will do that tomorrow :)

---

### Post by jeremy31 on 2016-05-11
It really should prompt you to enter a PIN in the keyboard after attempting to pair unless you changed from the default PIN option

---

### Post by Peter_Willemsen on 2016-05-12
Hi there,


For some reason, pairing trough the command line worked! I did 'scan on' before entering your codes otherwise it said device not found. It didn't ask me for a pin and it just worked.
So now I'm going to install and use the command line to pair (which should hopefully be done once :)) 

Thanks again!

---

