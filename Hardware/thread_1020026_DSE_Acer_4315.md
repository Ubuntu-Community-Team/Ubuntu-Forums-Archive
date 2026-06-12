---
title: "DSE Acer 4315"
date: 2008-12-23
forum: Hardware
---

### Post by gsimpson on 2008-12-23
Edit   Note these solutions not required now as wireless works with 10.04

DSE ([www.dse.co.nz](www.dse.co.nz)) in New Zealand have been brave enough to sell a Laptop with Linux. The implementation was a little flawed however and a fresh install of Ubuntu 8.04 is recommended.

The only thing I have found is the Wifi does not work after the install or after a Kernel upgrade.

The solution is: (updated see post 1st july 2009)

After the initial install of Ubuntu do the following in a terminal window (Applications>Accessories>Terminal). Copy, paste and run one line at a time:-

wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

sudo apt-get install build-essential

tar xfz madwifi-ng-r2756+ar5007.tar.gz

cd madwifi-ng-r2756+ar5007

sudo make

sudo make install

sudo modprobe ath_pci

sudo reboot


After a Kernel upgrade and the wifi has stopped working do the following in a terminal window:

cd madwifi-ng-r2756+ar5007

sudo make

sudo make install

sudo modprobe ath_pci

sudo reboot

---

### Post by HZipfel on 2009-06-29
Hi,

I purchased one of those computers and reinstalled ubuntu 8.04 and trying my luck on your instructions, however cannot download your suggested link.

Here is what it tells me:
pen@pen-laptop:/$ wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.


Have you got a current link?

Any help is appreciated.

Cheers

Holger

---

### Post by gsimpson on 2009-06-30
I will need to look into it. I have had no problems and my 4315 is working fine.

Some search results.

[http://madwifi-project.org/ticket/2240](http://madwifi-project.org/ticket/2240)

Got me to..

[http://madwifi-project.org/wiki/Support](http://madwifi-project.org/wiki/Support)

Will look further.

---

### Post by gsimpson on 2009-06-30
Try this and let us know how you get on

(out of date see solution 1st July 2009)

wget [http://snapshots.madwifi-project.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi-project.org/special/madwifi-ng-r2756+ar5007.tar.gz)

sudo apt-get install build-essential

tar xfz madwifi-ng-r2756+ar5007.tar.gz

cd madwifi-ng-r2756+ar5007

sudo make

sudo make install

sudo modprobe ath_pci

sudo reboot


After a Kernel upgrade and the wifi has stopped working do the following in a terminal window:

cd madwifi-ng-r2756+ar5007

sudo make

sudo make install

sudo modprobe ath_pci

sudo reboot

---

### Post by HZipfel on 2009-06-30
Everything works up to : sudo make > I get: make: No targets specified and no makefile found. Stop.

Any ideas?

---

### Post by HZipfel on 2009-06-30
Looking at the readme file tells me to look under [http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192) to read how to enable the AR5007-based WLAN, since the code in the download is outdated ... however ticket/1192 is outdated too ....:confused:

---

### Post by gsimpson on 2009-07-01
Yes the Readme file is 

You most likely downloaded this tarball since you are looking for a version
of MadWifi which supports the AR5007 chipset family, which is for example
used in the EeePC.

However, since you've downloaded this tarball, you've followed outdated
instructions. The code that this tarball once contained is now obsolete.
Please follow these instructions to enable your AR5007-based WLAN device:
[http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

If you have any questions about it, please contact our regular support
channels:
[http://madwifi.org/wiki/Support](http://madwifi.org/wiki/Support)

Thanks.


There must be a solution so will look into it.

---

### Post by gsimpson on 2009-07-01
OK I found this at [http://www.linuxforums.org/forum/ubuntu-help/113460-install-wifi-acer-4315-atheros-ar5007eg.html](http://www.linuxforums.org/forum/ubuntu-help/113460-install-wifi-acer-4315-atheros-ar5007eg.html)

I have elaborated on it as the wildcards interfered with previous downloads and may throw some users


Cut and paste this to a terminal a line at a time

wget -c http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz

tar xvf madwifi-hal-0.10.5.6-current.tar.gz

cd madwifi-hal-0.10.5.6-r4100-20090929

sudo make install

sudo modprobe ath_pci

sudo modprobe wlan_scan_sta

sudo reboot



I did this to ACER 4315 and wifi still working

Let us know how you get on[PHP][/PHP]

---

### Post by HZipfel on 2009-07-01
Your a champion. Thank you for this :guitar:

---

### Post by gsimpson on 2009-12-19
Have installed 9.10 on Acer 4315. Appears ok. Instructions above work to get the wireless going. :)

---

### Post by gsimpson on 2010-05-02
Update.

Have installed Ubuntu 10.04 LTS - the Lucid Lynx

The wireless works 'out of the box'. Brilliant. So the above solutions are now redundant. :popcorn:

The sound works fine but not the microphone. I set the sound hardware settings to output only and rely on a USB webcam for skype etc.

---

