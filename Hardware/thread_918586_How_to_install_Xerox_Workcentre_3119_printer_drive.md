---
title: "How to install Xerox Workcentre 3119 printer drivers on Hardy Heron"
date: 2008-09-13
forum: Hardware
---

### Post by cornelius80 on 2008-09-13
Hi guys,

I've read through some posts on this issue and haven't yet found a solution to my problem. eg. "http://ubuntuforums.org/showthread.php?t=392225"

I have managed to download the drivers from "http://www.support.xerox.com/go/getfile.asp?Xlang=en_GB&XCntry=GBR&objid=56673&EULA=0&prodID=WC3119&Family=WorkCentre&ripId=&langs=English&plats=Linux&Xtype=download&uType=#suppplat" as directed and attempted the install.

However, I encountered "CUPS: 'server-error-internal-error" when I followed bamakojeff's guide. 

Any suggestions,please?

regards,
Cornelius:guitar:

---

### Post by EnGorDiaz on 2008-09-13
> **cornelius80 said:**
> Hi guys,

I've read through some posts on this issue and haven't yet found a solution to my problem. eg. "http://ubuntuforums.org/showthread.php?t=392225"

I have managed to download the drivers from "http://www.support.xerox.com/go/getfile.asp?Xlang=en_GB&XCntry=GBR&objid=56673&EULA=0&prodID=WC3119&Family=WorkCentre&ripId=&langs=English&plats=Linux&Xtype=download&uType=#suppplat" as directed and attempted the install.

However, I encountered "CUPS: 'server-error-internal-error" when I followed bamakojeff's guide. 

Any suggestions,please?

regards,
Cornelius:guitar:

what kind of packaging is it using tar.gz or .deb, .rpm?

---

### Post by alfkh on 2011-01-16
hi Cornelius,

Hope u didn't trash your 3119. i just acquired a 3119 on thursday. Currently i have it attached to an old winXP print server. I've not tried the scanning utility yet, but printing works. 

I've setup samba on my Ubuntu 10.10 (Maverick) laptop. Xerox Workcentre 3119 drivers come standard with Maverick (Ubuntu 10.10). The test page printed okay so did 1 of my documents. 

My personal opinion, i'm a Linux hobbyist, ie non-pro; is try upgrading your Heron if you haven't already. See if the drivers are there. If not, you may need to do an ubuntu 10.10 fresh install :sad:

Very important, make sure the kernel is up to date. Today, the latest kernel is 2.6.35-24; i think the default is 2.6.35-22. For the benefit of others reading this thread, to do an update
# sudo apt-get update
# sudo apt-get upgrade

or

System-> Administration-> Update manager

Like i said, i'm only a hobbyist!

Good luck, happy trails, & if u ever find out how to get the scanner working let me know!

alf

---

### Post by IcarusR on 2011-01-16
Xerox Workcentre 3119 is supported by the latest version of sane, listed status as 'good'.

If you are still using 9.04 you also may need to upgrade to at least 10.04 to get a version of sane that supports it.

---

