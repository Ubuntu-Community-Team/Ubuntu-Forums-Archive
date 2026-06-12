---
title: "Absolutely Love ubuntu just cant get wireless working on laptop!"
date: 2010-04-19
forum: Hardware
---

### Post by NEOSWOOSH on 2010-04-19
Hi ubuntu community after spending almost 20 000 troughout the years always having the latest pc just so it would be fast on windows finaly made the move ub 9.1 blew me away 
I just cant get the wireless to work heres my specs (I'd love Love help!plz)

:Toshiba Satelite L450 -03D
4gb Ram
Dual Core (not sure how fast)
500gb
Ubuntu 9.1

When I go to System->Admin->Hardware Drivers it says no no proprietary drivers found.
I've tried some tutorials but no luck I'm at the point where I'd name my fisrst born after the person who helps me figure this out!Thanx in advance!

---

### Post by nyinyizaw on 2010-04-19
:) You say no propriety driver . So u can use window wireless driver. You can copy window driver to ubuntu .Then from the software center, u can install wireless manager ( I am not sure the name exactly but I believe you can find it ) .After that, run that application and install driver . Restart ! 
            Make sure when installing software , your linux CD is in CD-ROM .  
            I think it will be OK!

---

### Post by Drenriza on 2010-04-19
have you tried to put a cable in the machine, get internet. And make and
 
```
apt-get update
```
```
apt-get upgrade
```
? and upgraded your system with all the newest files, patches, and so on.

---

### Post by NEOSWOOSH on 2010-04-19
Ok Thanx I will try this and REPORT BACK!!!

---

### Post by Native Dialect on 2010-04-19
Open up the terminal and type the following command

lspci -v

After that, you will get a long list of all the devices for your machine. Toward the bottom, you will see something like 


09:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Lite-On Communications Inc Device 6600
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at f0400000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

Once we know what your hardware is, we can help you find the correct drivers in order to get that working. Also, knowing what version of Ubuntu you are using currently, would be helpful. Some compatibility issues are remedied, simply by using the latest version.

---

### Post by NEOSWOOSH on 2010-04-19
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
14:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

That is my system.

I did what the first reply recommended and the problem with that approach is that Windows wireless drivers doesnt like the drivers (there are 4 diffrent one that I found on my windows partition) with every one it says" unable to see if hardware is present "
and then with 1 of them it says hardware is present (although it initially says unable to see"

I tried the suggestion in the second post and ubuntu did do an update but to no avail!
[FONT=Arial Black][SIZE=2]
Im running Ubuntu 9.1[/SIZE][/FONT]

Thank so much for helping!

---

### Post by NEOSWOOSH on 2010-04-19
**This is the current state**:

*-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:4000(size=256) memory:f2200000-f2203fff

---

### Post by NEOSWOOSH on 2010-04-19
Any |deas?

---

### Post by iponeverything on 2010-04-19
First, I like your subject. It's positive and not the usual negative subject line!

I think you might be in luck. See:

[http://ubuntuforums.org/showthread.php?t=1353049](http://ubuntuforums.org/showthread.php?t=1353049)

found it with string "realtek 8172 ubuntu" in google.

From your lspci:
```

14:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
```

---

### Post by Cabs21 on 2010-04-19
Just to be sure I know sometimes if your are not connected the the Internet your system will not find any drivers.  If you can hard plug your laptop into a LAN cable and connect to the net and try checking your drivers again.  My brothers laptop is just like that and needs to be connected first before he can get the drives for his wireless card.

---

### Post by UpsideDownFace on 2010-04-19
when I was having trouble getting my IBM thinkpad R50e to wireless network I did - at terminal :-

ping -c 3 localhost

ping -c 3 [www.google.com](www.google.com)

sudo apt-get install madwifi

and I looked with synaptic for "wifi" and got "wifi-radar" which tells you what wireless is nearby

I also use System > Administration > Network to configure my cable and wireless networking.

I hope this may help a bit

---

### Post by 1337_snic on 2010-04-19
Same issue here. :-( I head that ndiswrapper works good, but nothing here, I see in terminal my wireless card, but no luck on emulating the wireless driver for a linksys. Anyone wanna tell me why ndiswrapper says it is missing its utils file after i installed it? Mabey someone has the full packet of compatible versions for kubuntu 9.10. Thanks. 
:popcorn:

---

### Post by NEOSWOOSH on 2010-04-19
Hey Guys this is what I did and now atleast I have the "Hardware Drivers" program saying :Linux Driver for Realtek RTL819x WiFi cards

 				 				[dash86no]("http://ubuntuforums.org/member.php?u=578798") 				 				 			
  			Just Give Me the Beans!
 			[IMG]http://ubuntuforums.org/images/rank_2.png[/IMG]
 			  			  			 				 
				Join Date: May 2008
 				Location: Tokyo
 				 	  					Beans: 75 				
 			       Ubuntu Development Release  				 				 				 				 				    
 			
  	 	 	 	 		 		 			 			 				 				**Re: Realtek 8172 Wireless network not working** 			
 			 			 		   		 		 		I just followed the below launchpad thread and got my realtek 8172 working with Ubuntu Lucid alpha 64 bit

[https://bugs.launchpad.net/ubuntu/+s...6?comments=all]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/401126?comments=all")

To summarize:

1: Download the latest driver from Realtek's site:
[http://www.realtek.com/downloads/dow...Downloads=true]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true")

2: Unpack the archive, cd into the folder.

3: sudo su

4: make

5: make install

6: reboot

7: Enjoy wireless


(Thanx to this user)It still isnt showing up in any wireless programs I have and yes it is connected through regular ethernet does anyone know if this is the right drivr and what I have to do next???

---

### Post by NEOSWOOSH on 2010-04-19
In the Hardware Drivers app it now shows the driver but it says it is active/not in use
It says noproprietry drivers are active but not in use sheise!

---

### Post by NEOSWOOSH on 2010-04-19
[SIZE=7]It is My[/SIZE] absolute pleasure to inform you I am accessing this website via wireless and I am SOOOO exited I think I just might not sleep the rest of my life!I have a Microsoft replacement and I never have to use Microsoft again unless its the odd time in a virtual machine(Virusses like windows should be kept in inclusures) So
if anybody has the same problem lemi spill the beans on how to solve it.This last thread just before this one with the various steps DID work eventually not initially I had to reinstall ubuntu and do those steps first thing,I did them exactly the same way as I did before but they did not work after a fresh install in my case they worked I had to play around with my modem and router but ubuntu made me verrrrry happy thanx to everyone that helped and im gonna go now and say thanx to that person in the post that refferedme to the other forum thats where I found the thread above.

G'by windows
Cest' la vie

---

### Post by NEOSWOOSH on 2010-04-19
THANK YOU SO FRIGGIN MUCH one of those threads you linked me too had the ounce of magic thats makin me a very happy man.Whats your name so I can name my first born after you J/K!Thanx man Im gonna be awake untill im finished pimpin my ubuntu machine with compiz.

Oh somethin interestin Donno if you know but Ubuntu is head by Mark Shuttleworth....Him and me both come from the same place :South Africa 
Thanx a bunch

---

### Post by iponeverything on 2010-04-19
We spent a week driving through wine country in SA. Really liked it. I love Capetown too.

---

### Post by Native Dialect on 2010-04-20
I am glad others were able to help you with your problem. Sorry that I was not able to get to it first, after requesting your hardware information. Best of luck in the future.

---

