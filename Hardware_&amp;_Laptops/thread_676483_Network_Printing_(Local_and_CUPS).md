---
title: "Network Printing (Local and CUPS)"
date: 2008-01-23
forum: Hardware &amp; Laptops
---

### Post by support on 2008-01-23
(I have searched the forums... Hopefully this has not been posted elsewhere already.)

Two Questions:

First: Is it possible to set up a printer in CUPS that is only accessible to a limited group of clients? If so, how do you do set up the printer and create and edit the limited group?

Second: I have a local printer that receives its print jobs via local Ethernet connections. This printer is not on CUPS and should remain not on CUPS unless the first question above is easy/possible to implement. The printer is automatically recognized by and processes commands from Mac's connected to the same switch that it is connected to. However, the Ubuntu machine connected to the same switch does not detect the printer (when using the GUI printer setup utility in the Gnome desktop environment) and cannot be configured. What am I missing?

Hope this finds you well. Thanks for your help.

---

### Post by a_posse_ad_esse on 2008-01-23
You are able to grant/restrict access to users in CUPS.  There will be the option through the GUI setup process provided by System Settings.  It can be done through the terminal too if you want to get technical.

---

### Post by support on 2008-01-24
Because I must access the print server remotely via ssh, terminal instructions would be ideal.

---

### Post by a_posse_ad_esse on 2008-01-24
[This]("http://ubuntuforums.org/showthread.php?t=240282") should be of use.  HTH

---

