---
title: "Wireless DELL"
date: 2005-06-21
forum: Hardware &amp; Laptops
---

### Post by JeremyS on 2005-06-21
I'm completely new to Linux, so excuse me for my ignorance.  ](*,) 

I have a Dell Inspiron 1150, which I only use mainly for surfing wirelessly around the house, and such ( use my PC for everything else ). I've installed Ubuntu, and everything runs fine, as well as the internet. I've run into no problems, except I have no idea how to get connected wirelessly, or if its even possible. I've searched the forums, but didn't really come to anything that was my exact problem, and I don't know if it's different for different models, etc. If it's possible, any help on how to set it up ( as simplified as possible  :-P ) It would be greatly appreciated. If it's not possible, that's fine.

If this has already been discussed, if you could just direct me to to the link, that will be fine.

Thanks.

---

### Post by Zelut on 2005-06-21
I did a quick lookup of your Inspiron 1150 and I don't see any onboard wireless card.  To get this workin' we'll need to know what type of wireless card you're using.  I'm assuming you bought one?  Maybe a pcmcia or usb?  Let me know that and we'll be one step closer.

---

### Post by JeremyS on 2005-06-21
I went here - [http://www.pcmag.com/article2/0,1759,1579106,00.asp](http://www.pcmag.com/article2/0,1759,1579106,00.asp)

and It says - Dell TrueMobile 802.11g wireless

That sounds right. Hope that's not bad news.  :-|

---

### Post by superdav42 on 2005-06-21
To get that Wireless card to work you need to install ndiswrapper. Ndiswrapper is a rather crude way of loading windows drivers in linux to get the network card to work. 
A wiki how-to can be found here:

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper)

The hardest part is finding the right inf for your driver. If you still have windows installed then that's the easiest way to get it. Otherwise you'll need to download it from the internet or a cd and use wine to extract it.

Some general info about linux on that laptop can be found here:

[http://www.geocities.com/acarirfan/inspiron-1150.html](http://www.geocities.com/acarirfan/inspiron-1150.html)

---

### Post by JeremyS on 2005-06-21
Thanks for the information.

Like I said in my original post, I'm very new to Linux in general, so any help would be great. The first steps of the Ndiswrapper aren't clear to me.  :?  If someone could give me detailed steps on how to do this, it would be appreciated.

Sorry to be a bother, but you gotta learn somehow, right?  :-#

---

### Post by jasmuz on 2006-01-29
Did you ever got that card working?..if not PM me...i will help

---

### Post by thk on 2006-01-29
Don't go to ndis until you try the built in drivers. Go to the system -> administration -> networking dialog (look on the top panel for the "system" menu) and select the wireless device. Now click on properties and set the essid/key + dhcp or manual ip. Once done it should active right away. I've never had any problem with wireless on a Dell/Linux laptop, ever. (Currently on a Dell X1.)

---

