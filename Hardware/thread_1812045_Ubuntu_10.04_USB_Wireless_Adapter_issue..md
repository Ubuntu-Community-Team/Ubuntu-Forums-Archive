---
title: "Ubuntu 10.04 USB Wireless Adapter issue."
date: 2011-07-25
forum: Hardware
---

### Post by Trilogin on 2011-07-25
I installed Ubuntu 10.04 on an old computer for a friend of mine, it works great. He can connect to the internet through his router using a Cat5 cable and it works fine. Unfortunately for me, he wants the machine to be wireless compatible. 

He has a Netgear WG111 (I think that is the complete model number). It is a USB Wireless adapter, but everything that I read about it has said that it has major compatibility issues with Linux no matter which drivers are used. 

I went to thinkpenguin.com and found that they have a wireless USB adapter, and I showed it to my friend, and I think he would rather have a PCI wireless card.

Will any of the PCI WIreless adapters from newegg.com work for him or do I have to look in a bunch of other places? Is there any particular brand that supports linux better than any others?

---

### Post by jramshu on 2011-07-26
I have a cheap old Belkin PCI card that works fine with the B43 drivers in an old Dell laptop. Not sure if you can get one of them anymore like it.

---

### Post by old_codger on 2011-07-27
> **Trilogin said:**
> I installed Ubuntu 10.04 on an old computer for a friend of mine, it works great. He can connect to the internet through his router using a Cat5 cable and it works fine. Unfortunately for me, he wants the machine to be wireless compatible. 

He has a Netgear WG111 (I think that is the complete model number). It is a USB Wireless adapter, but everything that I read about it has said that it has major compatibility issues with Linux no matter which drivers are used. 

Where have you read that?

[http://www.qbik.ch/usb/devices/showdev.php?id=3614](http://www.qbik.ch/usb/devices/showdev.php?id=3614)

I thought it worked right out of the box but, if not, you should be able to use ndiswrapper as detailed here...

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

To ask the obvious question, have you tried connecting using the Netgear WG111? Might be worth plugging it in and trying

lsusb

to see if it's listed at least.

---

### Post by Trilogin on 2011-07-28
I found a list that was like a Wiki, I don't remember if it was from the ubuntu site or not but I did a search on googlubuntu and that page was the one I found. I can look for it again, I will update this post with it. 
 
This site said that ndiswrapper and the other linux wireless driver both caused this wireless adapter to run slow and also caused major issues with the other computers hooking up through the router, making them run slower or something. Let me find the site and double check the facts.

EDIT**
 WG111v1 
    ndiswrapper + netwg111.inf 
    No 
    No 
    No 
    Works with ndiswrapper and the CDROM provided by netgear. See [WifiDocs/Device/NetgearWG111]("https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111") 
    

   2005-09-09 
     WG111v2 
    Realtek 8187 
    ? 
    ? 
    Yes (Feisty/Hardy) 
    Yes 
    Works out of the box with Feisty(No WEP) and Hardy(with WEP) 
    2008-08-02 
     WG111v2 
    Realtek 8187 
    rtl8187 
    ? 
    Yes (Feisty/Hardy) 
    Yes, with caveats 
    Using either ndiswrapper + netgw111 or native  rtl8187 drive, performance was terrible as an interface or under Kismet.   Saw 1-3 networks vs 15 using built-in atheros.  Test run on two hw  samples. 
    2008-08-19 
     WG111v2 
    rtl8187 
    ? 
    Yes 
    Yes 
    Works out of the box with Jaunty. 
    

   2009-09-25 
     WG111v3 
    rtl8187B 
    ? 
    ? 
    Yes 
    Yes 
    Worked immediately in Intrepid AMD64 with  WPA2. Worked immediately on Karmic (Intel P4.) and worked in Lubuntu  natty 11.04 out of the box on a plll 600mhz compaq armada m300
    20011-05-24 
     WG111v3 
    ? 
    rtl8187 
    ? 
    Yes (with caveats) 
    Yes (with caveats) 
    Worked immediately in Jaunty AMD64.  However,  file transfers are limited to ~ 200 kilobytes / sec (2mbit).  Worse,  while this card is (slowly) downloading, ping times to the local router  are on the order of 4-8 seconds for all of the wifi devices on the local  network.  Router is Linksys WRT54GL; this is the only device (of many)  that I've seen this problem with. Reports strong signal strength even  while dropping packets. 
    2009-04-28 
     WG111v3 
    rtl8187 
    rtl8187 
    ? 
    Yes 
    Yes 
    works out of the box with Karmic (64-bit).  link problems with Sitecom WL-154 router (no connection, low data rate).  Perfect with Zyxel P660HW-D1 (using WPA2-PSK). 

Provided by [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear)

I am pretty sure that he has the WG111v3, and ndiswrapper and rtl8187 both seem to have issues with this USB adapter. I know that when he plugged it into his machine, which is a Pentium 4 e-Machines PC that originally had XP on it, the Ubuntu 10.04 that I put on it did not autodetect this adapter and install the appropriate drivers. 

Also, I believe he is using a Netgear router so there shouldn't be any issues with the wireless adapter picking up the wireless signal once the adapter is installed and working.

---

### Post by Trilogin on 2011-07-29
It turns out that my friend's router was screwed up so the adapter wasn't picking up any signal. Once he reset the router to factory settings and plugged the USB dongle into his Ubuntu PC, the Ubuntu PC was able to connect to the internet just fine. 

Plug and play, just like old_codger said. Thanks!

---

