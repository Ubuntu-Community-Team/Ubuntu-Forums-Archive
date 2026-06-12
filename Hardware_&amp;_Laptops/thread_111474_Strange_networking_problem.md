---
title: "Strange networking problem"
date: 2006-01-02
forum: Hardware &amp; Laptops
---

### Post by mssm on 2006-01-02
Hi,

I am a longtime reader but this is my first post. I have the following strange problem. 

My system :
AMD 64 laptop with an external USB HD with 4 partitions connected

My OS :
Breezy with the latest kernel

My wireless card : 
Atheros with AR5212 chipset(listed under device manager)

Gateways :
eth0(for wired)
ath0(for wireless)

I always work on the wired network, so I never noticed this problem before. Earlier, I had switched between the wired and wireless network but with the ethernet cable always being plugged in. Moreover, my wireless was not encrypted.

1st problem :
------------
Today, I did the following : with the ethernet cable being plugged I tried to switch to wireless network with now WEP encryption turned on. It's a 128-bit WEP encryption. The tool from System -->Administration -->Netwroking didn't allow me to type the 26-bit long hexadecimal key. I don't know what's the alternate way to do. Does the networking tool in gnome support 128-bit encryption?

2nd Problem
---------------
Next, I unplugged the ethernet cable. All the strange problems started occurring at this point. First, during boot it could not mount the 4 partitions of the extl. HD(later when I plugged the ethernet cable back again it could). This was really strange! Apparently, netwrok has nothing to do with mounting different partitions, right? Next, the network connection applet, synaptic etc. etc. were not working. I started kwifimanager but it's behaviour was erratic. When I clicked on 'Scan for network' button , it hangs almost everytime. After few reboots(booting and rebooting were taking exceptionally long time), I was able to run synaptic and other processes but this problem persists. From command line, I executed : 'iwlist ath0 scan'. The results was segmentation fault.

What caused this segmentation fault? I have no clue. I remember that I worked with wireless before but without WEP key and with ethernet cable plugged in, under breezy without any trouble.

What is the best software for handling wireless network under linux?

One last word : I used hoary for a month. I never had this problem.

Sorry for this long post. Any help will be highly appreciated.

---

### Post by dannyboy79 on 2006-08-17
Ok well I can solve your first problem only by means of a GUI though as I am a linux newbie and am trying to use the command line but this seemed much easier when I wanted to get it done fast. There is a program called WIFI Radar. It is in synaptic. Yes you can use 128 bit encryption, I am using Xubuntu and 128 bit encryption with my laptop, Netgear Router and netgear wireless card. Support right out of the box believe it or not. So just install WIFI Radar and then it should show up within your Applications then Network, well at least that's where it showed up when I installed it in Xubuntu.

As far as the second problem, well it sounds to me like you really confussed ubuntu with going back and forth between interfaces (wired and wireless) and your network connection was lost for a while and that's why the network connection applet and synaptic weren't working. Due to this it's possible that the proper usb modules or hotplug didn't get loaded properly and it could of just been like a domino effect with stuff going screwy. I believe your best bet is going to be to install WIFI RAdar. As I said I think it in the repositories but if it's not here is some great install instructions on the its website. [http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/). 

Private message me if you get it or not and maybe I can help.

---

### Post by bwilson on 2006-11-18
My TrendNet 443PI card was detected by Dapper on PowerPC, but dhclient could not get an IP from my Dlink router's DHCP server. I used Wifi Radar and it got an IP!
Thanks for the tip.

---

