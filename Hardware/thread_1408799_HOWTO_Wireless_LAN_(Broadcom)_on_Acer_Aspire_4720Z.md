---
title: "HOWTO: Wireless LAN (Broadcom) on Acer Aspire 4720Z with Ubuntu 9.10"
date: 2010-02-16
forum: Hardware
---

### Post by moodylamb on 2010-02-16
After about 2 or 3 years away from Linux, I busted it back out when my free trial of Windows 7 expired.  The first problem I ran into, as many do, is getting the wireless LAN to work.  I didn't find a thread relating to this exact laptop, and had to do a bit of research of my own to find the answer, so I figured I'd post a quick howto for anyone else running into this problem.

So here's how I got my wireless Broadcom LAN to work on my Aspire 4720Z with Ubuntu 9.10.  

BTW: this not only made my wireless LAN work, it made my WLAN LED button work, too!

1. Pop in the DVD or jump drive that you used to install Ubuntu.
2. Open your file browser (Places>Home)
3. Navigate to your install media (for me, the DVD drive) and continue to pool>main>d>dkms
4. Right click dkms_2.1.0.1-0ubuntu1_all.deb and click "Open with GDebi Package Installer"
5. In the Package Installer window, click "Install Package"
6. Once the package finishes installing, once again on your install media, navigate to pool>restricted>b>bcmwl
7. Right click bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb and click "Open with GDebi Package Installer"
8. In the Package Installer window, click "Install Package"
9. Reboot and enjoy your wireless LAN action!

---

### Post by xeclipsex on 2010-02-19
thank you have been having same issue with my 5517  will try it and post if succsessfull

---

### Post by Ignotus Angelus on 2010-04-26
Well, to me, that didn't work... I have the same computer as you and did every step the way you did, and now the wireless option won't even show up there...
 
*sigh*

---

