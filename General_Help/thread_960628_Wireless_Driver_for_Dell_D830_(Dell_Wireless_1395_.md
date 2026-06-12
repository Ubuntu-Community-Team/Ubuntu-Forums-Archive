---
title: "Wireless Driver for Dell D830 (Dell Wireless 1395 WLAN Mini-Card)"
date: 2008-10-27
forum: General Help
---

### Post by compucv621 on 2008-10-27
Any place I can find a Wireless Driver for the Dell Wireless 1395 WLAN Mini-Card Driver on a D830? Dell doesn't provide one, and Google hasn't been helping me out too much. I'm running Ubuntu 8.04 (32-bit)

Thanks

---

### Post by Ayuthia on 2008-10-27
> **compucv621 said:**
> Any place I can find a Wireless Driver for the Dell Wireless 1395 WLAN Mini-Card Driver on a D830? Dell doesn't provide one, and Google hasn't been helping me out too much. I'm running Ubuntu 8.04 (32-bit)

Thanks

If you have a wired connection, you should just run the updates and then go to System->Administration->Hardware Drivers and there should be an option for Broadcom STA(wl) for you.  Once you enable it, your wireless should work.  This driver is available in 8.04.1, but not in 8.04 (The driver came somewhere between the two releases)

---

### Post by Yellow Pasque on 2008-10-27
Dell may not provide a Linux driver, but there is probably a Linux kernel driver for the chipset that the card is based on, and if not, you might be able to use a Windows driver with ndiswrapper.

First identify the wireless chipset with:
```
sudo lshw -C network
```

---

### Post by nasar2k2000 on 2008-10-27
> **compucv621 said:**
> Any place I can find a Wireless Driver for the Dell Wireless 1395 WLAN Mini-Card Driver on a D830? Dell doesn't provide one, and Google hasn't been helping me out too much. I'm running Ubuntu 8.04 (32-bit)

Thanks

you have to use ndiswrapper for this. i have the XPS M1330 and it has the same wifi card and it only works with ndiswrapper. follow the following procedure:

blacklist bcm43xx

	echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

2. install ndiswrapper and related files

	sudo apt-get install ndiswrapper-common ndisgtk

	(this should also pull in the 'utils' package)
	when I was all said and done, I had
		ndiswrapper 1.45
		ndiswrapper-utils 1.9
		ndisgtk   (you don't really need this, and my instructions don't make use of it)

3. download and extract [http://ftp.us.dell.com/network/R174291.exe](http://ftp.us.dell.com/network/R174291.exe)

	this is a ridiculous bit of bloat, but the most complete INF for 43xx devices

4. go into folder DRIVER_US inside the result of what you did above

5. use ndiswrapper to install bcmwl5.inf

	sudo ndiswrapper -i bcmwl5.inf
	sudo ndiswrapper -m	(this one will give you a bunch of warnings - ignore)
	sudo ndiswrapper -ma
	sudo ndiswrapper -mi

	(I don't honestly know if the last three steps are necessary, but can't hurt)

6. reboot your machine

---

### Post by wdmora on 2010-02-26
nasar2k2000,

After trying all day unsuccessfully installing the Wireless card, I tried your method!
Way easier!

Nice!

Thank you so much!!

It finally works!!!!

---

### Post by alramsey on 2010-05-02
There is a linux driver available for a number of Broadcom wireless modems, which includes Dell's 1395 WLAN Mini-Card.  I have this on my XPS M1530.  Use the driver available from Broadcom:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

I successfully installed it on Ubuntu 10.04 after following the installation directions in the README file.

==========

Just to follow up, I just found out I can auto-install the proprietary driver for my wifi device:

System > Administration > Hardware Drivers

From there, Ubuntu automagically determines what proprietary drivers were applicable to my hardware.  My NVidia graphics driver was also updated this way.  For the wireless driver, I'd recommend this approach rather than manually downloading the driver.

---

