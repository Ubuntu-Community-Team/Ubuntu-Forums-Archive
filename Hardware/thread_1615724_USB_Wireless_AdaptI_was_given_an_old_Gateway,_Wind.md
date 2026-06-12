---
title: "USB Wireless AdaptI was given an old Gateway, Windows 98 SE laptop. The laper Problem"
date: 2010-11-07
forum: Hardware
---

### Post by DanInKtown on 2010-11-07
I was given an old Gateway, Windows 98 SE laptop. The laptop has no network board, and it _had_ no wireless adapter.  I installed Trendnet TEW-424 UB (Rev 3.13) wireless adapter. The laptop was able to connect wirelessly to the Internet, via our local coffee shop’s wireless network. The laptop could not make a wireless connection via the Verizon (my ISP) router at my home. Verizon’s tech support person told me that their network did NOT support Windows 98. 

At home, I downloaded and burned an Xubuntu installation CD on my my desktop computer. Then I installed Xubuntu 10.10 , dual booted with Windows 98, on the laptop.  When I booted up Xubuntu, Xubuntu presented a small window to inform me that wireless service was available and telling me to click on an icon (at a corner of the small window) to make the connection. When I clicked on the icon, Xubuntu allowed me to choose my Verizon router’s signal (from among several signals) and it led me through what was necessary to make the connection.   

Since I prefer Ubuntu anyway, I installed Xubuntu 10.10 as the only system on my laptop. At first, when Xubuntu booted up Xubuntu presented a small window informing me that wireless service was available and telling me to click on an icon (at a corner of the small window) to make the connection. Three times when I tried to click on the icon, as the cursor approached the small window, the small window disappeared, and as I  moved the cursor away the small window would reappear. The fourth time, the small window did not appear again. Thereafter, when Xubuntu booted up, the small window no longer appeared. 

[As a sanity check, I reinstalled Xubuntu from the CD. The small window appeared three times and then disappeared. I also tried reinstalling Xubuntu and taking the laptop to the coffee shop before rebooting. Similarly, the small window appeared three time. Then it was gone forever. I supose if I had a Windows 98 SE installation disk I could try a clean installation of Windows and follow it with a dual boot installation of Xubuntu. But I don't have a Windows 98 SE installation disk.] 

[B]What I have is an Xubuntu laptop with no Internet connection to it. The laptop can read USB thumb drives. Across the room from the laptop, I also have a desktop that is connected to the Internet. The desktop can download stuff and write it to USB thumb drives. Although I like  and use Ubuntu, I'm not very familiar with command line Linux. 
[/B]
Someone on Craigslist's Linux forum suggested that I use the network manager, *wcid*. I was able to download a Sourcforge *wcid* installation file to my desktop computer, copy the file to a USB thumb drive, and copy file again onto my laptop computer. Following instructions included in the installation file, I was able to install *wcid* on the laptop. 

When I ran *wcid* it recognized my Verizon FIOS router's wireless network and it displayed the network's name. (*wcid* also recognized my neighbor's wireless network, which was on another channel than mine was.) The settings I gave *wcid* for my network are shown in [http://img833.imageshack.us/img833/751/verizonsetting.png](http://img833.imageshack.us/img833/751/verizonsetting.png) . *wcid* seemed to indicate (along the bottom of its window) a successful log on, but the message "Connection Failed: Unable to get IP address" popped up a little later later. Of course, the laptop still can't get online. 

Verizon says they don't troubleshoot Linux, but that if the laptop were running Windows they'd check to see if TCP/IP was loaded correctly. Should I do that on my laptop? If yes, how? 

Again, keeping in mind that my laptop has no network card and no Internet connection, and keeping in mind that my knowledge of command line Linux is rudimentary: **What do I have to do to get the Xubuntu laptop to communicate via its Trendnet TEW-424 UB wireless adapter and Verizon FIOS' router?**

---

### Post by efflandt on 2010-11-07
I have not tried xubuntu for awhile, but when you freshly install it, doesn't it have **Network Connections** somewhere in one of its menus or **Edit Connections...** if you right click on the network icon in top panel.  You probably just need to configure that with SSID name and security settings, and check the boxes to **Connect automatically** and **Available to all users**.  At least that is how it is in regular ubuntu.

Once you configure that, it should automatically connect when you boot, without having to do anything.  Note that is you install wicd, that uninstalls network-manager, because the programs conflict with each other.

---

