---
title: "microphone and bluetooth not work with HP laptop VICTUS 8"
date: 2023-05-07
forum: Hardware
---

### Post by tianfan on 2023-05-07
OS is ubuntu 22.04
The Speaker work well,but the sound input device not work.
setting->sound->input .the option “input device" is blank.
no matter  the Integrated microphone of the laptop or plug the earphone&#12290;




```
head -n 1 /proc/asound/card2/codec*
Codec: Realtek ALC245
```

```
head -n 1 /proc/asound/card1/codec*Codec: ATI R6xx HDMI

```

when i start it with Windows 11,the speaker and microphone work well and  I found that the Speaker of this laptop work with Realtek ALC245 & sound input work with AIT R6xx HDMI
I don't know why the microphone not wok in Ubuntu .

bluetooth dosen't work. there is some information :

```

systemctl status bluetooth


&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor pre>
     Active: active (running) since Sat 2023-05-06 16:35:59 CST; 1 day 8h ago
       Docs: man:bluetoothd(8)
   Main PID: 813 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 18153)
     Memory: 1.4M
        CPU: 37ms
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;813 /usr/lib/bluetooth/bluetoothd


5&#26376; 06 16:35:58 Victus8 systemd[1]: Starting Bluetooth service...
5&#26376; 06 16:35:59 Victus8 bluetoothd[813]: Bluetooth daemon 5.64
5&#26376; 06 16:35:59 Victus8 bluetoothd[813]: Starting SDP server
5&#26376; 06 16:35:59 Victus8 systemd[1]: Started Bluetooth service.
5&#26376; 06 16:35:59 Victus8 bluetoothd[813]: Bluetooth management interface 1.22 initialized




```


```


bluetoothctl scan on
No default controller available



```

---

### Post by tianfan on 2023-08-08
anyone who know how to fix it

---

