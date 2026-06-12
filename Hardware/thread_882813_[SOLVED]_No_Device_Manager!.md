---
title: "[SOLVED] No Device Manager!"
date: 2008-08-07
forum: Hardware
---

### Post by new2ubun2linux on 2008-08-07
Hi, can anyone help?

I have just loaded Ubuntu 8.04.1 on my Sony Vaio SZ1 and it seems OK, but the wireless network adaptor doesnt seem to be working, so I had a look in Help and it says to start Device Manager (System>preferences>Hardware Information) but thats not there on my menus!

I did have the wireless adaptor working under 7.10 some time ago, so I know it should work, but I can't find Device Manager!

---

### Post by tuxxy on 2008-08-07
Did you read the guide

[https://help.ubuntu.com/8.04/internet/C/wireless.html](https://help.ubuntu.com/8.04/internet/C/wireless.html)

---

### Post by new2ubun2linux on 2008-08-07
Hi Tuxxy, yes that is where I got the instructions to go to "System>Preferences>Hardware Information", and I'm sure that if I could get into Hardware Information I could get it going (I think that is what I did in v7.10)

But the problem I have is that the "Hardware Information" entry is not listed in my System>Preferences menu!! Don't know why not, but it definitely isn't there!

Any ideas, or does anyone know another way to launch Hardware Information (or Device Manager)?

---

### Post by linux_tech on 2008-08-07
Open Hardware Drivers (System->Administration->Hardware Drivers in source file ubuntu/internet/C/wireless.xml
or 
System -> Administration -> Network to determine whether the device has been properly recognized by the system

---

### Post by new2ubun2linux on 2008-08-07
Yes, I tried that - under Hardware Drivers it says "No Proprietary Drivers are installed" and the window is empty, and in the System>Admin>Metwork it lists Wireless Connection and says under it Roaming Mode Enabled. Right click on the Network Icon (next to the Date top RH corner - what I would have called the 'system tray' in windows - what is it in Linux?) lists "Enabled Networking" and "Enabled Wireless" and both are ticked.

My problem really is the lack of "Hardware Information" on the menus... Where's it gone and how do I start Device Manager" (or is it "Hardware Information" or are they the same thing?) if it's not on my menus. Just to prove I'm not being stupid I have attached a screanshot of my menu showing that "Hardware Information" is missing...

---

### Post by new2ubun2linux on 2008-08-07
For info (if it helps) I have run Terminal and the command lshw -class network listed the correct network card for my PC. Here is the relevant part of the output:

*-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:0d:54:08
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

and as I said - it used to work under v7.10, so my problem isn't actually with the card, it is the fact that "Hardware Information" isn't on my menu! So I can't get into Device Manager to correctly configure it.

---

### Post by new2ubun2linux on 2008-08-11
Just to let anyone who reads this know - Device Manager is not loaded in Hardy (v8.04.1) by default so the documentation referring to "System > Preferences > Hardware Information" is inaccurate.

Device Manager can be installed via Add/Remove... and then appears under "Applications > System Tools".

Hope that helps. Marked the thread solved:)

---

