---
title: "Never used Linux before, dual-booting a laptop, hardware problems"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by Cyber Akuma on 2008-01-28
I tried to look through the hadware compability/incompability sticky topics on this forum but Firefox for some reason could not load the links.

I have a Toshiba Satellite A215-S7413 Laptop, with the RAM upgraded to 4gb and the HDD upgraded to 250GB.

I cloned my stock drive to a  200gig partition on the new drive and let Ubuntu partition the rest.

Anway, Ubuntu and Vista both dual-boot fine, now that Ubuntu has been Installed, I needed help on installing drivers for devices it could not detect such as my WiFi hardware, Sound hardware, and others.

I installed the 64bit version of Ubuntu 7.10.

According to Vista's device manager, I have a Realtek RTL8187B Wireless 802.11b/g USB 2.0 WiFi card and the sound hardware is simply listed as "Realtek High Definition Audio"

A friend told me to go to Synaptic Package Manager and check everything in the "Ubuntu Software" and "Updates" tabs, then to find the "Windows Wireless Drivers" WiFi update and install it. Although this didnt seem to do much since there were no drivers listed in the app.

Afterwards, he told me to try to install this: [http://danmarner.blogspot.com/2008/01/rtl8187b-linux-native-driver-works-on.html](http://danmarner.blogspot.com/2008/01/rtl8187b-linux-native-driver-works-on.html)

But after enabling it with the sudo ./wlan0up command I couldent get it to connect to my WiFi network (granted, I have a slightly strange setup, static IPS and WEP 128) and after this I couldent even connect through a wired setup until I rebooted Linux.

So anyway, I am compeltely clueless on what to do, I have been using Windows for years, but I have no idea how to even install applications or how the navigate through the filesystem, I was barely able to setup my wired connection.

Is there any way I can make Ubuntu scan my system for any hardware it can detect that it has no drivers installed for the way Windows can? It would make it a lot easier to identify what it has not been able to setup/find drivers for. I know that at the very least it cannot install my WiFi and sound card, possibly my Bluetooth and 3D hardware as well, and I have no idea what else.

At this point I just simply installed every system Update that Ubuntu warned me about, I am not sure what to do next.

Any help would be appreciated, Thanks.

---

### Post by RudolfMDLT on 2008-01-28
For Future reference - Is this what you have?: [http://www.toshibadirect.com/td/b2c/rdet.jsp?poid=394265&seg=HHO](http://www.toshibadirect.com/td/b2c/rdet.jsp?poid=394265&seg=HHO) It says here, right at the bottom, that you don't have bluetooth but you seem to think that you do? ;)

I'll do my best to answer most of your questions and to help where I can. 

Linux doesn't have a device manager for installing hardware - as far as I know! :) and I have never needed one. Most of the time you never need to install anything, the Linux Kernel takes care of most of it for you. I own 2 pc's and a laptop and I have only ever had a problem with ati graphics cards.

The problems that you are facing is that you bought a system that really is not Linux friendly! :) Due to some companies being more anal than others, some devices work better than others... and some just won't. Your ati card is something that has been causing hassles for years! :) 

But lets not give up right now... 

Firstly, to give you a "graphical view" of your hardware, install hardinfo, in the terminal copy and paste:
> sudo apt-get install hardinfo


also in the terminal, please type the following command and paste the entire output here. Please paste the output in code/quote brackets(second row, 4th button from the left of the font tool bar when you reply to this.) Also, make sure that the terminal is as wide as you can stretch it.

> lspci


Now, lets get the network working. You'll be learning some of the backend of Ubuntu here! :)

Please get close to your Wireless access point, enable the driver like you where told in the howto and paste the output of these commands, one by one:

> iwconfig
> iwlist scan
> lsmod | grep wlan
> lsusb

Also, in the top right of your screen there should be an icon that looks like 2 computers,  when clicking on this icon, do have a wireless option?

Now, this has all just been to give me a very good look at what is going on. Can you also please tell me:

1)what the SSID is of the access point
2)What make is the access point and the router
3)The IP address of your gateway (eg. adsl router ect..)

Could it also be possible for you to turn off the WEP of WPA encryption just for testing purposes.


Report back as soon as you can and goodluck!

Rudolf

PS:

Some general stuff you would want to read:
[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)
[http://ubuntuforums.org/showthread.php?t=515573](http://ubuntuforums.org/showthread.php?t=515573)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by gamermic on 2008-01-28
Great work!

---

### Post by RudolfMDLT on 2008-01-28
> **gamermic said:**
> Great work!

Thanks man! ;) Lets hope Cyber Akuma finds it useful aswel! 

@Cyber Akuma

If the Wireless driver does give us crap later there still is hope. I just went to look through the NDISwrapper site and found your EXACT chipset under their "working" list. What is NDISwrapper?
> NdisWrapper is effectively an open-source driver (technically described as a kernel module) that allows Linux to use standard Windows XP drivers for wireless network devices. You might describe NdisWrapper as being a translation layer between the Linux kernel and the Windows drivers, which can be installed using NdisWrapper’s configuration tools.

Don't go here yet - Lets see if the native driver works first - but here is a very detailed HowTo on how to get NDISwrapper working for your card:
[http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/)

also, here is the page where I found your chipset. [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_o-z/)

It's a big list so do a search for RTL8187B. Could you maybe confirm the brand of your card? If you insert the driver CD that came with the laptop, what brand is  listed in the install?

---

### Post by Cyber Akuma on 2008-01-29
Sorry for the late reply

> **RudolfMDLT said:**
> For Future reference - Is this what you have?: [http://www.toshibadirect.com/td/b2c/rdet.jsp?poid=394265&seg=HHO](http://www.toshibadirect.com/td/b2c/rdet.jsp?poid=394265&seg=HHO) It says here, right at the bottom, that you don't have bluetooth but you seem to think that you do? ;)


Yeah, thats the one. Huh, I could have sworn I saw drivers for bluetooth hardware listed in Vista's device manager, strange.

> **RudolfMDLT said:**
> I'll do my best to answer most of your questions and to help where I can. 

Linux doesn't have a device manager for installing hardware - as far as I know! :) and I have never needed one. Most of the time you never need to install anything, the Linux Kernel takes care of most of it for you. I own 2 pc's and a laptop and I have only ever had a problem with ati graphics cards.

Well, so far the video seems to be working fine, although I havent tried anything requiring 3D acceleration yet.

> **RudolfMDLT said:**
> The problems that you are facing is that you bought a system that really is not Linux friendly! :) Due to some companies being more anal than others, some devices work better than others... and some just won't. Your ati card is something that has been causing hassles for years! :)

Ouch...... any 3d rendering benchmark/testing apps for Linux that I can try to test it?

TO be perfectly honest Linux was not on my mind when I purchased this thing, it was $400 at Black Friday and kind of an impulse buy, when I decided to upgrade the HDD just in case I figured why not dual boot so I can learn how to use Linux since for over a decade now my only expirence has been Windows and DOS.

> **RudolfMDLT said:**
> Firstly, to give you a "graphical view" of your hardware, install hardinfo, in the terminal copy and paste:


also in the terminal, please type the following command and paste the entire output here. Please paste the output in code/quote brackets(second row, 4th button from the left of the font tool bar when you reply to this.) Also, make sure that the terminal is as wide as you can stretch it.

> 
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

Question: I noticed the command is ls**PCI**, does this scan the PCI bus? Because Vista's device manager said USB 2.0 at the end of my WiFi card's name. Is it possible its internally wired to the USB bus?


> **RudolfMDLT said:**
> Now, lets get the network working. You'll be learning some of the backend of Ubuntu here! :)

Please get close to your Wireless access point, enable the driver like you where told in the howto and paste the output of these commands, one by one:

Errr, about my WiFi setup. Remember when I said its a strange setup? It dosen't broadcast it's SSID...

iwconfig:
> 
lo        no wireless extensions.

eth0      no wireless extensions.

iwlist scan:
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

lsmod | grep wlan:
(nothing happened)

lsusb:
> Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 006 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 006 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 006 Device 001: ID 0000:0000  



> **RudolfMDLT said:**
> Also, in the top right of your screen there should be an icon that looks like 2 computers,  when clicking on this icon, do have a wireless option?

Nope, just wired and modem.

If I type that command I mentioned previously from the drivers I mentioned a Wireless option appears but it dosent work and makes wireless not work either until I reboot.

> **RudolfMDLT said:**
> Now, this has all just been to give me a very good look at what is going on. Can you also please tell me:

1)what the SSID is of the access point
2)What make is the access point and the router
3)The IP address of your gateway (eg. adsl router ect..)

SSID: CybeHouse

Access Point: Linksys WRT54GS (not just plain G) Firmware v4.71.1 I am not sure which hardware revision it is, I know its not a version 1 because those had 20 leds on the front panel and mine has 8, but I know its older then a version 4 because I purchased it before Linksys reduced the amount of ram and flash they contained, and version4+ firmware is at 1.06.1. All I know is that its somewhere between version 1.1 and 3.0, Linksys claims the serial number should say the version next to it but it dosent.

Gateway: My router's gateway is 192.169.1.1, my cable modem's is 24.12.216.1

> **RudolfMDLT said:**
> Could it also be possible for you to turn off the WEP of WPA encryption just for testing purposes.

Sure, but shoudlent we get drivers installed for it first?

---

### Post by Daelyn on 2008-01-30
> **Cyber Akuma said:**
> 

Question: I noticed the command is ls**PCI**, does this scan the PCI bus? Because Vista's device manager said USB 2.0 at the end of my WiFi card's name. Is it possible its internally wired to the USB bus?


That is entirely correct.

```
lspci
``` scans the pci bus for any attached stuff, also tries to identify what manufacturer it is and what kind of "device".
To check your USB bus for that dodgy wireless card, run the following command in terminal and post your output please.

```
lsusb
```

Lets see what we can do about this :)

---

### Post by RudolfMDLT on 2008-01-31
> Sure, but shoudlent we get drivers installed for it first?
Yes, Though I first needed to verify that they work or don't.

> But after enabling it with the sudo **./wlan0up** command I couldent get it to connect to my WiFi network (granted, I have a slightly strange setup, static IPS and WEP 128) and after this I couldent even connect through a wired setup until I rebooted Linux.

Did you enable the drivers with **that** command before posting this:

> Errr, about my WiFi setup. Remember when I said its a strange setup? It doesn't broadcast it's SSID...

iwconfig:
Quote:
lo no wireless extensions.

eth0 no wireless extensions.
iwlist scan:
Quote:
lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.
lsmod | grep wlan:
(nothing happened)

Because even if you have a hidden SSID, "iwlist scan" will show it. I have an even more complex setup - I use a Wireless Selfhealing Mesh by Meraki. Even though Windows only shows 1 Access point, doing an "iwlist scan" reveals all 4 AP's, their MAC address, the kind of WEP or Version of WPA they are using and also which channel they are working on.

Anyway, Did you enable the driver before doing all these commands? 

Because:
> iwconfig:
Quote:
lo no wireless extensions.

eth0 no wireless extensions.

lo is the loopback adapter and eth0 is the Wired adapter. There is no wlan or ath0?

Also;

"lspci" Tells me all that is on the PCI BUS. There is no Wireless network in your pci bus, only the Wired Adapter.

"lsusb" Confirms my fears, and that is that your Wireless is on the USB bus. Now, I may be paranoid, but getting a USB Wireless adapter to work is a little more difficult than a standard adapter.

Anyway, If you did enable the wireless driver before posting, then the drivers are indeed not working and it seems not even loaded - "lsmod", lists all modules and drivers loaded. Then we may need to go the Ndiswrapper route.

Could you please just once more, try to load the drivers first, then do a "iwlist scan" and a "lsmod | grep wlan".


@Daelyn,

Thanks for jumping in! :) I didn't think the the OP was coming back! Don't go away either, I'm not too hot with Ndiswrapper.... ;)

---

### Post by Cyber Akuma on 2008-01-31
Whoops, sorry about that, I forgot to run that wlan0up command before posting that.

iwconfig:
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Channel=4  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


iwlist scan:
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:52:5F:94
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:8
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 
                    Quality:14  Signal level:0  Noise level:89
                    Extra: Last beacon: 1457ms ago

lsmod | grep wlan:
(nothing still happens)

EDIT: Bah, damn auto-smilies

---

### Post by RudolfMDLT on 2008-01-31
Thought so! LOL! ;) Thats fine!

> Cell 01 - Address: 00:0F:66:52:5F:94
ESSID:"<hidden>"
Protocol:IEEE 802.11b
Mode:Master
Channel:8
Encryption key:on
Bit Rates:11 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 11
Quality:14 Signal level:0 Noise level:89
Extra: Last beacon: 1457ms ago

This is good news!

Give me a couple of minutes to find my laptop so I can make DOUBLE sure of the next step. Unfortunately, we'll have to do things manually as you say this driver crashes stuff.

Now - Linux command intro:

**ifconfig** - This shows your current IP configuration
**sudo ifconfig eth0 192.168.10.2/24** - Changes eth0's IP address to 192.168.10.2 with a subnet mask of 255.255.255.0
**sudo ifconfig eth0:1 192.168.10.2/24** - Regardless of your primary config, this command adds a second alias to eth0, called eth0:1 with that specific setup. This is really cool! You can now work on multiple IP ranges at the same time - that is;
> Gateway: My router's gateway is 192.169.1.1, my cable modem's is 24.12.216.1
you can setup wlan0 on the 192.168.1.X range and wlan0:1 on the 24.12.216.1 range and work independent of the gateway. Though - this works on copper connections, I have yet to try it on wireless! ;)
**iwconfig** - Lists the Wireless config of your card
**iw[COLOR="Blue"]list[/COLOR] auth** - lists the authentication capabilities of your card - this is very important, make sure WPA is in the list.
**iw[COLOR="Blue"]list[/COLOR] encryption** - this lists the encryption key sizes you can use - make sure 128bit is in the list. 


Now, to make a permanent change to the network config, the changes need to be in the config file: /etc/network/interfaces.

I just need to make sure of something, back now.

[COLOR="Red"]Remember to enable your wireless![/COLOR] :)

---

### Post by RudolfMDLT on 2008-01-31
First, lets get rid of unneeded bacggage, go to system-->preferences-->sessions and uncheck "network manager". apply the changes, close all saved work and press "[alt]+[ctrl]+[backspace]". this is a quick reboot.

To try and connect your laptop to the Wireless AP using your current config:

press [ALT]+[F2] and copy and paste this command
> gksu gedit /etc/network/interfaces
press enter:

Here you can see multiple interfaces.

Now, find the line that says "iface wlan0 inet ..."

Did you set your AP to use an ascii or a HEX password?

Now make it look like this
**ascii:**

> iface wlan0 inet static
address 192.169.1.111
netmask 255.255.255.0
gateway 192.169.1.1
wireless-key s:MYPASSWORD
wireless-essid CybeHouse

**HEX:**

> iface wlan0 inet static
address 192.169.1.111
netmask 255.255.255.0
gateway 192.169.1.1
wireless-key MYPASSWORD
wireless-essid CybeHouse

[SIZE="2"]If you don't know whether you used ascii or HEX or don't know what I'm on about, try the 1st and then the second.[/SIZE]

Now, save the file. Open the terminal and type the following:
> sudo /etc/init.d/networking stop

and then(press the up arrow)
> sudo /etc/init.d/networking start


You should be connected.

run this command:
> ping 192.169.1.1

if you get an error, paste the output of:
> iwconfig
and 
> iwlist scan

then try the second config, if you still get errors, do the same commands again and paste the output.

For the sake of testing, now disable ALL security on the AP.

open up the interfaces config file and make the wlan0 part look like this:
> iface wlan0 inet static
address 192.169.1.111
netmask 255.255.255.0
gateway 192.169.1.1
wireless-essid CybeHouse

If this doesn't work, post back and we'll see what we can do! :'(

If you need to use your Ethernet connection again to post back the results, paste the results in a text file, re-enable network manager, do a quick reboot and stuff should work! 

Goodluck!

PS: I'm late for a date so I really typed this fast! I found and corrected the technical errors but excuse the language errors! :)

---

### Post by Cyber Akuma on 2008-01-31
> **RudolfMDLT said:**
> 
**ifconfig** - This shows your current IP configuration
**sudo ifconfig eth0 192.168.10.2/24** - Changes eth0's IP address to 192.168.10.2 with a subnet mask of 255.255.255.0
**sudo ifconfig eth0:1 192.168.10.2/24** - Regardless of your primary config, this command adds a second alias to eth0, called eth0:1 with that specific setup. This is really cool! You can now work on multiple IP ranges at the same time - that is;

you can setup wlan0 on the 192.168.1.X range and wlan0:1 on the 24.12.216.1 range and work independent of the gateway. Though - this works on copper connections, I have yet to try it on wireless! ;)
**iwconfig** - Lists the Wireless config of your card
**iw[COLOR="Blue"]list[/COLOR] auth** - lists the authentication capabilities of your card - this is very important, make sure WPA is in the list.
**iw[COLOR="Blue"]list[/COLOR] encryption** - this lists the encryption key sizes you can use - make sure 128bit is in the list. 


Now, to make a permanent change to the network config, the changes need to be in the config file: /etc/network/interfaces.

I just need to make sure of something, back now.

[COLOR="Red"]Remember to enable your wireless![/COLOR] :)

A few questions about this:

1. Why am I configuring eth0? Isn't that my wired connection? That one is working fine... until I use the sudo ./wlan0up command that is.

2. My router before I disabled DCHP showed 192.169.1.100 as the first IP it would hand out, I thought this meant the devices that connect to it could only have ips from .100 to .255. Would 192.168.10.2 work?

---

### Post by RudolfMDLT on 2008-02-01
Sorry about the confusion! Those commands are just examples.

If you do get your wireless to work, then you are going to have to work without the network manager and enter the IP's by hand. Those where just examples that I wanted to get down and out of the way. When new people hear terminal, they usually run away, so I just put down those commands to show that it's not all that bad! :) You shouldn't be using them now - they are just the basic example commands when working with static ip's.

Do this:

> iwconfig - Lists the Wireless config of your card
iwlist auth - lists the authentication capabilities of your card - this is very important, make sure WPA is in the list.
iwlist encryption - this lists the encryption key sizes you can use - make sure 128bit is in the list. 

and then do post 10. Post 9 is just the background that I thought would be needed for my explanation in post 10 which I wasn't 100% sure of at the time of writing post 9.
[COLOR="Purple"]
EDIT: If you don't mind saying, where do you live? or please post your true time when you post next sothat I know when you are online? I don't know about you, but I would really like to fix this! ;)[/COLOR]

---

### Post by Cyber Akuma on 2008-02-04
Didn't work

First of all, my network/interfaces was already configured what you said, probably from the gui-based network manager I attempted to use earlier. The only difference is I had set my laptop's ip to 192.169.1.128.

When I attempted to ping my router's gateway I got "destination host unrechable"

I tried disabling the MAC filter and WEP, removed the ascii password from the file, and restarted my network services but but it still coudlent connect.

However, at this point I noticed something interesting, it claimed it was pinging from 192.169.1.127, not .128

.127 is the IP I gave my lan connection.

Oh, and don't worry, I may be new to the Linux terminal but I am not a stranger to commandlines, I constantly use the shell even to this day in Windows and back in the 95/98 days I had to use DOS mode a lot, sometimes even needed to use a floppy with a minimalistic config.sys and autoexec.bat to run old games that could not see past the 640k area of ram.

iwconfig:
> lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  Mode:Managed  Channel=11  
          Access Point: Not-Associated   Bit Rate:11 Mb/s   
          Retry:on   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0






iwlist scan:
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:52:5F:94
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:8
                    Encryption key:on
                    Bit Rates:11 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 
                    Quality:31  Signal level:0  Noise level:52
                    Extra: Last beacon: 1811ms ago


I live in the -6 Central timezone but my schedule has been erratic lately.

---

### Post by RudolfMDLT on 2008-02-05
Mmmmmmm

Could you please try the above again, while unhiding the ESSID and please paste the output of the following commands:

> ifconfig
and
> route -n

Then please try the following, copy and paste one by one and edit the IP address where relevant:
> 
sudo su
ifconfig eth0 down
ifconfig wlan0 down
ifconfig wlan0 192.169.1.111/24 up[INDENT]# If you get an error, just do it again[/INDENT]
iwconfig [COLOR="Red"]wlan0[/COLOR] mode Managed essid "YOURESSID" #Include the " "
route add default gw 192.169.1.1 [INDENT]#this should be the gateway address[/INDENT]


Let's see if this works.... :confused:

:)

---

### Post by Cyber Akuma on 2008-02-06
The ESSID is not listed as hidden in the interfaces file

When I tried that set of commands it said that ath0: no such device.

Also, why was it showing as trying to ping from 192.169.1.127 instead of 192.169.1.128?

---

### Post by RudolfMDLT on 2008-02-07
> **Cyber Akuma said:**
> The ESSID is not listed as hidden in the interfaces file



I need you to unhide the SSID on the access point.


> When I tried that set of commands it said that ath0: no such device.
Thats my oversight, ath0 is what all the Wireless cards are called that I work with, sorry, it has now been corrected.

> 
Also, why was it showing as trying to ping from 192.169.1.127 instead of 192.169.1.128?

Did you have an Ethernet cable plugged in at any time? Ubuntu will always default to cable over wireless. Thats why I asked for the ifconfig and the route commands as they'll show me whats ticking and where your laptop will go hunting for an external point first.

Try the instructions again, though if they don't work my advice would be to call it quits, and try the ndiswrapper route, as we have really then exhausted every possible way of getting this thing to work the normal way.

---

### Post by Cyber Akuma on 2008-02-08
ifconfig:
> eth0      Link encap:Ethernet  HWaddr 00:A0:D1:82:D0:36  
          inet addr:192.169.1.127  Bcast:192.169.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:500 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:46253 (45.1 KB)  TX bytes:46253 (45.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:44:18:13:3D  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:4 overruns:0 frame:0
          TX packets:234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42 (42.0 b)  TX bytes:9828 (9.5 KB)


route -n:
> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.169.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.169.1.1     0.0.0.0         UG    100    0        0 eth0

Still didnt work, ping said it was pinging from .111 now but I got the same destination host unrechable error.

I did not have a cable plugged in while I was trying this before and getting .127

---

### Post by RudolfMDLT on 2008-02-08
Thanks, that plainely spells out the symptom.

You do realize that you can't ping without an IP address? :)

If after doing this:

> ifconfig wlan0 192.169.1.111/24 up

you get this back;

> wlan0 Link encap:Ethernet HWaddr 00:16:44:18:13:3D
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:1 errors:0 dropped:4 overruns:0 frame:0
TX packets:234 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:42 (42.0 b) TX bytes:9828 (9.5 KB) 

Without this:
> inet addr:192.169.1.127 Bcast:192.169.1.255 Mask:255.255.255.0

then clearly things are not working at the most basic level, which then leads to this:

> Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.169.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 eth0
[COLOR="Red"]0.0.0.0 [/COLOR][COLOR="Blue"]192.169.1.1[/COLOR] 0.0.0.0 UG 100 0 0 eth0

The above tells me that [COLOR="Red"]all [/COLOR] IP addresses will be pointed to the [COLOR="Blue"]gateway[/COLOR], using interface eth0.

If you are sure that you have tried assigning an IP to the wireless adapter, and we are getting these results then I think we now have to conclude that this won't work. I may be wrong, but as far as I can see, this thing is just not playing ball. If you still won't give up, :), you now have all the tools that you need. You'll have to assign IP addresses in the text config file, and then try and get it to bind to the AP. 

My advice would be to follow this guide;
[http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/](http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/)

It's only a detailed general procedure HowTo, but it is the best start that you might get. I suggest trying that and then starting a new thread with Ndiswrapper.   

Also -  This guy got it working by compiling the drivers - [http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/#comments](http://www.datanorth.net/~cuervo/blog/2007/09/26/no-more-vista/#comments)

but i HAVE to agree with him... WHY THE HELL would anybody put a USB WiFi card in a laptop?????

If you go here, 
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#362](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#362)
You'll see that it's the only damn card that is not supported by linux.

Best of luck and sorry we couldn't get it going yet! :)

EDIT: I screwed up my Xorg.conf onmy laptop and had to use BASH commands to get the thing to connect. It took two commands and I was flying. anyway, here is a complete list of manual networking commands:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by Cyber Akuma on 2008-03-11
Damn, I really need to keep better track of my subscriptions, sorry about how long it took me to reply.

I have no idea why they would interally wire it to the USB bus instead of the PCI bus.

If these drivers won't work, what about that ndiswrapper thing you was talking about?

---

