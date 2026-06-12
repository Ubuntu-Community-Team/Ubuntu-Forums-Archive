---
title: "Microsoft Bluetooth Mobile Mouse 3600"
date: 2016-05-16
forum: Hardware
---

### Post by sgarman on 2016-05-16
Hello. I bought one of these mice a few months ago and have never been able to get it working on a variety of Ubuntu systems (15.10 and 16.04) running different Bluetooth receivers. The mouse can be set up to work fine under Windows 8 however. 

I've tried using blueman and bluetoothctl, with no success. The closest I've come is getting the mouse to pair using bluetoothctl, but for some reason it is not then recognized as an HID device. I'm curious if anyone has gotten this mouse to work, or might know what it is about the hardware (Bluetooth LE?) that is making it incompatible?

It's a nice piece of hardware, but so far appears to be incompatible with Ubuntu systems. For the time being, it's a paperweight. 

Thanks,

Scott

---

### Post by pioterek01 on 2016-05-20
This worked for me - 15.10

```
hciconfig hci0 sspmode 1
hciconfig hci0 down
hciconfig hci0 up

bluetoothctl
agent KeyboardOnly
default-agent
pair XX:XX:XX:XX:XX:XX
trust XX:XX:XX:XX:XX:XX
connect XX:XX:XX:XX:XX:XX
```

Original:
[http://askubuntu.com/questions/636712/logitech-mx-anywhere-2-mouse-pairs-but-doesnt-do-anything/660918#660918](http://askubuntu.com/questions/636712/logitech-mx-anywhere-2-mouse-pairs-but-doesnt-do-anything/660918#660918)

---

### Post by sgarman on 2016-05-20
Thanks for the reply! However in 16.04, I get the following error when I try to run hciconfig hci0 sspmode 1:

Can't set Simple Pairing mode on hci0: Input/output error (5)

I am however able to run that command without an error on a 15.10 system. So something has changed in the default bluetooth settings in 16.04. Through some web searches it sounds like I need to set security to "none" in /etc/bluetooth/hcid.conf, which I tried. After rebooting I'm still getting the same error. Since the hcid.conf file doesn't exist by default, it's quite possible that I'm not formatting it properly:

```
options {
    autoinit yes;
    security none;
    pairing multi;
    passkey "0000";
}
```

---

### Post by capemayal on 2016-05-22
I have the same mouse on 16.04.  It would work fine for a minute or so, maybe less, then it loses connection, or probably, 16.04 loses the connection.

The only way to work again is to turn BT off and back on.

I have a System76 Lemur.  I asked them, and their response is that BT 4 isn't well supported in 16.04.  Not much of a response.

---

### Post by sgarman on 2016-11-05
I'm happy to report that this mouse works great in Ubuntu 16.10. I guess I'll have to find a new paperweight. ;)

---

### Post by capemayal on 2016-11-18
sgarman - what did you do to get the 360 to work?  I'm using a System76 Lemu6.  The 3600 connects, then disconnects.  I've installed, rebooted.  Uninstalled, rebooted.  Installed again, rebooted.  Still the same results.  An answer from S76, when I got this lappy is that BT isn't supported very well in 16.10.

---

### Post by sgarman on 2016-11-18
Hi capemayal - I tested the mouse by running the Xubuntu 16.10 live image, and used blueman-applet. I just added the mouse using the typical workflow for any other BT device - I put the mouse in pairing mode by long-pressing the power button, scanned for new devices in blueman-applet, and paired and added it using the GUI. I tried turning the mouse off and on again a few times to confirm it re-connected successfully. My laptop is still running 16.04 until I have time to upgrade to 16.10 in a couple of weeks. Hope this info is helpful.

---

