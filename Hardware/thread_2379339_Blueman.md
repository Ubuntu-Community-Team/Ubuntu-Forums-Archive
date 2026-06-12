---
title: "Blueman"
date: 2017-12-04
forum: Hardware
---

### Post by angel mike on 2017-12-04
Do I need to install blueman i Ubuntu 16.04?
I have a usb bluetooth driver adapter for Linux ( from Think Penquin) which worked on initial install but not now.
Thanks Mike

---

### Post by jeremy31 on 2017-12-06
You shouldn't need Blueman as the bluetooth manager in 16.04 does work, see if this command will make the bluetooth work again
```
echo -e "power on\n scan on\n quit" |bluetoothctl
```

---

### Post by angel mike on 2017-12-06
Apologies Jeremy 31 for slow response. Ran the code in the terminal which gave following output#
```
 
michael@michael-XPS-11-9P33:~$ sudo echo -e "power on\n scan on\n quit" |bluetoothctl
[NEW] Controller 00:1A:7D:DA:71:0A michael-XPS-11-9P33 [default]
[NEW] Device 04:88:E2:5B:6E:77 Powerbeats Wireless
[NEW] Device 24:E3:14:52:78:0C 24-E3-14-52-78-0C
[bluetooth]# [sudo] password for michael: 
power on
[bluetooth]#  scan on
[bluetooth]#  quit
[DEL] Controller 00:1A:7D:DA:71:0A michael-XPS-11-9P33 [default]
michael@michael-XPS-11-9P33:~$ 

```
but still could not connect to Powerbeats headphones. They are listed and Bluetooth is shown 'on' but bluetooth is searching but not finding. Head pieces are activated and trying to connect.
Mike

---

### Post by jeremy31 on 2017-12-06
Let's try the following with the headset in pairing mode
```
echo -e "power on\n scan on\n pair 04:88:E2:5B:6E:77\n trust 04:88:E2:5B:6E:77\n connect 04:88:E2:5B:6E:77\n quit" |bluetoothctl
```

---

### Post by angel mike on 2017-12-07
Thanks Jeremy for that - output below. Still no pairing though. Device Search set to : Headohones. Sound Settings only shows : Sound through speakers.Mike
```

michael@michael-XPS-11-9P33:~$ sudo echo -e "power on\n scan on\n pair 04:88:E2:5B:6E:77\n trust 04:88:E2:5B:6E:77\n connect 04:88:E2:5B:6E:77\n quit" |bluetoothctl
[NEW] Controller 00:1A:7D:DA:71:0A michael-XPS-11-9P33 [default]
[NEW] Device 04:88:E2:5B:6E:77 Powerbeats Wireless
[NEW] Device 24:E3:14:52:78:0C 24-E3-14-52-78-0C
[CHG] Controller 00:1A:7D:DA:71:0A Discovering: yes
[CHG] Device 04:88:E2:5B:6E:77 RSSI: -65
[CHG] Device 04:88:E2:5B:6E:77 RSSI: -56
[CHG] Device 04:88:E2:5B:6E:77 RSSI: -43
[CHG] Device 04:88:E2:5B:6E:77 RSSI: -52
[CHG] Device 04:88:E2:5B:6E:77 RSSI: -38
[CHG] Device 04:88:E2:5B:6E:77 RSSI is nil
[CHG] Controller 00:1A:7D:DA:71:0A Discovering: no
[CHG] Controller 00:1A:7D:DA:71:0A Discovering: yes
[CHG] Controller 00:1A:7D:DA:71:0A Discovering: no
[bluetooth]# 

```

---

