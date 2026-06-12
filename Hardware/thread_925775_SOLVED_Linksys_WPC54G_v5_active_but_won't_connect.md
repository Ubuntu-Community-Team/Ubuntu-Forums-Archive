---
title: "SOLVED: Linksys WPC54G v5 active but won't connect"
date: 2008-09-21
forum: Hardware
---

### Post by dearephesus64 on 2008-09-21
The Linksys WPC54G version 5 pcmcia wireless network card gave me nothing but problems.  I searched these forums for a long time, but could only find similar questions left un-answered in derelict threads.

The card would light up, wireless networks would be detected by nm-applet or its kde equivalent, and one could begin to connect to a network, but it would never finish connecting.  The networks would then disappear from nm-applet and would not re-appear until reboot, but still no connection.

Under Ubuntu 6.10, I used the Windows Wireless Drivers front-end (ndisgtk from the repo) to activate the card with the .inf file from Linksys' website with ndiswrapper.  However, as soon as the kernel was upgraded, the official driver no longer worked.  I believe 2.6.24-14 generic was the last kernel that worked with the hardware and Linksys' driver.  Now that may be a coincidence, but I'm pretty sure it's the case for whatever reason.

Anyway, I ran off the older kernel for a while, but after a new install of 8.04 that old kernel was not even available that I could find.

My card's chipset is identified as the Libertas 88w8335, and after a lot of frustrated google-ing, I found a driver for that specific chipset.  The netmw25.inf file from that package worked!

I have attached netmw25.inf so that you can try it if you have been having a similar problem.  Just install ndisgtk and point it to that file.

Good luck.

---

### Post by dearephesus64 on 2010-11-05
After two years, I installed Ubuntu 10.04.1 on the same ancient laptop.  The solution above no longer works--I'm back to square one with WPC54g v5.

---

### Post by TrombaMarina on 2011-07-09
I am running into *exactly* the same problem on Ubuntu 11.04.  I found some instructions:
[https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k](https://help.ubuntu.com/community/WifiDocs/Driver/mrv8k)

Unfortunately, the end with, "you cannot connect to WPA2-secured networks with the mrv8k chipset and ndiswrapper in Feisty or Gutsy (which is currently on Tribe 5)"

So, no joy.

---

