---
title: "CUPS USB Problem - HP Laserjet 1200"
date: 2008-09-07
forum: Hardware
---

### Post by briantipton on 2008-09-07
I am having a problem.  I have recently moved to a new system for our Home File/Print server and am trying to get CUPS configured.  I had it working under 7.04, but I cannot for the life of me get it working in 8.04.  I have CUPS configured and accessible via the web interface, but cannot add a printer.

While troubleshooting as best as I could, I discovered that my Laser printer can only be seen as root.

lsusb as normal user gives:
```
brian@isaiah:/dev$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 051d:0002 American Power Conversion Uninterruptible Power Supply 
Bus 001 Device 001: ID 0000:0000
```

But when I do the following:
```
brian@isaiah:/dev$ sudo lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 03f0:0317 Hewlett-Packard LaserJet 1200
Bus 001 Device 004: ID 051d:0002 American Power Conversion Uninterruptible Power Supply 
Bus 001 Device 001: ID 0000:0000 
```

I don't remember my previous box needing root access to see the printer.

Please help.

Brian Tipton

---

### Post by phidia on 2008-09-07
What does "lpinfo -v" output?

You could try to add your printer using CUPS webinterface instead of gnome-cups-manager, to do this type [http://localhost:631](http://localhost:631) in firefox.

---

### Post by briantipton on 2008-09-08
Thanks for your help.

> **phidia said:**
> What does "lpinfo -v" output?

Here is my output:
```
brian@isaiah:~$ lpinfo -v
network socket
network beh
direct hpfax
direct usb://HP/LaserJet%201200
direct hp:/usb/HP_LaserJet_1200?serial=00CNC6063798
network http
network ipp
network lpd
direct scsi
network smb

```



> 
You could try to add your printer using CUPS webinterface instead of gnome-cups-manager, to do this type [http://localhost:631](http://localhost:631) in firefox.

I do not have gnome installed. It is just a vanilla server box with no graphical interface.  I just connect to it through SSH.  I have tried to configure a printer via the http://<server>:631.  I can get through the part where I select a driver then it hangs and never creates the printer.

I am very thankful for your help.

**UPDATE**

I just tried adding the queue again.  The CUPS admin program still hangs (never reloads), but if you let it go a very long time, it creates the queue.  I reloaded the admin page and, presto, my queue exists.  I wonder if this is a bug or what?

Thanks for the help.

---

