---
title: "Notebook freezes for some 5 minutes on hdd load."
date: 2011-04-10
forum: Hardware
---

### Post by ningo on 2011-04-10
Hello, 


I'm using a Notebook: Asus Extensa 5235 wich has a WDC WD1600BEVT-22 ZCT0 running Ubuntu 10.10.

I can reliably freeze the Notebook by running "stress --hdd 2" (it seems to work fine with just one active worker.) The command essentially does some write()/unlink() operations on the device. The device is ext4 formatted.

The fun part is that after some time (5-30 minutes) the notebook comes back to life. 

I've tried alot to nail down this problem and at this point it's either a faulty kernel or broken hardware, smart tells me all is fine however.

---

### Post by _obelix_ on 2011-06-19
Hi. I have the same problem here with Acer Extensa 5235 and Kubuntu 11.04. I test the "stress" Tool with live CD Knoppix 6.4 (Kernel 2.6.37) and it works fine. No freeze with "stress --hdd 2" on mounted hdd.

Is there such a Kernel parameter to fix the this problem on Ubuntu? With openSUSE 11.2 the Notebook works 2 years without trouble. 

Best regards

obelix

---

