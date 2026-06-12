---
title: "need help scanning or searching for wireless networks"
date: 2008-10-28
forum: General Help
---

### Post by sickman666 on 2008-10-28
Can someone please help me how to search or scan for available networks in range? I have tried to manually config to connect but nothing...so I need to search for networks in my range and try to connect that way. I need the internet for college and I may have to install windows( i dont want to do this as i love ubuntu) but i need my internet up and running. This internet problem happend after battery died and it shut down...i plugged it in and i have no internet now. I am running ubuntu 8.04 with built in broadcom adapter....thanks a lot in advance**:confused::guitar:**

---

### Post by TeoBigusGeekus on 2008-10-28
Install Wicd.
It is better than gnome network manager.

---

### Post by sickman666 on 2008-10-28
> **TeoBigusGeekus said:**
> Install Wicd.
It is better than gnome network manager.
I do not have wicd even listed nor do i have the internet to download it. Thanks for your response but im still stuck.:confused:

---

### Post by bobyy on 2008-10-28
Ciao .
From commmand line :

$sudo iwlist scan

:) enjoy

---

### Post by TeoBigusGeekus on 2008-10-28
If you could give me an email (of a friend of yours?) I can send you the deb file. 
Grab it with a flash drive and install it on your pc..

---

### Post by sickman666 on 2008-10-28
The terminal says
lo- interface doesnt support scanning
etho- same thing as lo
wmster0- same thing as etho and lo
wlan0- no scan results
any ideas what is happening thanks again

---

### Post by bobyy on 2008-10-28
Hmm strange...if you have wirelles there ..it must be displayed.
try to do a stop/start the network like:

$sudo /etc/init.d/networking stop ...and start

or do a restart.

regards.

---

### Post by sickman666 on 2008-10-28
Made no difference. Its weird. My driver is fine,the broadcom card is showing that it is fine. My battery died...then i plugged it back in and my internet will not connect or if it is it shows no bars for service. weird.

---

