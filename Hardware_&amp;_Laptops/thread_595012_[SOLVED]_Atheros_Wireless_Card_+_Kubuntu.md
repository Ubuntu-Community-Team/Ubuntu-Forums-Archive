---
title: "[SOLVED] Atheros Wireless Card + Kubuntu"
date: 2007-10-28
forum: Hardware &amp; Laptops
---

### Post by bogdan_5844 on 2007-10-28
This is the only thing between me and a complete linux envirronment.
There are a lot of threads on this,but none apply exactly to me.
So,i downloaded the Kubuntu 7.10 ISO,wondering if it will work with my Atheros AR5006EG wireless lan card.In Ubuntu it worked like a charm,in Kubuntu exactly the opposite.I find KDE a lot User-Friendlier than GNOME (i used both for like 6 months) so i want to stay on KDE,especially with the KDE4's launch so soon.So,what do I have to do to get this card working?I`m a little newbie in linux(rarely used the console)
so please have patience with me :popcorn:
P.S.I am writing this from Vista Ultimate,wich i simply hate(it came preinstalled)and i do miss Amarok :-D
P.P.S.Kubuntu,from the live cd,detects only the ethernet card,not the wireless one

---

### Post by bogdan_5844 on 2007-10-30
anyone? :(

---

### Post by AndrejTheHunter on 2007-10-30
Hi Bogdan_5844

I cannot help you, but have the same situation!
I think, the problem is not with KUbuntu, it can be the 7.10 version- in general. 

I bought an ACER Aspire 5720Z  Notebook a few days ago. It also has the Atheros AR5006EG Wifi. I Installed the GMOME  Ubuntu 7.10. The installer automatically set up a Locked driver for it from the Atheros Company.  My problem is that the lspci list contains this  hardware, but neighter iwconfig nor other wifi applications see this. I tried madwifi, blacklist, but till now I cannot solve this problem. I tried to install the windows driver through ndiswrapper, it accepted the driver(Hardware present: yes)  , but no changes about the wifi problem.

I was wondering why I can read in the Locked drivers list this text:Enabled <red circle> Not in use.. ??- (I read this in hungarian language, I only translated back to english- maybe this text can be a bit different but similar in the english version)

I was wondering about that, it means, that the wifi is not powered on?? But I cannot find any buttons for this on the notebook. There is one, but they are only software-processed custom-buttons for Windows.

Please anyone help us!

---

### Post by bogdan_5844 on 2007-10-30
well...I don`t think it`s the same,but is similar no doubt.
Ubuntu 7.04 and 7.10 both detect my wireless card P-E-R-F-E-C-T-L-Y(no doubt better than vista :P )
But Kubuntu 6.10,7.04 and 7.10 work like crap,and by that I mean that they don`t even SEE my card...
I don`t know how to use lspci or other linux commands,but from what I deduced from the GUI apps,Kubuntu 6.10 sees my card,but can`t use it for an unknown reason(meaning that I don`t have any idea).I think the same applies for the 2 other versions.

I still wonder...how can this WiFi card work perfectly in GNOME,and don`t work at all in KDE(Kubuntu)...maybe GNOME uses another hardware detection S/W?

IDK...if someone knows anything...that`ll be perfect.

P.S.I found that I can get on with GNOME for the moment :P But i really want to try the upcoming KDE4,wich is why i am so ancious for using Kubuntu

---

### Post by bobyy on 2007-10-30
Hello guys 
This is the tutorial step to step to solve your problem good luck.
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by bogdan_5844 on 2007-10-30
thanks for the info,but i find miself quite at home in GNOME :) but when KDE4 appears in December,i will need that help,thank you very much for help :popcorn:

---

