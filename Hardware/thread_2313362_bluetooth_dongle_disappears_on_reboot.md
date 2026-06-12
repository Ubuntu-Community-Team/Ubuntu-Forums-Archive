---
title: "bluetooth dongle disappears on reboot"
date: 2016-02-11
forum: Hardware
---

### Post by Nathan_Vreeland on 2016-02-11
When i reboot i have to unplug/replug my bluetooth dongle for it to register. It's kind of a pain in the butt, since i have to get out a usb mouse and re-connect my bluetooth mouse.

```
$ lsusbBus 001 Device 004: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0461:4d41 Primax Electronics, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:2107 Dell Computer Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




```

update. i tried adding the service start with no luck, tried [this]("http://askubuntu.com/questions/614319/ubuntu-15-04-bluetooth-no-adapters-found-dell-precision-m4800") and it started showing the bluetooth radio, but not turning on. and i have figured out that if i choose ubuntu advanced from the grub menu and choose the topmost choice, which is kernel 3.19.0-49-generic(oddly enough it is the same one that normally boots but it only works when i boot this way.) it both registers the bluetooth radio without me having to eff with it and auto connects to my magic mouse.

---

### Post by weatherman2 on 2016-02-11
Try restarting the bluetooth service after reboot.

Use a text editor to edit the file /etc/rc.local:


```
sudo gedit /etc/rc.local
```

(the file may be mostly comments - that is, lines that begin with "#").

At the bottom of this file, add the line:

```
service bluetooth start
```

then save the file and reboot.

I have a bluetooth mouse that occasionally won't re-connect after I wake up my computer from sleep - maybe 1/5 times.  I put that line above in one of the files in /etc/pm/sleep.d/ so that the bluetooth service restarts each time I wake the computer.  The mouse has worked reliably ever since.

---

