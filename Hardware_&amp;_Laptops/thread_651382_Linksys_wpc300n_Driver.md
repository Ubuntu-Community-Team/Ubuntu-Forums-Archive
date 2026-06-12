---
title: "Linksys wpc300n Driver"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by s1mp13m4n on 2007-12-27
I am somewhat of a Linux newbie.  I have tried several distros of Linux in the past and because of my lack of "real" knowledge I ended up always going back to Windows XP.  My current install of PCLinux2007 has the same issues as the rest, and I fear Ubuntu will as well.  Is there a drive for my Linksys wireless N card the wpc300n?  I have not found a solution in this forum, people ask the question but no one replies.  I am tired of viruses, spyware, and "attacks" that Windows is just over run with.  Heck I do not view porn or go to sites that I do not know or open attachments or use IE, but my laptop still got messed up with trojans.  I will switch to Linux if it simply "works" and will run without having to figure it out....at first...yes I want to learn but for now I want my install to simply work and then I can learn once it is installed.

---

### Post by Spr0k3t on 2008-01-04
Two problems with the the WPC300N card.

1. 802.11N
2. Broadcom chipset

True you can utilize the fwcutter or ndiswrapper with the drivers, but so far, I don't know of any working 802.11N card in Linux.  Your best bet is to stick with what works.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by Shannon_VanWagner on 2008-01-06
This problem appears on the Linksys forums:
[http://forums.linksys.com/linksys/board/message?board.id=Wireless_Adapters&message.id=346&jump=true#M346](http://forums.linksys.com/linksys/board/message?board.id=Wireless_Adapters&message.id=346&jump=true#M346)

I've sent an Email to [email]linksys-opensource@linksys.com[/email] (please do the same!!)

Subject: Please create (or allow creation of) a Linux driver for the WPC300N Wireless adapter

Dear Linksys,

Please create (or allow the fre creation of via [http://kerneltrap.org/node/7636](http://kerneltrap.org/node/7636) ) a Linux driver for the WPC300N Wireless adapter.

The problems with this wireless device working in Linux are highly visible at this point,
please see the article on cnet.com:
[http://www.cnet.com/8301-13880_1-9839735-68.html](http://www.cnet.com/8301-13880_1-9839735-68.html)
and also on digg.com here:
[http://digg.com/linux_unix/Ubuntu_Linux_Apps_Rock_and_Wireless_Sucks](http://digg.com/linux_unix/Ubuntu_Linux_Apps_Rock_and_Wireless_Sucks)

Thanks in advance for your great support!

Shannon VanWagner



Note: I will also ask Mr. O'Reilly to post this to launchpad as a bug.

---

### Post by lift28 on 2008-06-26
edited: the drivers on the cd caused problems
installed my driver with ndisgtk

sudo apt-get install ndisgtk (this should grab everything you need)
download the latest windows drivers from linksys unpack them into a folder
sudo ndisgtk
then point it to the .inf file in the driver dir

I had to remove a few extra .sys files:
sudo rm /etc/ndiswrapper/lsbcmnds/wec600n.sys
sudo rm /etc/ndiswrapper/lsbcmnds/wpc54g*

i did a reboot
i use wlassistant for a network manager(i roam a lot)

my speeds were pretty good
my speeds were 4300 kb/s up and down with the n card
my speeds were 2000 kb/s down and 1500 kb/s up with my g card

---

