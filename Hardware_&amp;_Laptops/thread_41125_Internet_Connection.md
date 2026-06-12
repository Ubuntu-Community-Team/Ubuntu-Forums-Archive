---
title: "Internet Connection"
date: 2005-06-12
forum: Hardware &amp; Laptops
---

### Post by varunvarde2007 on 2005-06-12
Hi all

I installed Ubuntu like 4-5 days ago. I am trying to connect to internet but i am not able to connect

my hardware specification:
Smartlink SL1900 PCI internal Modem (Detected by Ubuntu)

when i configured my ppp0 i configured it somewhat like this

Dialing No.: 172309
username: pcube
password:blahblah
modem port: /dev/modem(which is used for internal modem)

but i get a error which says that please check that your modem is connected to the system and it is not busy and i tried all the things i even changed the PCI slot on my comp (this problem came when i tried Auto Detect)

but still the same problem persists

so can anyone help me out with this problem i am really in need 

i will be really thankful to you if you help me out

Thanks in advance

Bye

---

### Post by tristan on 2005-06-12
Varunvarde2007 have you tried configuring your modem connection using **sudo pppconfig**? It's much simpler than trying to configure ppp from your network settings. 


If this doesn't work, then one other thing is to check that you actually have permissions to use the modem. System->Administration->Users and Groups. Click on your user and select Properties->User Privileges. Make sure you have **Access to Modem devices** and **Connect to Internet through modem devices** ticked.

Hope this helps.

---

