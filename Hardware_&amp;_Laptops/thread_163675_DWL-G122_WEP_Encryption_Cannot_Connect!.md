---
title: "DWL-G122 WEP Encryption: Cannot Connect!"
date: 2006-04-21
forum: Hardware &amp; Laptops
---

### Post by Mr_Welfare on 2006-04-21
Hi,
 
For the past two weeks I've bene trying to get my D-Link DWL-G122 USB adapter (ver. A2) up and running. I've installed niswrapper (not sure if its the lasest version though) and have used the window's drivers files from th CD. (PRISMA02.inf and the PRISMA02.sys found in the drivers>Winxp folder on the disk). Sadly, it cannot connect to my essid (default) which is WEP encrypted. If I remove the encryption, it works fine, but since I live near many different wireless networks, I would really like to keep the WEP encryption on as much as possible. 
 
Any help would be appreciated.
 
Mr_Welfare
 
Note: I am running a 64 bit (10 digit) encryption code.

---

### Post by localzuk on 2006-04-21
You shouldn't need to use ndiswrapper. Take a look at [http://anirudhs.chaosnet.org/blog/2005.10.23.html](http://anirudhs.chaosnet.org/blog/2005.10.23.html)
to have a look.

---

### Post by Mr_Welfare on 2006-04-21
[quote=localzuk]You shouldn't need to use ndiswrapper. Take a look at [http://anirudhs.chaosnet.org/blog/2005.10.23.html]("http://anirudhs.chaosnet.org/blog/2005.10.23.html")
to have a look.[/quote]
 
That is for ver. B1 of the card. I'm running ver. A2... as far as I can tell, A2 doesn't have a native linux driver.

---

### Post by Mr_Welfare on 2006-04-28
Has no one else had this problem before?

---

### Post by JNasci7906 on 2006-04-28
I have a similar problem, only mine stems from the actual getting my usb device recognized, if u have a link to how to use ndiswrapper (NEWB FRIENDLY) i would appreciate it, im sorry i cant help you, ive been running linux for about 5 hours now lol

~Nash

---

### Post by Mr_Welfare on 2006-04-29
[quote=JNasci7906]I have a similar problem, only mine stems from the actual getting my usb device recognized, if u have a link to how to use ndiswrapper (NEWB FRIENDLY) i would appreciate it, im sorry i cant help you, ive been running linux for about 5 hours now lol
 
~Nash[/quote]
 
Hi Nash,
 
Follow the instructions found [here]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto"). When installing the driver use the windws driver PRISMA02.inf and PRISMA02.sys. The PRISMA02.sys is found in the Winxp folder on the cd. Also, what hardware version is your USB key? (Check the back... it should say something lke A2, B1, etc.)
 
Mr_Welfare

---

