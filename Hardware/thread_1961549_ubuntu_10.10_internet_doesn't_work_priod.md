---
title: "ubuntu 10.10 internet doesn't work priod"
date: 2012-04-19
forum: Hardware
---

### Post by n4ane on 2012-04-19
I've recently installed ubuntu 10.10 onto my acer aspire 3100 and found that my internet flat out doesn't work, wired or wireless. When I connect the laptop to an ethernet wire, it says I am connected, but fails to load any pages or connect to the internet for any purpose (updater, drivers, etc.)
 
I am sure this post is missing vital information that would help fix my problem, so if anyone would be so kind as to tell me what I need to post so that people can help me find a solution, I'd be very grateful. I am not a linux guru person, and this is my first time using Linux. Any help would be greatly appreciated

---

### Post by Yellow Pasque on 2012-04-19
Is it possible for you to obtain a newer version of Ubuntu? 10.10 is EOL (end of life).

---

### Post by 2F4U on 2012-04-19
What is the output of ifconfig? How do you connect to the internet, where do you get an IP address? What network hardware do you have?

---

### Post by efflandt on 2012-04-20
I am certain that by default, if an ethernet cable is plugged in your system should try to use dhcp to get an IP address, etc. because that all works automatically to download additional files during initial installation, unless your network device is not recognized.

First look at the output of **sudo lspci -v** to see if it lists something after **Kernel module in use:** and **Kernel modules:** or post that here for your Ethernet controller and Network controller (or whatever your wireless device is called) wrapped in code tags (by highlighting that text and clicking **#** in message window).

If that does show modules, check the following:

**ifconfig -a** (to see if your eth has an IP address)

**route -n** (to see if you have any routing along with default route)

**cat /etc/resolv.conf** (to see if any nameservers are listed)

To use wireless, you probably have configure to that by right clicking on the network icon in upper right of screen, where you might be able to pick something to connect to, or else at least **Edit connections** to set up a wireless connection including whatever wireless security you use.

---

### Post by n4ane on 2012-04-20
I have not idea what happened but when I put this in it started working sudo lspci -v I do not know if the wired is working but I am happy I love 10.10 and I hate 11.04 and havent tried the new one

---

