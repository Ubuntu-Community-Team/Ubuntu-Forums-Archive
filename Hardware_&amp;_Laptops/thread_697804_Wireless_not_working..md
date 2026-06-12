---
title: "Wireless not working."
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by bhouncy on 2008-02-15
Hi. I just installed 7.10 on my laptop. I was working from the live CD and had the wireless network working. I started the install and now my wireless hardware doesn't exist. Well I had done a dual boot with XP and so I went back there to see any solutions and XP is saying the wireless doesn't exist there either! Has ubuntu blown up my card or is there a simple solution?

---

### Post by rspendl on 2008-02-16
Since it is really hard for drivers to blow up any hardware (especially wireless), you can try to check a wireless button on your computer. If you have accidentally switched it off, there is no wireless in either XP or Ubuntu. My other guess would be BIOS settings, but it is not really common for BIOS to disable wireless card.

Hope it helps,
Robert

---

### Post by uberlube on 2008-02-16
Your install of Ubuntu should not have affected your windows partition at all, so i agree that checking your wireless switch would be a good place to start. As for getting your wirless driver to work again i suggest using ndiswrapper.

---

### Post by bhouncy on 2008-02-16
Thanks for the replies. I tried the switch thing last night and it didn't make a difference. As for Linux not messing with XP this is the second time I've tried a dual boot on this laptop. The first time it stopped my touchpad mouse from working in XP. I was thinking it had something to do with my partitioning the drive during install. It had to resize the drive so maybe it did something there?

Anyway I ended up just reinstalling XP and got it to work. I'm wary of putting ubuntu back on the now partitioned drive just in case I get the same error.

What is ndiswrapper?

And I never thought about BIOS.

---

### Post by oldsoundguy on 2008-02-16
NDISWrapper is for wireless network cards that have little or no support in Linux itself (usually due to the non co-operation of the device manufacturer or chip manufacturer or both.)

[http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)
[http://en.wikipedia.org/wiki/NdisWrapper](http://en.wikipedia.org/wiki/NdisWrapper)

Google is your friend.

It is not the ONLY "wrapper" out there for some WinDOZE programs, but it is the most commonly used and appears to be the most reliable for it's use.

---

### Post by bhouncy on 2008-02-16
> **oldsoundguy said:**
> NDISWrapper is for wireless network cards that have little or no support in Linux itself (usually due to the non co-operation of the device manufacturer or chip manufacturer or both.)

[http://ndiswrapper.sourceforge.net/joomla/](http://ndiswrapper.sourceforge.net/joomla/)
[http://en.wikipedia.org/wiki/NdisWrapper](http://en.wikipedia.org/wiki/NdisWrapper)

Google is your friend.

It is not the ONLY "wrapper" out there for some WinDOZE programs, but it is the most commonly used and appears to be the most reliable for it's use.

Thanks for the links.

The card worked with the liveCD so I would imagine it should work with installed version.

---

### Post by oldsoundguy on 2008-02-16
I posted this on another thread involving Atheros based chipset wireless, but this MAY be of help:

system>
administration>
network settings>
highlight wireless connections (make sure it is checked)>
properties>
fill in the blanks (select your network and password .. enable automatic configuration)>
click OK>
close>

your network card should be working (provided the chipset was recognized in the first place.)

IF NOT NDISWrapper!

---

