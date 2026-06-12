---
title: "Which Netbooks are the most Linux friendly?"
date: 2010-07-08
forum: Hardware
---

### Post by connel on 2010-07-08
I'm looking to buy a net-book. At the moment I've got a Dell Inspiron 1525 laptop. It runs Ubuntu just fine. So at first I was thinking of getting a Dell Mini. However I've been looking around in places like Comet and Currys (since I live in England) and have found a couple of really nice HP and Samsung net-books that have fare superior looks (in my opinion any way :) ) and much better battery lifes. These are:

The Samsung N150
Specs are here:
[http://reviews.cnet.co.uk/laptops/0,39030091,49304784,00.htm](http://reviews.cnet.co.uk/laptops/0,39030091,49304784,00.htm)

And the HP 210-1003
Specs are here:
[http://www.play.com/PC/PCs/4-/13194001/Hewlett-Packard-Mini-210-1003SA-Intel-Atom-N450-1-66GHz-1GB-250GB-10-1-Windows-7-Starter-Netbook-Blue/Product.html](http://www.play.com/PC/PCs/4-/13194001/Hewlett-Packard-Mini-210-1003SA-Intel-Atom-N450-1-66GHz-1GB-250GB-10-1-Windows-7-Starter-Netbook-Blue/Product.html)
(Just noticed that play.com says this has built-in Bluetooth which it didn't say in Currys)

Both use the same Intel Atom N450 1.66GHz processor, Intel Graphics Media Accelerator 3150 graphics card and the Intel NM10 Express chip-set.

I have always thought Intel were Linux friendly but didn't want to fork out £300 on a net-book that doesn't run Linux!

Could someone reassure me that these net-books work well with Linux (Like does the Bluetooth, WiFi, Keyboard hot keys etc. work well).

Thanks!!! :)

---

### Post by ianmillington on 2010-07-08
For a compatibility list take a look here

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

As a priority I would recommend you buy one where the wireless is reported to "work out of the box" as you don't want to be messing about too much with it. If it has got the GMA500 graphics card (which I think the dell mini has) it's not linux friendly due to requiring 3rd party drivers so logic says avoid.

Hope this helps

---

### Post by ajgreeny on 2010-07-08
Have a look at the X10 netbook from Novatech here in the UK, which you can get without an OS and runs 10.04 UNR or standard gnome desktop as if it was made to use it as its OS.

I have the previous version with an atom 270, so shorter battery life, but nevertheless a great little netbook.  Everything works, absolutely everything as far as I have been able to test.
[http://www.novatech.co.uk/novatech/laptop/range/x10black.html](http://www.novatech.co.uk/novatech/laptop/range/x10black.html)

---

### Post by KegHead on 2010-07-08
hi!

My Dell mini 9 has been flawless.

2gb ram, 16gb ssd.

KegHead

---

### Post by ianmillington on 2010-07-08
I can understand that. I have a 4 year old dell notebook myself which with Kubuntu 10.04 goes like a rocket.

However, my perception of Dell has deteriorated somewhat. They say they support ubuntu but when you hit the "shop for ubuntu laptops" you get taken to a list of 36 laptops without a single one running ubuntu - all windows 7. That's not what I call support and I have concluded that when Dell start to supply what I want, then I'll consider buying. 

I have checked and it would appear that the new Dell Mini runs the intel NM10 which I understand works with linux.

The Novatech seems very interesting - when I'm next in the market for a new machine I'll certainly bear them in mind - so long as they can confirm it'll work of course:-)

---

### Post by connel on 2010-07-08
I took this from the compatibility list ianmillington sent me:

> Samsung N150

WiFi didn't work from the install image, but did once the installed Ubuntu had upgraded to the latest kernel and modules. Sound, webcam and sleep all work as with the N140. Battery life is good: gets through a day of light use. My biggest complaint is that without LVM support I wasn't able to set up dual-boot with the Win7 Starter that came on the device.

There are some brightness issues:

    * 574250

I have decided I would prefer the Samsung because it has much better battery life than the Dell Mini everyone is recommending. The reason I am buying a netbook is because I need a more portable device than my laptop and the Dell Mini only has 3.5 hours battery life compared the the Samsung's 8/9 hours. The Novatech netbook being mentioned sounds good but I still need Windows (:(!!!!!!!) as I prefer Word to OpenOffice any day (as much as I love Linux). The quote above states they could not get the laptop to dual boot with Windows 7 starter. Is this possible yet? Is Grub not compatible with Windows 7??

Thanks for all your help everyone!!!

P.S. is the problem with booting into Windows 7 a Grub 2 issue? Would Grub 1 have the same problems (as I also use openSUSE on another machine that uses Grub 1)

---

### Post by ianmillington on 2010-07-08
Couple of thoughts:

What version of office will you be running (given that some versions now run pretty well on wine). Are there any other apps for which you require windows? 

Would I be reading too much into it if I were to conclude you want to use windows for your serious stuff and linux for browsing etc? If so, maybe a Win7/ Android combination like the Acer could be for you. If it comes preinstalled, it should be guaranteed to work. Never used one though so I can't say whether it's any good :)

---

### Post by connel on 2010-07-08
Well I have been running Office 2007 but will probably upgrade to 2010 for Uni. I have had 2007 running well in Wine but the fonts looked really funny and I am really really fussy. I also have a Nokia phone and require OVI suite to back up my texts and stuff.

I would prefer to be able to run a full Linux distro on the netbook rather than Android. I pretty much do all my tasks in Linux apart from my course work. I am doing Software Engineering at Uni next year so will be doing a lot of Java programming and stuff I will hopefully be able to do in Linux. I also love KDE and really want to learn Qt and C++ so will need a full distro to do such things.

I've kinda got my heart set on the Samsung I mentioned because it looks super cool, has amazing battery life and has Windows 7. I was just wondering if the problems I quoted about dual booting where solved since that was written?

Thanks :)

---

### Post by libssd on 2010-07-08
I'm not a fan of the Dell netbooks. £219.98 Inc VAT for the Novatech (without OS) sounds like a no-brainer. £30 more for Windows 7, which might be worth the added cost, as there are times when you just have to have Windows (but check that it comes with recovery disks to reinstall Windows if something goes wrong with partitioning). From the photo on their site, it looks an awful lot like a rebranded Acer, but netbooks are such commodity devices that they all look pretty much the same, and have the same specs.

I have an Acer D150, which runs flawlessly with Ubuntu 10.04 or Linux Mint Isadora.

Consider factoring in a compact external optical drive in your purchase cost -- invaluable for backup/restore, no matter what OS you run. Backup/restore with USB thumb drive is also possible, but I have had more issues with that approach. DVD backup/restore has always worked flawlessly for me.

---

### Post by ianmillington on 2010-07-08
I wouldn't know about the dual-boot issue tbh but it does seem to be a bit of a dealbreaker, potentially.

I now only have windows XP in a Virtualbox VM as my uses for it are so limited so I don't dual-boot any more, but I would be very surprised if the issue was confined to that netbook.

---

### Post by connel on 2010-07-08
> **ianmillington said:**
> I wouldn't know about the dual-boot issue tbh but it does seem to be a bit of a dealbreaker, potentially.

Yeah that's why I was I was a little concerned :).

> **ianmillington said:**
> I would be very surprised if the issue was confined to that netbook.

Yeah I thought it would be mega strange if Grub didn't work just on that laptop when it came to dual booting but did on other netbooks.

Think I'm gonna gamble on it because it looked so nice in the shop lol.

Thanks for all your help everyone!!

---

### Post by Wittaker on 2010-07-11
I'm using using the Lenovo S10-3. Everything works out of the box except the brightness keys (function+up\down). You can change the brightness when booting the machine however. Also, suspend is a little flaky sometimes.

The keyboard on the S10-3 is best-in-class. The battery life is a bit short though. Just doing basic internet browsing, I haven't managed to break 5 hours of continuous use.

I'd recommend you take a look at the HP mini 5102. Good keyboard, great touchpad, and great battery life. I haven't managed to find anyone who's tried linux on it however, so I'm not sure of compatibility.

---

