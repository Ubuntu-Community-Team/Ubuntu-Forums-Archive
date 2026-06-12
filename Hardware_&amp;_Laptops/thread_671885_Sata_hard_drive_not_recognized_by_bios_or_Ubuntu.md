---
title: "Sata hard drive not recognized by bios or Ubuntu"
date: 2008-01-19
forum: Hardware &amp; Laptops
---

### Post by bethebunny on 2008-01-19
I just put together a new rig with a 500gb Seagate 7200.11 HDD.
Motherboard is MSI K9A2 Platinum AM2+ 790FX
Processor is an Athlon 64 x2 6400+

I have a SATA CD/DVD RW drive on the same set of Sata ports as the hard drive, which is recognized perfectly by the bios and Ubuntu, and boots the 7.10 Gutsy live cd perfectly. When I load Gparted, or try to install Ubuntu from the live cd, they don't find any drives. In desperation I tried a Vista 32 Ultimate boot disc, which starts installation but also finds no drives.

Bios has SATA controller enabled, have tried booting with IDE, AHCI and RAID RAID modes, with and without another IDE drive connected (my old comp's drive, which boots Debian perfectly but bluescreens at the XP login screen, which I am for the moment ignoring since it is most likely a missing driver or something).

When booting from the live cd without an IDE drive, there are no hd* or sd* entries in /dev. One suggestion I found while googling help forums for answers was to format the hard drive, which would be fine and dandy if Ubuntu or Debian could see it.

My current theory is that the drive is busted, but if there is anything I can try before I RMA it and have to wait a week to get my system running.

Any suggestions are welcome.

---

### Post by logos34 on 2008-01-19
> &#8226; 4 SATA II (1~4) ports by AMD® SB600
&#8226; 2 SATA II (5~6) ports by Promise® T3, support SAS ready devices, for storage devices only


try plugging hdd into ports 5 or 6.  Now does the Bios see it?

---

### Post by bethebunny on 2008-01-19
I tried one of those sata slots but I couldn't actually find anywhere in the BIOS that showed what devices were connected to them. However, I still had the same problem of the Ubuntu installer not finding any drives. I have absolutely no experience in setting up Raid controllers, so there may be a problem where I have a BIOS setting to run as a Raid or something, I'm not really sure. Regarding the last two slots, it has been an oft-voiced concern that they have issues, being on a separate raid controller, though as I was not interested in setting up a raid nor did I think I would be needing the last two SATA slots I payed them little attention.

Long story short, no, I couldn't get it to be recognized in 5/6 either.

Edit: *Awesome* sig ;)

---

### Post by logos34 on 2008-01-19
Raid should be disabled--it sometimes causes a problem.  

Until you can get the bios to see the hard disk, you can't install.

---

### Post by TJOHO on 2008-01-19
Hello,

I have a similar problem, although BIOS does recognize my drive, which is a Hitachi SATA drive.

It's in an OS-less PC I just bought, and I tried first to install Ubuntu on it. The Live CD loaded just fine but when I tried to install and got to the screen for choosing partition to install on, there were no partitions to choose from!

I figured it may have been a formatting issue, so I installed WinXP instead. The drive came with two partitions from the shop, one of which was NTFS formatted, so I installed WinXP to that and figured I would install Ubuntu to the other partition afterward.

Even after installing WinXP (which went without a hitch) the Ubuntu installation program would not recognize either of my two partitions. I just get the screen to select a partition and no partitions to select...:rolleyes:

---

### Post by bethebunny on 2008-01-19
That is an odd problem, however I too have experienced issues with the Ubuntu installer when selecting/building partitions (not just on this drive). Normally on a new drive that I'm having trouble with I'll break out my Debian Netinstall disk, which has a particularly blunt partition feature, and usually my problems are solved.

I'm now fairly positive the drive was just DOA, based on similar experiences to mine in several other forums. I'll be RMAing it later today. Thanks for all the input.

---

### Post by TJOHO on 2008-01-19
Sorry to hear you got a bad drive. 
That is not the case for me, however. WinXP works fine (as fine as WinXP can :) ).

Does a partition need a particular formatting (ext3?) to be recognized by Ubuntu? My one remaining partition is not formatted yet.

Note: Utter Linux newbie here. This was supposed to be my first foray into it.

---

