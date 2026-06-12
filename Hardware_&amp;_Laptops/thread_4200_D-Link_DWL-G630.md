---
title: "D-Link DWL-G630"
date: 2004-11-12
forum: Hardware &amp; Laptops
---

### Post by mdweezer on 2004-11-12
This is a 802.11G card, at the moment i'm just using it to connect to B networks.

Is it possible to set this card up in linux?  I've heard lots of the G cards arn't supported yet.

Thanks all!

---

### Post by randy on 2004-11-12
I'm not sure if there's a native Linux Driver. The last dlink card I had didn't but I could get it to work with the ndiswrapper driver.

---

### Post by Starwoid on 2004-11-13
I think your g630 uses the Atheros chipset, like my g650? You'll have to check this.

If you, Ubuntu picked up my g650 during installation, and installed the right driver. If not, just hunt around for the madwifi driver (google search on madwifi) and this will do the trick.

If you want to connect to a 'g' network, you'll need wpa. This isn't part of the driver at the moment unfortunately, so you'll need a handy separate program called 'wpa_supplicant'... again a google search will find it for you. Read the doc's carefully before running it, you have to setup its config file carefully. Once this is working, and you are connected to your network, its quite easy to put the startup of wpa_supplicant into your linux startup scripts, so it starts on bootup.

I have my dlink g650 pcmcia card connected to my wpa psk airport extreme basestation, and it works quite nicely.

Hope this helps

---

### Post by mccan on 2005-02-02
I got this card to work by doing the expert install.  It saw the card (something like acx111) and I selected it (though it did not load during install, perhaps selecting it got kernel support installed?).  When prompted I downloaded all of the Ubuntu updates.  I downloaded and unzipped the latest XP driver from the d-link website (using unzip at the command line).  Then using synaptic I downloaded the ndiswrapper and following instructions to install (something like -i for install and -m for write configuration).  I was then able to click on the computer/system configuration/network menu item and added wlan0.  I had to use a hex wap key (not ascii -- 128bit worked).  

Good luck!

David

---

### Post by zombie1991 on 2005-02-07
This is all I did to get it to work this evening.  I had wireless already with an older linksys card.  The WPC11 v2.5.  To get that one working all I did was change one number in /etc/pcmcia/config .  I did a cardctl info and got my manfid.  There was one one number off.  I changed 0x1613 to 0x1612.  Rebooted and set up my card.  That was sweet.

To get this one going I installed ndiswrapper from repository.  I copied the xp drivers folder from the cd to my hard drive.  cd'd to location, typed ndiswrapper -i (name of  driver).inf  .  typed ndiswrapper -m.  It said adding alias to wlan0 and to something else.  Typed ndiswrapper -hotplug (not sure if I should have but I did).  Then typed modprobe wlan0.  Went to network settings after lights started flashing on the card and set it up.  It's working now but I have yet to turn it off or reboot.  I added ndiswrapper to /etc/modules in the hopes that that will start it up next time I reboot.

Forgot to mention.  I do not have the wpa stuff installed and I haven't tried to transfer files from computer to computer so I'm not sure if I'm at 54 or 11.  iwconfig says 54.  I hope it is.



============================================

I just reinstalled and tested my method for the G630.  You do NOT have to type:
ndiswrapper -hotplug

as it does nothing.  It worked as I said though for the rest.  Copy the drivers ndiswrapper -i (driver).inf
ndiswrapper -m
modprobe wlan0
then set it up in networking options.

---

### Post by eyephisc on 2005-02-11
Ubuntu is great!  I have this same card.  Question:  is it bad for any reason to start wpa_supplicant and the ndiswrapper module on startup even if you don't have the card installed?

Thanks!

---

### Post by MEW on 2005-02-28
I have the same card, and I got it working fine using zombie1991's instructions (Thanks). Then, I couldn't get it to work again after I restarted. If I run ndiswrapper -l to list installed drivers, it lists mrv8k51.inf and says "hardware NOT present". 

Figuring that If it would work once, it would work again, I uninstalled the ndiswrapper driver (ndiswrapper -e mrv8k51.inf) and removed the wlan0 alias line from the modprobe configuration.   I then tried to reinstall the driver (ndiswrapper -i then -m, then modprobe wlan0), and it still doesn't work.  

Does anyone have any ideas?

---

### Post by skgu67 on 2005-04-01
On 11-13-2004, Stawoid wrote:
> 
I think your g630 uses the Atheros chipset, like my g650? You'll have to check this.

If you, Ubuntu picked up my g650 during installation, and installed the right driver. If not, just hunt around for the madwifi driver (google search on madwifi) and this will do the trick.

If you want to connect to a 'g' network, you'll need wpa. This isn't part of the driver at the moment unfortunately, so you'll need a handy separate program called 'wpa_supplicant'... again a google search will find it for you. Read the doc's carefully before running it, you have to setup its config file carefully. Once this is working, and you are connected to your network, its quite easy to put the startup of wpa_supplicant into your linux startup scripts, so it starts on bootup.

I have my dlink g650 pcmcia card connected to my wpa psk airport extreme basestation, and it works quite nicely.

Hope this helps

I've gotten wpa_supplicant via the Synaptic Package Manager and tried reading every FAQ, How-To and other document I can find via google or the Ubuntu wiki and I _still_ can't get my D-Link G650 (rev C) to work.  Any chance you could post a step-by-step of how to get it running (or point me to one if I've somehow managed to miss an existing document)?  I've found instructions for the wpa_supplicant.conf file, instructions for how to call wpa_supplicant, instructions for how to activate the adapter, but nothing that tells me if it matters which order the various steps occur in or how to turn off the built-in network manager that wants to run the card using WEP instead of WPA-PSK.

TIA.

-- A true noob

---

### Post by benkorkor on 2005-04-09
I'm also having a little difficulty getting wpa_supplicant installed. Reading the wiki, it says to:

Now compile it with "make" and copy wpa_supplicant, wpa_passphrase and wpa_cli to some place that is in your $PATH, e.g., /usr/local/bin.

Now where is my $PATH? and what do i do with /usr/local/bin??

I read that WEP 40bit or 128bit is insecure so I need to change to WPA-PSK as soon as I can.

Any help would be appreciated.

---

### Post by syrnick on 2005-05-19
[QUOTE=zombie1991]
============================================
I just reinstalled and tested my method for the G630.  You do NOT have to type:
ndiswrapper -hotplug

as it does nothing.  It worked as I said though for the rest.  Copy the drivers ndiswrapper -i (driver).inf
ndiswrapper -m
modprobe wlan0
then set it up in networking options.
[/QUOTE]

Cool. That really works! Thanks.

Alex.
P.S.: I have DWL-G630 revB.

---

### Post by darkbane on 2005-06-13
I'm having tons of issues with my network card.  I'm using ndiswrapper and following the steps that I've see on tons of websites now, but I still can't get it to work.  I'm using dwl-g630 rev C.  Which driver is everybody else using.  I've tried win98, 2k and xp drivers, nothing seems to work.  I keep getting an invalid driver error when I do a list in ndiswrapper.

I'd appreciate any help you guys have to offer.

thanx

db

---

### Post by peacemaker885 on 2005-06-22
I got this card working using madwifi drivers:

1. Downloaded and compiled latest cvs:
cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/madwifi \
co madwifi

2. modprobe ath_pci

3. dowloaded and compiled wpa_supplicant enabling these:
# Driver interface for madwifi driver
CONFIG_DRIVER_MADWIFI=y
# Change include directories to match with the local setup
CFLAGS += -I../MadWifi/madwifi   --->change this!

4. Created wpa_supplicant config file:
 ctrl_interface=/var/run/wpa_supplicant  # for wpa_cli support

network={
  ssid="myssid"
  psk="mypasskey"
  key_mgmt=WPA-PSK
  proto=WPA
}

5. Created a script home-wifi.sh:
ifconfig ath0 up
wpa_supplicant -Dmadwifi -iath0 -c/etc/wpa_supplicant.conf -bb

6. Get ip via dhcp:
dhclient ath0

If everything goes ok, change "-bb" in home-wifi script to "-B"

Hope this helps.

---

### Post by peacemaker885 on 2005-06-22
All of the stuff I wrote above are from the respective README's or FAQ's of the respective websites:

[http://madwifi.sourceforge.net/](http://madwifi.sourceforge.net/)
[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)

---

### Post by imz on 2005-07-06
I found the comments here useful for making my DWL-G630 rev. C card work. Now I'm using native linux drivers, the madwifi ones (0.9.14.9) mentioned in the previous comment.  

I'm not using Ubuntu.
Since the D-Link site lacked information on this model under linux ([http://support.dlink.com/faq/view.asp?prod_id=357&question=General%20Wireless)](http://support.dlink.com/faq/view.asp?prod_id=357&question=General%20Wireless)), I used to be in doubt whether the errors I get can be overcome. But this page gave me hope. ;) Finally, I made it work by giving "acpi=off pci=routeirq" to the kernel I use (so, the problem was with the kernel probably).

Thanks.

---

### Post by DataHazard on 2005-07-08
I am having a pain dealing with this card. I have the ver. C1 of the G630 and ndiswrapper will not work.  When I go to load the driver ndiswrapper returns about 9 lines each with the words "Cant Locate" on it and after if I ry to type in modprobe ndiswrapper or modprobe wlan0 it says no module found. pleas help me.

FYI the versions A and B of this card use the TI chipset and madwifi or the native acx111 drivers work well for these cards but if you have C1 or C2 then you have the Atheros chipset and madwifi will not work.

---

### Post by peacemaker885 on 2005-07-23
Update:

On my first post, I wasn't using Warty or Hoary..but Sarge.  I was didn't mention this before because I thought it wouldn't really matter.  Anyways, I had to re-install my laptop, downloaded the latest madwifi from cvs and then re-compiled.  For some reason, this latest version wouldn't run properly on my setup.  The connection was down every few seconds.

I then decided to try ndiswrapper agian.  I tried it before but was unable to get it working.  I followed the [instructions](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)  on their website, but used the stable version and not the latest via cvs.  

The one thing I did differently this time was use the driver that is linked on their [wiki](http://ndiswrapper.sourceforge.net/mediawiki-1.4.6/index.php/List)  and not the ones that came with it on cd.  

For some strange reason, it worked!  I looked the file sizes of the downloaded vs the cdrom ones and didn't see any difference.

---

### Post by wolfdragon_2848 on 2005-09-30
I'm having some problems with this card, rev C. I've managed to install ndiswrapper and what I think is the right file for the driver (no other files would work). I got the driver off the D-Link site. "wlan0" appears on network-admin and on the taskbar. Those are the things that seem to have gone right. However, the card's lights blink alternately (I don't think they're suppose to do that if everything's working fine) and the connection properties show that packets have been received but none have been sent (???).  I can't ping anything or access the internet. It seems to display signal strength correctly but I could be wrong. My AP uses WEP but I'm pretty sure that I've entered the right key.

(On another note, I also have another wireless card, Netgear, and that one doesn't work properly either. The link light is suppose to blink when it transfers data and it never does, it stays constantly lit. I'm pretty sure I had installed the driver correctly but I wasn't able to access the internet with that one either.)

---

### Post by pbureau on 2007-01-19
I also have the dlink G630 Rev C1 under Ubuntu 6.10

Hardinfo info reconizes it as ;
Atheros Communications, Inc. AR5005G 802.11abg NIC

ndiswrapper -l reveals;
Installed ndis drivers:
net5211 driver present, hardware present 
(this driver loaded from CD rom of Dlink)


iwconfig reads;

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"PBLC"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=56/94  Signal level=-39 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig read;
ath0      Link encap:Ethernet  HWaddr 00:11:95:4A:02:E8  
          inet6 addr: fe80::211:95ff:fe4a:2e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
wifi0     Link encap:UNSPEC  HWaddr 00-11-95-4A-02-E8-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13059 errors:0 dropped:0 overruns:0 frame:25615
          TX packets:20021 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1757300 (1.6 MiB)  TX bytes:966403 (943.7 KiB)
          Interrupt:11 Memory:d0ca0000-d0cb0000 

So what do I need to get this thing going... I am lost after all the posts...
Hellllllp!

PS: trying to get this to work with WPA-TIK network , thanks

---

### Post by nnolan on 2007-04-19
I'm having problems with a D-link DWL-G630 as well.  Mine is a Ver. C2.  It shows as being the AR5005G chipset as ath0.  It installed fine in both Edgy and Feisty.  The card works fine on an unsecured network, but WPA is another story.  I cannot establish a connection at all while using WPA.  I've tried network-manager-gnome.  I've tried using the various keywords in /etc/network/interfaces that work with wpasupplicant in the newer distributions.  Is there a problem with the driver / kernel with this version of the card or what.  I thought the card would be golden since it is an Atheros chipset.  I also have a Zydas 1211 usb adapter, if that is easier to make work.  Any advice or help would be welcome.

---

### Post by pg1978 on 2007-06-24
After much searching through these forums  I have managed to get my wireless going, despite being clueless with linux.
My DWL-g630 is rev A1 (I haven't seen many other posts on this rev). The XP driver did not work with ndiswrapper but the Win98 driver works well:
[http://www.dlink.com/products/support.asp?pid=317&sec=0#drivers](http://www.dlink.com/products/support.asp?pid=317&sec=0#drivers)
Cheers

---

### Post by zetha on 2007-08-27
Hi there! if someone needs to configure it... Dlink has linux drivers... check here [http://www.dlinkla.com/home/productos/producto.jsp?idp=709](http://www.dlinkla.com/home/productos/producto.jsp?idp=709)

---

### Post by mikecool on 2008-01-10
Hi, is there anyone use this adapter on TOSHIBA Satellite 3000?

I bought one for that aged laptop, but OS can't find it at all. What's wrong with that? I tested the adapter with a brand new Dell laptop. It works well.

Thanks!

---

### Post by JonNicholson on 2008-01-10
I had a problem with this, but not now.  I upgraded to Ubuntu 7.10, installing and running the ndiswrapper install program:  install "Windows Wireless Drivers" using the "Add/Remove" program on the "Applications" menu, on the GUI desktop menu bar.  

Before you open the ndiswrapper installation, get the Windows XP driver .inf file for the D-Link DWL-G630.  I copied the whole folder "WinXP" from my Windows XP install CD into my "Documents" folder on my PC.  Then I ran "Windows Wireless Drivers", browsed to the "WinXP" folder, and double-clicked on the file "TNET1130.INF".  This installed the driver.  Then I closed the program window.

Next, I went to the "System" menu on  the desktop menu bar, selected the "Administration" sub-menu, and started the "Network" program.  Alternatively, you can click on the network icon on the desktop menu bar and select "Manual configuration".  This will open the network configuration window.

I double-clicked on "Wireless Connection", which called up the wlan0 Properties box (you can also just click on the "Properties" button).  I _de_-selected "Enable roaming mode", so that I could choose "Automatic configuration (DHCP)" on the "Configuration" menu.  You also need to have "WPA Personal" selected on the "Password type" drop-down menu.  Then I clicked "OK" to close the box.  Once you do this, you can click on the "Wireless connection" check box to activate the connection.  I also did the _same procedure for the wired connection_, although I don't know if this is necessary.  It seemed like I should be consistent, and my wired connection still works fine.

I'm not proficient enough to understand why you have to de-select "Enable roaming" on the configuration menu -- but after this procedure, my DWL-G630 works great.

Good luck!

---

### Post by mikecool on 2008-01-14
> **mikecool said:**
> Hi, is there anyone use this adapter on TOSHIBA Satellite 3000?

I bought one for that aged laptop, but OS can't find it at all. What's wrong with that? I tested the adapter with a brand new Dell laptop. It works well.

Thanks!

Finally, I fixed this problem by repairing the laptop by myself. The PCMCIA dock is looser from the mainboard. Now it works well with my BUFFALO AP.

---

### Post by blissb2599 on 2008-05-18
My setup:  Gateway 600YGR with Kubuntu 8.04.  Installed and updated and all that using the wired port.

Turned off the machine, slapped in the DWL-G630 (just purchased from CompUSA for $14.99) turned on the machine, and that was it.  The KNetworkManager showed all the local wireless networks -- I selected the one I wanted, and was connected.  No driver hassles, no configuration issues, and best of all for me, no ndiswrapper stuff to deal with.

I have to say I'm impressed, both with KUbuntu and dlink...

Bill

---

