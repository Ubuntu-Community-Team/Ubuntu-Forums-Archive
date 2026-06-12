---
title: "Cant Re-enable Wifi"
date: 2009-09-03
forum: Hardware
---

### Post by tropnevad on 2009-09-03
Hi

I have been using UNR on my acer aspire one for a few months now and everything is fine, however one day on the network i disabled wifi and networking in order to save some battery, however now i can only re-enable networking, and the re-enable wifi option does not come up?  How can i re-enable my wifi?

Thanks in advance

---

### Post by hal10000 on 2009-09-03
Please post the content of the file /etc/network/interfaces and the output of lspci (if your wireless card is pci) resp. lsusb (if you have an usb wireless-card)

---

### Post by arcull on 2009-09-03
did you try to run the network manager and enable wifi from there?

---

### Post by jjjjeremy on 2009-09-03
what do you get if you run "sudo dhclient"

---

### Post by jalirious on 2009-09-05
Ha! Exact same thing with me. The re-enable wifi switch doesn't work on the AA1. 

Last time I fixed it by dual booting into linpus and using the wifi on-off switch there. Problem solved.

But this time I don't have the dual boot [...]

---

### Post by jalirious on 2009-09-06
Ok. I managed to fix my wifi through the time honoured method of pissing about.

[do the following]

sudo apt-get install subversion
svn co [http://svn.madwifi-project.org/madwifi/trunk](http://svn.madwifi-project.org/madwifi/trunk) madwifi
cd madwifi/scripts
sudo ./find-madwifi-modules.sh -r
cd ..
make
sudo make install

System->Admin->Hardware Drivers

enable madwifi mofo

reboot

Now, this is the weird bit. In the folder where I'd downloaded a previous version of madwifi (i.e. the directory with the makefile), I entered

make clean

and the wifi started working. make clean just removes some of the unneeded files when compiling from source, so that it then started then must have been coincidental.

[good luck]

---

### Post by jalirious on 2009-09-06
possibly move switch once to the right [no response], then reboot

---

