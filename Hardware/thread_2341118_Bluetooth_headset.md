---
title: "Bluetooth headset"
date: 2016-10-25
forum: Hardware
---

### Post by vanili on 2016-10-25
Hi!

My bluetooth headset behaves a bit strange. I can connect it and even can see it in the sound settings, however, trying to run a test sound in settings (or any sound at all) produces just some noise. Running an application with sound effects (e.g. media player), results in freeze of the application, and it unfreezes only when the headset is disconnected or default audio device is changed. 

The same headset works fine on the same Ubuntu version (even the same computer), when I use an external bluetooth-usb adapter and connect the headphone with it. 

I've tried different sound settings, but still no solution. I am really puzzled how it can be. It probably may be explained with the bluetooth back compatibility issues (internal bluetooth device is 4.1 and usb is 2.1), but officially bluetooth version should be fully compatible... 

Any ideas what can it be, and how to make the headset work?

```
$uname -a
Linux 4.4.0-36-generic #55-Ubuntu SMP Thu Aug 11 18:01:55 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

$hciconfig
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 68:14:01:4A:A0:08  ACL MTU: 1024:8  SCO MTU: 50:8
    UP RUNNING 
    RX bytes:723 acl:0 sco:0 events:52 errors:0
    TX bytes:3209 acl:0 sco:0 commands:52 errors:0
```

---

### Post by jeremy31 on 2016-10-25
This is the result of changes to bluez and pulseaudio.  Later I will edit and add a terminal command that works for me to switch

```
pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` off; sleep 2 ; echo -e "disconnect MAC_ADDRESS\n quit"|bluetoothctl;sleep 5; echo -e "connect MAC_ADDRESS\n quit"|bluetoothctl; sleep 5; pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` a2dp_sink
```

Just replace MAC_ADDRESS with the MAC of your audio device, you can find it in bluetooth manager or using ```
bluetoothctl
``` Use capital letters in the MAC and use CTRL + d to quit bluetoothctl

---

### Post by vanili on 2016-10-26
Thank you very much for help.

I'll try it a bit later and after will come back telling if it worked or not

---

### Post by vanili on 2016-10-26
unfortunately this solution did not work...

```
pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` off; sleep 2 ; echo -e "disconnect 00:1A:7D:71:3E:6F\n quit"|bluetoothctl;sleep 5; echo -e "connect 00:1A:7D:71:3E:6F\n quit"|bluetoothctl; sleep 5; pacmd set-card-profile `pacmd list-cards | grep bluez_card -B1 | grep index | awk '{print $2}'` a2dp_sink
[NEW] Controller 68:14:01:4A:A0:08 ubuntu [default]
[NEW] Device 00:1A:7D:71:3E:6F BH100
[bluetooth]# disconnect 00:1A:7D:71:3E:6F
Attempting to disconnect from 00:1A:7D:71:3E:6F
[bluetooth]#  quit
[DEL] Controller 68:14:01:4A:A0:08 ubuntu [default]
[NEW] Controller 68:14:01:4A:A0:08 ubuntu [default]
[NEW] Device 00:1A:7D:71:3E:6F BH100
[bluetooth]# connect 00:1A:7D:71:3E:6F
Attempting to connect to 00:1A:7D:71:3E:6F
[bluetooth]#  quit
[DEL] Controller 68:14:01:4A:A0:08 ubuntu [default]
No such profile: a2dp_sink

```

I also tried what is described here
[URL="http://askubuntu.com/questions/775523/after-updating-to-16-04-bluetooth-audio-a2dp-mode-stopped-working"]http://askubuntu.com/questions/775523/after-updating-to-16-04-bluetooth-audio-a2dp-mode-stopped-working
[/URL]but headset is still not working...

---

