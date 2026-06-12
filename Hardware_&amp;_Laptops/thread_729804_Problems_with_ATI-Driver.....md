---
title: "Problems with ATI-Driver...."
date: 2008-03-20
forum: Hardware &amp; Laptops
---

### Post by BurgerKing on 2008-03-20
At first: Hello @ All!
I've to say that I'm a German Kubuntu-User so please don't be angry if my English isn't as well as you are used to hear ;)
In the German Forums no one could help me, so I've registered here and hope that somebody out there can help me solving my Problem.
I'm fearing I cannot say you exactly what my Problem is, the only thing that I can say at the moment is that I have the Xorg.0.log and Xorg.conf, which I added to this Post.
I also should say that I use Ubuntu 8 hardy with the KDE-Desktop, so Kubuntu.
I used in Past Kubuntu 7.10 but some programms needed newer Librarys...however I've 'killed' my old so I tried out the Alpha 6 Release of Kubuntu =)
Here is a link to my Webspace 'cause I couldn't upload my Xorg-log, it's to big or something that kind....[http://suizide.lima-city.de/Xorg.0.log.txt]("http://suizide.lima-city.de/Xorg.0.log.txt")

I would be very glad if anybody out there could help me I'm just before crying =(

Best regards
Burger

---

### Post by Bablefish on 2008-03-20
HUGE WARNING The only ATI driver out there is 64 bit, and if your computer is 32 like mine I say STOP!!! right now. If you go any further you could crash your video driver.

---

### Post by IsawSp4rks on 2008-03-20
> **Bablefish said:**
> HUGE WARNING The only ATI driver out there is 64 bit, and if your computer is 32 like mine I say STOP!!! right now. If you go any further you could crash your video driver.

Not true.  Quoted from the ATI Driver Install wiki:-

> this installer is for 32bit and 64bit systems

BurgerKing, follow the steps in this guide : [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.3_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.3_Driver_Manually)

that will ensure you have totally removed the older driver, installed the correct dependencies and then will have the the latest driver (8.3) installed.

This driver only works properly with ATI x#### cards.

---

### Post by BurgerKing on 2008-03-22
I've tried everything and nothing did work...
BUT: Yesterday, I did a click-mistake and Guarddog (my Firewall) blocked everything...
After a reinstall of the ati-drivers, I think it was the 25th time, it was working!
I have been crying of happiness!
But after I noticed that firefox refused to work I solved my Firewall-disconfiguring, and then I saw the source of my Error: The Updates! In the hardy updates are 3 packages: fglrx-kernel-source, fglrx-kernel-source-dev and xorg-driver-fglrx. If I update these after the regular installation with the ati-installer, the driver begins to freak out xD
Whatever, It seems that the driver of the Hardy-repositories has got problems with AGP-Cards, with 9550er-Series Cards or whatever....
However, It works when I refuse to update the driver...I don't know if this problem is public but my problem was definitely caused by the fglrx-update... So I want to thank you all for your work...
Ubuntu is not an Alternative to windows, it breaks the window XP

Have a nice day
Burger

---

### Post by BurgerKing on 2008-03-22
I'm sorry guys but I jumped around to early....
After an upgrade to the Beta-Release my old Problem is the same...
If somebody could help me I would be very pleased....

So, please help me!

Yours sincerely
Burger

---

### Post by BurgerKing on 2008-03-23
*push*

---

