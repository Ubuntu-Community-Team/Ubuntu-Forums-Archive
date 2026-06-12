---
title: "Network Everywhere PCMCIA on Presario 1200"
date: 2005-07-16
forum: Hardware &amp; Laptops
---

### Post by abaker82 on 2005-07-16
Hello all.

Recently I was given a copy of the Ubuntu distro and recommended my roomate to it as his laptop is older and would benefit the transistion from XP.  I am a complete Linux n00b and am very frustrated with the following problem:  I cannot get the wireless pcmcia card to work for the life of me. ](*,)   It is a network everywhere model # NWP11B 2.4 ghz 802.11b card that works fine under Windows.  The connection under Ubunto is described as "lo" and seems to be redundantly cycling....  any help for a n00b thats tired of windows?

---

### Post by mhancoc7 on 2005-11-10
I just got my Network Everywhere PCMCIA wireless working on my Compaq 1750. This is what I did. 

First install ndiswrapper-utils. Just open Synaptic (System - Administration - Synaptic Package Manager) and search for ndiswrapper-utils.

Second download the windows drivers: [ftp://61.56.86.122/cn/wlan/rtl8180l/ndis5x-8180(173).zip]("ftp://61.56.86.122/cn/wlan/rtl8180l/ndis5x-8180(173).zip")

Extract the files.

Now create a folder in your home directory named network_card with a folder in it named driver. (network_card/driver).  Now copy the .INF and .sys files to your new network_card/driver folder.

Now open a terminal (System Tools - Terminal) and run the following commands. USER=your username.

cd /home/USER/network_card/driver
sudo -s
ndiswrapper -i NET8180.INF
ndiswrapper -l
ndiswrapper -m
modprobe ndiswrapper

You will now need to go to System - Administration - Networking to configure your new wireless connection. I checked the box to note that it is configured and selected DHCP instead of Static. Now it is working great. It even starts up at boot. No need to modprobe each time. This is awesome.

I hope this helps.

God Bless, Jereme

---

