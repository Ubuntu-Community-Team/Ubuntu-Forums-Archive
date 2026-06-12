---
title: "Trying to connect to a windows shared printer without success"
date: 2015-04-20
forum: Hardware
---

### Post by kidzstang on 2015-04-20
I have an HP Deskjet 9800 connected to a Windows XP computer connected to a windows domain running on a Windows 2000 server. I am trying to print using that printer from a Ubuntu 14.04 computer connected to the domain using Likewise. I have tried to install the printer connection on the Ubuntu machine  using System Settings -----> Printers ------> Add -----> Network Printer -----> Windows Printer via SAMBA. I can see the printer and connect to it. I can verify that I have connection but when I go to the next step to apply the driver nothing happens. I can scroll through the manufacturers but cannot pick (highlight) any of them. The system then seems to go unresponsive for a very long time. Any suggestions here?

I also downloaded HPLIP-3.14.4 but I'm sure what it is really doing. It seems that I needed to attach the printer to the ubuntu computer for it to install the driver but I'd like to keep the printer connected to the Win XP computer. 

I'm lost - any help would be appreciated.

Thanks in advance,
Jack

---

### Post by gordintoronto on 2015-04-21
Have you looked at this page:
[http://hplipopensource.com/hplip-web/models/deskjet/deskjet_9800.html](http://hplipopensource.com/hplip-web/models/deskjet/deskjet_9800.html)

Is this domain connected to the Internet? You're running systems which have not had security updates for some time, so it would be prudent to keep them disconnected.

You might consider connecting the printer to your Ubuntu machine just to get the driver installed. Even though the printer is 10 years old, it should still work.

---

