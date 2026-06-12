---
title: "Sun Quad 4-port PCI Ethernet Card"
date: 2011-10-20
forum: Hardware
---

### Post by huntkey on 2011-10-20
Hi experts,

I recently bought a Quad NIC FE card on Ebay. I installed it in my desktop. It didn't crash my PC yet which is the good thing. However I'm confused by its numbering. For example if I do
root@Ubuntu:~# ifconfig | grep eth
eth0      Link encap:Ethernet  HWaddr bc:ae:c5:19:ee:59  
eth4      Link encap:Ethernet  HWaddr 00:03:ba:33:d9:a9  
eth1-eth4 Link encap:Ethernet  HWaddr 00:03:ba:33:d9:a9  
eth2-eth4 Link encap:Ethernet  HWaddr 00:03:ba:33:d9:a9  
eth3-eth4 Link encap:Ethernet  HWaddr 00:03:ba:33:d9:a9  

Eth0 is the built-in port on my motherboard BTW.

Does this type of numbering make sense to you guys? How can I check if the driver has been installed correctly? I did lspci and here is what it gives me:

08:00.0 Bridge: Oracle Corporation EBUS (rev 01)
08:00.1 Ethernet controller: Oracle Corporation Happy Meal 10/100 Ethernet [hme] (rev 01)
08:01.0 Bridge: Oracle Corporation EBUS (rev 01)
08:01.1 Ethernet controller: Oracle Corporation Happy Meal 10/100 Ethernet [hme] (rev 01)
08:02.0 Bridge: Oracle Corporation EBUS (rev 01)
08:02.1 Ethernet controller: Oracle Corporation Happy Meal 10/100 Ethernet [hme] (rev 01)
08:03.0 Bridge: Oracle Corporation EBUS (rev 01)
08:03.1 Ethernet controller: Oracle Corporation Happy Meal 10/100 Ethernet [hme] (rev 01)

I guess that I just want to make sure the driver for it is installed successfully. How can I confirm it? I am still new to Ubuntu and Linux... Please get easy on me!

Thanks!

---

### Post by diasf on 2011-10-20
plug the cables? :)

---

### Post by huntkey on 2011-10-22
> **diasf said:**
> plug the cables? :)

Thank you for your reply. Right now I have all 4 cables plugged in a switch. However I still see the same...

dzhao@Ubuntu:~$ ifconfig | grep eth
eth0      Link encap:Ethernet  HWaddr bc:ae:c5:19:ee:59  
eth4      Link encap:Ethernet  HWaddr 00:03:ba:33:d9:a9  
eth1-eth4 Link encap:Ethernet  HWaddr 00:03:ba:33:d9:a9  
eth2-eth4 Link encap:Ethernet  HWaddr 00:03:ba:33:d9:a9  
eth3-eth4 Link encap:Ethernet  HWaddr 00:03:ba:33:d9:a9  

I used the "ethtool" software to check the physical status of the links but no matter which cable I unplug all above 4 interfaces show "up" all the time... I'm really confused... Any ideas?

thanks!

---

### Post by Codak on 2011-11-21
Hey Huntkey,

Check out this blog about a similar card used for networking in GNS3. I actually stumbled onto you comments while working on installing one for myself.  I will post something once I verify it works on my machine.

mellowd.co.uk/ccie/?p=286


Thanks for posting your question


UPDATE

I've had success.


1. I did the lspci | grep Oracle command for my card.  My part number was as follows:  Sun Quad Port 10/100MB PCI Fast Ethernet Network Interface. 270-5406-06  Keep in mind the back part of the card will not fit in the pci slot. I'm not sure how this will affect the functionality.  Please check out this blog of someone else installing the same thing. 

[http://danielhertzberg.wordpress.com/2011/05/18/dynamips-server-on-way-to-begin-ccie-training/](http://danielhertzberg.wordpress.com/2011/05/18/dynamips-server-on-way-to-begin-ccie-training/)  

 My screen shot:  [http://ppl.ug/cTgDUcVnvj8/](http://ppl.ug/cTgDUcVnvj8/)


2.  I used ifconfig and turned on eth2 using "  ifconfig eth2 up  "  I then verfied I had all 4 ports showing up in ifconfig.

  My screen shot:  [http://ppl.ug/Zx9MaKi5Fj8/](http://ppl.ug/Zx9MaKi5Fj8/)


3. I IP'd one port on the 4 nic.  I also IP'd my switch.  I verified connectivity via mac-address-table on the switch.  The screen shot will show what I saw on the screen. I was then successfully able to ping and no errors generated on the switch from the communications.  


My Screen shot:  [http://ppl.ug/KMX0Ys_NFn4/](http://ppl.ug/KMX0Ys_NFn4/)


I managed to pick up and old E6500 Sun Data Center and I have a ton of these cards ready to be installed.  I hope to use mine for a open source firewall.

---

### Post by huntkey on 2011-11-24
Hi Codak,

Thank very much for the help. However the problem is still not solved... I can't see your attached screenshots too for some reason. 

I can't find the model number of the card anymore. I hope I have the same card as yours...

$ lspci
08:00.0 Bridge: Oracle Corporation EBUS (rev 01)
08:00.1 Ethernet controller: Oracle Corporation Happy Meal 10/100 Ethernet [hme] (rev 01)


$ sudo vi /etc/udev/rules.d/70-persistent-net.rules

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10ec:0x8167 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="bc:ae:c5:19:ee:59", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x108e:0x1001 (hme)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:03:ba:33:d9:a9", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x108e:0x1001 (hme)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:03:ba:33:d9:a9", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

# PCI device 0x108e:0x1001 (hme)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:03:ba:33:d9:a9", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"

# PCI device 0x108e:0x1001 (hme)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:03:ba:33:d9:a9", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


It is strange that my Ubuntu names the last one eth1 again. I have tried to delete all the configs except for eth0 but the result is still the same after reboot

$ sudo ip link

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0-eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 00:03:ba:33:d9:a9 brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 00:03:ba:33:d9:a9 brd ff:ff:ff:ff:ff:ff
4: eth2-eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 00:03:ba:33:d9:a9 brd ff:ff:ff:ff:ff:ff
5: eth3-eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 00:03:ba:33:d9:a9 brd ff:ff:ff:ff:ff:ff
6: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether bc:ae:c5:19:ee:59 brd ff:ff:ff:ff:ff:ff

Any idea why...?
Thanks!

---

### Post by Codak on 2011-11-24
Hey Huntkey,

I'm out of town for the holidays and not next to my desktop.  I will look over the data while I'm on the road and compare it to my setup once I get home. 


Here are newly updated links for my screen shots.  I will take more once I get back. 

Grep result

[http://downloads.thelabaddictz.com/grepOracle_1.png](http://downloads.thelabaddictz.com/grepOracle_1.png)

Ifconfig results
[http://downloads.thelabaddictz.com/Oracle_ifconfig_2.png](http://downloads.thelabaddictz.com/Oracle_ifconfig_2.png)

Switch Connectivity Results
[http://downloads.thelabaddictz.com/ConnectivityToSwitchwithMacs.png](http://downloads.thelabaddictz.com/ConnectivityToSwitchwithMacs.png)
I get green activity lights on all ports that have something plugged into them.  




I've had the same issue of naming conventions changing every time I reboot the machine with this card installed.  I don't know why it does this.  I've had to delete all ethx names from my network setting manager and reset in order to clear it up.  I found my part number printed or etched on the chip side of the board next to REV 1 (in my case). I have several boards back in the office. I'll see if they have similar issues.  


If I violated any posting rules, give me until tomorrow and I'll edit this post to comply.

---

