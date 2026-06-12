---
title: "My new rig comes this weekend...."
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by heitjer on 2009-03-31
Hi,
this weekend will be busy. My new computer is coming and I am determined to go full Ubuntu. I have been running Ubuntu for some time already on my Server (w/o desktop), recently used it on an older Laptop and Mythbuntu. Now it is time to get my main machine "upgraded". I am exited to break now completely with my Windows history!

I am only a little bit concerned about a few Windows programs, Quicken and TurboTax due to my history over the years.

So I read up on WINE or other software pieces and I think we can work something out. 

Here is my question:

[LIST]
[*]Should I install as dual boot and then WINE to it? 
[*]If so - which OS should I install first - Ubuntu or Win XP?
[*]Shall I leave Windows completly behind? What are my alternatives to Quicken? Can I convert existing files?
[/LIST]

Sidenote - I have been reading up a lot on KDE and GNOME. I like DigiKam but I read it comes with a bunch of dependencies of KDE. I don't intend to start a big dispute here on one over the other but should I consider kubuntu from the start? How stable is the recent KDE release on QuadCore rigs? Thoughts?

One more question...I get the QuadCore9550 - should I use the Desktop-amd64 distro?

Thanks a bunch!

---

### Post by Partyboi2 on 2009-04-01
You could install ubuntu to the whole drive then use something like virtualbox or vmware to run windows as a guest operating system, that way you can boot windows if you ever need to.

---

### Post by heitjer on 2009-04-01
Thanks - I read up on VIRTUALBOX, is this better conceptually than WINE? I would require a full install but it would not be bootable - correct?

---

### Post by Partyboi2 on 2009-04-01
Not every windows programs will run well with wine some programs work better then others. Check [[COLOR=Blue]here[/COLOR]]("http://appdb.winehq.org/") to see how compatible the programs you want to run are with wine. The advantage of using virtualbox and installing xp as a guest is you won't have that problem. 
Running windows through virtualbox is not bootable from grub (that I am aware of) instead you would start windows by opening virtualbox (Applications>System Tools>Virtualbox) then you would start windows up.

---

### Post by Simian Man on 2009-04-01
There is Gnucash which has most of the features of Quicken - though you should try it yourself to see if it will work for you.  Turbotax I don't know about.

For wine, you don't need a valid copy of Windows to run Windows programs.  For a VM, you do so if your program works with wine, that may be better.

You should install Ubuntu and then install KDE on top of that.  Kubuntu isn't really a separate distribution, it just installs KDE by default instead of Gnome.  Both DEs can be installed at once.

Lastly you can use either 32 or 64 bit versions.  64 will give better performance (especially if you have more than 4 gigs of ram).  Historically 64 bit Linux had some compatibility issues (Java and Flash), but that is all but history.

---

### Post by heitjer on 2009-04-01
Thanks Guys!

I have a valid copy of XP so I will go the Virtualbox way. It seems cleaner to me for now. I also read the latest scores that place Virtualbox ahead of VMware. Impressive!

I have only 4 GB Ram - should I go 64bit? Please advise. Here is my new rig - the case arrived today. Nice. I like the "*New Case Smell*".....

[mushkin 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400)]("http://www.newegg.com/Product/Product.aspx?item=N82E16820146731")
[CORSAIR CMPSU-650TX 650W Compatible with Core i7 Power Supply]("http://www.newegg.com/Product/Product.aspx?item=N82E16817139005")
[Western Digital Caviar Black 640GB 3.5" SATA 3.0Gb/s Hard Drive]("http://www.newegg.com/Product/Product.aspx?item=N82E16822136319")
[Intel Core 2 Quad Q9550 2.83GHz]("http://www.newegg.com/Product/Product.aspx?item=N82E16811119137")
[GIGABYTE GA-EP45-UD3R ATX]("http://www.newegg.com/Product/Product.aspx?item=N82E16813128359")
[HIS Hightech IceQ Turbo Radeon HD 4670 H467QT512P]("http://www.newegg.com/Product/Product.aspx?item=N82E16814161252")[Arctic Silver 5 Thermal Compound]("http://www.newegg.com/Product/Product.aspx?item=N82E16835100007")
[ARCTIC COOLING Freezer 7 Pro 92mm CPU Cooler]("http://www.newegg.com/Product/Product.aspx?item=N82E16835186134")

---

