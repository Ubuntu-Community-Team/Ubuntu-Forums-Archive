---
title: "No Wireless Network after upgrade to 9.10"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by swatsbiz on 2009-10-30
I have just upgraded my wife's 9.04 distro up to 9.10 through upgrade manager, everything went fine, however after reboot, I have no network connection.

It's a wireless network connection, and all the settings are still there, it's just not detecting the network.

Any help would be appreciated.

David

---

### Post by MorlanXaos on 2009-10-30
I've got the same problem, after installing the update, the network manager was unable to log me in again. It does not show me any network available.

Wifi's card driver is Ok.
Wifi-Spy shows me all the connections available around.

[I]xavier@xavier-casa:~$ sudo lshw -C network
*-network
   description: Wireless interface
   product: 88w8335 [Libertas] 802.11b/g Wireless
   vendor: Marvell Technology Group Ltd.
   physical id: 1
   bus info: pci@0000:04:01.0
   logical name: wlan0
   version: 03
   serial: 00:1e:2a:47:44:17
   width: 32 bits[/I]
clock: 66MHz
capabilities: pm bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+mrv8335 driverversion=1.55+Marvell,02/22/2005,3.1.1.7 latency=64 link=no multicast=yes wireless=IEEE 802.11g
resources: irq:17 memory:febf0000-febfffff memory:febe0000-febeffff

---

### Post by wiley692 on 2009-10-30
I am having the same problem with both my Dell Inspiron 1525 and Mini 9.

---

### Post by dummy910 on 2009-10-30
if it's an Atheros based card, try:
```
sudo apt-get install linux-backports-modules-karmic
```
then reboot.

---

### Post by NormanFLinux on 2009-10-30
No problems here with wireless in 9.10 on both my Dell Inspiron e1505 and Dell Mini 10. They both have a Broadcom wireless card.

---

### Post by bcooperb on 2009-10-30
No wireless on a Dell XPS m1730 Laptop.

Clean install 9.10 64bit 

I'm not sure how to look and see what hardware I'm running via command line.

I plugged in a network cable and the internet is running on there, but was running this one 9.04 32bit wireless no problem before new install.

In my network connections I don't show anything for Wireless.

Any ideas on what to check for my wireless connect. Any help would be great!


EDIT ****

*-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0efc000-f0efffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5754M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:21:9b:d4:85:89
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5754m-v3.23 ip=10.38.33.86 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:31 memory:eeff0000-eeffffff



I'm not sure what I"m looking for here?


EDIT **

Per

---

### Post by swatsbiz on 2009-10-30
> **dummy910 said:**
> if it's an Atheros based card, try:
```
sudo apt-get install linux-backports-modules-karmic
```
then reboot.

Done that, still no networks available :-(

here's the output from:

```
sudo lshw -C network
```

```
*-network  UNCLAIMED
description: Ethernet controller
product:  AR2413  802.11bg NIC
vendor:  Atheros Communications Inc.
physical id:  8
bus info:  pci @0000:01:08.0
version:  01
width:  32bits
clock: 33MHz
capabilities:  pmbus_mastercap_list
configuration:  latency=32 maxlatency=28 mingnt=10
resources:  memory: fbff0000_fbffffff 
```

Many thanks again

David

---

### Post by swansong on 2009-10-30
After upgrading from 9.04 to 9.10, my Atheros (ar5212/ar5213) wireless device was not working, although it had been working before the upgrade. After hours of searching many, many websites, I found a post that mentioned "blacklist-ath_pci.conf". I typed "gksudo gedit /etc/modprobe.d/blacklist-ath_pci.conf". This is what opened:

# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
blacklist ath5k 

I put a "#" in front of the last line (#blacklist ath5k) saved the file, and rebooted (logging out and back in probably would have worked, but after all my searching and reading I wasn't taking any chances.)

It works.

---

### Post by swatsbiz on 2009-10-31
Thanks that worked for me too, why would Ubuntu do that?

---

### Post by rguttkuhn on 2009-10-31
I have to ask the same question; Why would Ubuntu do that?

I am a seasoned Windows IT guy who dipped his feet into the Linux experience a few months ago.
I installed Ubuntu 9.04 on my aging Siny VAIO PCG-SRX87 - and I was impressed.
I only had to "hack" with the xorg.conf file to get my screen resolution to 1024x768. Aside from that everything just worked. Network, sound, even VPN into our work windows domain. Wow.
Then I get the message that 9.10 is available. Sure I want to upgrade. That's when things started to get annoying.
The new Ubuntu loads fast and looks really nice - but no wireless. I thought that maybe the upgrade ends up with a funky mix of old and new and decided to install 9.10 from scratch. Still no wireless.
Installing 9.04 from scratch yesterday got my wireless back.

Why would something that worked fine out of the box be broken in an "upgrade". Makes no sense to me.
And no I have no idea what kind of wireless card is in that thing. Ubuntu recognized it fine in 9.04. It just worked.

All I can say that this is frustrating. I am back to 9.04 and now have to remember all the little edits I did to get my shares mapped and the data rsynced with my freenas server and all those little things that impressed me with my little Linux notebook in the first place.

---

### Post by bluepenny65 on 2009-10-31
> **swatsbiz said:**
> Thanks that worked for me too, why would Ubuntu do that?


Are you on an Atheros card too or Broadcom? I am still having this freggin' issue with broad...even after doing some recommended steps in other threads.

---

### Post by acornbrain on 2009-10-31
It took me a whole day researching fixes when trying to get my wireless adapter to work when I clean-installed 9.04 a few months ago...so now I am really gun-shy about upgrading. I still consider myself a big newbie.

Is upgrading to 9.10 universally recommended? What are the benefits? Am I being paranoid here? Am I going to have to teach this thing to walk and talk all over again? By this point, I've probably forgotten most or all the stuff I did to get everything running just so in the first place.

---

### Post by swatsbiz on 2009-10-31
> **bluepenny65 said:**
> Are you on an Atheros card too or Broadcom? I am still having this freggin' issue with broad...even after doing some recommended steps in other threads.

My previous post should show that it's Atheros.

On a more positive note, my Acer Aspire 1350 which rarely worked with Windows properly, didn't work with 8.* or 9.04, is working nicely under 9.10.

---

### Post by swatsbiz on 2009-10-31
The Network seems to be having trouble staying connected then a reboot is required ... :-( still not great for an upgrade

---

### Post by zenboy on 2009-10-31
> **swatsbiz said:**
> Done that, still no networks available :-(

here's the output from:

```
sudo lshw -C network
```

```
*-network  UNCLAIMED
description: Ethernet controller
product:  AR2413  802.11bg NIC
vendor:  Atheros Communications Inc.
physical id:  8
bus info:  pci @0000:01:08.0
version:  01
width:  32bits
clock: 33MHz
capabilities:  pmbus_mastercap_list
configuration:  latency=32 maxlatency=28 mingnt=10
resources:  memory: fbff0000_fbffffff 
```

Many thanks again

David



    Didn't work for me. I got BCM4306 Broadcom card on my Dell D400 laptop. The last line showed "blacklist ath_pci", but did not worked when I put # in front of it and reboot.
  This thread with be bombarded with hundreds of posts pretty soon after people start installing this new release, looking for the wireless solution. 
This problem is similar to the intel video problem on Ubuntu 9.04 that many people were having. After digging through thousands of posts and trying a dozen of suggestions, I couldn't get the video to work at probably. I had to install Ubuntu 8.04 to learn this new Linux OS many people were raving about. 
   This is some of the number of Linux issues that scare potential users away because "it does not work out of the box" like it should  (even after going through dozens of suggestions like I did to get the problem resolve). 
    I wait and see if there is any other suggestions to get the problem fixed before I dump Ubuntu and install Windows 7.
Frustrated and disappointed to see that Linux isn't still  the desktops on most of the PCs out there like many IT articles rave about. :(

---

### Post by Jesus_Valdez on 2009-10-31
I had a few problems with the driver for a broadcom card on my Dell inspirton 1525.

What I did is, in Synaptic uninstall the packages call bcmwl-kernel-source, del the residual conf. and re-install it.

After that, my network is alive again.

---

### Post by dummy910 on 2009-10-31
> **swatsbiz said:**
> Done that, still no networks available :-(

here's the output from:

```
sudo lshw -C network
```

```
*-network  [color=red]UNCLAIMED[/color]
description: Ethernet controller
product:  AR2413  802.11bg NIC
vendor:  Atheros Communications Inc.
physical id:  8
bus info:  pci @0000:01:08.0
version:  01
width:  32bits
clock: 33MHz
capabilities:  pmbus_mastercap_list
configuration:  latency=32 maxlatency=28 mingnt=10
resources:  memory: fbff0000_fbffffff 
```

Many thanks again

David
I ran into the same thing this morning on a users laptop who was absent and just let the upgrade continue on it's own.

Any who, check out this link, as I posted the fix(**Note:** the ***-network  [color=red]UNCLAIMED[/color]** line is the key phrase in the aforementioned output of **lshw -C network** ):
[http://ubuntuforums.org/showpost.php?p=8206369&postcount=5](http://ubuntuforums.org/showpost.php?p=8206369&postcount=5)

---

### Post by rbsteinbach on 2009-10-31
Hi Guys:  I just had the opposite situation.  I had 9.04 installed on an IBM TP-G41 and could not get the wireless adapter to work, although the hard-wire adapter worked flawlessly right out of the box (so to speak).  Just ran the on-line/in-place upgrade to 9.10 and now the wireless adapter (Atheros) is recognized and works fine. :p Just thought you might be interested.

---

### Post by zenboy on 2009-10-31
> **dummy910 said:**
> I ran into the same thing this morning on a users laptop who was absent and just let the upgrade continue on it's own.

Any who, check out this link, as I posted the fix(**Note:** the ***-network  [color=red]UNCLAIMED[/color]** line is the key phrase in the aforementioned output of **lshw -C network** ):
[http://ubuntuforums.org/showpost.php?p=8206369&postcount=5](http://ubuntuforums.org/showpost.php?p=8206369&postcount=5)

I finally got the wireless to work on my dell d400 laptop with broadcom modem. 
I originally did sudo gedit blacklist-ath_pci.conf and put # at the bottom for blacklist ath_pci, which didn't work after I rebooted.
I then followed your direction in [http://ubuntuforums.org/showpost.php?p=8206369&postcount=5](http://ubuntuforums.org/showpost.php?p=8206369&postcount=5). 
I did ls in the directory to look for bcm****.conf for my broadcom card but only found black -ath_pci.conf file that I originally edited.  
Did a sudo apt-get install linux-backports-modules-karmic to reboot the computer. Still no prevail.
Then I went to my linksys router and did a show SSID broadcast and reboot the router. 
Went to the wireless network connection on laptop and saw my SSID and are able to connect to the router.  To see if the wireless connection connected permanently, I disable SSID broadcast on the router and reboot it as well as the laptop. 
Finally got it to work. 
Now I don't know whether it was the linux-backports-modules-karmic installation or the SSID broadcast that the wireless card needs to see for the first in order to connect, but it is finally working.
Sorry if I need to explain in details ; I just think that some other newbies such as I might need a helping hand. Now let see if there are other glitches with this new release that may come up. Thanks to everyone for the great support!

---

### Post by 44tr on 2009-11-06
For some reason the wireless is broken on the initial release of 9.10 for the broadcom adapter.  This thread shows the quick fix and details.

[http://ubuntuforums.org/showthread.php?t=1304978&highlight=dell+inspiron+E1505+wireless](http://ubuntuforums.org/showthread.php?t=1304978&highlight=dell+inspiron+E1505+wireless)

Basically, you update the repositories, install bcmwl-kernel-source package and reboot and it should work (it did for me!).  Remember to select the network to connect to; it doesn't do it by itself.  Some other hints and links on the thread.  A little goof for the Ubuntu release team, but it is a big job.

---

### Post by bwzz on 2009-11-09
I installed 9.10 on Acer Aspire One and worked out of the box.
When I installed it on DELL Inspiron Mini, and Wireless didn't work.
 
After checking few threads, found this solution:
 
Re-install: bcmwl-kernel-source and bcmwl-modaliases via Synaptic Package Manager
 
but when I went to the Synaptic Package Manager, the 
**bcmwl-kernel-source and bcmwl-modaliases **
was NOT installed!!!
Once installed and rebooted, the wireless work just fine...

---

