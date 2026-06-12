---
title: "Trendnet &amp; NVIDIA hardware help"
date: 2010-04-10
forum: Hardware
---

### Post by james.euless on 2010-04-10
I have older hardware that apparently is very difficult to get working with Ubuntu.  After a couple of days researching and tinkering, this is what I found.

My wireless adapter is a Trendent TEW-444UB.  The instructions on how to get the driver to work is found here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

It is not made clear, you need all three of the files for it to work.  

2.2.1. Currently Supported Releases
1.For 9.10 Karmic Koala
a.[http://packages.ubuntu.com/karmic/misc/ndiswrapper-common](http://packages.ubuntu.com/karmic/misc/ndiswrapper-common)
b.[http://packages.ubuntu.com/karmic/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/karmic/misc/ndiswrapper-utils-1.9)
c.[http://packages.ubuntu.com/karmic/net/ndisgtk](http://packages.ubuntu.com/karmic/net/ndisgtk)
And the manufacturers driver is found here: [http://www.trendnet.com/](http://www.trendnet.com/)

Follow the instructions on the ndiswrapper and it should all work out.  I did have a little trouble getting Ubuntu to recognize the adapter on startup, but a couple of restarts seems to have cured that.

The next problem I had was poor resolution caused by old graphics card.  I use NV11DDR [GeForce2 MX200].  The way I found that out was to go to Applications > Accessories > Terminal and run lspci.  Somewhere down there you'll see VGA compatible controller: and that is the card.  Next, there seemed to be all kinds of ideas on how to make this work.  ENVY did nothing for me.  In fact, I could not get it to load.  

The answer was pretty simple:
1.Application > Ubuntu Software Center > Search Nvidia
2.Download NVidia binary X.Org driver ('version 96' driver)
3.Download NVIDIA X Server Settings
4.System > Administration > Hardware Driver.
5.It should load the new driver, and all you to use the NVIDIA X Server setting to manage your resolution.  
6.There is probably a reboot in there somewhere too to get all the hardware recognized. 

That's it.  It only takes about an hour if you know all the steps.

---

