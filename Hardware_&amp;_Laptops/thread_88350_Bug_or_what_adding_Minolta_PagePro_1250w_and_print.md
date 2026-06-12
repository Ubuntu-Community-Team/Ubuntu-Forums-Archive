---
title: "Bug or what: adding Minolta PagePro 1250w and printing"
date: 2005-11-10
forum: Hardware &amp; Laptops
---

### Post by muchio on 2005-11-10
Hi, sorry for duplicating the post, but I can't stay with Ubuntu without being capable to print :( ...
I have Minolta PagePro 1250W usb printer, fresh Ubuntu 5.10 on AsusA2500L laptop.
1. I'm able to add this printer.
2. It binds to the serial insteal of usb. I failed to change port.
3. Unable to print.

Here's some stats:
```
marius@home:~$ lsusb
Bus 004 Device 005: ID 2821:5002
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 004: ID 0409:0040 NEC Corp.
Bus 003 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 0686:3006 Minolta Co., Ltd
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0461:4d03 Primax Electronics, Ltd Kensington Mouse-in-a-box
Bus 001 Device 001: ID 0000:0000
```

Could you help me, please.
Cheers!

---

### Post by rjwood on 2005-11-10
see my reply at this thread
[http://www.ubuntuforums.org/showthread.php?t=88337](http://www.ubuntuforums.org/showthread.php?t=88337)

I hope this helps

---

### Post by muchio on 2005-11-10
[QUOTE=rjwood]see my reply at this thread
[http://www.ubuntuforums.org/showthread.php?t=88337](http://www.ubuntuforums.org/showthread.php?t=88337)

I hope this helps[/QUOTE]

Thanks for your tips, but it didn't help. I'm totally lost, because when I look into printer details via System->Administration->Printing I see that printer location is definately not usb://MINOLTA-QMS/PagePro%201250W, as the foomatic-gui shows.
Maybe I miss something? Weired... I bet it will sound stupid, but should I try Kubuntu? Maybe KDE will handle that damn printer better? :)

P.S. M$ stuff was a bit easyer, but I'm trying hard... ;)

---

### Post by cardo on 2005-11-10
:(  I am having the same problem with Breezy and PagePro 1200W : the printer is installed, but after I try to print a test, the status of printer gets off-line.

I haven't found a solution for a couple of days.

The only fact I know is that this bug is Ubuntu-related, as my printer worked under Mandriva LE 2005 and Suse 10.0 without any extra configuration.

---

### Post by muchio on 2005-11-11
Yeah, this is definately a bug. Someone has already added it to the bugtracker.

---

