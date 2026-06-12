---
title: "Huawei E1752C Modem - WCDMA Only"
date: 2012-02-02
forum: Hardware
---

### Post by LiamOS on 2012-02-02
Hi,

I'm running Ubuntu 10.04 amd64 on a HP G62, in Ireland attempting to connect to the O2 network.

As of late, my Huawei modem has been connecting to GPRS far too much for my liking, so I'm attempting to find out if it's possible to set it to a WCDMA only or equivalent setting, as it is on Windows using the supplied program.
Unfortunately, I'm a complete newbie when it comes to modems and such, so my escapades with minicom in the terminal failed dismally(I can't even figure out how to enter commands).
Does anybody have any idea on how I might achieve this? Thanks.

Liam.

---

### Post by LiamOS on 2012-02-08
Problem solved.

I installed moserial, and selected my device in port settings(/dev/ttyUSB3 in this case), and used the appropriate command from the following:

2G Only: AT^SYSCFG=13,1,3FFFFFFF,2,4
3G Only: AT^SYSCFG=14,2,3FFFFFFF,2,4
2G Preferred : AT^SYSCFG=2,1,3FFFFFFF,2,4
3G Preferred: AT^SYSCFG=2,2,3FFFFFFF,2,4



Commands and other useful information found here:
[http://forum.huawei.com/jive4/thread.jspa?threadID=320231](http://forum.huawei.com/jive4/thread.jspa?threadID=320231)

---

### Post by chamalsl on 2012-03-22
I did this on Ubuntu 10.10.

Follow these steps.

1. Click on System Menu.
2. Click on Preferences menu.
3. Select Network Connections.
4. Click on Mobile broadband tab.
5. Select your broadband connection.
6. Click on Edit button.
7. Enter root password when prompted.
8. Ubuntu will display a window with settings for your broadband connection.
9. Select mobile broadband tab.
10. Under Advanced select Type drop down menu.
11. Select option 3G(UMTS/HSPA)
12. Click Apply.

---

