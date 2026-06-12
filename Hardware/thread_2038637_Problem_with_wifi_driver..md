---
title: "Problem with wifi driver."
date: 2012-08-07
forum: Hardware
---

### Post by thomas15v on 2012-08-07
Hello, I am totaly noob on ubuntu. 
But i have a problem with my wifi driver. 
It loses his connection evry time. First it connects and internet works good. Buth after some time it say's no internet connection.
I have a toshiba sattelite c660-1r1 and my wifi module is a realtek 81880CE. I have installed the driver from realtek and getting the folowing :confused:. (now the wifi module works fine). 
Here some screens with information.
[IMG]http://img268.imageshack.us/img268/671/schermafdrukop201208070.png[/IMG]

(Grlmp now works that ***** module fine.)
(hup again lost when editing this post)

---

### Post by thomas15v on 2012-08-09
Ok, i have shearched a lot and dit some tweaks as:
google dns
reinstall driver
and updating to ubuntu 12.04 LS.
Now it seems to work fine.
But what totaly fixed the problem was this...
[IMG]http://img191.imageshack.us/img191/7382/schermafdrukvan20120809.png[/IMG]
MTU is think i the bytes per second that are sended to make sure you stay connected. Can it be. 
If there are problems again i let you know ;).

---

### Post by thomas15v on 2012-08-11
Ok, now i realy messed it up. I tryed to install some backports. And ubuntu bricked so i removed the partitions restored the MBR for windows. And downloaded a fresh iso and installed it again. Now the wifi takes 1 a 2 min to connect and have i only internet the first 20 seconds and than wifi stay's connected but no internet. (Note: this is a fresh install nothing is changed, only in the folder were the drivers is located, did i the folowing: sudo su; make; make install;exit;exit) 
What i also find strange is that if i install the internet works perfect but not in ubunu itself.

---

### Post by antiartist on 2012-08-11
Do you mean the RTL8188CE ??  

Is the driver you are using current?  [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=272&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PFid=48&Level=5&Conn=4&ProdID=272&DownTypeID=3&GetDown=false&Downloads=true)

---

### Post by thomas15v on 2012-08-11
Yes, that is the driver i use. I can connect wifi but have only 20 a 30 seconden internet after that the connection is establish. For activation i did "sudo modprobe rtl8192ce". I also tryed the windows driver but then the device doesn't start at all :').

:confused:But how can it that i have internet and than not anymore? I also tryed to deactivate the firewall but that also not worked.

---

### Post by Doj on 2012-08-11
This is probably not going to help, but have you changed the channel on your router and maybe tried using only G speeds to see if it would still disconnect?

If you are coming from Windows on the laptop, did you ever have low signal warnings? The wireless seems to disconnect faster on my laptop on Ubuntu than Windows, and that's probably because the linux driver gives up faster or something...

---

### Post by thomas15v on 2012-08-11
Hmm, on windows i have no problems with the wifi module. But i must tell that the modem has a very low range. On my android phone the wifi icon never gets full.

---

