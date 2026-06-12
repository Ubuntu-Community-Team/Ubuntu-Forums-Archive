---
title: "D-link DWA 643"
date: 2007-09-04
forum: Hardware &amp; Laptops
---

### Post by jbrockk13 on 2007-09-04
I have a Compaq pesario v5000 with a built in Broadcom wireless bcm4318. Having a heck of a time getting to work. I do have a Express card slot on computer and have been thinking about getting this card. My question is has anyone had any experience using Ubuntu with this card or any other pre N or draft N cards? Also how has been anyones experince using D-link products with Ubuntu? Thanks

---

### Post by bkj1 on 2007-09-15
I got this card to work under Ubuntu.  I was/am still having problems with my built in intel 3945 abg (which I think is a bad card).  Can't connect to anything with this card.  Anywho, what I did to get the dwa-643 to work on my dell 1720 was this.

First I had to get my express card slot working by issuing the following command:
sudo modprobe pciehp pciehp_force=1

Then i cleaned out my /etc/network/interfaces file and removed everything except for the lo interface information.

Next:
I installed ndiswrapper using synaptic (ndiswrapper-common & ndiswrapper-utils-1.9)

Next:
I copied the inf/sys/cat files to my hd from the supplied cd: (net5416.inf, net5416.cat, ar5416.sys)

Next:
I installed the driver using: sudo ndiswrapper -i net5416.inf

Next:
sudo ndiswrapper -l

Next:
sudo depmod -a

Next:
sudo modprobe ndiswrapper

Next:
sudo ndiswrapper -m (which resulted in adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...)

Next:
sudo nano /etc/modules and add ndiswrapper to the last line

Then using nm-applet to manage my interfaces i entered my WAP key and BAM I was connected immediately and have been using this connection ever since.  It has been a rock solid connection.   

I used the following links to help me get this card installed:
[https://help.ubuntu.com/community/ExpressCard](https://help.ubuntu.com/community/ExpressCard)
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

NOTE:  I am a novice ubuntu/linux user.  I am only stating here what I did to get the dwa-643 to work for me under my current hardware.  I am still having to enter my WAP (already had the wpasupplicant package installed) key every time I login though.  Still trying to get this worked out under the kde environment.

UPDATE: Using knetworkmanager + kwalletmanager = no more having to enater WAP key.

Hope this helps.

---

### Post by tmas on 2007-11-08
I`ve got the wma 645 card, it looks pretty the same as wma 643... Wondering if I could use the same way to install my card..?

---

### Post by RD1945 on 2007-11-18
Does anyone know how to get the DWA-643 card to work under the 64-bit version of Gutsy?
I tried this little tutorial but it doesn't seem to work (the card won't come up).

I suppose this is for 32-bit only?

Thanks in advance

---

### Post by jcmourey on 2007-11-23
I got my DWA-643 card to work under Ubuntu 7.10 thanks to bkj1's steps above. Thanks a bunch!

One small problem, though. The card will only connect in 802.11g mode. If I change my router (D-link DIR-655) settings to allow only 802.11n connections, the card won't connect, nm-applet stays stuck in 'attempting to join the wireless network...'

It's kind of a bummer, I got this card for the 802.11n capability.

Have you or anyone been successful in getting the card to work in 802.11n mode?

I downloaded the latest XP driver from dlink.com (version 1.20), but it didn't fix the problem. As a side comment, dlink actually a bug in the .inf file which I had to fix before installing with ndiswrapper (several old references to a no longer existing 5211.reg section, when all the other references had been changed from 5211.reg to 5416.reg and 5211.DelReg to 5416.DelReg). Strangely, Windows XP didn't complain about it when I installed the  driver in XP, but ndiswrapper did when I installed it in Ubuntu.  Probably XP being lax about driver errors ? For reference, I am indeed able to connect in 802.11n mode from Windows XP.

I've attached the fixed net5416.inf file for those interested (download the 1.20 package from [ftp://ftp.dlink.com/Wireless/dwa643/Drivers/dwa643_drivers_120.zip]("ftp://ftp.dlink.com/Wireless/dwa643/Drivers/dwa643_drivers_120.zip")
and then replace the net5416.inf file with the one attached in this post, you can run a diff to see what I changed).

Any help would be much appreciated.

Thanks.

---

### Post by kegobeer on 2007-12-31
I tried this method to get my 643 working, but I never had any luck.  The card's light flashed on and off, and I could see my network, but I could never connect.  I ended up installing the madwifi experimental for AR5008, and now the card works.  However, it is stuck at 802.11g, just like jcmourey.  I don't think the MIMO chip is fully supported just yet, so there will only be g speeds until either the HAL is changed or the next madwifi release moves away from HAL.

I followed these guides:
[http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008](http://www.thinkwiki.org/wiki/How_to_checkout_and_install_madwifi_experimental_driver_for_ar5008)
[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

Hope this helps someone else.

Edit: It doesn't look like n is coming to Linux via madwifi anytime soon.  Perhaps in the new ath5k drivers: [http://madwifi.org/ticket/1636](http://madwifi.org/ticket/1636)

---

