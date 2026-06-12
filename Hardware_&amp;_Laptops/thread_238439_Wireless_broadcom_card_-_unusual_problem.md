---
title: "Wireless broadcom card - unusual problem"
date: 2006-08-17
forum: Hardware &amp; Laptops
---

### Post by Mazza558 on 2006-08-17
Hi,

I'm trying to get my belkin wireless card to work under Ubuntu. I can safely say I've won half the battle - I've got as far as this:

Installed ndis drivers:
bcmwl5  driver present, hardware present

Which is encouraging. My problem occurs when I try to activate the interface in Networking. The first thing I notice is that the interface isn't named "wlan0" as it should be, but it is names "eth0" or somethnig similar. If I run "iwconfig" in the terminal, There is no sign of wlan0 being configured, because all the wireless status information appears to be under eth0. 

What is wrong? ](*,)

---

### Post by wieman01 on 2006-08-17
Well, "eth0" is - in all likelihood - your ethernet adapter. It appears that "ndiswrapper" had not installed correctly or rather... the Windows driver. 

Your wireless interfaces should definitely be "wlan0" rather than anything else if you are using "ndiswrapper".

That said, could you reconfigure "ndiswrapper" and load the driver once again? Make sure that all driver files (e.g. *.sys, *.inf, *.cat, etc.) are all in the same directory when you deploy the "*.inf" file.

There is a good guide:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by mdmarmer on 2006-08-17
This problem is not unusual -- I think it always occurs in Dapper with Broadcom cards

;-)

You need to blacklist bcm43xx (the new Broadcom native driver) -- then ndiswrapper will work [after reboot]

if you want to set it up now, try
rmmod ndiswrapper
rmmod bcm43xx
modprobe ndiswrapper

But, for permanent solution, add [as root]
blacklist bcm43xx
to /etc/modprobe.d/blacklist

You can search this forum (broadcom ndiswrapper dapper howto -- example search)

to find a how-to and other posts on this [http://www.ubuntuforums.org/showthread.php?t=201902](http://www.ubuntuforums.org/showthread.php?t=201902)

Mike

---

### Post by wieman01 on 2006-08-18
> **mdmarmer said:**
> This problem is not unusual -- I think it always occurs in Dapper with Broadcom cards

;-)

Interesting... So does the Linux driver have a problem? If not, why would we want to install "ndiswrapper" in that case at all? I don't use Broadcom so I am just curious.

---

### Post by Mazza558 on 2006-08-18
OK, thanks for all your help. I'll try these things and report back to tell you if it worked.

---

### Post by Mazza558 on 2006-08-18
OK, just tried to get rid of the drivers to reinstall them. (Bearing in mind I set them to load at startup)

Here is the error message:

```
-@--desktop:~$ ndiswrapper -e bcmwl5
Can't remove file /etc/ndiswrapper/bcmwl5/14E4:4320:1799:7000.5.conf (Permission denied) at /usr/sbin/ndiswrapper line 166
Can't remove file /etc/ndiswrapper/bcmwl5/bcmwl5.sys (Permission denied) at /usr/sbin/ndiswrapper line 166
Can't remove file /etc/ndiswrapper/bcmwl5/bcmwl5.inf (Permission denied) at /usr/sbin/ndiswrapper line 166
Can't remove file /etc/ndiswrapper/bcmwl5/14E4:4320.5.conf (Permission denied) at /usr/sbin/ndiswrapper line 166
Can't remove directory /etc/ndiswrapper/bcmwl5 (Permission denied) at /usr/sbin/ndiswrapper line 166
```

---

### Post by wieman01 on 2006-08-18
The last resort is reinstalling ndiswrapper library (after a complete removal). This way all your previous settings will disappear entirely. These 2 libraries should be reinstalled (using Synatpic):

1. ndiswrapper-utils
2. ndisgtk

Then install them once again and load the driver.

---

### Post by Mazza558 on 2006-08-18
OK, I have a huge status update. I found a driver which would be more likely to work with the card after looking through the list of ndiswrapper compatible drivers. I then uninstalled ndiswrapper via synaptic. I reinstalled it and set up the better driver. However, it appears the old driver is still present after a reinstall. So, now I have the old "bcmwl5" driver saying "driver present, hardware present" but with "bcmwl5a" (the new driver) saying the same thing. 

mdmarmer, 

I tried to follow those steps but it said something like "action not permitted". 

A quick look at networking still shows "eth0" but not "wlan0"

What now? 

Thanks in advance.

---

### Post by Mazza558 on 2006-08-19
Anyone else know what I can do?

---

### Post by mdmarmer on 2006-08-19
You have 2 choices to get Broadcom wireless working
1) native driver bcm43xx -- uses eth0 -- needs windows firmware and fwcutter
Example how to (note -- you still haven't told us the specifics of your hardware [make and model of laptop, exactly which Broadcom card you have -- this how to is tailored to Broadcom 4318])

[http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+dapper+howto](http://www.ubuntuforums.org/showthread.php?t=197102&highlight=broadcom+dapper+howto)

Note -- after ndiswrapper doesn't work, if you try to get bcm43xx working, you could need to blacklist ndiswrapper
===
2) ndiswrapper -- works on wlan0 -- needs windows drivers and you need to blacklist bcm43xx so that the 2 drivers don't interfere with one another

Example how to [http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom+dapper+howto+ndiswrapper](http://www.ubuntuforums.org/showthread.php?t=185174&highlight=broadcom+dapper+howto+ndiswrapper)

Hope this helps -- it really isn't impossible ;-)

Mike

[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)  (Dapper wiki)

---

### Post by Mazza558 on 2006-08-20
The hardware I'm using isn't a laptop, it's a HP pavillion T770i desktop PC. I use a wireless card because it is physically impossible to connect to the PC with internet capabilities with a cable. 

The wireless card is the Belkin 54g Wireless Desktop Network Card (model number: F5D7000 Rev 3) and the broadcom chipset is BCM4306. 

Could you tell me a bit more about fwcutter and what it does?

EDIT: It appears the fwcutter method can only be used if you have an internet connection on the PC already. (Which I don't)

As for the blacklisting, I have already stated that it comes up with the error "action not permitted".

Thank you very much for your help so far.

---

