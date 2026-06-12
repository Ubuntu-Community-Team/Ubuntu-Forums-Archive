---
title: "Can't get COM port to show up in WinXp Virtualbox"
date: 2010-04-16
forum: Hardware
---

### Post by johnnybeem on 2010-04-16
I'm running Ubuntu 9.10 and installed a Windows XP virtual machine which runs in VirtualBox OSE. I'm trying to set a virtual COM port to pipe to a file just so that I can check the serial output of a Windows program.

I configured VirtualBox to enable COM1 as a host pipe to /tmp/vboxcom1. The "Create Pipe" box is checked. The problem is very simple, the pipe looks to be created on the Ubuntu side, but no COM ports show up in the Device Manager on Windows.

$ file /tmp/vboxcom1 
/tmp/vboxcom1: socket

I hate Windows as much as you do, haha but unfortunately have to use it for this application... Please help if you can, thanks.

---

### Post by johnnybeem on 2010-04-24
Anyone?

---

### Post by P4man on 2010-04-24
Maybe a silly suggestion, but even if it doesnt show up, maybe it does work? 
Have you tried sending anything to com1 ?

---

### Post by johnnybeem on 2010-04-25
I've tried opening hyperterminal but the COM ports don't show up so I can't send to them in this way...

---

