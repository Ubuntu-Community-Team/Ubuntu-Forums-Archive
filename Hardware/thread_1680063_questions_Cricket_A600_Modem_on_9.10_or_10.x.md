---
title: "questions: Cricket A600 Modem on 9.10 or 10.x"
date: 2011-02-01
forum: Hardware
---

### Post by BentFX on 2011-02-01
I've got the Cricket A600 usb modem on 9.10, and it is working OK (2 annoying issues, get to that in a second.)

Biggest question... I've got kernel 2.6.31, is my A600 driver going to work OK in an IPv6 world? If not, I need to get it sorted before the big switch takes place. Any feedback is appreciated!

Now the two annoying issues...

First, if my connection is dropped, I have to unplug and replug the modem to get it to return to a workable state. (or reboot) If I disconnect using the network manager, it will dial out again no problem. But if the connection is broken by cell phone voodoo, I have to force a hard reset of the device by un/replugging it.(flipflop.sh doesn't even recognise it when it's in this state) Does anyone else experience this? Is it fixed in a later kernel?

Second, The modem causes drastic slowdown of boot time (over 1 minute added) (Asus G50VT-X1 laptop). This isn't strictly a Linux issue. Not only does it cause the BIOS POST to drag out to about 15 seconds. It also causes both of my OS's to just kind of hang for about a minute during boot. This seems to be linked directly to the modem hardware. Has anyone else experienced this? Is there maybe a firmware fix?

All replies will be taken seriously(unless they're just foolish :)

-----------------

Arguing on the Internet is like bowling... It is a great pastime... But everybody in the game, is wearing ugly shoes.

---

### Post by BentFX on 2011-02-01
I just dug into it a bit, and am a little more concerned now... When I go into 'connection information' for the A600 it shows all IP values are currently IPv4, as expected. Yet if I go into 'edit connections' in the network manager, my eth0 shows tabs for both IPv4 and IPv6 settings. The A600 only shows a tab for IPv4 settings. This leads me to believe the device or the driver is not IPv6 capable.

Someone, SOMEONE, please... solve my worried mind! :)

---

