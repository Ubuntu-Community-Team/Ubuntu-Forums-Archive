---
title: "Bluetooth don't work"
date: 2020-09-22
forum: Hardware
---

### Post by jonik2018 on 2020-09-22
[[IMG]https://imageup.ru/img169/3658159/screenshot-from-2020-09-23-06-11-17.png[/IMG]]("https://imageup.ru/img169/3658159/screenshot-from-2020-09-23-06-11-17.png.html")

In setting i can't switch on bluetooth.

[HTML]
systemctl status bluetooth.service
&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
     Active: inactive (dead)
       Docs: man:bluetoothd(8)
[/HTML]

---

### Post by &amp;wP*!) on 2020-09-26
Check whether Bluetooth was disabled in BIOS/UEFI. If yes, enable it. If it is not possible to enable it, it can mean your firmware does not support it. Try to update your BIOS firmware. If this still does not solve your problem, then there is nothing you can do.

If it was enabled, reboot and check whether the system service is enabled now. 

if not, then run following commands:
```
systemctl start bluetooth.service
systemctl enable bluetooth.service
```

After that try to connect your Bluetooth device.

Tell us whether the tips above solve your problem.

---

### Post by jonik2018 on 2020-09-30
> Check whether Bluetooth was disabled in BIOS/UEFI. If yes, enable it. If it is not possible to enable it, it can mean your firmware does not support it.

In previous system Win10 Bluetooth ran without BIOS settings, so I don't think that problem is there.

> if not, then run following commands:

don't help

---

### Post by cigtoxdoc on 2020-10-06
What does the following mean?  I have not been able to use bluetooth with my LG SH3K(C8) soundbar and speaker since there was an upgrade to Ubuntu last week -- 1 OCT 2020.   Moreover, it does not only affect current PC (Dell Vostro 3500 with either Targus or brand new Plugable USB adapters, but the same thing happens on my hp E842 laptop, which has built-in Bluetooth.  That machine is dual-boot Ubuntu 20.04 and Win 10 64.  When running Win 10, Bluetooth works fine.

What do I need to do to get Ubuntu to work with my speakers?

Thank you,

John


johnl@john-Vostro-3500:~$ systemctl status bluetooth.service
&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2020-10-06 18:33:37 EDT; 6min ago
       Docs: man:bluetoothd(8)
   Main PID: 819 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 9323)
     Memory: 2.3M
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;819 /usr/lib/bluetooth/bluetoothd

Oct 06 18:33:50 john-Vostro-3500 bluetoothd[819]: Endpoint registered: sender=:1.64 path=/MediaEndpoint/A2DPSink/sbc
Oct 06 18:33:50 john-Vostro-3500 bluetoothd[819]: Endpoint registered: sender=:1.64 path=/MediaEndpoint/A2DPSource/sbc
Oct 06 18:38:38 john-Vostro-3500 bluetoothd[819]: /org/bluez/hci0/dev_08_EF_3B_6F_49_C8/sep1/fd0: fd(32) ready
Oct 06 18:38:54 john-Vostro-3500 bluetoothd[819]: Suspend: Connection timed out (110)
Oct 06 18:39:04 john-Vostro-3500 bluetoothd[819]: Suspend: Connection timed out (110)
Oct 06 18:39:06 john-Vostro-3500 bluetoothd[819]: Abort: Connection timed out (110)
Oct 06 18:39:29 john-Vostro-3500 bluetoothd[819]: /org/bluez/hci0/dev_08_EF_3B_6F_49_C8/sep1/fd1: fd(32) ready
Oct 06 18:39:45 john-Vostro-3500 bluetoothd[819]: Suspend: Connection timed out (110)
Oct 06 18:39:55 john-Vostro-3500 bluetoothd[819]: Suspend: Connection timed out (110)
Oct 06 18:39:57 john-Vostro-3500 bluetoothd[819]: Abort: Connection timed out (110)
johnl@john-Vostro-3500:~$

---

### Post by jonik2018 on 2020-10-07
[this works](https://webwiks.com/techcorner/get-ralink-rt3290-bluetooth-work-in-linux/)
But after reboot module Ralink rt3290 (rtbth) doesn't run automatically and it's next issue.

---

