---
title: "intel 2200bg wireless card"
date: 2004-12-28
forum: Hardware &amp; Laptops
---

### Post by labbe on 2004-12-28
Ok...
I have a centrino laptop with a Intel 2200Bg wireless card....
Anyone that can help me to get it working?
This is all I know:
after the "uname -r" command I get this:
2.6.8.1-3-386  

Please help me!

---

### Post by Krash1201 on 2004-12-28
intel wireless hasn't released the source for their drivers yet, so to get the wireless working, you have to use a package that will allow you to install the windows driver in linux.  for this, most of what i have run across in trying to install my wireless card is ndis wrapper found <a href="http://ndiswrapper.sourceforge.net/">here</a>.  follow the installation wiki for the how to.  you need to make sure you have the source available becasue the install requires that you build the package from source if you download it from source forge.  the easier way if you have a lan connection is to look for it in synaptic and install from there.  after you get ndis wraper installed, you have to load the windows driver.  source forge's install wiki for ndis wrapper explains how to do all fo this.  i have yet to get it working for my dell true mobile internal wireless card, but i have heard others have little to no problem with the install.

---

### Post by dredd on 2004-12-29
I'm using the same wireless card on my Acer TM3200 and I just added it in "Network" in the System configuration menu.
I added a new card and selected Wireless and it came up as Eth1, everythink works fine as long as you don't use DHCP. One strange thing is that the LED indicating that wireless is on never lights up, but it works perfectly anywhay.

Did you see if the Ubuntu installer detected it when you installed your system, it detected mine as an Intel Wireless, so I suspect Ubuntu uses the driver from ipw2200.sourceforge.net?

Hope you can get it right!

Greetings
Björn / Sweden

---

### Post by labbe on 2004-12-29
I can try one more time before i use the link krash gave me..
But I can use DHCP on the router??
I've tried it all, but the wireless connection turns off or something.
In network connection where you ca turn on and off connection; It wont work. 
after a few seconds it turn off.

---

### Post by theBlackDragon on 2005-01-11
[QUOTE=Krash1201]intel wireless hasn't released the source for their drivers yet,[/QUOTE]

[Excuse me?](http://ipw2200.sourceforge.net/)

---

### Post by labbe on 2005-01-12
okay, I needed to use manuel dhcp and take all myself..but it works now, and the drivers are on Ubuntu...

---

### Post by theBlackDragon on 2005-01-12
[QUOTE=labbe]okay, I needed to use manuel dhcp and take all myself..but it works now, and the drivers are on Ubuntu...[/QUOTE]

I had problems with it myself, the network connection didn't want to go up, I couldn't even select wlan0 in the networking dialog...so I started installing stuff from the wired connection and at once wireless just started to work... Why? Beats me ](*,)  but hey, it works...

---

### Post by LB06 on 2005-01-13
I think a modprobe ipw2200 will do the trick.

---

### Post by theBlackDragon on 2005-01-13
[QUOTE=LB06]I think a modprobe ipw2200 will do the trick.[/QUOTE]

No it didn't, drivers were already loaded for everything required by ipw2200 (I searched the forums and tried about everything suggested)

---

### Post by souki on 2005-01-14
the ipw2200 module is working very well for me, but I had to activate the wireless link before getting it to work

check your manual to see if there is a button to activate it, my laptop has one

before activate:
iwlist eth1 scanning
eth1      No scan results

after activate:
iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: XX:XX:XX:XX:XX:XX
                    ESSID:"XXXXXXXX"
                    Protocol:ieee 802.11g
                    Mode:Master
                    Channel:7
                    Bit Rate:54Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Extra: RSSI: -52  dBm
                    Encryption key:on

---

### Post by jerome bettis on 2005-01-17
[QUOTE=Krash1201]intel wireless hasn't released the source for their drivers yet, so to get the wireless working, you have to use a package that will allow you to install the windows driver in linux.[/QUOTE]

 8-[  :rolleyes: 

i'm currently using the intel supported ipw2200 driver available at ipw2200.sourceforge.net with mixed results.

all you need to do to get the driver working is have hotplug configured properly as a prerequsite, and then go dowload the latest version of the driver and firmware.

extract the tar files, and mv the *fw files to /usr/lib/hotplug/firmware .  then cd into the ipw2200* directory and sudo make ; sudo make install ; sudo reboot and you should be good to go.

of course you'll need to edit /etc/network/interfaces and supply the parameters for the card in there as well.  mine was eth1 under debian, i recently switched to ubuntu, and now it's eth0.

the card works OK most of the time, occassionally dropping off completely.  a simple sudo modprobe -r ipw2200 ; sudo modprobe ipw2200 ; ifup eth0 does the trick, sometimes just sudo ifdown eth0 ; sudo ifup eth0 will fix it.  this seems to happen with every router i've been connected to, which is why i think it's an issue with the card.

the driver has made pretty good progress from v0.02 to v0.19 and i hope gets better connectivity and supports monitor mode in the future.

---

### Post by theBlackDragon on 2005-01-17
@jerome bettis: that driver ships default with Ubuntu (don't know what version though), but I had problems getting it to actually work... I nearly resorted to installing it from source when it magically started to work just fine...

---

### Post by jerome bettis on 2005-01-17
[QUOTE=theBlackDragon]@jerome bettis: that driver ships default with Ubuntu (don't know what version though)[/QUOTE]

really?  i didn't know that.  when i put the in install cd in for the first time, it detected and recognized the card, i entered my essid and wep key but the network wasn't going up.  i had to install w/o the network and get the drivers from another computer.

if it really does ship with the driver, it's likely to be an old version.  the ipw2200 project doesn't maintain debian packages.  if i remember correctly, the last package was 0.04 which sucked ass.

check that side reguarly for updates, each one i've got has made the card better and better.

---

### Post by theBlackDragon on 2005-01-17
[QUOTE=jerome bettis]really?  i didn't know that.  when i put the in install cd in for the first time, it detected and recognized the card, i entered my essid and wep key but the network wasn't going up.  i had to install w/o the network and get the drivers from another computer.

if it really does ship with the driver, it's likely to be an old version.  the ipw2200 project doesn't maintain debian packages.  if i remember correctly, the last package was 0.04 which sucked ass.

check that side reguarly for updates, each one i've got has made the card better and better.[/QUOTE]

I think it's actually a pretty new version that ships with Ubuntu, as it's included in the kernel modules package, which is assembled by the Ubuntu devs...

---

### Post by jerome bettis on 2005-01-17
hey speak of the devil v 0.21 was just released today.

"# Provided __iomem typedef for pre-2.6.9
# Changed firmware event/error log dumping to be masked with IPW_DL_FW_ERRORS flag. If you encounter a firmware error, your kernel log will now just log the firmware restart.
# Fixed compilation warnings when CONFIG_IPW_DEBUG and CONFIG_IEEE80211_DEBUG are not defined
# Fixed warning on unused return code from pci_set_consistent_dma_mask
# Fixed #525 compilation problem with gcc 2.9.5 due to __FUNCTION__ not being followed by whitespace. (thanks to Dave Hansen)
# Fixed #530 problem after any resume (thanks to Henrik Brix Andersen)
# Fixed #363 problem after S4 resume (thanks to Yi Zhu)
# Fixed #488 problem with bridged networks and Ad-Hoc by adding target MAC to station table, regardless of if they are actual Ad-Hoc cells (thanks to Alex Hudson)
# Fixed #221 problem with setting mode immediately after load causing failures
# Incorporated fixes to use __iomem (thanks to Stephen Hemminger)
# Fixed #502 support for 64-bit platforms (thanks to Pedro Ramalhais and Angelo DiNardi)
# Fixed #431 problem with pci_alloc_consistent being handed a u32 instead of dma_addr_t (thanks to Jacek Wysoczynski and Marek Rudniewski)
# Fixed #379 problem w/ non-encrypted 802.1x authentication (driver no longer disassociates on privacy capability change -- similar to the behavior of ipw2100)
# Fixed #509 problem w/ resetting nic possibly leaving status variable bit set for a command being active.
# Fixed #450 problem w/ scan results not providing signal and level statistics"

i'm gonna give it a try here right now.

---

### Post by jerome bettis on 2005-01-17
holy crap this is sweet.  i normally can't get a signal in this room and it's working great with the new driver.

---

