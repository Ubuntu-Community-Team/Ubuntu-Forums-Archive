---
title: "Hawking Network Issues"
date: 2007-03-12
forum: Hardware &amp; Laptops
---

### Post by railroadfan77 on 2007-03-12
Hello, 

     I am somewhat new to Linux, but do have some experience with Sun Solaris OS thanks to my job. I am used to Windows, but sick and tired of the constant security flaws and patches. Anyway I downloaded Ubuntu 6.10 last Friday and installed it over the past weekend. I had heard Ubuntu is good in that it has alot of drivers and can usually find just about anything. I have a Hawkings HWP54G PCI network card and I can't connect to my network. the RaLink 2500 driver was loaded and I am pretty sure that is the correct driver since I had a similar issue with Fedora 5. 
I have read some posts that say something about a ndiswrapper, but I don't think this is the problem since the connection does show up under the networking gui under administration. When I do a ifconfig on ra0, Ubuntu tells me its UP but I can't ping anything other than my host IP address. The card shows no life at all in Ubuntu but works like a champ in WinXP. Any suggestions? I do lilke Ubuntu so far and really want to try and convert over to that once I get my feet wet. 

Thanks, 

railroadfan77

---

### Post by denver on 2007-03-12
What is the output of ifconfig?
who are you trying to ping? 
Are you trying to ping a machine on your local network or on the Internet?

---

### Post by railroadfan77 on 2007-03-13
Denver, 
    
      The results of ifconfig tells me that my interface is up and operational. If I assign an IP address, I get that information back. If I use the Ubuntu network tools, I can see that I am sending out packets with a ping but I am not getting anything back. I have pinged both the 127.0.0.1 and the ip address that I assigned to the interface. Both IP addresses respond just fine. There is no difference if I set the IP statically or if I try to let DHCP assign it. I tried both ways and still nothing. When I check my modem with my Win2k box, I do not show any connection from the Ubuntu PC. Like I said its as though the card isn't activating. 

railroadfan77

---

### Post by denver on 2007-03-15
I asked you for the output of those commands because i wanted to see how you set up your network card( IP, netmask, Gateway ).  From what i gather, you have a wireless ethernet card. I found [this guide]("https://help.ubuntu.com/community/WifiDocs/Driver/acx111?action=show&redirect=WifiDocs%2FDevice%2FAcx111") that might be of some help.
Its posible that you have the driver for the card but not the firmware. Good luck!

---

