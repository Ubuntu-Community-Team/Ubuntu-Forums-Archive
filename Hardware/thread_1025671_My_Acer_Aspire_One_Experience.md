---
title: "My Acer Aspire One Experience"
date: 2008-12-30
forum: Hardware
---

### Post by f37u5g0d on 2008-12-30
I have a 120GB acer aspire one with 1 gb of ram and a 1.6 GHz intel atom processor.  I used unetbootin to install ubuntu 8.10 on a separate partition so I can dual boot with the windows xp that came with the netbook.  Here are my problems:

Wired networking doesn't connect on the newest ubuntu kernel (2.6.27).  It attempts to get a network address for about a minute (both lights are on in the nm-applet) and then it fails and says no connection.   What the hell?  I have never heard of this happening to anyone and there are no other cases of this happening to an acer aspire one anywhere else on the forums that I can find.  Anyone have any ideas?

Wireless does not work I tried the madwifi-hal driviers by following the instructions at [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) After following these instructions absolutely nothing happened.  Does anyone know of a method that works?

I cannot mount my windows xp partition (/dev/sda2).  I get some error about rebuilding ntfs-3g with fuse support?  What is fuse?  I thought that I would have the packages I needed to read ntfs installed by default.

I want to try out ubuntu netbook remix but I don't know exactly what it is and which packages I need.  It seems as if this is two projects with the same name and that both are incomplete?  Can someone give me the full story on this?

Thank you for any help!!

---

### Post by gettinoriginal on 2008-12-30
See if this is any help:  :P

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

---

### Post by f37u5g0d on 2008-12-30
I have been using that guide and I think that I have gotten everything that I can out of it.  Like I said in my original post it did not help with wifi.  And it doesn't mention anything about ntfs or wired internet.  It is vague on ubuntu netbook remix which is why I asked about it here.

---

### Post by gettinoriginal on 2008-12-30
I do appologize, I did not notice the link in your post.  I did find this about drivers, post 16, but you might want to peruse the whole thread as it discusses alot of problems and solutions.  :P

[http://ubuntuforums.org/showthread.php?t=855906&page=2](http://ubuntuforums.org/showthread.php?t=855906&page=2)

[http://ubuntuforums.org/showthread.php?t=739998](http://ubuntuforums.org/showthread.php?t=739998)

---

### Post by f37u5g0d on 2008-12-30
I figuered out the netbook remix thing.  Pretty cool!  And I figuered out why I couldn't access my ntfs partition.  I had to add it to my privileges under preferences > users and groups.  I still have the following problems.

Wireless - I have tried the latest madwifi drivers and I have tried ndiswrapper.  There is no wireless extension found at all in the nm-applet and if I run ifconfig -a I get a loopback interface, eth0 (wired) and, some something called pan0 which is an ethernet device but not a wireless extension.

Wired - Doesn't connect under newest kernel.  Tries to connect, nothing happens.

I have a new problem as well.  I have several packages according to synaptic that are "local and/or obsolete".  If I mark them for removal it also attempts to remove things like ubuntu-desktop ubufox and other essential packages.  What is going on here?

---

### Post by f37u5g0d on 2008-12-30
Ok another update.  Wired is working again under the newest kernel.  I have no idea what changed it.  Perhaps it was just a fluke that is wasn't working before.  So now my issues are wireless and the local/obsolete files in synaptic.  Any ideas?

---

### Post by gettinoriginal on 2008-12-30
To get rid of any files no longer needed:
```
sudo deborphan | xargs sudo apt-get -y remove --purge
sudo apt-get autoclean
```
Anything left in local/obsolete is either something you installed outside of synaptic, or is outdated and no long in the updates.  But as long as it is working, leave it alone.

Since I am not running wireless, I am only going on what I read in the threads, so I will keep looking, sorry not more help.  :p

---

### Post by f37u5g0d on 2008-12-30
My wired ethernet is down again.  I found this problem quite odd.  I gave myself a static ip and it instantly I was "connected" according to the nm-applet.  (All of this btw is on the newest 2.6.27 kernel)  when I ping anything such as 192.168.1.1 (my gateway) I get no response from 192.168.1.112 (the ip that I gave my self)  Any and all addresses do this.  Same thing happens with a traceroute.  I have decided that I am going to try a different linux distro.  One aimed more at netbooks.  I really liked some aspects of ubuntu netbook remix.  No hard feeling for ubuntu though!  I still use it on my desktop :)  I just really need networking on my netbook and ubuntu isn't cutting it :(

---

### Post by gettinoriginal on 2008-12-30
Sorry we couldn't get it going, but good luck, and keep checking back in the forums, there may be a solution in some upcoming updates.  :P

---

### Post by stchman on 2008-12-30
I have the AA1 running Intrepid and it works perfectly.

To get the wireless working do this:

```
sudo apt-get install linux-backports-modules-intrepid-generic
```

These modules have support for the Atheros wireless cards.

To get the SD card reader working do the following:

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

Create a file /etc/modprobe.d/aspireone with the following content:

```
####################################################################
# Module options for the Acer AspireOne
#
# Enable USB card reader
options pciehp pciehp_force=1
install sdhci for i in 2381 2382 2383 2384; do /usr/bin/setpci -d 197b:$i AE=47; done; /sbin/modprobe --ignore-install sdhci
```

The commands are only 2 lines.  The documentation makes it look like three lines.

Next put:
```
pciehp
```

In your /etc/modules to load up at startup.  Reboot.

This works like a champ for BOTH SD card readers.

The webcam works somewhat spotty.

---

### Post by infinitejones on 2008-12-31
> **f37u5g0d said:**
> Wired networking doesn't connect on the newest ubuntu kernel (2.6.27).  It attempts to get a network address for about a minute (both lights are on in the nm-applet) and then it fails and says no connection.   

Wireless does not work I tried the madwifi-hal driviers by following the instructions at [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) After following these instructions absolutely nothing happened.  Does anyone know of a method that works?

Just a quick bump - the original poster may have given up but I'm suffering the same problems with wired and wireless networking.

I've re-installed from the 8.10 ISO - I assume this has an older kernel because from a fresh install, wired networking works. (Admittedly I didn't try wireless). Then following an aptitude safe-upgrade, which upgrades the kernel to 2.6.27, neither wired nor wireless works.

The Proprietary Hardware Drivers applet says that the Atheros driver is loaded and activated.

I guess I could just downgrade (or not upgrade) the kernel but that's a pain because Ubuntu will keep telling me to upgrade.

The instructions on the Aspire One pages on Ubuntu Community Documentation don't work.

Any ideas? Thanks! And happy new year!

---

### Post by f37u5g0d on 2008-12-31
Long story short I (the original poster) didn't give up.  I have a fresh ubuntu 8.04 install on my aspire one because of my no wired problem on 8.10.  I too am also going not upgrade to 8.10 until I am sure about it's compatibility.  I am going to do some research on networking on the acer aspire one and get back to this forum.  I need to fix the following:

Wireless
Read / Write ntfs partitions

The acer aspire one community page didn't help for me for 8.04 or 8.10.  I don't even have a wlan interface!  lspci does reveal the hardware though.

---

### Post by f37u5g0d on 2008-12-31
I have been trying to get ndiswrapper going.  For some reason it says that the driver is installed and that the hardware is present but it won't make a wlan0 interface.  Any ideas?

---

### Post by f37u5g0d on 2009-01-01
Bump

---

### Post by Davsdu on 2009-01-12
I cannot help you directly with your problem, I'm afraid, but instead I'd like to suggest [Easy Peasy 1.0]("http://geteasypeasy.com/"). It's a distro meant for netbooks and based upon Ubuntu 8.10 and the netbook remix interface. I've installed it on my Acer Aspire One 8gb ssd version and wifi worked out of the box. Kernel version is 2.6.27-8 with (cold) boot times around 50-60 seconds to desktop and internet connection (this can even be improved by tweaking the system). Response times are faster than Ubuntu 8.04 and 8.10 in my opinion. It's a pretty slick distro worth a try.

---

### Post by f37u5g0d on 2009-01-14
Thanks!

---

