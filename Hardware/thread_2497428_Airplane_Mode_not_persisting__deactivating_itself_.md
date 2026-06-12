---
title: "Airplane Mode not persisting / deactivating itself after wake-from-sleep"
date: 2024-05-04
forum: Hardware
---

### Post by csae2608 on 2024-05-04
Hello ,


noticed this undesired behaviour on my Thinkpad Laptop running 22.04 or 24.04 LTS <


have WiFi disabled, and after disabling additionally Bluetooth, the #AirplaneMode gets activated<


so far,so good.

however, after resuming the laptop from sleep, every time Bluetooth is found activated, although prior to putting laptop to sleep , the Airplane Mode is active.


Please provide a solution,
thanks.

---

### Post by #&amp;thj^% on 2024-05-04
Please try:
```
systemctl disable bluetooth
```
It should prompt you to enter your password

Also you could try:
```
 systemctl stop --now bluetooth

```
That should persist through out your session

EDIT After using my suggestions above, I needed to reboot to see the changes made.
```
 systemctl status bluetooth 
&#9675; bluetooth.service - Bluetooth service
     Loaded: loaded (/usr/lib/systemd/system/bluetooth.service; disabled; prese>
     Active: inactive (dead)
       Docs: man:bluetoothd(8)

```

I also have a script i use on Arch and it should work on Ubuntu as well.
```
 #!/bin/bash
wifi="$(nmcli r wifi | awk 'FNR = 2 {print $1}')"
if [ "$wifi" == "enabled" ]; then
    rfkill block all &
    notify-send 'Mode avion: actif'
else
    rfkill unblock all &
    notify-send 'Mode avion: inactif'
fi
```

---

### Post by csae2608 on 2024-05-05
hello , i was hoping for a simple solution

[HTML]systemctl disable bluetooth
Synchronizing state of bluetooth.service with SysV service script with /usr/lib/systemd/systemd-sysv-install.
Executing: /usr/lib/systemd/systemd-sysv-install disable bluetooth
update-rc.d: error: Permission denied

[/HTML]

thanks

edit>
[HTML]rich@rich-ThinkPad-A475:~$  systemctl stop --now bluetooth

[/HTML]

yields no change.

---

### Post by #&amp;thj^% on 2024-05-05
I filed a bug-report here: [https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/2064869](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/2064869)

Feel free to add yourself to it, helps with grabbing their attention

---

