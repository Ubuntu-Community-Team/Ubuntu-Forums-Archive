---
title: "Plantronics USB Dongle not recognized"
date: 2015-01-03
forum: Hardware
---

### Post by Neal_Johnson on 2015-01-03
I am new to Ubuntu.  I have successfully installed Unbuntu 14.04 and really like it.  It has revitalized an older laptop which I have inherited and I am really pleased.  However, I was hoping to use my Plantronics 995 Wireless headphones, but when I pluge the dongle into the USB port the device is not recognized in the Sound settings.  I searched the posts and it appears that the headphones may work, but all the other posts seem to at least see the device.

---

### Post by Bucky Ball on 2015-01-03
Welcome. With the USB dongle plugged in, can you open a terminal and issue:

```
lsusb
```

Hit return and show us the output from that. It should tell us whether the dongle is recognised by the system or not and we can work from there. ;)

---

### Post by Neal_Johnson on 2015-01-08
I can.  Here's what I see:

neal@neal-VGN-N160G:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
neal@neal-VGN-N160G:~$

---

### Post by Bucky Ball on 2015-01-09
This is possibly it:

```
 Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
```

Will do some digging, but we have some experts about that may get in before me and work this out for you.

---

### Post by Neal_Johnson on 2015-01-10
I ran the code you left a terminal and this is what I happened:

neal@neal-VGN-N160G:~$ Bus 002 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
No command 'Bus' found, did you mean:
 Command 'bus' from package 'atm-tools' (universe)
Bus: command not found
neal@neal-VGN-N160G:~$

---

### Post by Bucky Ball on 2015-01-11
Sorry, not code. It was from the output of 'lsusb' and think that's the device. Have been scarce for a few days but will have a look about shortly and see what I can find.

---

