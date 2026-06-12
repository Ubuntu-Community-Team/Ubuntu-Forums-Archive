---
title: "Bluetooth switch"
date: 2021-12-14
forum: Hardware
---

### Post by puppet007 on 2021-12-14
Hello everyone.


I cannot set the bluetooth switch to on in the configuration settings.  It seems that the switch is stuck on off. 
If I enable bluetooth in the console the switch is still on off. Same with the turn on option in the upper right corner. 

The keyboard worked fine for a month until today.  For some reason it has broken down.  I am using ubuntu 20.10. 
And since today I have to manual start bluetooth. Not for sure where to look now. 



1:57:09 PC systemd[1]: Condition check resulted in Bluetooth service being skipped.
dec 14 11:58:30 PC systemd[1]: Condition check resulted in Bluetooth service being skipped.
dec 14 12:01:04 PC systemd[1]: Condition check resulted in Bluetooth service being skipped.
dec 14 12:02:27 PC systemd[1]: Condition check resulted in Bluetooth service being skipped.
dec 14 12:03:42 PC systemd[1]: Condition check resulted in Bluetooth service being skipped.

dpkg --status bluez | grep '^Version:'
/home/puppet# dpkg --status bluez | grep '^Version:'
Version: 5.60-0ubuntu2.1


/home/puppet# bluetoothctl
Agent registered


Active: active (running) since Tue 2021-12-14 12:32:10 CET; 7min ago
       Docs: man:bluetoothd(8)
   Main PID: 31990 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 8180)
     Memory: 524.0K
        CPU: 40ms
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;31990 /usr/lib/bluetooth/bluetoothd

dec 14 12:32:10 PC systemd[1]: Starting Bluetooth service...
dec 14 12:32:10 PC bluetoothd[31990]: Bluetooth daemon 5.60
dec 14 12:32:10 PC systemd[1]: Started Bluetooth service.
dec 14 12:32:10 PC bluetoothd[31990]: Starting SDP server
dec 14 12:32:10 PC bluetoothd[31990]: Bluetooth management interface 1.20 i…ized
Hint: Some lines were ellipsized, use -l to show in full.

---

### Post by TheFu on 2021-12-14
Check out **rfkill**. Sometimes wifi and BT get "hardware locked". That tool can unlock both or either.

Beware of the extremely poor security for all BT connections.  I've been hacked 3 times in 25+ yrs.  The most recent was through bluetooth on a completely fresh install with full patches applied the day prior.  If you live a mile away from everyone else, it will probably be fine.  Much closer than that and BT signals can be received using a tin-can antenna.  Just beware.  [https://hackernoon.com/how-to-hack-bluetooth-devices-5-common-vulnerabilities-ng2537af](https://hackernoon.com/how-to-hack-bluetooth-devices-5-common-vulnerabilities-ng2537af)

---

