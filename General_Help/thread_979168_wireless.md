---
title: "wireless"
date: 2008-11-11
forum: General Help
---

### Post by popatag86 on 2008-11-11
i installed ubuntu and it shows no wireless networks in range, when I go to windows vista it connects wireless just fine...how do i get internet on ubuntu???!!

---

### Post by brandon88tube on 2008-11-11
Have you tried checking out this part of the forums? [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

Also you never stated what wireless card you have or anything so, we can't really help until you give us that information.

---

### Post by josephfuentes on 2008-11-11
I am having the same problem. Before I begin I am a newbie to Linux. I installed Ubuntu using Wubi on my Windows vista laptop. Like all laptops it has built-in wifi. Therein lies my problem. 

When I installed Ubuntu using Wubi and I thought it was going to be a Windows application but turns out it partitioned my disk and now I have dual boot. that's ok. I can use the basic applications like text editor and some basic stuff. For now I just want to get used to Ubuntu first.

Here's my problem. My ubuntu has NO connectivity to my wifi network. How do I set it so Ubuntu at least has access to the wifi adapter in my laptop so it can connect to the web?

---

### Post by brandon88tube on 2008-11-12
Like I said people, we need more info than "it doesn't work please fix it." What kind of wireless card do you have? Also did you ever try looking at the Networking & Wireless section of the forums?

---

### Post by Orlsend on 2008-11-14
What Versions of Ubuntu you have?

---

### Post by Hates BSOD on 2008-11-14
What type of wireless card do you have?
Intel should be no issues.
Linksys/broadcom = problematic.
Do you have a network cable connection available or only wireless?

---

### Post by Marius Derekus on 2008-11-15
Type this command in console 
```
lspci -v | grep Network
``` 
Post the output.
Also go to **System>administration>hardware drivers** and tell us what it says.

---

### Post by josephfuentes on 2008-11-27
I have a broadcom wifi adapter. I know that there are problems because there are no open source drivers for it. 

I was fortunate enough to get a book for beginners linux (that's me) that says something like this
lspci | grep Broadcom \ Corporation

then type
wget -c [http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmare_1.3-1_2_all.deb](http://ubuntu.cafuego.net/pool/feisty-cafuego/bcm43xx/bcm43xx-firmare_1.3-1_2_all.deb)
and then do a 
sudo with some stuff here

does this sound right?

---

### Post by darksideforge on 2008-11-27
I haven't tried my wireless but I'm going to later today. Based on this screen shot do you think I'll have any problems?  Also, I don't see any audio drivers listed and I know my sound isn't working so I've got to figure that out as well.
[IMG]http://ubuntuforums.org/showthread.php?t=992534&highlight=beginners[/IMG]

---

### Post by darksideforge on 2008-11-28
Nope...wireless not working. Currently trying code from other messages in an attempt to repair problem. So far, negres.

---

