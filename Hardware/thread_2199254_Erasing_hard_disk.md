---
title: "Erasing hard disk"
date: 2014-01-13
forum: Hardware
---

### Post by user1397 on 2014-01-13
So my laptop finally died (mobo, screen, charger port all went bad) so I decided to take it apart so I could at least retrieve the hard drive because I wanted to wipe it clean so that none of my data is on it anymore.

I took some pictures of the hard drive so you guys can see what it looks like.

I'm pretty sure the connection is some sort of PCI connection, but I wonder if I unscrew that bottom part if there will just be a SATA port which I could technically connect to my desktop?  It does say SATA on the label, so I know that much.  But I'm not sure if it's compatible with a desktop's SATA connection.

And the reason I haven't unscrewed that bottom part is because I don't have that type of screwdriver (yet) :P

---

### Post by CharlesA on 2014-01-13
[s]2.5"[/s] Laptop drives usually have microSATA ports, you would need to get an adapter ([like this]("http://www.monoprice.com/Product?seq=1&format=2&p_id=7640&CAWELAID=1329454714&catargetid=320013720000010928&cadevice=c&cagpspn=pla&gclid=CLrb3Iiy-rsCFcVFMgodhEQAuA")) to connect it to a desktop.

---

### Post by PJs Ronin on 2014-01-13
I find the best way of preventing access to old hard drives is targeted use of an 18" screwdriver and a claw hammer.   Apply one to the other and punch a hole through that lil sucker.

---

### Post by mips on 2014-01-13
> **ubuntuman001 said:**
> 
I took some pictures of the hard drive so you guys can see what it looks like.

I'm pretty sure the connection is some sort of PCI connection, but I wonder if I unscrew that bottom part if there will just be a SATA port which I could technically connect to my desktop?  It does say SATA on the label, so I know that much.  But I'm not sure if it's compatible with a desktop's SATA connection.

Those are standard SATA & Power connectors, it works just fine on a desktop. Sata cable goes to the small connector and the power connector goes to the bigger connector.

The connectors on 2.5" & 3.5" SATA drives are identical and interchangeable so go ahead and hook it up to your desktop.

Modern hard drives have a built in secure erase feature built into the ata controller/firmware.
See [https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase](https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase) to use the feature. Lot of text there which might look daunting but it actually boils down to only a few commands.

---

### Post by mips on 2014-01-13
> **CharlesA said:**
> [s]2.5"[/s] Laptop drives usually have microSATA ports, you would need to get an adapter ([like this]("http://www.monoprice.com/Product?seq=1&format=2&p_id=7640&CAWELAID=1329454714&catargetid=320013720000010928&cadevice=c&cagpspn=pla&gclid=CLrb3Iiy-rsCFcVFMgodhEQAuA")) to connect it to a desktop.

Laptops generally use 2.5" drives with standard SATA connectors as found on their bigger 3.5" brothers.

In the case of some ultrabooks & netbooks where 1.8" drives/SSDs are used the interface will be a microSATA connector.

The above holds true for SATA devices only.


On older PATA devices the 1.8" drives use a 'zif' connector, the 2.5" drives use a 44-pin 'mini-ide' connector and the 3.5" drives use a standard 40-pin 'ide' connector.

---

### Post by CharlesA on 2014-01-13
Well that's good to know. I must have been thinking of those slimline DVD drives, which pretty much force you use to mSATA because they are so small.

Thanks!

---

### Post by MrMichaelHill on 2014-01-13
> **PJs Ronin said:**
> I find the best way of preventing access to old hard drives is targeted use of an 18" screwdriver and a claw hammer.   Apply one to the other and punch a hole through that lil sucker.


+1 to that!

[http://www.networkworld.com/news/2011/042511-google-hard-drive-shredding.html](http://www.networkworld.com/news/2011/042511-google-hard-drive-shredding.html)


:P

---

### Post by Wray on 2014-03-01
[IMG]http://ubuntuforums.org/images/ubuntu-VB4/misc/quote_icon.png[/IMG] Originally Posted by **PJs Ronin** 					[[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=12898999#post12898999") 				
 				I find the best way of preventing access to old  hard drives is targeted use of an 18" screwdriver and a claw hammer.    Apply one to the other and punch a hole through that lil sucker.
=======================================================
But then it would not be very useful as a donation, would it?[-X

---

### Post by sudodus on 2014-03-01
> **mips said:**
> Those are standard SATA & Power connectors, it works just fine on a desktop. Sata cable goes to the small connector and the power connector goes to the bigger connector.

The connectors on 2.5" & 3.5" SATA drives are identical and interchangeable so go ahead and hook it up to your desktop.

Modern hard drives have a built in secure erase feature built into the ata controller/firmware.
See [https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase](https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase) to use the feature. Lot of text there which might look daunting but it actually boils down to only a few commands.

+1

If you cannot reuse it yourself, wipe it and give it to someone who needs it!

See [this link for tips how to wipe it with hdparm]("http://ubuntuforums.org/showthread.php?t=2124829&p=12555068#post12555068")

---

