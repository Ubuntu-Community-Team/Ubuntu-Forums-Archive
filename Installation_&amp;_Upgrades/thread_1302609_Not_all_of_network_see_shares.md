---
title: "Not all of network see shares"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by jaxinabox on 2009-10-27
I have 2 winxp machines and 3 ubuntu 9.04 on network. One of them I use as files server (and would like as print server). The 2 winxp PCs can see the server and functions properly, but the 2 other ubuntu machines can't see any of the network. I can ping the server and if i try to add the printer that attached to server it sees there's something there but i get share restriction error. It can also see the workgroup , but when you try to access it, it can't get share list. The next problem is there's a Dell 1100 laser that works fine locally but none of the PCs on network can print to it. I've looked at the smb.conf file and it looks pretty much like the basic setup of all I've seen out there. below the print settings if some can help i can the rest of the smb.conf. But my guess (i'm new so might be talking outta my *#@) that's some thing on the client side that wrong as far the ubuntu. I have no clue about the printing issue. Anyone? Help? 

###Printing###
  load printers = yes
  printing = cups
  printcap name = cups

###share definitions###


  Comment = all printers
  browseable = no
  path = /var/spool/samba
  printable = yes
  guest ok = no
  read only = yes
  create mask = 700

Thanks in advance!!:D

---

