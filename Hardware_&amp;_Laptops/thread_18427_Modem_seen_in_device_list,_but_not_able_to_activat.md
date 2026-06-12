---
title: "Modem seen in device list, but not able to activate"
date: 2005-03-06
forum: Hardware &amp; Laptops
---

### Post by chapterthree on 2005-03-06
Hello All,

I'm having an issue with my modem.  I checked the Device Manager, and I see that my modem is listed there, but when  I go to networking and try to activate it, it says that it can not activate it.  I have no idea where to turn, or how to troubleshoot this.  Any help would be greatly appreciated.

-Kevin

---

### Post by lordofkhemenu on 2005-03-06
[QUOTE=chapterthree]Hello All,

I'm having an issue with my modem. I checked the Device Manager, and I see that my modem is listed there, but when I go to networking and try to activate it, it says that it can not activate it. I have no idea where to turn, or how to troubleshoot this. Any help would be greatly appreciated.

-Kevin[/QUOTE]
Make/model of the modem?

---

### Post by chapterthree on 2005-03-06
The modem is a U.S Robotics 56K Faxmodem Win 1806

---

### Post by az on 2005-03-07
"The modem is a U.S Robotics 56K Faxmodem Win 1806"

That kind of modem does not work.  Many software modems have linux drivers available.  US robotics do not make linux drivers for any of their software modems.

The manufacturer of the modem does not care about open source software, or your freedom to know what is going on inside your computer.  They are not interested in doing business with you.

---

### Post by Ominus on 2005-03-07
Thought so...

---

### Post by wip3out on 2005-03-09
[QUOTE=chapterthree]Hello All,

I'm having an issue with my modem.  I checked the Device Manager, and I see that my modem is listed there, but when  I go to networking and try to activate it, it says that it can not activate it.  I have no idea where to turn, or how to troubleshoot this.  Any help would be greatly appreciated.

-Kevin[/QUOTE]

Hi,

I have the same issue as above. I have an LG modem: LM-I56N. It's supposed to have linux compatibility.?? Can anyone help me :?

---

### Post by az on 2005-03-09
Go to linmodems.org and download and run ScanModem.

---

### Post by wip3out on 2005-03-09
Thanks:)

---

### Post by wip3out on 2005-03-10
I did that and it picked up that I needed slmodem-2.9.10_netodragon.tar.gz, which I had anyway. So i installed it, but i can't get it to dial-up/activate. What do i have to do to get it to work???

I would really appreciate any help:)

---

### Post by az on 2005-03-10
Install sl-modem-deamon from universe.

Read the docs o using the alsa driver.

If that does not work, install sl-modem-source, linux-headers-XXYYZZ and build essential.  Then build the module.

---

### Post by wip3out on 2005-03-10
Please excuse my ignorance: "from universe"??

---

### Post by az on 2005-03-10
Universe package repository.

[http://higgs.djpig.de/ubuntu/www/warty/misc/sl-modem-daemon](http://higgs.djpig.de/ubuntu/www/warty/misc/sl-modem-daemon)


My mistake.  It is actually multiverse.

---

