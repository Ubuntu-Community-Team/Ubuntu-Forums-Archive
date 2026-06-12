---
title: "Samsung CLP-315 printer - Smart Panel not working"
date: 2009-09-03
forum: Hardware
---

### Post by semmelbroesel on 2009-09-03
Hi,
I am running the most current available Ubuntu version as far as I know (I'm no expert, so I keep forgetting what names the versions have), and if I remember correctly I downloaded the Linux driver for this printer from the Samsung site. (Hm, actually now that I think about it it is possible that Ubuntu recognized the printer by itself, so maybe that's the problem).
Anyway, I can print normally, the printer is shared through CUPS and my Windows network.
But I can't get the Samsung Smart Panel to work, so I have no way of seeing toner levels - the Ubuntu printer dialog does not get that information.
Since I don't know much about Linux (this is my first install and setup that I did by myself, and so far it's working), I'm wondering if maybe there is a unified driver in Ubuntu that is taking over, so the Samsung original driver won't work - or maybe I did something else wrong.
Is there someone who would be willing to walk me through ways to possibly fix this?
Thanks so much!

---

### Post by kamitsukai on 2009-09-04
> **semmelbroesel said:**
> Hi,
I am running the most current available Ubuntu version as far as I know (I'm no expert, so I keep forgetting what names the versions have), and if I remember correctly I downloaded the Linux driver for this printer from the Samsung site. (Hm, actually now that I think about it it is possible that Ubuntu recognized the printer by itself, so maybe that's the problem).
Anyway, I can print normally, the printer is shared through CUPS and my Windows network.
But I can't get the Samsung Smart Panel to work, so I have no way of seeing toner levels - the Ubuntu printer dialog does not get that information.
Since I don't know much about Linux (this is my first install and setup that I did by myself, and so far it's working), I'm wondering if maybe there is a unified driver in Ubuntu that is taking over, so the Samsung original driver won't work - or maybe I did something else wrong.
Is there someone who would be willing to walk me through ways to possibly fix this?
Thanks so much!

Your in luck I'm just about to install the smart panel and unified print driver for my samsung clp-300 so I will let you know how I get on =]

---

### Post by semmelbroesel on 2009-09-04
Great, thank!
I'll look forward to your experiences!

---

### Post by kamitsukai on 2009-09-04
> **semmelbroesel said:**
> Great, thank!
I'll look forward to your experiences!

Ok I'm now in the process of wanting to take a sledge hammer to my PC:( smart panel refuses to believe my printers plugged in and nothing will print...

off to find some help of my own:P

---

### Post by semmelbroesel on 2009-09-04
In my case, the printer works, even shared over the network. Just the Smart Panel thinks no proper driver is installed...
I wish I could remember what I installed - I may have just plugged it in and let Ubuntu sort it out, and that was it - but I just don't know anymore...
Well, good luck to you, too, and please share whatever you find out!

---

### Post by kamitsukai on 2009-09-04
> **semmelbroesel said:**
> In my case, the printer works, even shared over the network. Just the Smart Panel thinks no proper driver is installed...
I wish I could remember what I installed - I may have just plugged it in and let Ubuntu sort it out, and that was it - but I just don't know anymore...
Well, good luck to you, too, and please share whatever you find out!

probably let Ubuntu sort it out as I did before but I got fed up with the print quality...and not knowing what my toner levels where like:)

---

### Post by semmelbroesel on 2009-09-10
Any luck?

I meanwhile contacted Samsung, and it took me 4 emails (all of which apparently went to a new person each time without any previous contact saved) to get instructions on how to properly install the Linux drivers.
Haven't tried them yet, though, due to lack of time.

In case you'd like to try this first, here's what I received:

> When it comes to Linux we only offer a driver for support at this time. For all other support you would need to
search online Linux support forrums to see if anyone has an answer for your questions.


[Unified Linux Driver Install Guide]

1. Make sure that you connect your machine to your computer. Turn both the computer and the machine on.
2. When the Administrator Login window appears, type in root in the Login field and enter the system
password.
3. Download and extract the driver
[root@localhost root]#tar xzf [Downloaded File Name(XXXX.tar.gz)]
4. The driver will be extracted as ''cdroot'' folder in current path.
5. Execute installation program.
[root@localhost root]#./cdroot/autorun
6. When the welcome screen appears, click ''Next'' and proceed installation.

[Ubuntu OS Installation]

1. Download and extract the driver
2. Open ''Root Terminal''
3. Execute installation program.
$ sudo cdroot/autorun
4. After intall, PPD path is set again.
$ sudo ln -s /usr/share/cups/model/samsung /usr/share/ppd/custom/samsung
5. Execute Configurator, and Add your printer model name by Add Printer

Samsung Download Center:
[http://www.samsung.com/us/support/download/supportDownloadMain.do](http://www.samsung.com/us/support/download/supportDownloadMain.do)

Samsung Global Download Center
[http://www.samsung.com/us/support/download/supportGlobalDownloadAgreement.do](http://www.samsung.com/us/support/download/supportGlobalDownloadAgreement.do)

1-800-SAMSUNG (726-7864)

---

