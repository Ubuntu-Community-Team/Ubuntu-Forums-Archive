---
title: "Ubuntu - Vista Clash HELP to Uninstall"
date: 2008-02-23
forum: Hardware &amp; Laptops
---

### Post by philipsone on 2008-02-23
I have had a sad experience trying to get back into ubuntu. 

Following past success with ubuntu I just dual boot installed it on my 2 day old laptop, a Samsung R60 Plus running Vista. It's ubuntu 7.10 from a requested CD. 

The installation went badly and then there were a couple of reported restricted drivers. Things did not work well. Poor graphics, no printer or internet function to say the least. On restart neither ubuntu nor Vista would start. I have used the Samsung recovery CD but it fails and returns to the start. So far nothing works. Luckily there is no important data to lose. On this machine I just want to get back to a clean Vista installation without any partition. I thought I might take the hard disc out and put it into a usb caddy to format via my old computer but its connection is new and incompatible. Can anybody help please ?

---

### Post by EXCiD3 on 2008-02-23
What is the problem when your recovery disk fails?

You can delete your paritions via the LiveCD using the Partition Manager that comes with it and then using the recovery disk might not have any problems.

---

### Post by philipsone on 2008-02-24
EXCiD3  Thanks for your help.  

As you recommended I used the LiveCD and GParted from System/Admin/Partition Editor.
I am not too familiar at this level but after a lot of trial and error I managed to delete the new partitions and combine as ntfs. Eventually I got the recovery disc to complete and Vista is now back up. I feel that if I had known how to reset the boot instructions I might have got Vista to reboot without using the recovery disc. 
Thanks again for your rapid response.

During the process and using ubuntu even off the LiveCD, I continued to think how much I would still like to get ubuntu up as a dual boot option. It looks like such a neat system. But this little episode has scared me. The last time I installed it in dual boot with XP on an old Toshiba laptop it set up nicely. 

With my nice new Samsung R60Plus laptop which is quite well specified, ubuntu has conflicted with restricted drivers re the ATI graphic card, the Atheros wireless network adapter, and there was no communication between Evolution, Firefox and the local area connection although it seemed to be in good contact with the router. Perhaps my laptop is too new for the time being. I get the impression that such restrictions could be insurmountable for a mere mortal! So close yet so far away.

Whilst I am reasonably capable as a user I may have to conclude that my level of knowledge is inadequate to deal with these complexities when the going gets tough with this non mainstream approach. I shall however try to keep my mind open and perhaps a ubuntu solution will be revealed to me.

Best regards.

---

### Post by EXCiD3 on 2008-02-24
I'd love to help you get running on your laptop. It might seem like Ubuntu is a pain in the butt, however only the initial setup of it is the hard part. Everything should be smooth sailing after you get it installed and configured properly. Ubuntu has a hard time including drivers that are closed source as it breaks the philosophy of the distrobution. This leaves the user to install the drivers themselves.

What hardware, specifically, ATI card and Atheros wireless do you have? Exact model is important. If you could boot into the LiveCD once more and open Applications->Terminal and post the outputs of "lspci" and "lsusb" that will show us the exact hardware you have in your laptop. From there we can gather the info needed to get your laptop up and running.

I personally dual boot ubuntu and vista and prefer Ubuntu way more because once everything is working it is a rock solid os. Other distrobutions have better hardware support and may automatically install and configure the drivers for you hardware. remember ubuntu might not be the perfect distro for you, you should always look around.

---

### Post by philipsone on 2008-02-24
Thanks again
I shall be looking around

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 7930
00:02.0 PCI bridge: ATI Technologies Inc Unknown device 7933
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7935
00:06.0 PCI bridge: ATI Technologies Inc Unknown device 7936
00:07.0 PCI bridge: ATI Technologies Inc Unknown device 7937
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
01:00.0 VGA compatible controller: ATI Technologies Inc M64-S [Mobility Radeon X2300]
02:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15)
ubuntu@ubuntu:~$ lsusb
Bus 006 Device 003: ID 03f0:1717 Hewlett-Packard 
Bus 006 Device 002: ID 062a:0003 Creative Labs 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0a5c:2101 Broadcom Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
ubuntu@ubuntu:~$

Hope that helps
rgds

---

### Post by philipsone on 2008-02-27
Hi again EXCiD3

Did the outputs of "lspci" and "lsusb" offer an adequate  insight into my woe ?
Is there any hope for my Samsung running ubuntu ?

rgds

---

### Post by EXCiD3 on 2008-02-27
Sorry i havent had a chance to get back to you yet. Here is some info for your laptop on getting your hardware configured correctly.

Atheros Wireless: [http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/](http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/)
ATI Graphics: [http://ubuntuforums.org/showpost.php?p=3182144&postcount=2](http://ubuntuforums.org/showpost.php?p=3182144&postcount=2)

Let me know if u need help with anything. Feel free to contact me over IM if you want!

Good luck!

---

