---
title: "HP Wireless Problems"
date: 2008-06-14
forum: Hardware
---

### Post by mercury_may2112 on 2008-06-14
I'm in need of a laptop and I plan to partition the hard drive with Ubuntu 8.04. The guy at London Drugs I was talking to said that almost all Laptops have a problem wireless and its a pain to configure with Ubuntu.

The Laptop I was thinking of getting was:
[http://www.futureshop.ca/catalog/proddetail.asp?logon=&langid=EN&sku_id=0665000FS10100034&catid=](http://www.futureshop.ca/catalog/proddetail.asp?logon=&langid=EN&sku_id=0665000FS10100034&catid=)

But the guy I was talking to said that Certified Data laptops won't have the issue with the wireless. (This isn't the one I would get if I got a Certified Data):
[http://www.londondrugs.com/Cultures/en-US/Product+Detail/Computers.htm?BreadCrumbs=Computers;Computers;Computer%20Systems;Notebooks;Certified%20Data%20Core%202%20Duo%20MS-1719X%20Notebook%20Computer%20-%20Matte%20Black&Catalog=Computers&Category=Notebooks&ProductID=2827392&ProductTab=3](http://www.londondrugs.com/Cultures/en-US/Product+Detail/Computers.htm?BreadCrumbs=Computers;Computers;Computer%20Systems;Notebooks;Certified%20Data%20Core%202%20Duo%20MS-1719X%20Notebook%20Computer%20-%20Matte%20Black&Catalog=Computers&Category=Notebooks&ProductID=2827392&ProductTab=3)


So what do you guys know about laptop wireless incompatibility.

---

### Post by Alldan on 2008-06-14
:lolflag:
It's simply not true.

I needed just a few minutes to configure my atheros on my laptop.
 
On my desktop i needed an eternity (10 minutes) because i use an usb dongle without linux drivers an i had to install ndiswrapper and ndisgtk in order to use windows xp drivers.

By the way, some users reported that wpa password is lost after reboot. 
I use the solution from here:
 [http://ubuntuforums.org/showthread.php?t=773016](http://ubuntuforums.org/showthread.php?t=773016)

---

### Post by MarcG on 2008-06-16
> **Alldan said:**
> :lolflag:
I needed just a few minutes to configure my atheros on my laptop.
 

So how did you configure that? I've got a Compaq F716US, with an Atheros wireless. I installed 8.04, but the wireless does not turn on. The device manager says the drivers are turned on, though.

--Marc

---

### Post by Alldan on 2008-06-17
Network manager didn't work for me so i intalled wicd 
This is "my way": 

1 i installed wicd from here: [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php) (all installation information is here)
2 restart
3 reenter wireless password in network setup utility and verify connectivity (at this time wicd applet will show network activity)
4 enter wireless password in wicd utility in advanced settings and check "automatically connect"

After restart wireless started without problem for me

---

### Post by phidia on 2008-06-17
> **mercury_may2112 said:**
> I'm in need of a laptop and I plan to partition the hard drive with Ubuntu 8.04. The guy at London Drugs I was talking to said that almost all Laptops have a problem wireless and its a pain to configure with Ubuntu.

The Laptop I was thinking of getting was:
[http://www.futureshop.ca/catalog/proddetail.asp?logon=&langid=EN&sku_id=0665000FS10100034&catid=](http://www.futureshop.ca/catalog/proddetail.asp?logon=&langid=EN&sku_id=0665000FS10100034&catid=)

But the guy I was talking to said that Certified Data laptops won't have the issue with the wireless. (This isn't the one I would get if I got a Certified Data):
[http://www.londondrugs.com/Cultures/en-US/Product+Detail/Computers.htm?BreadCrumbs=Computers;Computers;Computer%20Systems;Notebooks;Certified%20Data%20Core%202%20Duo%20MS-1719X%20Notebook%20Computer%20-%20Matte%20Black&Catalog=Computers&Category=Notebooks&ProductID=2827392&ProductTab=3](http://www.londondrugs.com/Cultures/en-US/Product+Detail/Computers.htm?BreadCrumbs=Computers;Computers;Computer%20Systems;Notebooks;Certified%20Data%20Core%202%20Duo%20MS-1719X%20Notebook%20Computer%20-%20Matte%20Black&Catalog=Computers&Category=Notebooks&ProductID=2827392&ProductTab=3)


So what do you guys know about laptop wireless incompatibility.

The 1st link you provided says the wireless card is an intel. As a note it probably helps to just provide the specific card types in the laptops you are considering. It's not true BTW that atheros cards are _all_ simple to set up. It took a week of searching and troubleshooting for me to get mine working.
There is a [laptop testing site]("https://wiki.ubuntu.com/LaptopTestingTeam") for ubuntu and you might get some info there too. 
I may sound like a wet blanket here but I think it's good to let people know that there can be problems with laptops; in particular most of the hardware in a laptop is not swapable and it isn't always or predictably linux friendly.

---

