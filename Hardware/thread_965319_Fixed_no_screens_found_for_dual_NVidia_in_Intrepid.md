---
title: "Fixed no screens found for dual NVidia in Intrepid"
date: 2008-10-31
forum: Hardware
---

### Post by scottishnarn on 2008-10-31
If you have two nvidia cards (not just two monitors) and when you install the nvidia drivers you get dumped into a terminal then I finally found a solution.

You need to specify the BusID for your card in the xorg.conf file. You can find this by using ```
dmesg | grep nvidia
```

You then add the following line ```
BusID          "PCI:2:0:0"
``` to the device section of your /etc/X11/xorg.conf, obviously replacing 2:0:0 with the BusID of your card.

Thus, my device sections looks like this ```
Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7600 GS] 2"
    Driver         "nvidia"
    BusID          "PCI:2:0:0"
    Screen          0
EndSection
```

---

### Post by mybrownianmotion on 2008-10-31
This didn't work exactly right for me, but by monkeying around with it I managed to get it working :)

When I do dmesg | grep nvidia, instead of returning my bus id, it returns 6 lines of other stuff

[   34.244238] nvidia: module license 'NVIDIA' taints kernel.
[   34.499504] nvidia 0000:02:00.0: enabling device (0000 -> 0003)
[   34.499519] nvidia 0000:02:00.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[   34.499526] nvidia 0000:02:00.0: setting latency timer to 64
[   34.499971] nvidia 0000:01:00.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   34.499975] nvidia 0000:01:00.0: setting latency timer to 64

however, I copied what you put in your xorg into mine, and it almost worked (I could hear the login), so then I tried changing my bus id from the 2 that you have to 1, and I was able to get in. Thanks! 

The hardware drivers say I have a different version of the nvidia driver installed though :confused:

---

### Post by scottishnarn on 2008-11-01
Sorry probably my fault, it did return the bus id, it's just hidden. 

In the line ```
[ 34.499519] nvidia 0000:02:00.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
``` it gives the bus id as 0000:02:00.0 which in nvidia format is 2:0:0

It also gives the id for the other card as 0000:01:00.0 or 1:0:0 as you found out.

So when it almost worked it was enabling your screen on your other card which didn't have a monitor attached. You now need to read the xorg.conf file or search on how to enable SLI. Can't help you there I use my 2 cards to drive 3 monitors.

---

### Post by wgrant on 2008-11-01
Are you both using amd64, by any chance?

---

### Post by scottishnarn on 2008-11-01
I was but I got exactly the same issue when I installed the 32bit version. It was actually the 32bit version I got working. At some point I'm going to have to reinstall the 64bit version (I've got 5GB of memory so I really need the 64bit).

---

### Post by mybrownianmotion on 2008-11-01
I am also using 32 bit version.

---

