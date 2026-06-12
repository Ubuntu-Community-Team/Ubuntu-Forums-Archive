---
title: "IRC file download problems...Toshiba M35-S359"
date: 2005-06-07
forum: Hardware &amp; Laptops
---

### Post by kumpooterjooser on 2005-06-07
I installed ubuntu 5.04 on my Toshiba Satellite M35-S359 around three weeks ago.
The first two weeks I had minor/tolerable glitches none with IRC though. I was able to successfully download huge files/movies from IRC.

For the past week I have been running into a strange problem. When I request a file on IRC through DCC, download starts fine with nice speed ~ 150KB/s, but after sometime (anything between 2 to 15 mins) the download just stops and the download speed begins to decrease, although no packet is coming in, as file-size is not changing. Eventually I get the message DCC for file xyz stalled.

Since I was using mIRC client(running in Cross Office) to connect to IRC networks, I thought maybe Cross Office settings is the issue.

Here are some of the unsuccessful options that I have looked into  :???: 

1. Trying to eliminate Cross Office, I installed wine and ran mIRC with it

2. Maybe mIRC was the problem, so I connected to IRC using XChat IRC, the problem still persists.

3. Maybe my Belkin router is acting up, so I connected my cable  modem directly

4. Turned off firewall

5. Got a brand new Cable Modem.

6. Installed Debian.

7. Reinstalled ubuntu

All the above tryouts frustated me enough to try the download in Windows and 
surprisingly I was able to download the file from IRC using mIRC client. To test in Windows I had atleast 8 other simultaneous file downloads running in mIRC, one huge file download running in Firefox, and newsgroups binaries from Grabit. Even with all this traffic no problems in IRC. So I guess my ethernet card isnt the problem. 

Also in Windows I downloaded the file from the same sender on IRC as I was trying in ubuntu.

I tried to download files using my wireless connection in ubuntu and ran into the same issue in IRC.

The download problem only seems to be with IRC in ubuntu as Grabit and http/ftp transfers work fine.

I spend considerable time on my laptop for IRC file transfers, leading me to switch back to Windows  :mad: 

I would appreciate if someone can help me to fix this issue.

Here is the line from 'Device Manager'
pci.product    82801BD PRO/100 VE (MOB) Ethernet Controller
info.vendor    Intel corp.

Thanks

---

