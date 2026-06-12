---
title: "Fixed DWA-130, read before installing ubuntu"
date: 2010-12-14
forum: Hardware
---

### Post by ShootEmUp on 2010-12-14
First off the DWA-130 XP (vista and 7 drivers do not work with ndiswrapper) 64bit drivers are NOT compatible with 64bit Ubuntu (stupid D-link), You have to do a 32bit install to use ndiswrapper with this.

Step 1. Install Ubuntu, Read elsewhere for help with this
Step 2. Get ndiswrapper [Read Here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installation")> 2.1. Installing Packages (With Internet access on the Ubuntu computer)
If you already have Internet access via some other method while logged into Ubuntu:

1. Ensure the multiverse and universe repositories are enabled; see AddingRepositoriesHowto

2. Install the ndisgtk package from the Ubuntu repositories.

sudo apt-get install ndisgtk
If you don't know how to install applications then you can read this guide.

2.2. Installing Packages (With Internet access on another computer)
Download the files below according to the release you have:

2.2.1. Currently Supported Releases
For 10.04 Lucid Lynx
[http://packages.ubuntu.com/lucid/misc/ndiswrapper-common](http://packages.ubuntu.com/lucid/misc/ndiswrapper-common)
[http://packages.ubuntu.com/lucid/ndiswrapper-utils-1.9](http://packages.ubuntu.com/lucid/ndiswrapper-utils-1.9)
[http://packages.ubuntu.com/lucid/ndisgtk](http://packages.ubuntu.com/lucid/ndisgtk)
For 9.10 Karmic Koala
[http://packages.ubuntu.com/karmic/misc/ndiswrapper-common](http://packages.ubuntu.com/karmic/misc/ndiswrapper-common)
[http://packages.ubuntu.com/karmic/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/karmic/misc/ndiswrapper-utils-1.9)
[http://packages.ubuntu.com/karmic/net/ndisgtk](http://packages.ubuntu.com/karmic/net/ndisgtk)
For 9.04 Jaunty Jackalope
[http://packages.ubuntu.com/jaunty/misc/ndiswrapper-common](http://packages.ubuntu.com/jaunty/misc/ndiswrapper-common)
[http://packages.ubuntu.com/jaunty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/jaunty/misc/ndiswrapper-utils-1.9)
[http://packages.ubuntu.com/jaunty/net/ndisgtk](http://packages.ubuntu.com/jaunty/net/ndisgtk)
For 8.10 Intrepid Ibex
[http://packages.ubuntu.com/intrepid/misc/ndiswrapper-common](http://packages.ubuntu.com/intrepid/misc/ndiswrapper-common)
[http://packages.ubuntu.com/intrepid/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/intrepid/misc/ndiswrapper-utils-1.9)
[http://packages.ubuntu.com/intrepid/net/ndisgtk](http://packages.ubuntu.com/intrepid/net/ndisgtk)
For 8.04 Hardy Heron
[http://packages.ubuntu.com/hardy/misc/ndiswrapper-common](http://packages.ubuntu.com/hardy/misc/ndiswrapper-common)
[http://packages.ubuntu.com/hardy/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/hardy/misc/ndiswrapper-utils-1.9)
[http://packages.ubuntu.com/hardy/net/ndisgtk](http://packages.ubuntu.com/hardy/net/ndisgtk)
For 6.06 Dapper Drake
[http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils](http://packages.ubuntu.com/dapper/misc/ndiswrapper-utils)
[http://packages.ubuntu.com/dapper/net/ndisgtk](http://packages.ubuntu.com/dapper/net/ndisgtk)
 For advanced users: There is a known bug in these Debian packages, detailed in this thread. If you are having issues after installing from these packages, the kernel module may not have installed, so you may get the error FATAL: Module ndiswrapper not found when you run modprobe ndiswrapper in the terminal. To avoid this problem, it's best to compile from the source available at [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/). This is fairly simple but requires the build-essential package to be installed. You can install this offline using apt-cdrom from the command line or the synaptic package manager with the ubuntu install CD.

Copy the appropriate files over to a directory on your Ubuntu computer (e.g. your Home directory) and install them in this order:


sudo dpkg -i ndiswrapper-common_*.deb
sudo dpkg -i ndiswrapper-utils-*.deb
sudo dpkg -i ndisgtk_*.deb
 The commands listed above are a general example of how to install a .deb package from the command line. You need to be in the directory where the files were copied to. If you are new to the terminal, consider reading BasicCommands.

2.3. Installing Packages (Without Internet access)
Without an Internet connection, you can still install ndiswrapper-utils from the Desktop CD. If you installed from that, the repository in which ndiswrapper-utils is found is on the CD, but not within the live session. You need to boot into your new Ubuntu installation and then reinsert the Desktop CD. You will be asked if you want to add the packages on the CD to your list of repositories.
If you installed using the Dapper Alternate CD, those packages except ndisgtk are included on it.

Put the CD into the drive, click System > Administration > Synaptic Package Manager and search for ndis. If you don't know how to install applications, read this guide.

Step 3. Blacklist other wireless drivers
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
Add these lines to /etc/modprobe.d/blacklist

```
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist r8192s_usb
```

Reboot

Step 4. Download DWA-130 windows drivers
[Download Here]("http://www.dlink.com/products/default.aspx?pid=DWA-130&tab=3")
I personally had revE, download your revisions drivers (don't worry, it's a zip file)
Extract, look inside for the XP/2000 32bit drivers (should be WinXP2000, if not don't worry)

Step 5. Install drivers via ndiswrapper
Go to System-Administration-Windows Wireless Drivers
Click "Install New Driver", select the XP/2000 32bit drivers (from where you extracted them at)
Click Install

Step 6. Connect to internet
Now if Gnome network manager has detected your wireless, you should be able to just connect at this point
If not Reboot

Step 7. Enjoy!

Problems: None that I know of yet, let me know If you do

Hope this helps!

Feedback
> **bkratz said:**
> I have been using the DWA 130 for several years. Mine is the version A. There are actually five versions available, some of which actually have a Linux driver available on the D-Link website and ndiswrapper would not be needed. The user should verify which version he/she has before proceeding. I did not have to blacklist any drivers at all.

Thank you for your feedback, I say to blacklist the drivers because they can interfere (not always, but can) with ndiswrapper.
And yes revC has linux drivers available (sorry forgot to mention it).

---

