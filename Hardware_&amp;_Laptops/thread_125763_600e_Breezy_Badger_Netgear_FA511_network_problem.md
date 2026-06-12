---
title: "600e Breezy Badger Netgear FA511 network problem"
date: 2006-02-04
forum: Hardware &amp; Laptops
---

### Post by tarotking on 2006-02-04
hey everyone,

I've set aside a large chunk of time to finally get my networking set up.

currently it is not working. I am unable to get an IP address from dhclient. But the status lights are working on the card. So the connection from the card to the network is working.

==========steps==============

insert the pcmcia card

/var/log/messages
PCI: enabling devica 0000:06:00.0 ( 0000 -> 0003 )
tulip1: MII transceiver #1 config 3100 status 7849 advertising 05e1
eth0: ADMtek Comet rev 17 at 00014800, 00:0F:B5:8E:38:2C, IRQ 11
tulip already loaded

lsmod | grep pcmcia
pcmcia    24584   4
pcmcia_core    44932   3   pcmcia, yenta_socket, rsrc_nonstatic

lsmod | grep tulip
tulip   45088   0

ifconfig eth0
eth0   Link encap:ethernet hwaddr 00:0F:B5:8E:38:2C
         BROADCAST MULTICAST   MTU:1500 Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)
         Interrupt: 11 Base address:0x4800

sudo ifdown eth0
ifdown: interface eth0 not configured

sudo ifconfig eth0 down
sudo ifcofig eth0 up

/var/log/messages
eth0: Setting full-duplex based on MII#1 link atner capability of 45e1

sudo ifup eth0
Ignoring unknown interface eth0 = eth0


sudo cardinfo
<<tells me that socket 1 and socket 0 are empty even though the card is currently in the pcmcia slot>>

lspci <<lines related to network>>
Ethernet controller: Linksys 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 11)




my current boot options include acpi=off pnpbios=off apm=off .  This is from trying to get a different ethernet card to work.



i would like to get the ethernet working soon. help would be appreciated. If i left any imformaton out, just let me know.

---

### Post by tarotking on 2006-02-04
i just remembered one more step.


trying to get an ip via dhclient


sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with id 7848
 killed old client process, removed PID file.
Internet Systems consortium DHCP client V3.0.2
Coppyright 2004 Internet systems consortium.
All rights reseved. 
For info ...

Listening on LPF/eth0/00:0f:b5:8e:38:2c
Sending on LPF/eth0/00:0f:b5:8e:38:2c
sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 inteval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 inteval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 inteval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 inteval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 inteval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 inteval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 inteval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.



couldnt get an IP this way =' (

---

### Post by wolfchri on 2006-04-07
Hello tarotking,

same issue here - the funny thing is, that I sometimes have some throughput, sometimes not. It also seems that the card does not see incoming traffic. 

I have a Thinkpad 600E, and the card can be used without a problem on PCLinuxOS 9.1 and Damned Small Linux on the same machine. On Debian and Ubuntu, no chance. 

I tried ndiswrapper and the Windowsdrivers yesterday night, but obviously I forgot to blacklist the tulip driver, so I hab no success. Will try it later again, with the tulip driver blacklisted. 

I also have the WG511, this card runs on Dapper with the prism54 driver, but only with the 2.6.15-19 kernel, not with the brand new 2.6.15-20 kernel. 

Will also try ndiswrapper here. 

Here, the FA511 is being recognized in lspci as "N" - something is going wrong with the pcmcia driver, my guess. I have turned off nearly every device that takes away IRQs, but still a mess.

To sad that PCLinuxOS is simply to bloated for such an old machine - it even fixes this damned sound issue with the cs4236 driver.

Did you get the FA511 running on Dapper meanwhile?

---

### Post by wolfchri on 2006-04-07
I got the Netgear FA511 running on Dapper using ndiswrapper.

Just blacklist the tulip driver in /etc/modprobe/blacklist,

and take the Windows driver (you can download them here: [http://kbserver.netgear.com/release_notes/D100175.asp]("http://http://kbserver.netgear.com/release_notes/D100175.asp"))

If you are unsure, use the WG511 HowTo as a guidance. [http://www.ubuntuforums.org/showthread.php?t=156228]("http://http://www.ubuntuforums.org/showthread.php?t=156228")

The FA511 then shows up as wlan0 in the network setup / ifconfig. Just keep the wlan fields for SSID etc. empty and enter only the LAN typical information.

Any ideas how to tell ndiswrapper that it should show the card as eth0 instead of wlan0? I changed /etc/modprobe.d/ndiswrapper and commented out the wlan0 entry, but the card still is being identified as wlan0....

---

### Post by python_boot on 2006-05-10
Well, it looks like I have found the right thread. I am also trying to get the FA511 to work on my 600e with Ubuntu 5.10, but I am running into the same issues. ](*,) 

Perhaps foolishly, I have tried using ndiswrapper with my 5.10 install but the card will only use tulip. I cannot figure out how to get it fully blacklisted. I have it blacklisted in /etc/modprobe.d/blacklist, and I even created /etc/modprobe/blacklist so I could blacklist it there, but I haven't made any decent progress. I don't have an excerpt from /tail/var/messages since the 600e is still offline, but it looks like ndiswrapper tries to handle the card but can't because tulip is "already loaded".

The only instructions I have found for using ndiswrapper to get the FA511 functional on a 600e come from wolfchri's [Dapper on a TP 600e](https://wiki.ubuntu.com/LaptopTestingTeam/Thinkpad600E) page. I am willing to accept that using Dapper instructions to install an alternate driver on Breezy might not be the best idea, but I've been beating my head against a wall for a while. Have any of you made any progress with ndiswrapper and 5.10?


python_boot

P.S. I would just upgrade to Dapper flight 6 and try the steps again, but for some reason the Dapper install hangs at the keyboard selection screen. But that's an issue for another thread. :)

---

### Post by wolfchri on 2006-05-10
python,

what does lsmod say? Is the tulip module really being loaded while blacklisted? Can not imagine that.

I do not think that this is a special issue of Breezy - the ndiswrapper solution should work with Breezy as well, there no fundamental differences between this versions. However, make sure you have the latest ndiswrapper. 

If everything fails, you could go the brutforce way and unload the tulip module at startup, using the custom init script /etc/rc.local, adding some rmmod tulip, maybe using the force switch, and then loading ndiswrapper (again, maybe you also have to unload it first). 

However, this is not the elegant way :-) and I am quite sure that there is something wrong with your blacklist config.

Since Dapper is nearly finished, you might go the easier way and switch to Dapper. I recommend a new installation, not an upgrade. Only not so good thing with Dapper is the slowdown of the GUI due to the new cairo rendering machine - Breezy felt faster on the desktop. May you want to try Xubuntu.

---

### Post by python_boot on 2006-05-11
Well, went ahead and installed Dapper on the 600e and gave ndiswrapper another shot. At first it didn't appear to work, but once I turned off my router's IP address reservation, the laptop was able to connect. For some reason, wlan0 doesn't have a MAC address--it is displayed as 00:00:00:00:00:00--so I can't assign a specific IP address to the laptop. But, at this point, I'm just happy that I finally got it connected.

Wolfchri, you're right; Dapper is pretty sluggish on my 600e. I'm going to blame it on the 128 MB of RAM. I think I'll take your advice and try xubuntu.

Thanks for the help!


python_boot

---

### Post by python_boot on 2006-05-12
I just installed xubuntu and it is definitely snappier than ubuntu-desktop. Also, I was able to get ndiswrapper up and running in less than 15 minutes. I am writing this post from the TP 600.

Life is good.

---

### Post by ingo on 2006-05-23
Hi there,

I've been suffering the same problem. No IP address even though Xubuntu recognised my card! Well, don't fret, there is a really simple solution.No need even to install ndiswrapper. All you have to do is:

1. find out what your card is called by typing 
_sudo iwconfig_
It will probably be wlan0 or somehting like that
2. type
_sudo ifdown wlan0_ (or whatever your card is called)
3. type
_sudo iwconfig wlan0_ (or whatever your card is called) essid "YOUR NETWORK NAME" key s:YOUR WEP KEY PHRASE
4. type
_sudo ifup wlan0_ (or whatever your card is called)


Right, that should do it. 
And in case you're fed up with typing sudo all the time try this:

_sudo bash_

at the start and then you've got a root shell.
Finally, it might be a good idea to write a simple script for this, as you'll probably get fed up typing all that lot every time you want to get into your network. Here is how:

1. get into the root shell (see above) and change into /usr/local/bin. Type
_touch mynetwork_ (or the name of your network or a nice short name you remember easily)
2. Now open the file /usr/local/bin/mynetwork with your favourite editor (I use vi, but nano is very user friendly...) and type the following:

#!/bin/bash
#my network

ifdown wlan0
iwconfig wlan0 essid "YOUR NETWORK NAME" key s:YOUR WEP KEY PHRASE
ifup wlan0

#end

3. Save it and Bob's your uncle. Now every time you want to log into your network just type
_sudo sh mynetwork_
and you're in. BTW, it doesn't matter which directory you're in :)

You might want to do write other scripts for other networks. If in doubt check the man pages for iwconfig (man iwconfig)

HTH 

Ingo

---

### Post by tarotking on 2006-06-02
Well I can not say that I found the most convenient way of fixing my problem, but I did find a solution.


The original problem is that when I installed the system I was installed a xircom pcmcia card ( which didnt work ). This led to me buying and trying to install the Netgear FA511 on a running system (ubuntu 5.10).


Eventually, I decided to try a clean install with the card in the slot during installation. This led to the card being recognized properly.


Though not the most elegant of solutions, sometimes technology needs a kick to jumpstart it.

---

### Post by RonKaminsky on 2006-06-05
The ndiswrapper solution wolfchri proposed *seems* to be working for me. I had the same problem with the FA511 on an install of Dapper (Flight 6) on an Acer TravelMate 333T.

I've already invested a lot of work on the system since installing, so I shudder at the suggestions of reinstalling with the card in the slot. Anyway, I use two different cards, one at work and one at home, and only have one slot (although the other card, an old 3Com, has never given me any problems under Linux). Maybe some Ubuntu guru can tell us how to rerun the install hardware detections without actually reinstalling????

I am also getting errors from the DMA driver, something which says:

"ali15x3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr"

and I'm curious if that has something to do with the tulip driver not working properly --- did/do you guys with the Thinkpad 600E have the same DMA driver problem?

---

### Post by wolfchri on 2006-06-06
Ron,

*in theory*, there should not be any need for a new hardware detection like during installation - the kernel and the hardware detection during bootup should do this. If that does not work, it is quite unlikely that a new installation will change that. 

I would rather recommend to try several kernel parameters qith regard to DMA.

Very unspecific, I know :roll:

---

### Post by RonKaminsky on 2006-06-11
The ndiswrapper solution under Dapper seems less than ideal with regards to throughput. I clocked a few transfers and got the following approximate numbers:

FA511 (ndiswrapper) connected to TBase10 -> 330kB/s
FA511 (ndiswrapper) connected to TBase100 -> 660kB/s
3Com 3C589D-Combo Etherlink III connected to TBase10 -> more than 800kB/s
FA511 under DSL connected to a different TBase100 -> 3000kB/s or more

(note: the DSL number was taken from DSL's network throughput monitor, other numbers are from FTP transfer rates)

I decided that I can live with the bad throughput --- if I need to do any really large transfers I can reboot into DSL.

Oh, and the problem which I thought had to do with DMA (ali15x3) may only concern the SMBus which enables hardware monitoring, so I've decided to live with it also (after trying many sets of boot parameters at startup without success)...

---

