---
title: "ipod not recognised in lucid"
date: 2010-07-21
forum: Hardware
---

### Post by lister171254 on 2010-07-21
I have two systems both running 64bit lucid.

One of the systems recognises when I plug in the ipod and handles that event as expected, the other system does not log any events when I plug the ipod in. I know that it's plugged in and the usb connections works as the battery on the ipod charges.

Does anybody have any ideas/suggestions?

---

### Post by csoler on 2010-07-21
Look if you see a process called usbmuxd running:

ps -u root | grep usbmuxd

if not, then launch it in foreground, and see what it prints when you plug your ipod:

sudo /usr/sbin/usbmuxd -f

Normally this device handler is launched automatically when you plug your ipod, according to the rules in  /lib/udev/rules.d/85-usbmuxd.rules

You can also chez that the 85-usbmuxd.rules file really exists on your PC. If not, then there is an instalation problem somewhere.

---

### Post by quantumottle on 2010-07-25
I've been trying for 2 weeks to figure out why my iPod no longer mounts - but I continuously run into threads like this one that come to a sudden dead end with no conclusion. Very frustrating indeed...


---------------

[I FINALLY found a solution]("http://wwww.ubuntuforums.org/showthread.php?p=9636742#post9636742"), it worked for me anyway.

---

