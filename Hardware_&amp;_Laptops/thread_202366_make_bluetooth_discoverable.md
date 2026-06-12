---
title: "make bluetooth discoverable"
date: 2006-06-23
forum: Hardware &amp; Laptops
---

### Post by kmerchant on 2006-06-23
Hi,

I wanna transfer some files from my PDA to my laptop via bluetooth, but my PDA cant detect the laptop. Can anyone help.. thanx

Regards

KMerchant

---

### Post by th3james on 2006-06-23
What bluetooth app are you using?
kbluetoothd (the best one IMO) is discoverable by default

---

### Post by kmerchant on 2006-06-23
Hi,

Thanks for the post. As suggested i installed kbluetoothd but no luck. I get the following error:

Link points to "/tmp/ksocket-khurram"
Link points to "/tmp/kde-khurram"
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/mb-applet-system-monitor.desktop has Type=PanelApp instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/mb-applet-system-monitor.desktop
kio (KService*): WARNING: The desktop entry file /usr/share/applications/mb-applet-clock.desktop has Type=PanelApp instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/mb-applet-clock.desktop
kio (KService*): WARNING: The desktop entry file /usr/share/applications/mb-applet-menu-launcher.desktop has Type=PanelApp instead of "Application" or "Service"kio (KService*): WARNING: Invalid Service : /usr/share/applications/mb-applet-menu-launcher.desktop
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbluetoothd: HciListener::HciListener()
kbluetoothd: WARNING: No usable bluetooth device found.
kbluetoothd: Using hci0 as default bluetooth device.
kbluetoothd: TrayIcon::slotMruMenuUpdate
kbluetoothd: Kbluetoothd: Error opening HCI socket
kbluetoothd: TrayIcon::slotMruMenuUpdate

Do you think is a problem with the device installation....

I have a Billionton PCMCIA Card

regards

Kmerchant

---

### Post by ctsdownloads on 2007-04-25
Alright, looks like running this in a shell:

> hciconfig hci0 piscan

fixes the not being discoverable on the desktop problem, now onto a fresh set... Man, Dapper never had this much to deal with in the bluetooh arena. Anyway, here is the next problem.

After successfully pairing the phone with the PC, re-running 

> sudo hciconfig hci0 inqmode 0

to compensate for more Edgy bluetooth bugs, then running:

> sudo /etc/init.d/bluetooth restart

I am still not able to send or receive files; via right click and send to or with send-to or even the launcher I made for gnome-obex-send, nothing works.... 

I am, not upgrading to Feisty (just read the horror stories with upgrades), so it's Edgy or forget it. Please help.

---

### Post by ctsdownloads on 2007-04-25
Please tell me [this was fixed]("https://launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/70718") in Feisty...

---

### Post by ctsdownloads on 2007-04-25
I may try kbluetoothd then as gnome-bluetooth is buggy as hell. Thanks, will report back.

---

### Post by ctsdownloads on 2007-04-25
Well I don't know why for sure, but adding both

> gnome-bluetooth

and

>  kdebluetooth

did the trick. gnome-obex-send as a launcher as well as "right click send-to" is now working.

---

