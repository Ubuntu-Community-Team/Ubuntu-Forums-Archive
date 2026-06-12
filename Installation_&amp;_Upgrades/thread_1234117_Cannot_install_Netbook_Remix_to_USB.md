---
title: "Cannot install Netbook Remix to USB"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by littlestpretzel on 2009-08-07
What I would like to do is install Ubuntu Netbook Remix to a USB and then be able to boot from there whenever I want while still keeping the Windows side of by netbook the same. I have been playing with it for a while and cannot find Create USB Startup or USB install that some people refer to. Can someone either give me a somewhat simple (new user here) alternative or a way to get/find the USB install that should have come with it? 
Thanks.

---

### Post by Mighty_Joe on 2009-08-07
Did you follow the link on the  [UNR download page]("http://www.ubuntu.com/GetUbuntu/download-netbook") that tells you how to [use the UNR IMG file]("https://help.ubuntu.com/community/Installation/FromImgFiles")?

---

### Post by littlestpretzel on 2009-08-07
Yes, I can get the main Ubuntu menu and have the option to install but that is only to install onto my existing hard drive, not the USB. But there is a good chance that I am missing something.

---

### Post by Mighty_Joe on 2009-08-07
Ah!  I see what you are saying.  You can boot up the UNR install on a USB drive, but you want to install it to the same disk you booted from.  
This is just wild speculation on my part, but can you boot up using another USB drive?  I believe UNR will not let you install to the boot device (I don't have a netbook handy to test with).

---

### Post by littlestpretzel on 2009-08-07
That actually makes a lot of sense. So lets say I get a second USB, plug it in. What will I do from there? Will I be able to go in to the install menu and choose between the USB and the hard drive?? I will give it a try and see what happens. 
Thank you so much for your help!

---

### Post by Mighty_Joe on 2009-08-07
Let us know if it works.  It's just my wild guess at this point.

---

### Post by pofadda on 2009-08-07
I have an Acer Aspire One for a while and want to do this same thing: install Ubuntu to a USB so as not to mess with the Linpus OS on it.  Not understanding that the .img is a .iso but bigger I now see that I too need to install the full OS from the remix .img so I need to know:
[LIST]
[*]has anybody actually done this?
[*]how big is Ubuntu when installed on a HDD?  This is aat least how big the stick will need to be...
[*]has anything been done to reduce/control the OS's file updates while it runs so as to reduce the rate at which the USB stick will wear out from too many file writes?  Puppy Linux does this but I want Ubuntu instead.
[/LIST]  
This is going to be fun (or frustrating, leading to LTSFL** rage)!

Pofadda.
**Life's Too Short For Linux

---

### Post by Mighty_Joe on 2009-08-09
> **pofadda said:**
> I
[LIST]
[*]has anybody actually done this?
[/LIST]


Install Ubuntu?  Sure.  I'm typing from an 8GB flash drive with Kubuntu installed.  See [my post here]("http://ubuntuforums.org/showpost.php?p=7497700&postcount=4") for links to some install and config instructions I found to optimize a flash install.  It takes a little more than 2Gb.

---

### Post by GeorgeVita on 2009-08-09
Hi **littlestpretzel**,
before installing to the removable media, check if it is fast enough and think about using SD or SDHC cards that may fit "inside" the card reader (if your netbook has one) and cannot removed accidentally.

My Speed Check: [http://acomelectronics.com/GeorgeVita/Gdsk_bnch.txt](http://acomelectronics.com/GeorgeVita/Gdsk_bnch.txt)
Graph: [http://acomelectronics.com/GeorgeVita/extPoll.jpg](http://acomelectronics.com/GeorgeVita/extPoll.jpg)

Also add me to those running from HD, USB and SDHC full installations (running on EeePC 1000H) and Puppy 4.21 from a microSD card installed into my 3G modem (ZTE MF636) forming a "Linux on 3G stick!".

I would like to add a warning: When installing Ubuntu you must take care about partitioning (GParted) and where will be the Grub boot manager. **You must NOT format any wrong drive and Grub should be placed to your external removable media and not to the default sda hard disk!**

See attached pictures:
[w1.png]("http://acomelectronics.com/GeorgeVita/w1.png")
At "Prepare disk space" you must choose your removable media with "Erase and use the entire disk". A wrong selection here may result to a lost Hard Disk!

[w2.png]("http://acomelectronics.com/GeorgeVita/w2.png")
When "Ready to install", click "Advanced" to choose the right position for the boot loader

[w0.png]("http://acomelectronics.com/GeorgeVita/w0.png")
Choose your removable media to place boot loader and NOT the default sda!

Some users are first removing (physically) the Hard Disk, then boot from the removable media and install to the other removable media. Always you must recognise where is which media (checking total size or volume label).

A note about "life expectancy" for the media (read/writes): As Ubuntu has a new release every 6 months and the next UNR version comes after 2 1/2 months do you feel that you will keep your installation for a long period to test data integrity?

Another similar thread: [http://ubuntuforums.org/showthread.php?t=1179595](http://ubuntuforums.org/showthread.php?t=1179595)

Regards,
George

---

