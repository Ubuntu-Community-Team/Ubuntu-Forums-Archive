---
title: "Ubuntu 9.10 appears to have installed incorrect network adapter"
date: 2010-02-18
forum: Hardware
---

### Post by kungfujones on 2010-02-18
I have installed Ubuntu 9.10 in Virtual PC 2007 SP1 on a Win7 host. The installation autodetected and installed eth0 & eth1, both appear to be exactly the same, and both appear to be for the incorrect adapter. Below is the output of lspci (i have to type this in as I cannot copy/paste, so I have only included the Ethernet controller lines):
00:0a.0 Ethernet controller: Digital Equipment Corporation DECchip 21140 [FasterNet] (rev 20)
00:0a.1 Ethernet controller: Digital Equipment Corporation DECchip 21140 [FasterNet] (rev 20)

My network card is actually an Intel 82566MM Gigabit. How do I get the correct one installed and configured?

It also did not detect my wireless card. Not sure if I should open a new thread for that or not.

Any help is appreciated.
Thanks.

---

### Post by Julita on 2010-02-18
Your lshw, please!

---

### Post by kungfujones on 2010-02-18
holy crap, that's huge! I will only give the -network entries for now, let me know if you need more (remember i have to type all this in):
*-core
 *-pci
  *-network:0
       description: Ethernet interface
       product: DECchip 21140 [FasterNet]
       vendor: DEC (spelled out)
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 20
       serial: 00:03:ff:80:d9:7b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master rom ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 latency=64 multicast=yes
       resources: irq:11 ioport:e880(size=128) memory:febfe000-febfefff memory:febd0000-febdffff(prefetchable)
  *-network:1
       description: Ethernet interface
       product: DECchip 21140 [FasterNet]
       vendor: DEC (spelled out)
       physical id: a.1
       bus info: pci@0000:00:0a.0
       logical name: eth1
       version: 20
       serial: 00:03:ff:80:d9:7b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master rom ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=10.42.17.166 latency=64 multicast=yes
       resources: irq:11 ioport:ec00(size=128) memory:febff000-febfffff memory:febe0000-febeffff(prefetchable)

The mac addresses do not look familiar to me either, below is a dump of ipconfig from the host (win7):
Ethernet adapter Bluetooth Network Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Bluetooth Device (Personal Area Network)
   Physical Address. . . . . . . . . : 00-21-86-09-8B-4E
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Wireless LAN adapter Wireless Network Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Intel(R) Wireless WiFi Link 4965AG
   Physical Address. . . . . . . . . : 00-1F-3B-85-D9-7B
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : *********
   Description . . . . . . . . . . . : Intel(R) 82566MM Gigabit Network Connecti
on
   Physical Address. . . . . . . . . : 00-1E-EC-30-0E-72
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::b8d5:2591:4999:72de%11(Preferred)
   IPv4 Address. . . . . . . . . . . : 10.42.17.107(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Thursday, February 18, 2010 7:13:00 AM
   Lease Expires . . . . . . . . . . : Thursday, February 18, 2010 12:13:23 PM
   Default Gateway . . . . . . . . . : 10.42.17.1
   DHCP Server . . . . . . . . . . . : 10.44.0.65
   DHCPv6 IAID . . . . . . . . . . . : 234888940
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-13-07-B1-4A-00-1E-EC-30-0E-72

   DNS Servers . . . . . . . . . . . : 10.0.1.1
                                       10.0.2.1
   Primary WINS Server . . . . . . . : 10.35.69.21
   Secondary WINS Server . . . . . . : 10.38.5.38
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter isatap.{2811284D-AFE3-46F7-89BA-E98CB1118DAE}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 11:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.albertsons.com:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : **********
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #2
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter isatap.{40BA69FA-494E-4812-99F2-F713E08D1A05}:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #3
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes


btw, thanks for the quick response!

---

### Post by Julita on 2010-02-18
Well, according to lshw, your ethernet is Intel(R) 82566MM and wifi is Intel(R) Wireless WiFi Link 4965AG, so the system recognizes your hardware... Digital Equipment Corporation DECchip 21140 is, in fact, PCI bridge. Is there any trouble with it?

What do you mean, you have to type all this in? You can copy/paste it... Or you don't have internet in Virtual machine? It uses LAN, so if you have Internet in your machine, you should have it also in Virtual machine.

By the way, the best virtual machine is Virtualbox. It should work flawlessly in Windows...

---

### Post by kungfujones on 2010-02-18
okay, that's good.
copy/paste doesn't work between the virtual pc client and host (i haven't found any virtual machine additions for this version of linux), and unfortunately i don't have a version of vmware compatible with win7.

so then it looks like the adapter is installed and working. so the next step would be to get the connection to work. right i can't ping anything. i did configure the proxy, but this doesn't seem to have made a difference. not sure what to do now.

thanks.

---

### Post by Julita on 2010-02-18
Virtual PC has issues with Internet access in it; the possible solution is:
1. go to the virtual pc console (main thing)
2. highlight the system you are using, and click on the settings button to the right (this window runs in host, not in virtual os)
3.go down to networking
4.under adapter1, choose your wireless card/ connection (i have a laptop with a wireless card)
5.now go back into Ubuntu and at the top right of the screen, you see the little network connection thing, click on it and say wired connecton (even if it is really wireless) and that should be it. (from [http://arcanecode.com/2007/10/18/installing-ubuntu-710-under-virtual-pc-2007/](http://arcanecode.com/2007/10/18/installing-ubuntu-710-under-virtual-pc-2007/)) 

Please post if it helps.

---

### Post by louieb on 2010-02-18
Have not used Virtual PC - But in Virtual box the network adapter (and all other hardware)  is set by Virtual box - there is a list to choose from. None of them is what is really installed in the PC. 

In a virtual machine your hardware is type is determined by the Virtual Machine software - it may or may not be what is installed on the PC. 

Check the VM settings  - my guess is that Ubuntu is picking up whatever device the VM is emulating. 

[Virtualization]("http://ubuntuforums.org/forumdisplay.php?f=308")

---

### Post by kungfujones on 2010-02-18
originally i had the vpc network settings set to:
1. the wireless adapter
2. the wired adapter
under this config, the wired was connected (eth0 & eth1), just couldn't do anything (ping, etc.), the wireless showed nothing; this was the install config, btw, in other words, i set the network settings to these two adapters and in that order prior to installing ubuntu

i followed the instructions 1-5 and set the vpc network settings to:
1. the wireless adapter
under this config, i have no connectivity

thanks.

---

### Post by Julita on 2010-02-18
I have found this solution as well: In Virtual PC 2007, under settings for the environment, change the network adapters to 2, the first one being shared networking (nat) and the second, being your actual network adapter.

Then under Ubuntu 9.10, system, administration, network - make sure eth0 being the shared networking adapter is ticked under the connections tab, highlight it and click properties. Making sure that roaming mode is unchecked and if your environment supports it set it to DHCP or set a static IP. ([http://techrepublic.com.com/5208-6230-0.html?forumID=101&threadID=230334&messageID=2400263&tag=content;leftCol](http://techrepublic.com.com/5208-6230-0.html?forumID=101&threadID=230334&messageID=2400263&tag=content;leftCol))
It seems that it is a global problem with Virtual PC. By the way, why not try and install Virtualbox? It works more smoothly with networking+Linux than Virtual PC.

---

### Post by kungfujones on 2010-02-18
i went and checked out virtualbox, installed it, then installed an ubuntu virtual machine on it, works great! thanks for the suggestion and all your help.

---

