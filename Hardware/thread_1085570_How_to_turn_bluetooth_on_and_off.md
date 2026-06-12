---
title: "How to turn bluetooth on and off"
date: 2009-03-03
forum: Hardware
---

### Post by gtr33m on 2009-03-03
This is a revival of this thread [http://ubuntuforums.org/showthread.php?t=120403&page=2]("http://ubuntuforums.org/showthread.php?t=120403&page=2").

The solution provided by **sayantandas** works well but needs a minor update for Jaunty.  Very small fix to the script changing "if ps -A | grep -c bluetoothd-serv" to "if ps -A | grep -c bluetoothd"

Modified instructions:

```
#!/bin/bash
if ps -A | grep -c bluetoothd
then 
gksudo /etc/init.d/bluetooth stop 
sudo hciconfig hci0 down
sudo rmmod hci_usb
else
sudo modprobe hci_usb reset=1
gksudo /etc/init.d/bluetooth start 
fi
```

copy and paste this code by making a shell script. give it executable permission. name it something like 'bluetooth_toggle.sh' put it in the /bin folder, make a shortcut to ur desktop . Double click on it, select run, and thats it. u can toggle the bluetooth.

As a bonus, if you set the bluetooth icon to display only when device is present in the bluetooth-applet, you get a visual indication of bluetooth being on or off!:popcorn:

---

