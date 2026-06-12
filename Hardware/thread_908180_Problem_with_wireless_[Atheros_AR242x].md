---
title: "Problem with wireless [Atheros AR242x]"
date: 2008-09-02
forum: Hardware
---

### Post by bbandruin on 2008-09-02
I've recently bought a nice laptop (Asus X50SL) to try out some Linux distributions and Xubuntu seemed like a good start. But now I want to get my wireless working and I'm having some difficulty with that. I've browsed the forums here quite a lot, but haven't been able to find an apt solution.

lspci gives me:
```
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```
So my card is detected, right?

sudo lshw -C network:
```
  *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:1f:c6:42:0f:5b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.2 duplex=full ip=192.168.1.100 latency=0 link=yes module=sis190 multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
```

iwconfig gives me:
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

iwlist wlan0 scan:
```
wlan0     Interface doesn't support scanning.
```

No problems with it being not detected, it just doesn't show up as a wlan device?
I've tried getting it to work with madwifi, but that doesn't work. (And I don't have the cd-rom with drivers with me right now.)

Any suggestions as what I'm doing wrong/can do?

---

### Post by Astinsan on 2008-09-02
You need to build a drver by hand because your card isn't supported by the module you have... Here are the steps I used to get my hp dv9720us.

(From [http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html))


If you have Atheros AR5007 wireless network adapter follow this procedure to make it work in ubuntu 8.04

For i386 Users

First go to System–>Administration–>Hardware Drivers” and disable by un-ticking the following option

Atheros Hardware Access Layer (Hal)

Then Reboot your system.

Preparing your system

sudo apt-get install build-essential

Then open the terminal from Applications–>Accessories–>Terminal and copy the following command

wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

tar xfz madwifi-ng-r2756+ar5007.tar.gz

cd madwifi-ng-r2756+ar5007

make

sudo make install

sudo modprobe ath_pci

sudo reboot

That’s it now your wireless should work without any problem.

For AMD64 Users

If you are using 64 bit version following this procedure

Blacklist the default driver

echo “blacklist ath_pci” | sudo tee -a /etc/modprobe.d/blacklist

Download the 64 bit driver

wget [http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz](http://blakecmartin.googlepages.com/ar5007eg-64-0.2.tar.gz)

Extract driver using the following command

tar xvf ar5007eg-*.tar.gz

tar xvf ndiswrapper-newest.tar.gz

Ensure you have your kernel headers and the build essential package.

sudo aptitude update

sudo aptitude install linux-headers-$(uname -r) build-essential

Install ndisgtk

sudo apt-get install ndisgtk

Either use ndisgtk to install the driver or

sudo ndiswrapper -i net5211.inf

Load up ndiswrapper every time Linux is loaded

sudo modprobe ndiswrapper

echo “ndiswrapper” | sudo tee -a /etc/modules

Restart your system using the following command

sudo reboot

Your card should have been detected and it should show available networks but if it does not, try

sudo iwlist scan

---

### Post by bbandruin on 2008-09-02
Thanks for your help, but I'm still not succeeding at it. Your link ([http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)) is outdated. It let's me download a README-file which says:
> However, since you've downloaded this tarball, you've followed outdated
instructions. The code that this tarball once contained is now obsolete.
Please follow these instructions to enable your AR5007-based WLAN device:
[http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)
So, OK, I just download the most recent tarball, extract it, make && make install it, but when I get to sudo modprobe ath_pci, it does nothing? I mean, I don't get any output from that and when I reboot, iwconfig says just the same as before: no wifi-devices?

Hmm, the lshw-command gives me this:
```
           *-network
                description: Ethernet controller
                product: AR242x 802.11abg Wireless PCI Express Adapter
```
But it's not an Ethernet controller, but a Wireless controller; perhaps that's the problem?

Any more help would be dearly appreciated, I'm really stuck with this (after having checked >9000 'solutions' on Google and these forums).

---

### Post by Eleaf on 2008-09-14
Same problem here..  My atheros card on my acer aspire 5520 works fine with ndiswrapper, but I can't get it working with madwifi.

I tried compiling and installing the drivers but modprobing ath_pci DOES NOT create a wireless device.

Any ideas?

---

### Post by Eleaf on 2008-09-14
I have found an update...  Download the latest file here: [http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/](http://snapshots.madwifi.org/madwifi-hal-0.10.5.6/) and uncompress.

Then make/make install/modprobe ath_pci..

I now get a wireless device in iwconfig and can connect to AP's...  Interesting!

---

### Post by Astinsan on 2008-09-15
In order for it to load every time you need to add  it to the file in etc called modules. Also atheros cards have a airplane mode switch option. My HP has one in the front. You need to tell the driver to ignore the setting. 

The line(s) that should be added are:
ath_pci rfkill=0
wlan_scan_sta


the option at the end that says rfkill=0 that is the airplane mode switch. It will not be needed in the future when the driver is complete from what I have read around. It basically turns off roaming mode. This will prevent your card from showing any access points from showing up.

After everything is added and enabled you can click the network manager icon and the wireless networks should show up. There is no need to add a device it should be added automatically by the network manager.

---

### Post by SilverAdder on 2008-09-15
I have an Acer Ferrari 5000, also with an Atheros wireless chipset. I used the automated script found [_here_]("http://ubuntuforums.org/showthread.php?t=798485&highlight=atheros+compatibility") with great success, multiple times. The post has some good info but basically you just download the scrip, chmod +x, and run it. After a while, your done and it worked flawlessly for me. I hope this helps.

---

