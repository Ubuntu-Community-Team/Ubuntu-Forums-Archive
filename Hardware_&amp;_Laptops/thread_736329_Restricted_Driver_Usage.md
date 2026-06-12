---
title: "Restricted Driver Usage"
date: 2008-03-26
forum: Hardware &amp; Laptops
---

### Post by Exsecrabilus on 2008-03-26
Sorry if this is in the wrong forum, looked and chose this one as the most relevant.



In my recently installed Gutsy Ubuntu, I'm having some issues.

[IMG]http://i212.photobucket.com/albums/cc134/Exsecrabilus/Picture1.png[/IMG]

I want to use all the restricted things, but I'm having issues.

The second one, the **Software modem driver**, is fine, I can enable it.

But when I click the first one, the **ATI accelerated graphics driver**, I get this:

[IMG]http://i212.photobucket.com/albums/cc134/Exsecrabilus/Picture25.png[/IMG]
Then this:
[IMG]http://i212.photobucket.com/albums/cc134/Exsecrabilus/Picture2.png[/IMG]

Same thing happens, with the third one, **Firmware for Broadcom 43xx chipset family**, I get this:

[IMG]http://i212.photobucket.com/albums/cc134/Exsecrabilus/Picture35.png[/IMG]
Then this:
[IMG]http://i212.photobucket.com/albums/cc134/Exsecrabilus/Picture3.png[/IMG]


SO MY QUESTIONS ARE:

1. **What does a software modem driver do?**

2. **How do I enable _*xorg-driver-fglrx*_ to enable _ATI accelerated graphics driver_?**

3. **How do I enable _*bcm43xx-fwcutter*_ to enable the _Firmware for Broadcom 43xx chipset family_?**

Please at least answer 2 and 3, they're really important!



Also, THANKS SO MUCH!!!!!

---

### Post by aysiu on 2008-03-26
My guess is that you're not connected to the internet, and RDM is trying to enable online software repositories sources to install those two packages. Until *bcm43xx-fwcutter* gets installed, can you use a wired connection to get things up and running?

---

### Post by Exsecrabilus on 2008-03-26
What is the bxmfwcutter-thing?

And I don't know much about this stuff, will a Linksys USB-thing work?

---

### Post by aysiu on 2008-03-26
I think it's for your wireless card, but actually if your modem driver is already installed, can you connect to the internet through that?

---

### Post by Exsecrabilus on 2008-03-26
I'm really sorry for asking, but what is a modem driver?
Is that like the Linksys USB-thing? Will that connect me to the Internet?

---

