---
title: "Debugging audio bluetooth problems"
date: 2014-07-21
forum: Hardware
---

### Post by dargaud2 on 2014-07-21
Hello all,
I have new bluetooth speakers (Loewe Speaker 2 Go) which work fine on my 2 Android devices and my HP laptop running latest kubuntu.
But my Dell Precision M6700, which is actually the computer I want to use it from, has trouble.

I first used the default KDE config, bluedevil, and it would connect, play for about 10 minutes, then the sound would be all hacked up for a minute, the device would disconnect, reconnect and it would do it all over again. And I tried watching a movie, there was a horrible 2s delay on the audio.

So I followed this ([http://www.tooleweb.ca/blog/?e=8](http://www.tooleweb.ca/blog/?e=8)) and now with blueman it's even worse: it connects for 2~5 seconds and disconnects right away. Signal strength is 45%, Link quality 100%, transmit power 51%...

How can I diagnose this issue ?!? Is the Dell bluetooth device worthless ?

```
$ dmesg | grep -i blue
[    8.600782] Bluetooth: Core ver 2.17
[    8.600801] Bluetooth: HCI device and connection manager initialized
[    8.600807] Bluetooth: HCI socket layer initialized
[    8.600810] Bluetooth: L2CAP socket layer initialized
[    8.600813] Bluetooth: SCO socket layer initialized
[    8.607537] Bluetooth: can't load firmware, may not work correctly
[    8.751789] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    8.751791] Bluetooth: BNEP filters: protocol multicast
[    8.751798] Bluetooth: BNEP socket layer initialized
[    8.752395] Bluetooth: RFCOMM TTY layer initialized
[    8.752403] Bluetooth: RFCOMM socket layer initialized
[    8.752407] Bluetooth: RFCOMM ver 1.11

# When connecting:
[ 6721.147980] input: 00:1D:DF:67:58:F7 as /devices/virtual/input/input21

```

---

### Post by dargaud2 on 2014-07-21
Beuh... I desinstalled all bluetooth components, reinstalled them and bluedevil and now it works... go figure.

---

