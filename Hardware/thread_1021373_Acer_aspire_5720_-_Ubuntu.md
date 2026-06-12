---
title: "Acer aspire 5720 - Ubuntu"
date: 2008-12-25
forum: Hardware
---

### Post by sybot_uk on 2008-12-25
Hope this is the correct place for this, as a complete newbie, got Ubuntu 8.10 installed and working on Acer Aspire 5720, thought might be useful to share.

Hard-disk was already partitioned into 2 parts. Ubuntu installer wasn't giving me satisfactory options for where to install, it wanted to either overwrite whole drive or steal part of the data partition. Decided to go for manual. I shrank the Vista partition by 12gb using the Vista disk partition editor (right click computer and select manage). When got to partition tool in Ubunutu installation chose manual, created a 10gb ext3 partition and mounted root (/) to it. Also created a 2gb linux-swap partition. Installation went through without any problems.

I read through this guide first- 
[https://help.ubuntu.com/8.10/installation-guide/i386/index.html](https://help.ubuntu.com/8.10/installation-guide/i386/index.html)

After installation sound was working ok which i had read it might not. The only problem was that wireless wasn't working as no drivers installed. The wireless card is an Atheros AR5007EG. 

This link:
[http://ubuntuforums.org/showthread.php?t=792158](http://ubuntuforums.org/showthread.php?t=792158)
has some very useful info but the main method superseded by this:
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

I downloaded
[http://packages.ubuntu.com/intrepid/linux-backports-modules-2.6.27-7-generic](http://packages.ubuntu.com/intrepid/linux-backports-modules-2.6.27-7-generic)

using Vista and saved it on the Data partition, then back in Ubuntu i double clicked to install. When i did
sudo lshw -C network
at the terminal it now showed that the drivers were OK but still not picking up my wireless network in network congfig, did
sudo iwlist scanning
from the terminal and it found the network. Was then available in the drop down list of networks in the bar at the top of the screen. Is now all working fine.
 
Maybe this isn't the best way to do things, as i said i am a newbie, but worked for me.

---

### Post by sybot_uk on 2008-12-25
I've since found out this was not the correct way to install the wireless card drivers as when i allowed Ubuntu to update the wireless stopped working so i plugged in a cable connection to the net and did:
sudo apt-get install linux-backports-modules-intrepid-generic

This reinstalled the correct driver and is now working ok.

---

### Post by russu52 on 2009-01-28
i first installed ubuntu 8.10 in the D: and left vista on the c:
when i found that ibex works pretty well (much better than vista, i made a clean wipe and am running on ubuntu only. everything seems to work ok - except the xd card, while sdhc is ok

---

