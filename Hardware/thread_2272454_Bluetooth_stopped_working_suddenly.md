---
title: "Bluetooth stopped working suddenly"
date: 2015-04-06
forum: Hardware
---

### Post by prodicus on 2015-04-06
I am not able to see `bluetooth` symbol on the `panel`. 
I checked with `Unity Tweak Tool` and there is a tick mark for bluetooth.

Further, I ran the command `sudo service bluetooth status` and it gave `bluetooth start/running, process 744`
```

    tasdik@Acer:~/Dropbox/code$ rfkill list
    0: acer-wireless: Wireless LAN
            Soft blocked: no
            Hard blocked: no
    1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
```

And 

    ```
tasdik@Acer:~/Dropbox/code$ sudo bluetoothd -d -n
    bluetoothd[18809]: Bluetooth daemon 4.101
    bluetoothd[18809]: src/main.c:p****_config() parsing main.conf
    bluetoothd[18809]: src/main.c:p****_config() discovto=0
    bluetoothd[18809]: src/main.c:p****_config() pairto=0
    bluetoothd[18809]: src/main.c:p****_config() pageto=8192
    bluetoothd[18809]: src/main.c:p****_config() auto_to=60
    bluetoothd[18809]: src/main.c:p****_config() name=%h-%d
    bluetoothd[18809]: src/main.c:p****_config() class=0x000100
    bluetoothd[18809]: src/main.c:p****_config() Key file does not have key 'DeviceID'
    D-Bus setup failed: Name already in use
    bluetoothd[18809]: Unable to get on D-Bus
```


Because of it I am not able to transfer files between my PC and mobile devices. 

Any ideas guys?

---

