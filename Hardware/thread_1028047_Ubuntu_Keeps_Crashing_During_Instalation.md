---
title: "Ubuntu Keeps Crashing During Instalation"
date: 2009-01-02
forum: Hardware
---

### Post by AndrewEgel on 2009-01-02
Hello. First time poster here on the Ubuntu forums. I hope this question hasn't been answered already (I've done an extensive search already in the forum search bar plus Google).

So before I go on I should mention that my tech skill is somewhat high. I am a computer science major at San Jose State University, and I have had past experience with Linux distributions already. I already have Ubuntu running on my laptop with no problems what-so-ever. That is why this question stumps me. I will post my Hardware specs here before explaining the issue. Which is why I've posted in this forum, because I feel as though there is a hardware issue at hand that I am not seeing.

Motherboard: [Gigabyte GA-K8NSNXP](http://www.gigabyte.us/Products/Motherboard/Products_Overview.aspx?ClassValue=Motherboard&ProductID=1782&ProductName=GA-K8NSNXP) ([Link](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128245)). No I am not running any RAID array or anything. For the most part the board is nVidia, which likes open source (maybe it didn't like it back then when the board came out). Yes I have updated the BIOS to the latest version.

Processor: AMD Athlon 64 3400+ 2.4 GHz ([Link](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103484))

Graphics Card: ATI Radeon X800 XT PE (Yes I know ATI cards don't like open source, but there aren't any graphical issues bar the first moment or two while it figures out what type of card it is).

Hard drive: Seagate 80GB IDE hard drive set to master/slave (I've tried both)

I'am trying to put Ubuntu (latest version (32 bit), and even a past version 8.04 (32-bit)) on my Desktop PC, however I get two issues:

32 bit Latest edition:
I will boot from CD and install Ubuntu, however it will proceed to merely "place ubuntu without installing it" deal and bring me to the desktop with the "install" utility on the desktop. I will proceed with installing it, but after some time, Ubuntu will just lock up and do nothing (I have to hard shut down in order to restart). It locks up at different times every time. The furthest I got was at the partition manager (although its crashed at the zone selection as well). It gives no error message. Nothing!

32 bit 8.04 Edition:
Loads up. However it merely drops a shell at the root. I can get the regular "help" command to execute, but the list is too long to read (Will not fit on my screen).

So that is my information dump, currently I am downloading 64 bit edition (latest) from a mirror. I will give that a try, but I doubt that it will work. I enjoy working in the Ubuntu platform, and I hope to get it running on my desktop. Any help would be appreciated.

-Andrew

---

### Post by Ripose on 2009-01-02
Try the install SAFE MODE option. Then try to update your video driver(s).

Is the HD partitioned & formatted already? (screwed up Windows partition?)
What monitor are you using?

Run Ubuntu from the CD and try Gparted.

BTW The K desktop causes problems like this, but then again you said you are using Ubuntu.

---

### Post by verex on 2009-01-02
What kind of CDs are you using? If CD-RWs (rewritable) this could be the problem. 

I recently had odd problems just after purchasing new PC and started to think that hardware is the problem. Tried many from the latest distros and most can't  install showing different errors. Almost give up Linux (for this PC) when somewhere met that rewritable CDs could be the culprit.

Sure enough the first normal CD made smooth installation.

---

### Post by AndrewEgel on 2009-01-02
> Try the install SAFE MODE option. Then try to update your video driver(s).
Tried this in safe graphics mode (I think thats what your suggesting). No luck

> Is the HD partitioned & formatted already? (screwed up Windows partition?)
I partitioned it in windows using disk management as ntfs, then deleted the partition, and it marked it as unallocated space.

> What monitor are you using?

HP w2007 Monitor (Wide screen). I think i'll try my old CRT monitor in just a moment and see if that fixes any graphical issues.

> Run Ubuntu from the CD and try Gparted.

From what I can discern (from a few tests last night) the partitioner finishes, it just got hung up on copying a file.

> What kind of CDs are you using? If CD-RWs (rewritable) this could be the problem.

I recently had odd problems just after purchasing new PC and started to think that hardware is the problem. Tried many from the latest distros and most can't install showing different errors. Almost give up Linux (for this PC) when somewhere met that rewritable CDs could be the culprit.

Sure enough the first normal CD made smooth installation. 

Im using CD-Rs (Philips, maybe I'll try something else). Funny you should mention this now... Just last night I tried using Ubuntu 8.10 64 bit. It started installing, then gave me an error message that it could not copy over a help file (That stopped the installation entirely), that might have been due to a bad disk (try burning it at a slower speed), or a bad CD/DVD drive (Im using it in a CD/DVD+RW drive)... hmm im no expert at CDs and DVDs, but could that lead to issues? In either case I think i'll try a new media to bur on. Thanks for the suggestion.

---

### Post by AndrewEgel on 2009-01-03
Okay so I've tried different media with both versions  of ubuntu. This time around the install went all the way in. However three minutes into the new install Ubuntu locked up. So this is a hardware issue with linux. I also downloaded openSUSE and tried installing that. Same issues: it locks up during installs at different times.

I ran openSUSE firmware check, and it reported something about a hole in my RAM (Apeteur? No idea what this means). So I guess I'm asking the linux community: Is my system just too outdated to run linux?

---

### Post by verex on 2009-01-03
> **AndrewEgel said:**
> I ran openSUSE firmware check, and it reported something about a hole in my RAM (Apeteur? No idea what this means). So I guess I'm asking the linux community: Is my system just too outdated to run linux?

No, Linux can run at far more ancient machines. 

May be you can try some tests like memtest86+ (for more rounds), etc. to check for errors in the hardware. If everything is OK ask a friend to burn CD on 100% trouble-free burner. At the end of the day this could turn out to be the difficulty.

Good luck!

---

### Post by dtrot55 on 2009-01-03
You could try re-burning the cd at a slower speed...instead of 48x try like 4x ... or use something liek partition magic and format that space you allocated for ubuntu again and try again...also there is a slight possibility that you could have a bad sector or something on that part of the disc that could be causing issues...just a thought...if you have a sea gate hard drive throw in the disk utility cd that came with it and run diagnostics just to check...doesn't hurt found out my hard drive had like 800,000 erros...ran a HD maintenance program and hard drive runs perfectly.

---

### Post by duds2008 on 2009-01-03
Have you tried disabling acpi?

---

### Post by kybKenny on 2009-01-03
In order to rule out the burning issues, you could try installing from an USB-stick (via **[http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")** for instance).
That is, if your system can boot from USB.

---

### Post by AndrewEgel on 2009-01-03
Great suggestions guys. I want to try all of them.

dtrot55-

Its a 3 year old HDD, and it never came with any CD. I'm assuming however your referring to a seagate utility that I could get either off of seagate's website or off of ultimate boot disk? If so which utility were you referring to? In either case I guess I'll run all of them + CHKDSK.

---

