---
title: "apple bluetooth keyboard connection unstable"
date: 2016-01-11
forum: Hardware
---

### Post by soungno on 2016-01-11
hi i'm using ubuntu 15.10
my hardware thinkpad x1 carbon 2gen

i'm using apple bluetooth keyboard 
Well used, but
Sometimes it is unstable

sometimes close connetion bluetooth keyboard
Each time, turn off and turn on the Bluetooth connection again, repeat the turn.
Is there a way that the connection can not be disconnected?

this log is my systemctl status bluetooth 

~$ sudo systemctl status bluetooth
&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since &#54868; 2016-01-12 09:39:39 KST; 25min ago
     Docs: man:bluetoothd(8)
 Main PID: 915 (bluetoothd)
   Status: "Running"
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;915 /usr/lib/bluetooth/bluetoothd

 1&#50900; 12 09:57:29 soungno-ThinkPad-X1-Carbon-2nd bluetoothd[915]: Access denied: org.bluez.Error.Rejected
 1&#50900; 12 09:57:57 soungno-ThinkPad-X1-Carbon-2nd bluetoothd[915]: Can't get HIDP connection info
 1&#50900; 12 09:58:33 soungno-ThinkPad-X1-Carbon-2nd bluetoothd[915]: (bluetoothd:915): GLib-CRITICAL **: Source ID 315 was not found when attempting to remove it
 1&#50900; 12 09:58:39 soungno-ThinkPad-X1-Carbon-2nd bluetoothd[915]: Can't get HIDP connection info
 1&#50900; 12 09:59:16 soungno-ThinkPad-X1-Carbon-2nd bluetoothd[915]: (bluetoothd:915): GLib-CRITICAL **: Source ID 329 was not found when attempting to remove it
 1&#50900; 12 09:59:16 soungno-ThinkPad-X1-Carbon-2nd bluetoothd[915]: 6C:70:9F:B7:F0:6D: error updating services: Input/output error (5)
 1&#50900; 12 09:59:24 soungno-ThinkPad-X1-Carbon-2nd bluetoothd[915]: Authentication attempt without agent
 1&#50900; 12 09:59:24 soungno-ThinkPad-X1-Carbon-2nd bluetoothd[915]: Access denied: org.bluez.Error.Rejected
 1&#50900; 12 09:59:37 soungno-ThinkPad-X1-Carbon-2nd bluetoothd[915]: Can't get HIDP connection info
 1&#50900; 12 09:59:38 soungno-ThinkPad-X1-Carbon-2nd bluetoothd[915]: ioctl_connadd(): File exists (17)

---

