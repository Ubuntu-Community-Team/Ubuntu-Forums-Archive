---
title: "How To:  Dell XPS M1210 - wireless"
date: 2007-01-13
forum: Hardware &amp; Laptops
---

### Post by dimeotane on 2007-01-13
Do you have a new Dell XPS m1210, with the "Dell Wireless 1390 Mini Card"?

And you were frustrated to find ](*,) wireless didn't immediately work with your fresh install of Ubuntu Edgy 6.10?

Don't despair, it took only a few minutes to get it working with ndiswrapper, and was quite easy to do.  Skip ahead if you already understand why setting up Ubuntu is well worth your time. 

(If this is your first try at setting up an Ubuntu system, you might wonder if it's worth it to invest an hour of your precious time "just to get your wireless working", and wonder if you should just stick with windows.  I've been using Ubuntu for over a year as my main system, and yes, it is well worth it.  Once it's set up, you really never need to do it again, until you buy a new PC and want Ubuntu on that too. In the pleasant years that pass, you will sit back and relax while you listen to your friends cry and complain about all their Windows trojans, spam, spyware, software subscription fees, and EULA's and other annoyances.  Why can't Ubuntu access this card 'automatically'?  Because big companies like broadcom refuse to  share their secret hardware information with the public; so you'll need to install their special drivers.)  


***And now the how to: ***

1) Verify you have the Broadcom 4311 card
-------------------------------------------------------------
Open your terminal: Applications-->Accessories-->Terminal

At the command prompt, type (without the $ prompt)
```
$ lspci | grep Broadcom
```
the output should show your network controller is the broadcom 4311



2) Get the broadcom drivers onto your m1210
----------------------------------------
This is probably the hardest part!

Option 1) for the windows lovers...
On a windows machine download and install the WIFI drivers from Dell. [http://ftp.us.dell.com/network/R115321.EXE](http://ftp.us.dell.com/network/R115321.EXE)
(It's a 48meg file, and unfortunately you only need 1 meg out of that!)
 
find the drivers folder at c:/dell/drivers/R115321/DRIVER on a windows machine.  Copy two files:  bcmwl5.inf and bcmwl5.sys to a USB memory stick.  Plug the stick into your m1210 and copy the files into a folder on your desktop called "broadcom-4311-driver".

Option2) for the Eleete user...
For the more advanced user, you can use your new m1210 with an ethernet line and download them on the m1210, and install using wine (I'd get wine installed by going to [www.getautomatix.com](www.getautomatix.com)). Dont' forget, to find your wine folder you'll need to go Places-->Home Folder, then View-->show hidden files.  mine were found under /home/dimeo/.wine/drive_c/dell/drivers/R115321/DRIVER.  Copy those to your desktop or home folder or whatever, you hacker.....

Option3) for the Ubuntu nOObies ...
Download bcmwl5.inf and bcmwl5.sys directly in a zip file from:
[http://files.filefront.com/6526092](http://files.filefront.com/6526092)
Download the file broadcom-4311-driver.zip to your desktop.  Extract the folder broadcom-4311-driver folder.


3) Install ndiswrapper 1.8
------------------------------------
Pop your Ubuntu Edgy 6.10 install CD in the drive.
Go to System-->Administration-->Synaptic Package Manager
enter your root password
search for ndiswrapper.

If you've been fiddling already with ndiswrapper, make sure all previous ndiswrapper packages in synaptic are uninstalled.
Then install ndiswrapper-utils-1.8


4) Install the Broadcom 4311 drivers with ndiswrapper
-----------------------------------------------------------------------------
In your terminal you're gonna basically do: 
$ sudo ndiswrapper-1.8 -i /whatever/path/to/your/driver/bcmwl5.inf

So assuming you downloaded your drivers to a folder on your desktop called "broadcom-4311-driver"

change your directory to there, and install the drivers:
```
$ cd ~/Desktop/broadcom-4311-driver/
```
```
$ sudo ndiswrapper-1.8 -i bcmwl5.inf
```

the output it gave me was  "forcing parameter IBSSGMode|0 to IBSSGMode|2" about a dozen times.  (Anyone know what's that about?)

```
$ ndiswrapper -l
```
you should read:
bcmwl5  "driver installed, hardware present"

check if everything is ready to load the ndiswrapper module:
```
$ sudo depmod -a
```
(if you dont get any output you are good)

load the module:
```
$ sudo modprobe ndiswrapper 
```

now check if the module was succefully loaded.
```
$ dmesg | grep ndiswrapper
```
the output should read:
"ndiswrapper version 1.22 loaded
"driver bcmwl5 (Broadcom, 11/02/2005 4.10.40.0)

make it load at boot:
```
$ sudo ndiswrapper -m
```

5)Pat yourself on the back and take a hackers break 
-------------------------------------------------------------------------
You've made a major milestone in becoming less dependent on Micro$oft, and joined a massive world wide community of free open source computing.  Enjoy!

---

### Post by Yerknutz on 2007-01-23
Wow great guide. I only wish I had the Broadcom wireless card in my M1210 to try this out...

Any chance you could write one for the Intel Pro WIreless 3945abg?  I'm guessing it would actually be the same guide, just with different INFs used,  I'd have no idea which ones I would need or if it would even work the same.

---

### Post by appsmanster on 2007-02-01
What issues are you having with the Intel Pro WIreless 3945abg? With the exception of having to enter the SSID under the network settings it works without any modifications.

---

### Post by appsmanster on 2007-02-01
The above ndiswrapper procedure will not work with your card.

---

