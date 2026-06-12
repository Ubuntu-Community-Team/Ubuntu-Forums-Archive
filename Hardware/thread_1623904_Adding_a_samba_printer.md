---
title: "Adding a samba printer"
date: 2010-11-17
forum: Hardware
---

### Post by fenomenoxp on 2010-11-17
Hello! 
I am trying to install a printer attached to a Windows 7 machine. 

The problem is that, when I try to add the printer through the control panel, it asks me for the URI of the device; which I don't know and don't know where to look up... There is no "scan" button or similar that I can use to detect the printer shared by the Windows PC.

Where should I look for the URI of the device? Or am I missing something?

Thanks in advance

---

### Post by IcarusR on 2010-11-17
URI for the device is the ip address. Below is the URI for my epson printer connected to my server.

> ipp://xxx.yyy.zzz.65:631/printers/Stylus-COLOR-600	

See this page for printer sharing setup.

[https://help.ubuntu.com/community/WindowsXPPrinter]("https://help.ubuntu.com/community/WindowsXPPrinter")

You will need to install SAMBA packages.

---

### Post by Morbius1 on 2010-11-17
Is the printer on Win7 shared? 
[http://windows.microsoft.com/en-US/windows7/Share-a-printer](http://windows.microsoft.com/en-US/windows7/Share-a-printer)

If you can't connect to it using "Windows Printer via Samba" in the Ubuntu printer configuration utility then try adding it directly using one of the following URI examples:
```
smb://WORKGROUP_NAME/MACHINE_NAME/PrinterName
smb://MACHINE_NAME/PrinterName
smb://192.168.0.100/PrinterName
```

---

### Post by fenomenoxp on 2010-11-18
thanks! Finally got it to work by adding directly the uri!

---

### Post by kliffs on 2010-11-18
Good to hear! Usually if all the right setting are enabled and the printer is shared it should automatically be detected.:confused:

---

