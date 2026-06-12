---
title: "Asus S7F Fn+F2 button switches both Wifi and bluetooth"
date: 2015-11-17
forum: Hardware
---

### Post by urrfaust on 2015-11-17
Hi everyone,

I have an Asus S7F (old laptop, cca. 2007) running Ubuntu Vivid with latest kernel.
The problem I have is that on this laptop the Fn+F2 button combination switches both Wifi and Bluetooth on and off at the same time. On Windows 7, the behaviour is different, as you can switch between WIFI/Bluetton ON -> Wifi On Bluetooth Off -> Wifi OFF Bluetooth On -> Wifi/Bluetooth OFF. 
Is there any way I can configure Fn+F2 so that it behaves the same way as on W7?
This is the output of rfkill list

```
rfkill list
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

I know that the driver in use is asus_laptop.

Thanks a lot for helping out

Si.

---

### Post by Vladlenin5000 on 2015-11-17
That was the typical behavior in many laptops from that era. In Windows the hardware switch (FN+F2 in your case) worked in tandem with a software ("driver") switch. The latter enabled the possibility of toggling between the four modes instead of the simple ON/OFF.
AFAIK, there never was such driver for Linux, for ASUS or any other.
You can always use the hardware switch to turn on WiFi and BT then disable one or another using the network or the BT indicators accordingly.

---

### Post by urrfaust on 2015-11-18
Then it must be a problem with the indicators. I'm using Gnome flashback and although it says that bluetooth is off, it is definitely on. Wifi indicator works.

---

### Post by Vladlenin5000 on 2015-11-18
Have you come to the conclusion it's "definitely on" because you searched for BT devices from another device and that one was showing? If so, I agree, there's something wrong.

---

### Post by urrfaust on 2015-11-18
Nope you're right. When the indicator is OFF, it is really off. I tried to connect to another device and it doesn't work.
I assumed it was ON because the bluetooth led is on :-)
So now the problem is: why is the led on when bluetooth is off?
I'll create another thread

---

### Post by Vladlenin5000 on 2015-11-18
The LED probably depends on the same proprietary driver/software we don't have for Linux. I guess you'll have to live with that.

---

