---
title: "facing problems with network connections with wireless connection on my notebook."
date: 2010-01-21
forum: Hardware
---

### Post by harish.ponnaganti on 2010-01-21
Hi all...

I am Harish kumar from India. I am using Ubuntu 9.10 in my notebook. It is made by Dell and the model number is XPS M140. The wireless network is not working properly since I have installed Ubuntu. I am using Trendnet wireless router to connect through wireless. Internet is not working in my laptop while connecting through wireless. The device address, i.e. 192.168.1.1 is working properly and it is showing the device details. But still I can not able to point out what the problem is. I have not installed any software for wireless connections while installing Ubuntu. 

Does the software from Dell company solve my problem? But Dell is not giving any softwares to support Ubuntu. Please guide me in this issue.

Thanking you in advance,

---

### Post by harish.ponnaganti on 2010-01-24
Some one please suggest me in this issue.

---

### Post by IcarusR on 2010-01-24
You say 
> wireless network is not working properly

Does it work at all ? 
Does it get an IP address ?

Does laptop work with ethernet cable ?

---

### Post by scrooge_74 on 2010-01-24
> **harish.ponnaganti said:**
> Hi all...

I am Harish kumar from India. I am using Ubuntu 9.10 in my notebook. It is made by Dell and the model number is XPS M140. The wireless network is not working properly since I have installed Ubuntu. I am using Trendnet wireless router to connect through wireless. Internet is not working in my laptop while connecting through wireless. The device address, i.e. 192.168.1.1 is working properly and it is showing the device details. But still I can not able to point out what the problem is. I have not installed any software for wireless connections while installing Ubuntu. 

Does the software from Dell company solve my problem? But Dell is not giving any softwares to support Ubuntu. Please guide me in this issue.

Thanking you in advance,

I'm also lost here, does the little icon on the top right corner tells you there is a wireless network in reach?, what model is that DELL? Im too lazy to go check what is that suppose to be. Is your laptop asking for any propietary drivers? (Maybe you have a broadcom card or something like that)

---

### Post by phubai on 2010-01-24
I believe it has an Intel Pro wireless of one form or another, so he shouldn't have a problem there. 

You haven't given us enough detail I'm afraid to be able to offer much help. If your network is broadcasting, you should be able to select it from the available wireless networks, and provide any security requirements you've set to enable you to connect and receive an IP address. You indicate that you have an IP which I suspect is your router's IP or default gateway. You must first connect to that router, and then you should receive an IP address. You can verify that easily by opening a terminal and typing:

```
ifconfig
```

You should see an inet address in the same range as your router gateway, in this case 192.168.1.X with X being the number assigned by your router. 

If you would provide a little more information, it would be very helpful.

---

### Post by harish.ponnaganti on 2010-01-27
I think everything is fine. Because sometimes the network is working normally. But few times it is not connecting. Eventhough it is showing that TrendNet is connected, and the device address, 192.168.1.1 works properly, but Internet is not accessible. Pages will not be displayed. What is worse, seldom it won't show any wireless connections at all. But always, Internet is accessible with direct cable connection (ethernet).

I don't know how to check the IP address of the system and how to set it manually as I am new to Ubuntu. Please suggest me...

---

