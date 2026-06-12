---
title: "Samsung SCX-4833FD &amp;&amp; CLX-3185FW Multifunction - scanning over Network"
date: 2012-01-17
forum: Hardware
---

### Post by l_masoumi on 2012-01-17
I'm having a problem with two Samsung multi-function printers Models are CLX-3185FW and SCX-4833FD.

They are both connected to the same network as my PC is in along with the other colleagues' PCs. 

I have Ubuntu 10.04.3 on my PC and Windows 7 on VirtualBox OSE. After I installed the drivers available on Samsung website I can PRINT and SCAN from my Virtual Machine (WIN. 7), but installing the UnifiedLinuxDriver_0.91, Smartpanel_0.91, and PSU_0.91 on my ubuntu, I can PRINT but I can NOT SCAN in Ubuntu.

Ubuntu does not discover any scanner on my network, except one "HP Color Laserjet 2840" which I added through System>Administration>New Printer, and I can use Application>Graphics>Simple Scan or XSane Image Scanner to scan documents with it.

Anybody has any idea on how I can make the Samsung scanners discoverable through network connection?

---

### Post by baltas125 on 2012-02-11
**Instructions how to set-up samsung CLX-3185FW**
After executing instructions I have successfully installed CLX-3185FW over the network. It prints and scans over the network.
I have made it on Ubuntu 11.10, 32bit;

Before installing you MUST REMOVE any other previously installed drivers for Samsung.
Originally taken from: [http://www.bchemnet.com/suldr/index.html](http://www.bchemnet.com/suldr/index.html)

Step 1 (edit sources):
sudo gedit /etc/apt/sources.list
Add lines:
#samsung drivers
deb [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian extra

Step 2 (install authentication key) :
wget -O - [http://www.bchemnet.com/suldr/suldr.gpg](http://www.bchemnet.com/suldr/suldr.gpg) | sudo apt-key add -

Step 3 (update sources):
sudo apt-get update

Step 4 (install packages):
Open ubuntu software center and install one by one all packaged that start with " samsungmfp-", excepting:
 - first install packages which do not have the word "legacy";
 - do not install packages which offer you to remove any other packages;
 - Do not install "samsungmfp-parallel" it should only be installed if your printer is actually connected via a parallel port;

Step 5a (check if you are in lp group):
Run in Terminal:
cat /etc/group | grep lp

If your accaunt name is next to lp, everything is ok, else add yourself to lp group, how to do it is explained here:

Step 5b (add yourself into lp group if needed)
sudo usermod -a -G lp USERNAME

( more information about groups: [http://www.liberiangeek.net/2011/10/add-users-to-existing-groups-in-ubuntu-11-10-oneiric-ocelot-2/](http://www.liberiangeek.net/2011/10/add-users-to-existing-groups-in-ubuntu-11-10-oneiric-ocelot-2/))

That's it! Now you can search for your printer in network and add it as clx-3180 series and it will work.

P.S. Previously I have made some changes to some files. But I do not know if it has any impact.
If you have executed the five step above and still no luck, try making those changes:
/etc/sane.d/xerox_mfp.conf
lines added:
#Samsung CLX-3170fn & CLX-3175FW
usb 0x04e8 0x342a

/etc/sane.d/xerox_mfp.conf
lines added:
#Samsung CLX-3185FW
usb 0x04e8 0x343d

/lib/udev/rules.d/40-libsane.rules
lines added:
# Samsung CLX-3185FW
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="343d", ENV{libsane_matched}="yes"

---

### Post by CalvinK on 2012-07-18
> **baltas125 said:**
> **Instructions how to set-up samsung CLX-3185FW**
After executing instructions I have successfully installed CLX-3185FW over the network. It prints and scans over the network.
I have made it on Ubuntu 11.10, 32bit;

Before installing you MUST REMOVE any other previously installed drivers for Samsung.
Originally taken from: [http://www.bchemnet.com/suldr/index.html](http://www.bchemnet.com/suldr/index.html)

Step 1 (edit sources):
sudo gedit /etc/apt/sources.list
Add lines:
#samsung drivers
deb [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian extra

Step 2 (install authentication key) :
wget -O - [http://www.bchemnet.com/suldr/suldr.gpg](http://www.bchemnet.com/suldr/suldr.gpg) | sudo apt-key add -

Step 3 (update sources):
sudo apt-get update

Step 4 (install packages):
Open ubuntu software center and install one by one all packaged that start with " samsungmfp-", excepting:
 - first install packages which do not have the word "legacy";
 - do not install packages which offer you to remove any other packages;
 - Do not install "samsungmfp-parallel" it should only be installed if your printer is actually connected via a parallel port;

Step 5a (check if you are in lp group):
Run in Terminal:
cat /etc/group | grep lp

If your accaunt name is next to lp, everything is ok, else add yourself to lp group, how to do it is explained here:

Step 5b (add yourself into lp group if needed)
sudo usermod -a -G lp USERNAME

( more information about groups: [http://www.liberiangeek.net/2011/10/add-users-to-existing-groups-in-ubuntu-11-10-oneiric-ocelot-2/](http://www.liberiangeek.net/2011/10/add-users-to-existing-groups-in-ubuntu-11-10-oneiric-ocelot-2/))

That's it! Now you can search for your printer in network and add it as clx-3180 series and it will work.

P.S. Previously I have made some changes to some files. But I do not know if it has any impact.
If you have executed the five step above and still no luck, try making those changes:
/etc/sane.d/xerox_mfp.conf
lines added:
#Samsung CLX-3170fn & CLX-3175FW
usb 0x04e8 0x342a

/etc/sane.d/xerox_mfp.conf
lines added:
#Samsung CLX-3185FW
usb 0x04e8 0x343d

/lib/udev/rules.d/40-libsane.rules
lines added:
# Samsung CLX-3185FW
ATTRS{idVendor}=="04e8", ATTRS{idProduct}=="343d", ENV{libsane_matched}="yes"

I tried all that and more and still no luck with a multifunction printer Samsung CLX 3185. I am unable to scan through USB or on the network. The scanner is not recognized. lsusb find the machine and I can print via USB or (lately with the help of till Kamppeter and an alien version of cups) or the network. My machine runs Precise LTS and is a Dell XPS 15z.
Thanks for your ideas.

---

