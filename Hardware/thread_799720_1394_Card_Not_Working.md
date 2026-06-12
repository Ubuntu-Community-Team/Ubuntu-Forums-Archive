---
title: "1394 Card Not Working"
date: 2008-05-19
forum: Hardware
---

### Post by hodenkat on 2008-05-19
One of my last hurtles in crossing over completely to Ubuntu is getting my videos from my DV camcorder to my laptop. Here's the issue - My laptop is a few years old and does not have built-in FireWire (IEEE-1394). I bought a PCMCIA to IEEE-1394 adapter card that works great in Windows, In Ubuntu Hardy using Kino the card is not even recognized. I've loaded all the packages I could find but with no success.

Is there anybody out there who has the same thing but has gotten it to work? What card are you using? Or, how did you get it to work if it didn't work the first time?



Thanks!

---

### Post by hodenkat on 2008-06-02
Ahhh...nevermind.

I get it now. Kino is broken and it looks like no solution is in sight. It needs raw1394 control and since I've been all across this great board looking for answers and tried everything I've found with no success, I think it's just better to use Windows for video capture. Maybe in a few months somebody will get Kino fixed and make a lot of people happy!
:lolflag:

---

### Post by blackdalek on 2008-07-06
I have the same problem, and the firewire support in Kino is not broken. Support for your particular PCMCIA firewire card is broken. 
I too am trying (so far without success) to find a working PCMCIA firewire card for my laptop.
Firewire in Kino works perfectly for almost every PCI firewire card in regular desktop PCs. Which is fine, but I want to be able to upload videos from my cam while I'm away from home with my laptop.
If anyone has any clues as to where I can find a working PCMCIA firewire card, please let us know.

---

### Post by Erlander on 2008-07-06
In a terminal window try 
```

gksudo kino
```

Rob

---

### Post by dotweb on 2008-07-20
Thanks :) you just saved me.
We can now produce our video in time using Linux insted of Windows.

---

### Post by daniele.rosa on 2008-07-20
A workaround ...

Loading the module raw1394 in the kernel:
modprobe raw1394
and changing the permission to the device raw1394 from:
crw-rw---- 1 root disk 171, 0 2008-07-20 09:23 /dev/raw1394
to
crw-rw-rw- 1 root disk 171, 0 2008-07-20 09:23 /dev/raw1394
using chmod 666 /dev/raw1394 makes kino usable by the desktop user.

---

### Post by dotweb on 2008-07-20
Thanks - Testet on a pc not used right now - now it even works with cinnelera - Great

//dotweb

---

