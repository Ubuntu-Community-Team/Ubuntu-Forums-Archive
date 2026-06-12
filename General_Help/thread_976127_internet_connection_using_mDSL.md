---
title: "internet connection using mDSL"
date: 2008-11-09
forum: General Help
---

### Post by Jefferies on 2008-11-09
I have just installed Ubuntu 8.10 on my machine.

In Windows XP Professional I connect to the internet with a AC8700 CDMA2000 1X mDSL Wireless Data Terminal of ZTE Corporation. The Data Terminal is equipped with a standard USB interface and supports CDMA2000 1X mDSL 

Can anyone tell me how I can set this thing up in Ubuntu, as I cannot get it to work.

I looked at this post: 

[http://ubuntuforums.org/archive/index.php/t-942873.html]("http://ubuntuforums.org/archive/index.php/t-942873.html")

But it is not much help.

It suggests that in terminal

> lsusb

but the problem here is that device does not register either in Windows or Linux as being attached to a USB port (although it is). Consequently, it does not show in the list of USB devices!

As a result, 

> sudo modeprobe usbserial vendor xxxx   product xxxx

and then

> kppp or > gppp

cannot be implemented.

The author then suggests that for 8.1 none of this is necessary, 

> just in the network settings add ur username and the password to the ppp connection and that is all!


Wrong. It does nothing whatsoever, as you have to start the USB device manually to establish a connection... and I can't get it onto Ubuntu... Grrrrrrrrrrrrrrrr :confused::confused::confused:

Please, can anyone help as I really want to start to use Ubuntu???

---

