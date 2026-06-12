---
title: "Intel PRO/2100 Wireless problems"
date: 2008-04-22
forum: Hardware
---

### Post by jeffla376 on 2008-04-22
Hi. I installed Kubuntu 7.10 on an older Centrino based laptop (Premio Kaypro C1000) and am experiencing problems with the Wireless adapter. It appears to me that the RF Radio is turned off. This laptop has a RF enable/disable button, but it apparently is not a hardware switch and since there is no driver for it, it does nothing. The Wireless adapter is an Intel PRO/Wireless 2100 and the driver used is IPW2100.

I am attempting to turn on the RF Radio in hopes that all will be well after I do that. I found documentation on the IPW2100 driver at [http://ipw2100.sourceforge.net/README.ipw2100](http://ipw2100.sourceforge.net/README.ipw2100) 

The relevant information from the document is below. If I go the the directory indicated and type cat rf_kill, I can see that the value is set to a "2", which means HW based RF kill is active (radio is off). I am at a loss as to how I can turn the radio on. From reading the information below, I thought I would need to somehow write a new value to the rf_kill helper file in Sysfs, but I can't figuyre out how to do that, and I'm not sure if a write will do the trick since the current value indicates that the RF kill is hardware based rather than software based.

Thanks,

Jeff


Info from the IPW2100 readme:
----- Device Level ------
For the device level files look in
	/sys/bus/pci/drivers/ipw2100/{PCI-ID}/

For example:
	/sys/bus/pci/drivers/ipw2100/0000:02:01.0

For the device level files, see /sys/bus/pci/drivers/ipw2100:

  rf_kill
	read - 
	0 = RF kill not enabled (radio on)
	1 = SW based RF kill active (radio off)
	2 = HW based RF kill active (radio off)
	3 = Both HW and SW RF kill active (radio off)
	write -
	0 = If SW based RF kill active, turn the radio back on
	1 = If radio is on, activate SW based RF kill

	NOTE: If you enable the SW based RF kill and then toggle the HW
  	based RF kill from ON -> OFF -> ON, the radio will NOT come back on


5. Radio Kill Switch
-----------------------------------------------
Most laptops provide the ability for the user to physically disable the radio.
Some vendors have implemented this as a physical switch that requires no
software to turn the radio off and on.  On other laptops, however, the switch
is controlled through a button being pressed and a software driver then making
calls to turn the radio off and on.  This is referred to as a "software based
RF kill switch"

See the Sysfs helper file 'rf_kill' for determining the state of the RF switch
on your system.

---

