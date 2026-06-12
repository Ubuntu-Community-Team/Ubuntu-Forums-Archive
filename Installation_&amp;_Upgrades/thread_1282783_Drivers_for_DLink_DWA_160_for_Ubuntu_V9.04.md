---
title: "Drivers for DLink DWA 160 for Ubuntu V9.04"
date: 2009-10-04
forum: Installation &amp; Upgrades
---

### Post by munkifisht on 2009-10-04
I am just getting into Linux, and I have a dual boot running, but as yet I still have to get access to the internet over my WiFi. I don't have a LAN connection available, and can't seem to find drivers for my wireless. I have checked the site, and I am not sure they even support it properly anymore. Any hlpe on where to get a good list of DLink linux drivers would be great. Also, could someone point me to some good guide on how to install them?

---

### Post by rreese6 on 2009-10-05
I have read that some people say that this just works under 9.04, however it doesn't seem to be working in your case.
It would be good to know if your system even recognizes it.
Do this command in a terminal and see if the Device is listed.
```
lsusb
```

If you look on the back of the device you can see the revision.

DLink DWA-160 Rev A has a linux driver:
[ftp://ftp.dlink.co.uk/wireless/dwa-160/DWA-160_driver_3.2.0.17_rev_A1_linux.zip](ftp://ftp.dlink.co.uk/wireless/dwa-160/DWA-160_driver_3.2.0.17_rev_A1_linux.zip)

If you have rev B then the xp driver is here you would have to use Ndiswrapper with this one:
[ftp://ftp.dlink.co.uk/wireless/dwa-160/DWA-160_driver_2.10_rev_B_XPVista.zip](ftp://ftp.dlink.co.uk/wireless/dwa-160/DWA-160_driver_2.10_rev_B_XPVista.zip)

To use a wrapper program that will use the Windows driver.
read here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by munkifisht on 2009-10-06
Hi,thanks for the tips, but I'm still having problems... Thanks to you I have the correct Linux driver for my device, but it is in an *.RPM format. is there anyway to run this in Ubuntu without an internet connection. As far as I can tell, I need Alien to run it but I can't figure out how to get this running without an internet connection. To do it the way other you suggesed I can't find how to do it without internet connection either

---

### Post by rreese6 on 2009-10-06
you could download alien on another computer and transfer it by USB stick or cd.
go here to download alien:
[http://packages.ubuntu.com/hardy/all/alien/download]("http://packages.ubuntu.com/hardy/all/alien/download")
then once you copy it over to your home directory you can open Terminal
then do ```
cd ~
sudo dpkg -i alien<TAB><ENTER>
```
and that should install alien.
note <TAB> means TAB key
and <ENTER> means ENTER key, just in case you were wondering.

---

### Post by munkifisht on 2009-10-22
It's taken me a while to get around to trying this again, I have been playing around with ubuntu on my laptop and am only now trying to put it on my main machine agian (I think it might be time to say bye bye Microsoft). Anywho, I tried to install alien, and got loads of warnings about dependencies not being  there.

I am thinking about going at this from another tack. My Laptop does have internet access, and I have a LAN cable. Is it possible to connect two computers with a LAN cable if one of them has the vinilla version of Jaunty running in a similar way as to how I connect my xbox to the interweb. If so, is there an idiot proof guide to how to set this up available anywhere. Thanks

---

