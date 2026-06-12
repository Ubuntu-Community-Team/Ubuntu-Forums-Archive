---
title: "wireless not detecting networks on HP Mini 110-3021"
date: 2010-07-27
forum: Hardware
---

### Post by Mario Y on 2010-07-27
Hi, I have a few hours searching in the forum for a way to activate my  wireless card, i have a HP Mini 110-3021, but it wasn't able to detect  any network, i tried some "solutions" from the forum, but didn't work  for my wireless card.
The ***iwconfig*** command found "wlan0" as a wireless extension, but when run ***iwlist wlan0 scan*** doesn't found anything (of course, there were networks)
The ***lspci*** command found:
"Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe"
Searching the [web of the manufacturer]("http://www.ralinktech.com/index.php"), it's easy to find the driver (software > linux) but to install it... really a mess (you can try it if you want)
Well, finally i found [this package]("http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu/pool/main/r/rt3090/rt3090-dkms_2.3.1.3-0ubuntu0%7Eppa1_all.deb"), it's a .deb i think it's made for karmic or jaunty, but worked for me. [This is the page]("http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu/pool/main/r/rt3090/"). After installing that .deb i was able to detect wireless networks.

I  think this info can be usefull for some, it should work not only for  the Mini 110-3021, the solution should work for any laptop with the RaLink RT3090  card. I suggest you run the ***lspci*** command to know your hardware.


P.S.  I still have problems with the bluetooth, it can't find any device, but  at this moment i don't care, maybe only need a reboot or something

---

### Post by rvr on 2010-07-30
My eee laptop 1001HA has a rt3090 card, but ubuntu never succeeded to support it; i think i`ve tried some 10 times; also after your guidance there is an empty place on [system - preferences - Network connections] Wireless.
 Quite easy is the support using pclinuxos or mandriva, where you can obtain it from synaptic, so it also keeps after a kernel-update. But they don`t support a persistant, when using an usb-stick.
So how can i get it working with ubuntu 9.04 , 10.4 standard or Netbook?
"This package" from Mario Y   is the link i used, then i saved it and opened it.

---

### Post by nate_nightroad on 2010-08-01
thanks bro, solved my problem!

yes,is true bluetooth is still having a prob but wifi enabled is good enough for me :)

---

### Post by kojackelle on 2010-08-02
Solved my problem also.  Lots of related forums out there with no solution.

---

### Post by superbarney on 2010-08-30
I had the same problem but finally got wifi working on the HP Mini 110,  running Ubuntu 10.04 Lucid Lynx. My Mini 110 came with an Intel N475  processor and Ralink RT3090 wireless card so I'm assuming you have the  same specs unless you're using the older Mini 110. Run [FONT=Courier New]lspci[/FONT] to check.

Here's how I did it:

[LIST=1]
[*]Fire up the terminal and enter ```
sudo add-apt-repository ppa:markus-tisoft/rt3090
```
[*]```
sudo apt-get update
```
[*]```
sudo apt-get install rt3090-dkms
```
[/LIST]
That's all. You might need to reboot after the last step, I don't remember if I had to. 

All the steps above except the last one can be found here: 
[https://launchpad.net/~markus-tisoft/+archive/rt3090]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090")

Enjoy!

Tell me if it works.

---

### Post by cartisdm on 2010-09-08
worked for me!!  thanks!!!!

---

