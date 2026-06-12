---
title: "Vodafone Dell Inspiron Mini 9 3G card"
date: 2008-10-28
forum: Hardware
---

### Post by oliverwebb on 2008-10-28
Anyone know if the 3G card in this laptop works with Ubuntu? Mine arrives tomorrow and I'll be sitcking 8.10 straight on it.

Any ideas?

---

### Post by chsub on 2008-12-08
Did you get the 3g card to work with a 8.10 install?

---

### Post by dc2447 on 2009-07-02
[me too]

Anyone know if the integrated HSDPA modem (3g) works with Ubuntu, any variants?

---

### Post by craptree on 2009-08-30
This card works with Ubuntu! It is identical to the Erricson F3507g

You can either use it via command line using the guide her [http://www.thinkwiki.org/wiki/Ericsson_F3507g_Mobile_Broadband_Module](http://www.thinkwiki.org/wiki/Ericsson_F3507g_Mobile_Broadband_Module)

Or alternatively, my prefered method: get it working properly and reliably with network manager via the cdc-ether interface. You'll need to update your kernel 2.6.31 and update your network manager. Guide available at - 
[http://sourceforge.net/apps/mediawiki/mbm/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/mbm/index.php?title=Main_Page)

As yet I can't get the GPS program to work from mbm, if anyone has any luck in jaunty, feel free to contact me!

Thanks
Riz

---

### Post by dc2447 on 2009-09-12
> **craptree said:**
> This card works with Ubuntu! It is identical to the Erricson F3507g

You can either use it via command line using the guide her [http://www.thinkwiki.org/wiki/Ericsson_F3507g_Mobile_Broadband_Module](http://www.thinkwiki.org/wiki/Ericsson_F3507g_Mobile_Broadband_Module)

Or alternatively, my prefered method: get it working properly and reliably with network manager via the cdc-ether interface. You'll need to update your kernel 2.6.31 and update your network manager. Guide available at - 
[http://sourceforge.net/apps/mediawiki/mbm/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/mbm/index.php?title=Main_Page)

As yet I can't get the GPS program to work from mbm, if anyone has any luck in jaunty, feel free to contact me!

Thanks
Riz

Thanks for the info.

I have just bought a mini 9 with wwan - have addded my SIM but running lsusb doesn't show 

Bus 006 Device 004: ID 0bdb:1902 Ericsson Business Mobile Networks BV


as per the wiki above.

Can I ask if you have a mini 9 and what the output of lsusb is please?

---

