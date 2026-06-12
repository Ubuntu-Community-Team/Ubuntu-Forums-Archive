---
title: "Wireless problem"
date: 2011-09-14
forum: Hardware
---

### Post by Gwaro on 2011-09-14
Hi all. I have installed Ubuntu 11.04 on a Hp pavilion dv1000.I cannot access wireless networks.The network indicator on wireless says device not ready.I tried the 'additional drivers' thing but i get the information that 'no proprietary drivers are in use on this system'.
please help.

---

### Post by gordintoronto on 2011-09-14
Open Terminal and enter this command:
lspci

One of the lines should include the string "802" and that is your wireless adapter. If it doesn't appear, that means your wireless adapter is turned off.

If it shows up, try connecting by Ethernet cable to your router, then run Additional Drivers.

---

### Post by Rednovastar on 2011-10-05
Ok guys sorry for breaking in on this thread cant figure out how to make a new one.. i have just got Ubuntu but is edgy version 6.1 and i have tried and tried to figure out how to get this wireless card to work.. the sudo lshw -c network brings up my wireless card but shows network:1 DISABLED it also shows all the drivers for it.. but it just does not recognize it to use it.. its an hp pavilion dv1000 and ohh i have tried to download a new version of ubuntu and it locks up and wont install from a usb drive or a cd.. /cry .. i and extremely new at linux and its shows when i try to run some of the command lines command not found.. ie ndiswrapper and rfkill.. both of those are not avail to me. any help would be appreciated thanks

---

### Post by grahammechanical on 2011-10-05
This link will help both of you

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

@rednovastar

Some commands will only work if you put the term sudo in front and then enter your password when asked to.

Regards.

---

### Post by gordintoronto on 2011-10-05
> **Rednovastar said:**
> Ok guys sorry for breaking in on this thread cant figure out how to make a new one.. i have just got Ubuntu but is edgy version 6.1...

Wireless support has changed immensely in the six years since Edgy was current.

---

