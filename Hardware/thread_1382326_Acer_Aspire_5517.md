---
title: "Acer Aspire 5517"
date: 2010-01-15
forum: Hardware
---

### Post by whikwire on 2010-01-15
I've been contemplating on buying a laptop for to learn linux with. My question is will the following laptop (I think it's Acer Aspire 5517) work with ubuntu:

[http://www.bestbuy.ca/catalog/proddetail.asp?logon=&langid=EN&sku_id=0926INGFS10132461&catid=28239](http://www.bestbuy.ca/catalog/proddetail.asp?logon=&langid=EN&sku_id=0926INGFS10132461&catid=28239)

It is a 64-bit processor but I'm curious if I could run a 32-bit Ubuntu?


Thanks again I don't want to buy a laptop to use with windows 7.

---

### Post by TBABill on 2010-01-15
That machine has sufficient processing power, memory, HDD space, etc. for Ubuntu. I have an ACER Aspire 5530 with a different configuration, but a couple years old and running flawlessly as far as capability with the OS. One note, however, is that the machine in the link you provided has an ATI video card so you may have to tweak your video configuration once you do an install of Ubuntu. ATI seems to be a bit tougher to configure, especially for newer users, than nVidia cards. That's not from experience, just from what I have seen posted on the forums. Search for ATI on the forums for other users' experiences. My nVidia experience on 2 different laptops was easy with Ubuntu (Karmic).

---

### Post by whikwire on 2010-01-15
that's been my worry the whole ati issue. should i avoid laptops that carry that configuration? also im a linux beginner so is it even possible for someone of my skill level to configure the system at this point in time.

also [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti) gave the video card a green light. does that mean im good to go?

---

### Post by whikwire on 2010-01-16
bump

---

### Post by TBABill on 2010-01-16
If you have confirmation someone else has successfully run with the card, shouldn't be a problem. you can always search the forum, or post to the forum, if you get it and need help. Being new shouldn't stop you unless you don't want to invest the time if it becomes necessary. 

Will they let you take a LiveCD with you to the store and run it from the CD without anything being installed?? That could let you know if it'll work and not harm their computer if you get a sales person really willing to work with you.

---

### Post by whikwire on 2010-01-16
so if it runs from the live cd all will be well?

---

### Post by whikwire on 2010-01-17
bump

---

### Post by TBABill on 2010-01-17
Yes if it will run from the LiveCD you should be perfectly fine with an install. It is the same software either way, just one is installed and the other is not.

---

### Post by Waffles McCoy on 2010-01-20
Hello! Just wanted to give you a heads-up that I just got an Acer Aspire 5517 last month and have it dual-booting Windows 7 & Karmic. It runs great for the most part, except for the wireless internet. Now, I'll readily admit to being VERY much a Linux-noob, but this wireless issue seems to have cropped up with others of a fairly wide range of proficiency with Linux who have this same machine. Wireless works perfectly in Windows, but signal strength is only around 80% at best, extremely erratic (especially when downloading torrents) and continuously loses connectivity when in Ubuntu. I've searched the forums, but haven't found an exact solution to the problem yet-- at least, not one I'm able to confidently implement at my current level of understanding. My husband (responsible for converting me to Ubuntu) suspects it *may* be that the wireless card in this model is simply too new to have had all the kinks worked out with the drivers for Linux. So, who knows... It may just be a matter of waiting?

All this hasn't been enough to turn me away from Ubuntu (heh!), and I'm still happy with this laptop besides that. It's a nice, solid, inexpensive little machine. I just wish I could ditch the ethernet cable. :(  Hope this was helpful info for ya!

---

### Post by t4thfavor on 2010-01-21
I have an acer/ati laptop (aspire 5100) and I can tell you that if you want reliable suspend to ram, you have to go intel/intel. ATI has already placed my 2 year old card on the legacy list for the linux driver, and so I am forced to either leave it on, or shut it down, neither are an ideal situation.

Also the xpress 1100 graphics adapter is slow as molasses, even when compared to my intel 945GM which is just bad if you ask me.

---

### Post by CareySchug on 2010-01-21
Maybe they made a change without changing the model number?

I have an Acer aspire 5517 bought last Friday, and with Ubuntu 9.10 the wired network came up fine, I upgraded with latest fixes today, but it stil doesn't recognise the wireless interface at all, not "network connections" window, not "ifconfig -a".  Only loopback and wired connections show.

I know others have said wireless "was an issue" without saying what they did, and still others said it worked out of the box, but only with 9.10, not with 9.04.  But for me, nothing recognised the existence of wireless in linux.  Works fine in Win 7.

This was purchased Jan 15, some of the files on the disk were dated mid December or maybe late December...

--Carey

---

### Post by CareySchug on 2010-01-21
Put my last post on hold while I download the 64 bit version of ubuntu... You would have thought I would have been asked "do you you really want to install the 32 bit on this machine?".  I think Solaris asked that, or else automatically detected and installed the correct version.  I've never had a 64 bit anything before...

--Carey

---

### Post by CareySchug on 2010-01-22
OK, I installed the 64 bit Ubuntu 9.10, downloaded the latest fixes (using wired connection)

Still does not recognise the existence of wireless hardware.

Any ideas on how to troubleshoot?  Is it possible the Debian archives would have a driver, and how would I look for it?

--Carey

---

### Post by Devo66 on 2010-09-11
Just an update for everyone.  Just playing around with this laptop and I installed Lucid x64 on it.  Wireless didn't work out of the box, but after installing updates and then the restricted Broadcomm driver suggested by Ubuntu, everything is working!  Wireless, Suspend, etc.  I also tested with and without the binary ATI video driver and everything works in both cases.  I didn't really test any 3D video performance, but in 2D, I didn't notice any difference in performance between the standard driver and the Binary driver.  I could watch Youtube videos full screen with both drivers.

---

