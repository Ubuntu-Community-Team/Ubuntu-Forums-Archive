---
title: "Hardy + XP Svc pack 3 + Seamless RDP"
date: 2008-10-20
forum: General Help
---

### Post by jona7han on 2008-10-20
I'm really struggling in getting Seamless RDP to work correctly in my setup. I have XP Service pack 3 installed on a PC, I downloaded and installed the Seamless RDP app to c:\seamlessrdp as per the documentation on the web. I enabled Remote Desktop. I use the this command that I got from this forum and other places on my Hardy install:

rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\notepad.exe" 10.40.0.87:3389 -u *** -p ***

But everytime rather than notepad opening up it opens RDP full screen and logs in. It doesn't load notepad either.

Is there anything I've missed, I really want to get this feature working.

thanks

---

### Post by nikolko on 2008-10-23
Hi,

I faced with the same problem, have no idea how to fix it.

---

### Post by oreomike on 2008-11-11
I can't tell you how frustrating this is.  I've spent at least 15 minutes every hour for the last 8 hours trying to get this thing working and still get some work done.

I'm connecting to a remote XP machine, not a virtual one.  I can't seem to figure out if it is an Ubuntu problem or an XP one.

I'm running 2.6.24.21 Ubuntu 8.04, rdesktop 1.5, and XP SP3.  grr. Maybe this will go away once I get Vista.

Anyone have any ideas?

---

### Post by cariboo on 2008-11-11
I not sure about Seamless RDP, but I've had good luck using vnc. VNCserver is available for windows and linux and it works seamlessly. You can get Realvnc here:

[http://www.realvnc.com/products/free/4.1/winvnc.html](http://www.realvnc.com/products/free/4.1/winvnc.html)

and tightvncserver is available in the repositoires.

Jim

---

### Post by oreomike on 2008-11-11
Well, for those who cannot choose alternate products and are forced to pick certain 'enterprise security approved' applications and operating systems, lets keep this thread on track and avoid 'you should use x instead' comments.

I've seen other folks say a reinstall worked for them, but a reinstall of what, they don't say.  I've downloaded the seamlessrdp stuff twice, but there is no 'install', just an unpack of the zip file.  Perhaps I need to get the source, but I don't have someting to build with.

I have McAfee and the Windows Firewall running on the XP machine, but neither shows any problems in the logs.

---

### Post by dignus on 2008-12-03
Same problem here, with x86 Ibex...

---

