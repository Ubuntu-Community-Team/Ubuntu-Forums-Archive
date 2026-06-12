---
title: "Smartlink modem in Notebook"
date: 2005-05-03
forum: Hardware &amp; Laptops
---

### Post by abmcr on 2005-05-03
In my DataModem.txt , result of scanmodem, i have  this:

       
 The soft modem Subsystem operates under a controller
   8086:24c6 82801DB ICH4 
 capable of supporting under Linux AT LEAST modem Subsystem chips from manufacturers:

	Broadcom
	AgereSystems
	Conexant
	Intel
	Smartlink

	Smartlink software in ALSA mode may support this modem 


I have tried with conexant driver but the modem not work. It is possible to use with Smartlink? In the Ubuntu starter guide i have found:

uname -r (must be 2.6.10-5-386)
wget -c [http://frankandjacq.com/ubuntuguide/sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-34_i386.deb](http://frankandjacq.com/ubuntuguide/sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-34_i386.deb)
sudo dpkg -i sl-modem-modules-*.deb
sudo apt-get install sl-modem-daemon

for install the smartlink modem; but after the installation i have a /dev/modem ? I can use gppp with the /dev/modem? Thank you

---

