---
title: "New member needing help"
date: 2007-04-20
forum: Indiana - US
---

### Post by skywarp04 on 2007-04-20
I am a new member to this forum and a new linux user.  This may be a silly question, but Is this forum more for happenings with Indiana Ubuntu Community or can I get support here too?  I am having a problem with Ubuntu locking up intermittently.  If this forum is for support to I will post more specifics for my problem.  Thank you.

---

### Post by simon.a.ruiz on 2007-04-21
Hey, there!

Go ahead and post details here. Both the forums and mailing list are available BOTH for "team business" and support purposes!

Welcome aboard!

---

### Post by skywarp04 on 2007-04-21
Great!!  Here's my problem.  I will probably have many questions, but here is my first problem.  I installed Ubuntu 6.0.6 LTS from a live cd that I got from a Linux fest recently at IUPUI.  The install went fine, but Ubuntu consistently locks up after being used for anywhere from 5 to 15 minutes.  It hard locks and will not respond to any input what so ever.  I am guessing that is a problem with x server.  The reason I think that is because I can switch to a terminal console by press cntl-alt-f1 and my computer does not lock up.  I really don't think it is a hardware problem because I have been using this same set for several years now with windows xp pro.  Here is my hardware configuration.  

P4 2.4 ghz Northwood Core w/ Hyper Threading
Abit IC7 motherboard w/ Intel 875 chipset
512 MB ram
80 gib Western Digital HDD using serial ATA
DVD burner also using serial ATA
ATI Radeon 9700 Pro video card
D-Link DWL-G510 wireless network card

My main problem is I am new to Linux and I don't know where to start.  Is there a log file I can view to see what is happening right before my computer locks?  What procedures can I use to isolate what is causing the problem?  I just need to know where to start.  I am patient and bound and determined to not let this initial set back deter me from learning Linux.  Any help is greatly appreciated.  I know you will probably need more info than what I have giving you, but this is all I can think of right now.   One other thing to keep in mind is that I do not have a working internet connection in Ubuntu right now.  I am working on that one.  It seems like I may have to use ndiswrapper to get my dlink card working correctly.  I think I can figure that problem out except my computer keeps locking up on me.  Thank you for you help!!

---

### Post by indytim on 2007-04-22
First of all, welcome to the forum.  Hope your journey into Linux proves to be fun.

A couple of things I'd like to suggest (sorry don't have an immediate solution to the problem you cited).  The board here is active, but not super active inasmuch as there isn't someone on-line monitoring new postings 24/7 (I think).   As a new user, you need/want resolution on your problems in short order.  My suggestion, in your case, if you don't get a response quickly on this board, you may want to head over to one of the other, more active boards in Ubuntu.  In the situation you mentined, I'd suggest either absolute beginner or the installation board.

Again welcome aboard.

IndyTim
(I'm actually in Carmel and not Indy)

---

### Post by simon.a.ruiz on 2007-04-22
> **skywarp04 said:**
> Great!!  Here's my problem.  I will probably have many questions, but here is my first problem.  I installed Ubuntu 6.0.6 LTS from a live cd that I got from a Linux fest recently at IUPUI.

My first suggestion would be to download you a copy of the latest version of Ubuntu, 7.04, burn it off, and use that. Unless you really need to have a version that is supported with security updates and such for more than 18 months, it really is advisable to use the most recent supported version. The cutting edge of Linux improves quickly and the almost one-year difference between Dapper and Feisty is pretty noticeable in terms of usability and hardware support, among others...

7.04 JUST came out, which is why we didn't have copies at the IU LinuxFest, though we were including copies of version 6.10 along with the "official" 6.06 CDs we were passing out. I'm guessing you got your CD from the USSG people, though, if it didn't include the Ubuntu Indiana branded copy of 6.10.

> **skywarp04 said:**
> The install went fine, but Ubuntu consistently locks up after being used for anywhere from 5 to 15 minutes.  It hard locks and will not respond to any input what so ever.  I am guessing that is a problem with x server.  The reason I think that is because I can switch to a terminal console by press cntl-alt-f1 and my computer does not lock up.

Likely a fair assesment.

Can you hit Ctrl-Alt-Backspace to reset the X server when it locks up?

Is it slow at all when you switch over to the terminal console?

> **skywarp04 said:**
> I really don't think it is a hardware problem because I have been using this same set for several years now with windows xp pro.

It's likely not a hardware failure, then, but it could theoretically be a hardware support problem. The biggest reason this might happen is hardware that requires closed/proprietary drivers or firmware.

> **skywarp04 said:**
>  Here is my hardware configuration.  

P4 2.4 ghz Northwood Core w/ Hyper Threading
Abit IC7 motherboard w/ Intel 875 chipset
512 MB ram
80 gib Western Digital HDD using serial ATA
DVD burner also using serial ATA
ATI Radeon 9700 Pro video card
D-Link DWL-G510 wireless network card

FYI, ATI cards are notoriously annoying under Linux, as well as most wireless network adapters, for the reason I just mentioned. You can usually get them to work, but it takes some work, sometimes. Perhaps if you use Ubunt 7.04, the new "Restricted Drivers Manager" will be able to automatically install the necessary ATI video card drivers. With the wireless card, I'd suggest Googling that exact model number and Ubuntu at the same time, something like "DWL-G510 Ubuntu", and see what pops up. This method, mixed with some perseverance and creativity, rarely fails me ;-)

> **skywarp04 said:**
> My main problem is I am new to Linux and I don't know where to start.  Is there a log file I can view to see what is happening right before my computer locks?  What procedures can I use to isolate what is causing the problem?  I just need to know where to start.

Check out your /var/logs directory. [http://www.cyberciti.biz/faq/linux-log-files-location-and-how-do-i-view-logs-files/](http://www.cyberciti.biz/faq/linux-log-files-location-and-how-do-i-view-logs-files/)

> **skywarp04 said:**
> I am patient and bound and determined to not let this initial set back deter me from learning Linux.  Any help is greatly appreciated.  I know you will probably need more info than what I have giving you, but this is all I can think of right now.

With that attitude, nothing will defeat you.

> **skywarp04 said:**
> One other thing to keep in mind is that I do not have a working internet connection in Ubuntu right now.  I am working on that one.  It seems like I may have to use ndiswrapper to get my dlink card working correctly.  I think I can figure that problem out except my computer keeps locking up on me.  Thank you for you help!!

Ouch! So not even your wired ethernet works? (assuming you have one)

Hope this helps, and that it find you having a beautiful day!

Simon

---

### Post by skywarp04 on 2007-04-25
I took your suggestion and installed 7.04.  My wireless network connection still does not work properly, but it solved my locking up problem.  At least I can do work on the system now without having to constantly restart!!  Good suggestion.  I misinterpreted new release as meaning that it might not be as stable as the previous LTS version, but it is not.  Thank you for your help!!

---

### Post by simon.a.ruiz on 2007-04-26
> **skywarp04 said:**
> I took your suggestion and installed 7.04.  My wireless network connection still does not work properly, but it solved my locking up problem.  At least I can do work on the system now without having to constantly restart!!  Good suggestion.  I misinterpreted new release as meaning that it might not be as stable as the previous LTS version, but it is not.  Thank you for your help!!

Ah, yes, wireless can be a real pain in Linux, still. Manufacturers simply don't think it's worth either providing Linux drivers or publishing the specs so that Linux developers can make their own.

Wireless network adapters are such a problem that some Linux users simply buy USB wireless adapters that are known to work with the linux kernel. Do not despair, however, with a little research my guess is you should be able to find a HOWTO published on the web that will help you coax some life out of your onboard wireless.

When I was working at Bloomington High School North, we purchased ten laptops with the idea of using them wirelessly. I googled for help based on their model (Dell Inspiron 1300), the wireless adapter model, and thing like "Ubuntu", "Linux", and "wireless" and  was able to find a HOWTO that detailed exactly how to use the ndiswrapper package to activate my wireless capabilities on those laptops.

(ndiswrapper is sort of a "last resort" package that utilizes drivers meant for Windows systems in order to provide the functionality a native driver would.)

I hope this is of any help and wish you luck.

Perhaps the "Hardware & Laptops" or "Networking & Wireless" forums here on ubuntuforums.org can be of more specific assistance in this matter.

Take care!

Simon

---

### Post by simon.a.ruiz on 2007-04-26
> **skywarp04 said:**
> I misinterpreted new release as meaning that it might not be as stable as the previous LTS version, but it is not.  Thank you for your help!!

P.S. Yeah, the LTS version merely guarantees that you will continue to get security patches and bugfixes for a long time--3 years on the desktop, 5 on the server. This is important in situations where you might not want to be upgrading the software on a regular basis and don't care about having the latest features (web servers, corporate desktop deployments, etc.)

In order to partake of the newest features (including hardware support, newer versions of software, the latest built-in shininess in Ubuntu) most of us stay with the latest stable release. In my experience, every new release is better than the last, including stability.

---

