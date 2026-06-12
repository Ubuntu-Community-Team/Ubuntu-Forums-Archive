---
title: "modem on HP Omnibook 6000"
date: 2006-01-26
forum: Hardware &amp; Laptops
---

### Post by Orion2000za on 2006-01-26
I have a feeling that my problem is not exactly new but here goes. I now run Kubuntu 5.1 nicely on a desktop PC and feel no need to "go windows" on that one.

So I installed Kubuntu 5.1 on a HP laptop, an Omnibook 6000, to see how that could work. 

Most things work as expected, that is good. Network card is part of a 3Com miniPCI combo card 10/100 that also hosts a 56K modem. 

And that is the problem. LAN card comes up nicely. BUT no modem. And in this case the laptop is meant to be used mainly with dial-up connection to internet from home or during travels. So it has to work.

Now I understand these miniPCI combo cards are a headache but is there anyone with ideas or solutions? Would be disappointing to scrap the whole project and revert back to XP. 

Cheers,
Orion

---

### Post by darm on 2006-01-26
I used to own Omnibook 6000 until recently.

Sorry to disappoint you, but there seems to be no way to make modem work under linux unless you write a driver yourself.

Besides, how do you find Kubuntu running on such a machine? I've experienced major slowdown on both ubuntu distros and moved to unofficial xubuntu and loved it - I'm now using it on my new laptop.

---

### Post by Orion2000za on 2006-01-27
To start with the good things; I have tried two earlier distributions of Ubuntu and they clogged the HP alright. BUT 5.10 feels much faster and slicker and with KDE is really nice.

Now to the bad part; this means uninstalling Kubuntu and back to XP. No way I can work with it if I can't use the modem and I will not buy an extra modem just for this.

Too bad but here the Linux community must do more homework if a "breakthrough" is ever to happen. Laptops are more and more becoming the main PC for many users and especially pros. 

If I should install for an NGO or company they are likely to have one or several laptops and not necessarily the latest. This is a major weakness for the spread of Open Source Linux!!

Orion :(

---

### Post by darm on 2006-01-27
Your omnibook must be loaded with tons of RAM!

Mine had 256M and I found XP rather slow either, so I used 2000 when I had to write some windows code for my graduation.

Well, too bad you are reverting to win...don't forget to check back in when you upgrade your laptop :D

---

### Post by Orion2000za on 2006-01-27
It has 256 Mb and XP is very hassle-free. OK I normally tweak quite a lot and admittedly it is mainly used by my family these days but I have no complaints actually.

After more internetbrowsing I have found out that it really looks like the modem will never work. Pity.

Orion

---

### Post by mips on 2006-01-28
[QUOTE=Orion2000za]To start with the good things; I have tried two earlier distributions of Ubuntu and they clogged the HP alright. BUT 5.10 feels much faster and slicker and with KDE is really nice.

Now to the bad part; this means uninstalling Kubuntu and back to XP. No way I can work with it if I can't use the modem and I will not buy an extra modem just for this.

Too bad but here the Linux community must do more homework if a "breakthrough" is ever to happen. Laptops are more and more becoming the main PC for many users and especially pros. 

If I should install for an NGO or company they are likely to have one or several laptops and not necessarily the latest. This is a major weakness for the spread of Open Source Linux!!

Orion :([/QUOTE]


Before you give up do me a favour and identify the MODEM chipset used by the 3Com card. Not all those cards use the 3com modem chipset strange as it may sound...

Post the PCI ID here, if you have the Lucent chipset version you can use the ltmodem driver.

---

### Post by Orion2000za on 2006-01-30
Don't know exactly the pci id but it clearly states in KDE that it is "3COm PCI Winmodem 56k" or something like it and states it "unknown".

Orion

---

