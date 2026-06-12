---
title: "HP dv9010us LiveCD/Install error"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by Snipersnest on 2007-07-22
Hello I have an HP dv9010us and dv9008nr Laptop both give me the same error when I try to launch Ubuntu CDs.
 
I'm sorry the image quality is poor its just my cell phone. If you have any ideas for a bootable fix please let me know.  Thanks

---

### Post by dougfractal on 2007-07-22
from [http://ubuntuforums.org/archive/index.php/t-308321.html](http://ubuntuforums.org/archive/index.php/t-308321.html)
> 
ppvanzella
April 3rd, 2007, 02:10 AM
Well, I found out that it was a ACPI problem.
I started the computer with the wireless switch turned off, and it worked perfectly. Then I installed ndiswrapper, turned the wireless on and had my wireless working 100%, with WPA.
After that, I had to have the wireless on to start the computer, otherwise it would hang on the x startup. With the new kernels it doesn't matter anymore.


I'm not sure if that means after update the kernel will be newer, or to test "gusty gibbon"

So
1 boot with acpi=off
2blacklist broadcom device
3install ndiswrapper

---

### Post by Snipersnest on 2007-07-22
Thanks for the reply.. I had seen this post prior to trying the install.  With my wireless switch in the off position I still have the same result.  
 
As far as the ACPI is that what you add to the GRUB boot command for like "noacpi" ?

---

### Post by dougfractal on 2007-07-22
[http://ubuntuforums.org/showthread.php?t=2620](http://ubuntuforums.org/showthread.php?t=2620)
 Using APM instead of ACPI? 

use both
"acpi=off noacpi"

good luck.  In the past I've had to install brezzy and upgrade-dist with this sort of thing.


from [www.linuxpromagazine.com/issue/64/Ask_Klaus_Knopper_on_Linux_Configuration_64.pdf](www.linuxpromagazine.com/issue/64/Ask_Klaus_Knopper_on_Linux_Configuration_64.pdf)
> The combination acpi=off noapic
pci=bios pnpbios=off solves the major-
ity of cases (for me),

---

### Post by Snipersnest on 2007-07-22
Just to follow up...
 
noacpi acpi=off  
 
load the GDM with a VERY laggy sound from ALSA.. I'm able to ALT F1 away and kill GDM. The errors keep coming.. I'm assuming the PNPbios options will take care of the rest..about to check.
 
I hope this stuff helps somebody out there a bit more.
 
I'll post results after I add the pnpbios commands

---

### Post by Snipersnest on 2007-07-22
Results are in and heres what I get...
 
```
BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
 
/bin/sh: can't access tty; job control turned off
(initramfs)

```
 
The system hangs up and I have to reboot...
 
I also get this
 
PCI BIOS BUG#81 found when I first boot up the system into the ubuntu install...

---

### Post by Snipersnest on 2007-07-22
By adding the following commands to the boot options:
```
nolapic noacpi acpi=off irqpoll pci=assign-busses pnpbios=off pci=routeirq
```
 
This BOOTED RIGHT UP... I still get the warning from the very first picture about bcm43xx_microcode5.fw but its able to walk around it and keep going.  
 
I still get the PCI BIOS BUG #81 .. BUT so do many many people if you google :)
 
Thanks Dougfractal for the pointers. Anything else I should know before doing a full dual boot install with XP ?

---

### Post by dougfractal on 2007-07-23
from [http://www.linuxquestions.org/questions/showthread.php?t=462995](http://www.linuxquestions.org/questions/showthread.php?t=462995)
> This is a how to on how to get the stubborn infamous Broadcom 43xx wireless cards working:

First download the drivers from my website:
freewebs.com/ronserver/bcm43xx.tar.gz


1) Blacklist bcm43xx driver
Open a Terminal window
Type "sudo gedit /etc/modprobe.d/blacklist"
At the bottom add the lines
# get rid of the default kernel drivers
blacklist bcm43xx

2) Make sure network interfaces file is correct
Type "sudo gedit /etc/network/interfaces"
Remove all comments ('#') that you see so that all devices arehandled by the default network manager.
I would reboot here and make sure the wireless light goes out

3) Install ndiswrapper
Put in Ubuntu CD. Open Synaptic Package Manager (ClickSystem -> Administration -> Synaptic Package Manager),search for ndiswrapper-utils, and install it.You could also type "sudo apt-get install ndiswrapper-utils (IF you are not using ubuntu then make sure you have ndiswrapper-utils somhow installed)

4) Conigure ndiswrapper
Open terminal and navigate the folder where your drivers are."cd Desktop/bcm43xx"
Type "sudo ndiswrapper -i oem3.inf"Then type "sudo ndiswrapper -m"
Type "sudo gedit /etc/modprobe.d/ndiswrapper"Change the one line in that file to read "alias eth1 ndiswrapper"

Now you should reboot so all the drivers load.

Once you reboot the wireless light on your laptop should be lit. If it worked, you should be able to click the Network Manager icon in the top right. It will probably show a disconnected ennection becuase the computer is not plugged in.
Left click it and select eth1 from the drop down menu.
Click Configure
Click Wireless Connection, then Properties. Here just enter your network information. If you're using an unprotected network you should only have to type yout SSID.

Click OK and you should now be connected! If a green signal meter and connected network icon appear in the upper right you'll know it worked.

> 
Anything else I should know before doing a full dual boot install with XP ? 
Sorry can't help here.

---

### Post by Snipersnest on 2007-07-23
If I had waited for you to reply I'm sure this would have been a smooth transition. However I installed and went to the DV9000 thread and tried an NDIS guide before getting your post.
 
Heres what I did [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29#head-ea76065f30b99d3b8472289cd049e2b141856b55](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29#head-ea76065f30b99d3b8472289cd049e2b141856b55)
 
I get nothing out of my wireless anymore since I followed that guide. I went back and did the small changes yours had but still got nothing.
 
If you have ideas I'll just wait for your reply this time. Thanks again

---

### Post by Snipersnest on 2007-07-24
If theres anybody out there that could help get my wireless going I'd be very greatful. I'm almost at a success point.
 
I've got a Broadcom 1390 internet card.

---

### Post by dougfractal on 2007-07-29
> **Snipersnest said:**
> If theres anybody out there that could help get my wireless going I'd be very greatful. I'm almost at a success point.
 
I've got a Broadcom 1390 internet card.

I'm sorry I did get back to you I was doing something else.
I suggest that this is a new topic.
You'll get better response with a new post.


google search "Broadcom 1390 ubuntu"

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)
 HOWTO: Dell Inspiron E1505 Wireless (Broadcom 1390 WLAN)

---

