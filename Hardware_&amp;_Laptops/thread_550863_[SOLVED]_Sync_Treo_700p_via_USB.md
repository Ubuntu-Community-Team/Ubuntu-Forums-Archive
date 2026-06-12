---
title: "[SOLVED] Sync Treo 700p via USB"
date: 2007-09-14
forum: Hardware &amp; Laptops
---

### Post by MarkLori on 2007-09-14
I'm using a Dell Latitiude C640 that is a 100% Ubuntu platform.  It has 1 USB port (old slow version).  
When I hook my Treo to the port I can see it come up in the Hardware Information Screen under the System Menu.  I cannot figure out how to make jPilot connect to it though.  I'm not sure what interface it sets up on (/dev/sda?).  I have tried all of them from jPilot but just keep getting errors about not being able to bind.  Basically all I can tell is that it is connected and the system sees it, but I can't figure out how to get it to sync to anything.  I'm not sure if it's a username issue, port issue or what but I've tried all I can think of.  

I can see that others have had similar issues, but the only real success I've seen on other posts is on bluetooth which I don't have.

Any help?

Thanks,
Mark:confused:

---

### Post by linuxwizard on 2007-09-14
You need to add module visor in Ubuntu 7.04. Look on this page for:: Notes for Releases. It tells you what you need to do. Follow the link there

[https://help.ubuntu.com/community/PortableDevices/PalmOS](https://help.ubuntu.com/community/PortableDevices/PalmOS)

---

### Post by uclalinux on 2007-09-25
install J-Pilot and under J-Pilots, File> Preferences>Settings where you see serial port type in "usb:" 

That should be it, then press the hot sys button on the J-pilot and then on your treo

---

### Post by jppaynesr on 2007-09-28
usb:
type that under preferences/settings/serial port. it will work.

---

### Post by MarkLori on 2007-10-02
Thanks all for the help!  Life is good.

---

