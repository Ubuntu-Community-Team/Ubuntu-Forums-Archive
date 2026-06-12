---
title: "Help needed. HP Pavilion dv2025nr laptop"
date: 2006-11-21
forum: Hardware &amp; Laptops
---

### Post by mva.led on 2006-11-21
Hello all,

I've been using Ubuntu for about a year now, and I would like to keep doing so.

Recently I bought an HP Pavilion dv2025nr Laptop and installed Ubuntu Dapper. Some of the hardware didn't work. I did an apt-get dist-upgrade to Edgy, and still the HW is not working.

My main concerns are the Conexant HDAUDIO Soft Data Fax Modem, and the Broadcom Wireless Network Interface.

I have read some posts here and there and find no solution.

ndiswrapper is not working because the Win drivers are for 64 bits and my Edgy is the "generic" one. The Win drivers for 32 bits I have found didn't work either. Any help with this issue?

Yesterday I was trying the Linuxant drivers for Conexant, but it seems that the nVidia nForce (my audio chipset which works ok) is confusing the scanModem utility, it didn't detect the Conexant Modem. I don't know why. I installed the hsfdrivers any way, but the only thing that happen was I lost the audio, so I rolled back. 


Can any one help me to get this working?

Best regards,
Manuel.

---

### Post by mva.led on 2006-12-19
I tried ndiswrappers with the right Edgy kernel for 64 bits and still, can't use the wifi. ndiswrappers says that the hardware is present, though. But I don't know if I have to do something else to have the driver working.

---

### Post by jml on 2006-12-19
I've read that computers that were designed to run Windows Media Center version of XP not infrequently have difficulties with Linux.  It appears that many of the hardware choices made by manufacturers are not always Linux Friendly.  For example the Broadcom Wireless card is notorious for being difficult to run in Linux.  First, Broadcom does not supply any Linux compatible drivers, they do not freely give out technical specs,etc.  Ubuntu does load a Broadcom driver at installation, but I have read here that it does not work well.  The steps to get the Broadcom card working are rather involved, but involve first "blacklisting" the Ubuntu installed Broadcom driver (searching this site for Broadcom and Blacklist should give you the details.)  Then you need to install NDISWRAPPER and then use the Windows compatible driver usually supplied on a CD that came with the laptop.

As far as your modem goes, its very likely a Winmodem.  Its not really a hardware modem, but simply emulates one from within Windows.  Linux usually will not recognize a Winmodem, but again, if you search this site for Winmodem or Linmodem you may find some help.  You may also want to search the Networking/wireless sub-forum for tips.  There are probably people much smarter than I am on these topics there.  Good Luck.

Joe

---

### Post by mrunion on 2006-12-19
Though not the same model this guy's blogs may help some:

[http://tusharg.blogspot.com/](http://tusharg.blogspot.com/)

---

