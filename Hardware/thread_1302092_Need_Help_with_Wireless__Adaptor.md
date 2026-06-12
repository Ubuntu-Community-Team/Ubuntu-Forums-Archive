---
title: "Need Help with Wireless  Adaptor"
date: 2009-10-26
forum: Hardware
---

### Post by viper707 on 2009-10-26
Hi ,

I got sick and tired of other os monoply , so decided to install Ubuntu , download and Beta version , Beautifully install no issues of any kind .except one  "wireless" and will be grateful if some one can assist me with that , it seems that driver is not found and installed.

OS  Ubuntu 9.10
Laptop  Dell Inspiron 1525 

Regards to all

---

### Post by Mr_Wonderful on 2009-10-27
maybe try installing WICD ?

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

seems to have solved all my wireless networking issues in the past..... not sure about its use with 9.10 though

Nick

---

### Post by northd_tech on 2009-10-27
Hi viper.  According to the Wiki, your wireless adapter could be any of: "Wi-Fi Card: Dell Wireless 1397 802.11g half mini-card or 1490 802.11a/g/n half mini-card, or Intel Next-Gen 4965AGN 802.11a/g/n Wi-Fi card."

Can you go into Windoze and check the hardware identification under System Manager?  You will likely need to use or install "ndiswrapper" to use the Dell Windows drivers.  Just quick search for "ndiswrapper" in the ubuntu Synaptic Package Manager and install all those packages "utils, common, ndiswrapper", etc.  You will also want to install "ndisgtk" to have a graphical tool to use with this.  That should install a "Wireless Windows Driver" icon to your administration menu, then you can install whichever Windows driver using that program.  

Depending upon the exact Wireless interface in the Inspiron 1525, you can download the Windows drivers at:

[http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&ServiceTag=&SystemID=INS_PNT_PM_1525&os=WLH&osl=en&catid=&impid=](http://support.dell.com/support/downloads/driverslist.aspx?c=us&l=en&s=gen&ServiceTag=&SystemID=INS_PNT_PM_1525&os=WLH&osl=en&catid=&impid=)

It really shouldn't matter whether you use Win 2000, WinXP, or Vista drivers (but 32 vs. 64 bit probably will matter on those Windows drivers).  You really only need the *.inf and the *.sys files from the correct windows driver.

You might want to start by reading this Howto:

HOWTO: WLan via Ndiswrapper
[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)

---

### Post by macd3v on 2009-10-27
> **Mr_Wonderful said:**
> maybe try installing WICD ?

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

seems to have solved all my wireless networking issues in the past..... not sure about its use with 9.10 though

Nick

I agree with Mr_Wonderful I too had issues with my wireless card on install but once i got wicd installed and configured it worked flawlessly.
I am also running 9.10

---

