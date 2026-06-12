---
title: "Now NETGEAR WG511 (v2) PCMCIA card connected"
date: 2006-07-13
forum: Hardware &amp; Laptops
---

### Post by didobuntu on 2006-07-13
Too Strong Ubuntu Team,

Now since the last Drapper Update, my NETGEAR WG511 v2 (made in China) PCMCIA wireless card runs like a charm on my old laptop (an Asus 3800S).

Thank you very much for all your efforts.

_____________________________________________________________________

Ubuntu for all ... and all for Ubuntu

---

### Post by dmery on 2006-07-14
Hi,
I have a Netgear pmcia WG511 v2 to attach to Acer Travelmate 290E
Do you know where can I get information about the procedure to install it ?
I means some information like "How to" "wiki" or some guide. :confused: 
Thanks in advance for your help 
Regards,
dmery:) 

PD I am using Dapper LTS 6.0.6

---

### Post by didobuntu on 2006-07-15
Hello dmery,

Before the last ubuntu update (I mean until kernel 2.6.15-25-686), I followed the following [wifidoc]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported"). But the WEP could not be detected ... I mean it runs only without wifi pass word (which is not recommended).


Now since 2.6.15-26-686 I don't need to follow these instructions. The wireless card is recognized at boot.

So first of all be sure that you are running the 2.6.15-26 kernel ... code "uname -r" and see the result to be sure.

Then, try to connect out of the box via System --> Administrator --> Network ... there see if wireless is detected .. If so clic on that device and then to properties to enter the strings concerning you wifi installation (I had to enter the password in hexadecimal).


Try this first and tell me if it runs


Good luck

---

### Post by John Jason Jordan on 2007-12-22
I finally got mine working with ndiswrapper in Gutsy x86_64. The details, including how to do it with 32-bit Gutsy, are here:

[http://ubuntuforums.org/showthread.php?p=3999047#post3999047](http://ubuntuforums.org/showthread.php?p=3999047#post3999047)

---

