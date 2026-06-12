---
title: "Trying to get MagicMouse working in Maverick"
date: 2010-10-13
forum: Hardware
---

### Post by MountainX on 2010-10-13
I've been reading a bunch of posts and I see people saying that the MagicMouse works out of the box, including scrolling. I can't get mine to work at all - not even to move the cursor.

I have a new clean install of Maverick.

Here's what I have done so far:
I started with System > Preferences > Bluetooth. 
It would recognize the MagicMouse, but it wouldn't connect.

sudo hcitool scan
Scanning ...
   XX XX XX XX XX   My Mouse
sudo apt-get install bluez-compat
sudo hidd --connect XX XX XX XX XX
Can't create HID control channel: Connection refused

I went back to the GUI tool, and this time the mouse appeared to connect. But it still wouldn't work. It acted like it wasn't connected. After reading some forums posts, etc. I opened System > Preferences > Bluetooth again, and the mouse is still listed but the "disconnect" button is disabled. So I assume that means the mouse is not connected.

I can't seem to get any further.

EDIT:
sudo modprobe -l *magic*
kernel/drivers/hid/hid-magicmouse.ko

EDIT 2:
 I opened System > Preferences > Bluetooth and I happened to notice that if I click the mouse, it's listing under "Devices" becomes bold and an icon (like a plug; for connected I presume) shows up -- but only for a fraction of a second. Apparently it is trying to connect but something is going wrong. 

Which logs should I check?

EDIT 3: syslog shows something...
Oct 13 20:19:11 MyComputer bluetoothd[1201]: link_key_request (sba=00:13:10:5D:54:FC, dba=XX:XX:XX:XX:XX:XX)
Oct 13 20:19:11 MyComputer bluetoothd[1201]: pin_code_request (sba=00:13:10:5D:54:FC, dba=XX:XX:XX:XX:XX:XX)
Oct 13 20:19:11 MyComputer bluetoothd[1201]: No agent available for 0 request
Oct 13 20:20:08 MyComputer bluetoothd[1201]: link_key_request (sba=00:13:10:5D:54:FC, dba=XX:XX:XX:XX:XX:XX)
Oct 13 20:20:08 MyComputer bluetoothd[1201]: pin_code_request (sba=00:13:10:5D:54:FC, dba=XX:XX:XX:XX:XX:XX)
Oct 13 20:20:08 MyComputer bluetoothd[1201]: No agent available for 0 request
Oct 13 20:20:12 MyComputer bluetoothd[1201]: link_key_request (sba=00:13:10:5D:54:FC, dba=XX:XX:XX:XX:XX:XX)
Oct 13 20:20:12 MyComputer bluetoothd[1201]: pin_code_request (sba=00:13:10:5D:54:FC, dba=XX:XX:XX:XX:XX:XX)
Oct 13 20:20:12 MyComputer bluetoothd[1201]: No agent available for 0 request
Oct 13 20:20:16 MyComputer bluetoothd[1201]: link_key_request (sba=00:13:10:5D:54:FC, dba=XX:XX:XX:XX:XX:XX)
Oct 13 20:20:16 MyComputer bluetoothd[1201]: pin_code_request (sba=00:13:10:5D:54:FC, dba=XX:XX:XX:XX:XX:XX)
Oct 13 20:20:16 MyComputer bluetoothd[1201]: No agent available for 0 request

---

