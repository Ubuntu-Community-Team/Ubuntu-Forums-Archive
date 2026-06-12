---
title: "Belkin F5D7050 v4000 wifi dongle will not work"
date: 2009-11-03
forum: Hardware
---

### Post by slowtrain on 2009-11-03
Summary:  After 2 full days online trying every set of instructions I could find, including Ubuntu community documentation, I was unable to get this dongle to work on Ubuntu 9.04 (64 bit system, tho that shouldn't matter).  If someone knows a solution, please let me know, but I'm not hopeful.

Conclusion:  I'd avoid buying a Belkin F5D7050 dongle.  The box doesn't tell you you're getting v4000 (you can tell by reading a serial # on the dongle and comparing it to info on the Belkin driver page for this device).

What I tried:  

a) Ubuntu community documentation for the Belkin F5D7050 v4000 (link below).  The documentation walks you through getting, compiling, and installing the zd1211b driver for the device (apparently what Belkin gives its PC customers).  Problem is, there seems to be no way to get the driver or make-able driver source files anymore.  Note that other drivers mentioned on bboards like the rt73 are not appropriate for the v4000.

b) ndiswrapper:  Getting a .inf file from either the Belkin install CD or by downloading the driver .exe from Belkin and partially installing via Wine.  The .inf file needs to be turned over to ndiswrapper, which should make it work for Ubuntu.  Problem is that none of the .inf files are recognized as viable drivers by ndiswrapper.

c) Installing the zd1211rw module that's already present in Ubuntu 9.04 and seeking to activate the interface with either Wifi-radar or code in the interfaces file followed by restarting networking.  This gets tantalizingly close--with Wifi-radar, I even get a ipaddress from my router and can see neighboring networks, but I simply am not able to download anything from the internet.

###

More details:

According to community documentation at the link below, it should be possible to get this wifi dongle to work, but following the instructions in the documentation is a dead end.

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver)](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_4000_(ZyDas_zd1211b_driver))

The instructions at that url direct me to a website to find the code for the zd1211b driver, but the code is no longer available at the download url provided by the documentation.  It is apparently available as a Subversion archive.  I'm not familiar w/ Subversion, but used the command listed on the website to download the most recent set of source files, which are divided into "Trunk" and "Vendor."  Tried to issue the make command mentioned in the community documentation in both of these directories.  I get a lot of what appear to be programming errors, and ultimately no driver gets made.  (One popular error msg:  error: too few arguments to function &#8216;iwe_stream_add_point&#8217;)

Some of the files on the Belkin installation CD seem to indicate that the zd1211b is, in fact, what that CD would install.  So, I tried to find another way to get the driver.  There are multiple bboard threads and web pages suggesting that ndiswrapper could be applied to the Windows .inf file of the driver.  These threads / websites say the .inf file can be extracted either from the Belkin CD or from the driver .exe file downloaded from the Belkin site and processed through Wine.  I tried both methods.  ndiswrapper does not recognize the .inf files that can be found on either the CD or in the directory created by Wine as valid drivers.  So, neither of these methods work, as far as I can tell.

The driver website mentioned in the community documentation indicates that the zd1211b has been updated and replaced by the zd1211rw driver.  So, I tried to get that into my active modules.  It seems the current system already has a zd1211rw driver, so I just used the following to activate it:  modprobe -v zd1211rw .  This seems to partly work.  After issuing this command (but not before), the package Wifi-radar lets me see all the wifi routers in my neighborhood, and even my own wifi router.  When I configure and seek to connect to my router, I even get an ipaddress.  But when I try to connect to the internet via the wifi dongle, I get nothing.  Here are some select lines from my messages log that shows what happens when I use the modprobe command.  The first couple lines are encouraging, but the last is where it probably fails:

Nov  2 19:27:16 Wheel kernel: [ 4032.779026] usbcore: registered new interface driver zd1211rw
Nov  2 19:27:16 Wheel kernel: [ 4032.986646] ^I(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Nov  2 19:29:20 Wheel kernel: [ 4156.348117] ADDRCONF(NETDEV_UP): wlan0: link is not ready

Instead of using Wifi-radar to activate wlan0, I also tried to rewrite my interfaces file and restart networking.  I tried the following commands.  Where you see a "#", there are some alternative configuration lines (of course, I removed the open authmode etc. when I tried out WPA2).  I also tried the code with and w/o the channel and mode lines.

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 down
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid "my_ssid"
#pre-up iwconfig wlan0 channel 6
#pre-up iwconfig wlan0 mode managed
#pre-up iwpriv wlan0 set AuthMode=WPA2PSK
#pre-up iwpriv wlan0 set WPAPSK="my_passphrase"
#pre-up iwpriv wlan0 set EncrypType=AES
pre-up iwpriv wlan0 set AuthMode=OPEN
pre-up iwpriv wlan0 set EncrypType=NONE

Irrespective of which alternatives I used, I could not even get assigned an ipaddress via this method.  When I restarted networking after altering the interfaces file, I got the following error msgs, which I suspect are pertinent:

wlan0     no private ioctls
Failed to bring up wlan0.

Bottom line here is that this is the kind of nightmare that Ubuntu should help users avoid.  I bought this wifi dongle because I knew there was community documentation saying it could be successfully installed.  Instead, I ran into many dead ends with out of date documentation.  I wasted lots of additional time on the huge number of webpages and bboard messages that are out of date or not relevant to the very specific type of hardware I have (instructions for the v3000 of the dongle are irrelevant for v4000, but much of the time the writers don't specify which version they are talking about).

If anyone has any additional suggestions on things to try, I'm all ears.

---

### Post by DirtyPC on 2011-06-12
Don't know how relevant this is to anyone but I solved this on my blog. Check my sig.

---

