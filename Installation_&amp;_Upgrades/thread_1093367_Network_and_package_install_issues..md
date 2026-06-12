---
title: "Network and package install issues."
date: 2009-03-11
forum: Installation &amp; Upgrades
---

### Post by t0mppa on 2009-03-11
Spent yesterday fighting to get my XWindows up after a fresh install (dual boot with earlier Windows Vista already up there), finally got there by midnight and got my hopes up for actually getting to do some work today.

Alas, todays issue has been with Ubuntu not recognizing my WLAN adapter (Atheros AR5007EG). I actually found some helping pages for that, but they required building up the new drivers using Make and friends.

Now, install didn't set things up for manually building Debian packages, so I've been left to do that myself. Only problem is that since my WLAN isn't working and I can't get on LAN for a few days (long story), the only option to get online is to boot back into Windows, download stuff there and reboot back to Ubuntu. I think we all know how lightning quick booting Windows is, so it's not exactly simple to install all these packages.

Can't use Synaptics or apt-get, since they both try to go online. So, I've tried downloading the packages from [http://packages.ubuntu.com]("http://packages.ubuntu.com"). That isn't exactly working, since apparently I need 'build-essential' up and running to build the drivers and it on the other hand requires gcc-4.3, g++ & libstdc++6-4.3-dev. Sounds simple, right? All these 3 packages require each other as dependencies (according to Synaptics at least) before I can install them though, so they all refuse to get installed. ;)

The small details: gcc & g++ are complaining that gcc-4.3-base is somehow wrong, but when I downloaded the base and tried to install it, it said there was a newer version of it already installed and refused to install. And libstdc++6-4.3-dev complains that gcc & g++ need to be installed first. So, any ideas on how to circumvent this one?

---

### Post by cariboo on 2009-03-11
If you are ownloading .deb packages from packages.ubuntu.com, you don't have to compile anything, just double-click the deb and gdebi will install it for you. As to your network problem, could you paste the output of the following command in your next post:

```
sudo lshw -C network > network.txt
```

You will have to open a Applications-->Accessories-->Terminal to enter the command. The command will create a text file called network.txt that you can copy to your windows partition so you don't have to try and remember what the output was.

Jim

---

### Post by theozzlives on 2009-03-11
A lot of packages are on the CD, just go to System > Administration > Software Sources, under Ubuntu Software tab check the box for the CD-ROM. Insert your CD and click close, then update.

---

### Post by t0mppa on 2009-03-11
Yes, the packages I downloaded are .deb and easy to install, but the solution insisted on needing 'build-essential', see [http://ubuntuforums.org/showthread.php?t=662877]("http://ubuntuforums.org/showthread.php?t=662877").

>   *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 10
       serial: 00:1e:68:d5:0a:48
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 firmware=5764m-v3.35 latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 9e:52:e2:7f:4d:eb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


Ah yes the CD, I got tired of burning multiple CD's on different speeds to get a working copy, so just used a USB stick instead to install from. I tried what you're suggesting, but since I don't have a working CD, just the USB stick, I cannot set it up to read from a CD, it doesn't recognize the stick as a valid option.

---

### Post by t0mppa on 2009-03-12
Well, turned out that install had downloaded version 12 for gcc-4.3.2-base and all the packages in package.ubuntu.org were version 11 (and base is one of their dependencies), so they refused to install. Silly in a way, since the base only consists of text documents, no real data there.

Anyhow, I went to Debians site and grapped a pure source package for version 12 from there and educated myself on how to build from source in Linux, so something good came out of the issue, just wasted quite a bit of time figuring all the things out. :/

Nevertheless, now I got my WLAN adapter working. Case closed.

---

### Post by pallinger on 2009-04-07
As I had a similar problem I've edited the small python script posted [here]("http://ubuntuforums.org/showthread.php?t=174354&highlight=simple+download+packages+dependencies+windows%3F") to work with the current site. 

You can download it from here: [ATTACH]108997[/ATTACH]

You use it like this: 
```
python UbuntuPackageGrabber.py [http://packages.ubuntu.com/intrepid/dosbox](http://packages.ubuntu.com/intrepid/dosbox)
```

After that, you can feed the created *packages.html* to a download manager, or just feed it to wget like this:
```
cat packages.html |sed "s/.*'\(.*\)'.*/\1/" | xargs wget -c
```

---

### Post by t0mppa on 2009-04-14
Sounds pretty useful for cases like this. Think I'll grab a copy of that for a rainy day. However, last time I had wireless issues was when an Ubuntu update killed both my Vista and WLAN at the same time (fortunately I was able to get wired access to internet though), so it ain't always that simple. :/

---

