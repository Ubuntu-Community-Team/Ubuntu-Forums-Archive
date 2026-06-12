---
title: "Installing printers on 7.10 in command line"
date: 2008-04-10
forum: Hardware &amp; Laptops
---

### Post by webbyfeet on 2008-04-10
Hello,

I'm seeting up a small office network and I'm setting up a printer server.
This is the environtment:

[LIST]OS: Ubuntu 7.10 - 64bit AMD and Intel computers alternate desktop CD.
[/LIST][LIST]
[*]Machine : DELL PowerEdge T105 - Dual Core Opteron 1214, 2.2GHz, 2X1MB Cache
[/LIST]

I'm a trying to install two printers on this machine:
 
[LIST]
[*]Epson EPL-6200L
[/LIST]
[LIST]
[*]Dell 3110 CN
[/LIST]

I haven't been able to get the GUI to function properly yet so I'm using command line. I do however have a webmin system going. You've probably guessed I'm a newby and need some help... but I can read any documentation you may point me to taht would help me out.

When I use the **lpinfo -v** command, I get:

[INDENT]network socket
network beh
direct usb://Dell/Color%20Laser%203110cn
direct usb://EPSON/EPL-6200L
direct epson:/dev/usb/lp0
direct hpfax
direct hp
network http
network ipp
network lpd
direct scsi
network smb[/INDENT]

Then I retreived the drivers .ppd files and put them in the usr/share/ppd/cups-included/ directory.

following this I did the commands: 

[LIST]
[*]sudo lpadmin -E -p EPL6200L -v epson:/dev/usb/lp1 -P /usr/share/ppd/cups-included/Epson/epl6200.ppd -u allow:all
[/LIST]
[LIST]
[*]sudo lpadmin -E -p Dell3100cn -v usb://Dell/Color%20Laser%203110cn -P /usr/share/ppd/cups-included/dl3100cn.ppd -u allow:all
[/LIST]
[LIST]
[*]sudo lpadmin -E -p EPL6200L -v usb://EPSON/EPL-6200L -P /usr/share/ppd/cups-included/Epson/epl6200.ppd -u allow:all
[/LIST]

If I then go to the Webmin interface the two printers are there, but If I try to print a test page I get:

Printing test page with command lpr -PEPL6200L bw\.ps ..
.. command failed!
Printing test page with command lpr -PDell3100cn bw\.ps ..
.. command failed!

I must be missing some stage or have done something wrong, can anyone help?

---

