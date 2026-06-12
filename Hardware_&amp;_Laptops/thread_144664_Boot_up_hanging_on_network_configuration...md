---
title: "Boot up hanging on network configuration.."
date: 2006-03-14
forum: Hardware &amp; Laptops
---

### Post by nuky on 2006-03-14
Hi, 
 
I'm having trouble with my network card being configured at boot-up. I'm using Kubuntu Linux on a Fujitsu Siemens Scaleo P PC. Initially, my on-board LAN port wasn't ebing recognised so I installed a PCI LAN card from an old PC and it worked fine for about a week. But recently, when I boot up my PC, it hangs at the point where it says "Configuring network devices...". If I look at the verbose screen, these are the last few lines:
* Restoring resolver state....            [ok]
* Setting up networking....              [ok]
* Reading desktop files....                [ok]
* Starting hotplug subsystem....       [ok]
* Configuring network interfaces....   
 
The only way I can get past this is by pressing Ctrl+c, but then it hangs again saying "Waiting for network interface to come up....". I then press Ctrl+c once more and it continues the boot up like normal from there. 
 
Then once I am in KDE, I have to go to Control Centre -> Internet & Network -> Network Settings, and enable the eth0 device in Administrator mode. Then my internet and everything works fine. I have also checked the box in that page where it says "Configure Interface..." and checked the box where it says, "Activate when the computer starts". And still it hangs during boot up. BUT sometimes, just sometimes, even after it has hung on the boot up and i have used Ctrl+c to bypass that, the internet and everything will be working straight away once I log into KDE without having to enable it in the settings!

I'm sorry, this turned out a little long, but my query really is: what can I do to stop it hanging in the above places during the boot up? 
 
Any help would be great as it really is a troublesome thing.
 
Many thanks, 
Nuky.

---

### Post by hw-tph on 2006-03-14
Install ifplugd and disable network hotplugging. That is my preferred way of doing it, both on laptops and on desktops. Configuration is very straightforward - simply add the name of the device ifplugd should watch to /etc/default/ifplugd: ```
INTERFACES="eth0"
HOTPLUG_INTERFACES=""
ARGS="-q -f -u0 -d10 -w -I"
SUSPEND_ACTION="stop"

```

This will bring up the network whenever a cable is connected to the network card of your computer, and also bring the interface down gracefully when the cable is disconnected. I can't live without it on laptops and it comes in handy on desktops with shaky connections as well. Oh, and it does away with the long wait for the network to come up on boot.


Håkan

---

### Post by nuky on 2006-03-14
Thanks for the suggestion. However, it still hangs at that same place. And I also noticed this in the boot up which wasn't there before:

 Starting Network Interface Plugging Deamon....     [failed]

Once I have got into KDE, and i do "ps ax | grep ifplugd" I get:
10097  ?     Ss     0:00  /usr/sbin/ifplugd -i eth0 -q -f -u0 -d10 -w -I

I think I have set it up properly and I have also disabled hotplugging by commenting out the "mapping hotplug" lines in the /etc/network/interfaces. Is this the right way of disabling it?

---

### Post by theadventuresofanidealist on 2006-09-28
same problem here, but i cant get into ubuntu to change it, so what do i do?

---

