---
title: "broadcom 2045 bluetooth not discovering devices"
date: 2018-12-05
forum: Hardware
---

### Post by markwinger on 2018-12-05
I just installed ubuntu studio on an old hp pavilion db9000.  I got everything working except the built in bluetooth.

I am able to plug a usb bluetooth dongle in it works fine so I am trying to figure out how to get the internal bluetooth to work.

I have installed ubuntu studio:
$ uname -a
Linux luke-HP-Pavilion-dv9000-EW680AV-ABA 4.15.0-20-lowlatency #21-Ubuntu SMP PREEMPT Tue Apr 24 08:11:51 UTC 2018 i686 athlon i686 GNU/Linux

I have never worked with bluetooth on linux before so I am not sure what to post that may help figure out how to fix the problem.

The bluetooth is a broadcom bcm 2045.   Ran some commands I found on trouble shooting but not sure what it all means.  What else should I add to help identify the problem.

$lsmod | grep bluetooth
bluetooth             466944  41 btrtl,btintel,bnep,btbcm,rfcomm,btusb
ecdh_generic           28672  1 bluetooth

$rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
7: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

$sudo systemctl status bluetooth
bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2018-12-04 21:08:48 CST; 11h ago
     Docs: man:bluetoothd(8)
 Main PID: 3732 (bluetoothd)
   Status: "Running"
    Tasks: 1 (limit: 4553)
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;3732 /usr/lib/bluetooth/bluetoothd

Dec 05 08:36:54 luke-HP-Pavilion-dv9000-EW680AV-ABA bluetoothd[3732]: HID Information read failed: Request attribute has encountered an unlikely error
Dec 05 08:36:54 luke-HP-Pavilion-dv9000-EW680AV-ABA bluetoothd[3732]: Protocol Mode characteristic read failed: Request attribute has encountered an unlikely error
Dec 05 08:36:54 luke-HP-Pavilion-dv9000-EW680AV-ABA bluetoothd[3732]: Read Report Reference descriptor failed: Request attribute has encountered an unlikely error
Dec 05 08:36:54 luke-HP-Pavilion-dv9000-EW680AV-ABA bluetoothd[3732]: Read Report Reference descriptor failed: Request attribute has encountered an unlikely error
Dec 05 08:36:54 luke-HP-Pavilion-dv9000-EW680AV-ABA bluetoothd[3732]: Read Report Reference descriptor failed: Request attribute has encountered an unlikely error
Dec 05 08:36:54 luke-HP-Pavilion-dv9000-EW680AV-ABA bluetoothd[3732]: Read Report Reference descriptor failed: Request attribute has encountered an unlikely error
Dec 05 08:36:54 luke-HP-Pavilion-dv9000-EW680AV-ABA bluetoothd[3732]: Report Map read failed: Request attribute has encountered an unlikely error
Dec 05 08:36:54 luke-HP-Pavilion-dv9000-EW680AV-ABA bluetoothd[3732]: HID Information read failed: Request attribute has encountered an unlikely error
Dec 05 08:36:58 luke-HP-Pavilion-dv9000-EW680AV-ABA bluetoothd[3732]: Endpoint unregistered: sender=:1.34 path=/MediaEndpoint/A2DPSource
Dec 05 08:36:58 luke-HP-Pavilion-dv9000-EW680AV-ABA bluetoothd[3732]: Endpoint unregistered: sender=:1.34 path=/MediaEndpoint/A2DPSink


The device appears to work partially.  I started bluetoothctl and was able make the device visable to my phone.  If I tried to pair with my phone the phone askes for a pid but the laptop does not tell me the pid.  I tried 0000 and 1234 and i get invalid pid.

I tried lookig for device specific drivers for the broadcom and their website says they dont have them and I need to get them from microsoft.  I downloadded and extracted a set of windows files and tried installing them with ndiswrapper.  The extract has many .inf files and one of them installed but made no difference.  I don't have any idea what to do next.  Any ideas?

Thanks, Mark.

UPDATE-I was just looking around and the I started to wonder if it had to do with the bluetooth devices I am trying to connect with.  The device am an interested in is an adafruit feather blue lte.  This is a Low Energy device.  Maybe the braodcom 2045 does not support this newer protocol.  Any one know?

---

### Post by markwinger on 2018-12-07
I was correct.  I just successfully paired it with an old bluetooth  2.0 speaker.  Problem Solved

---

