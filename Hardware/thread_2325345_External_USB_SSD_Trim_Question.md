---
title: "External USB SSD Trim Question"
date: 2016-05-21
forum: Hardware
---

### Post by 11Cats on 2016-05-21
I'm running 14.04 Trusty. 

I have 3 older SSD's in external USB HD enclosures that I use for backups/files. They are always plugged in to my desktop, and my system runs 24/7.

My question is: is trim automatically enabled for external SSD's? If not, I would like to set it up as a cron job. What I have been doing so far (just in case it is not automatic) is changing directory (CD) to each SSD in turn and issuing the **[COLOR=#0000FF][FONT=Arial]sudo fstrim -v /[/FONT][/COLOR]** command hoping that covers it.

---

### Post by mc4man on 2016-05-21
You cannot trim usb ssd drives. You'll need to leave garbage collection to the drives themselves. To run trim on those drives you'd need a sata connection

---

### Post by 11Cats on 2016-05-21
> **mc4man said:**
> You cannot trim usb ssd drives. You'll need to leave garbage collection to the drives themselves. To run trim on those drives you'd need a sata connection

OK, thanks. Do they actually do the garbage collection themselves, freeing me from concerning myself with this? If the make/model matters: One is a Samsung 830 series, one a Samsung PM810, one a Plextor from 2013.

---

### Post by sudodus on 2016-05-21
Trim is possible even with a USB pendrive, as described in the following link

[https://www.kingston.com/datasheets/DTWS_us.pdf](https://www.kingston.com/datasheets/DTWS_us.pdf)

> SPECIFICATIONS
>
Capacities
2
 32GB, 64GB, 128GB* (*build to order)
>
Speed
3
&#8226;  Max Sequential Read/Write speeds: 250/250 MB/s 
&#8226;  Sustained Random 4k Read/Write: 3,750/9,800 IOPS 
&#8226;  PCMARK® Vantage HDD Suite Score: 22,250
>
[COLOR="#0000FF"]**Supports TRIM**[/COLOR] and S.M.A.R.T commands
>
Dimensions 
75.29mm x 22.98mm x 16.44mm
>
Operating Temperature 
32°F to 140°F (0°C to 60°C)
>
Storage Temperature 
-4°F to 185°F (-20°C to 85°C)

I think you must check the specifications of the SSDs and the external boxes for each of your external drives to find out if they support trim.

-o-

An alternative is to connect your SSDs via eSATA, for example with this rather simple and cheap adapter: [2 Port SATA to eSATA Slot Plate Bracket](https://www.startech.com/Cables/Drive/eSATA/2-port-SATA-to-ESATA-Slot-Plate-MF~ESATAPLATE2)

---

### Post by 11Cats on 2016-05-21
> **sudodus said:**
> Trim is possible even with a USB pendrive, as described in the following link

[https://www.kingston.com/datasheets/DTWS_us.pdf](https://www.kingston.com/datasheets/DTWS_us.pdf)



I think you must check the specifications of the SSDs and the external boxes for each of your external drives to find out if they support trim.

-o-

An alternative is to connect your SSDs via eSATA, for example with this rather simple and cheap adapter: [2 Port SATA to eSATA Slot Plate Bracket]("https://www.startech.com/Cables/Drive/eSATA/2-port-SATA-to-ESATA-Slot-Plate-MF~ESATAPLATE2")

OK, first with the trim: I had found this (from here:[https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Only-for-computers-that-are-always-on:-daily-by-cron):](https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Only-for-computers-that-are-always-on:-daily-by-cron):)

[COLOR=#000000][FONT=Arial]Then type in the terminal (use copy/paste):[/FONT][/COLOR]
[COLOR=#0000FF][FONT=Arial]gksudo leafpad /etc/cron.daily/trim[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Press Enter.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Copy/paste the following blue text into that empty text file:[/FONT][/COLOR]

[COLOR=#0000FF][FONT=Arial]#!/bin/sh
# call fstrim-all to trim all mounted file systems which support it
set -e
#
# This only runs on Intel and Samsung SSDs by default, as some SSDs with
# faulty firmware may encounter data loss when running fstrim under high I/O
# load (e. g.  [https://launchpad.net/bugs/1259829](https://launchpad.net/bugs/1259829)). You can append the
# --no-model-check option here to disable the vendor check and run fstrim on
# all SSD drives Like this (remove the hash):
#exec fstrim-all --no-model-check
exec fstrim-all[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]Save the text file.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]d. Now copy/paste the following command into the terminal, in order to make the file executable:[/FONT][/COLOR]
[COLOR=#0000FF][FONT=Arial]sudo chmod +x /etc/cron.daily/trim

[/FONT][/COLOR]This seems to indicate that any mounted SSD that can trim, will trim when the cron item is executed, but I wasn't sure if it would take for USB SSD's.

Now, onto the point about going from USB to SATA. I want to do that, but I have read that whether or not that will work depends on the motherboard. My computer is a Dell Optiplex 7010. I've tried to find it out for my desktop, but have not been able to confirm or deny it will work. And ... Sorry if this is a dumb question ... how would the SSD be powered with that set up in your link? Drives have the eSata and power wires when installed internally.

---

### Post by 11Cats on 2016-05-21
**sudodus: **I just realized the eSATA in your link was the kind that used 2 other eSATA internal connectors - I thought you meant this type: [https://www.amazon.ca/StarTech-com-PEXESAT322I-Express-eSATA-Controller/dp/B00952N2DQ/ref=sr_1_1?ie=UTF8&qid=1463861671&sr=8-1&keywords=external+sata+card](https://www.amazon.ca/StarTech-com-PEXESAT322I-Express-eSATA-Controller/dp/B00952N2DQ/ref=sr_1_1?ie=UTF8&qid=1463861671&sr=8-1&keywords=external+sata+card)

I don't have any free eSATA connectors in my desktop, so I had considered using the PCI Express SATA in the above link - that is the type I'm not sure will work with my computer. But I still don't understand how the SSD (or HD) would be powered this way.

---

### Post by sudodus on 2016-05-21
There are external boxes with separate power input either directly from the power grid or via USB. I would suggest separate power input to the external box(es).

Maybe this is an alternative: [http://www.icydock.com/goods.php?id=142](http://www.icydock.com/goods.php?id=142)

---

### Post by 11Cats on 2016-05-21
> **sudodus said:**
> There are external boxes with separate power input either directly from the power grid or via USB. I would suggest separate power input to the external box(es).

Maybe this is an alternative: [http://www.icydock.com/goods.php?id=142](http://www.icydock.com/goods.php?id=142)

OK, I see how that works now for the power. That looks like the perfect solution for me, now I just have to figure out whether or not my Dell Optiplex 7010 can make use of the PCI Express SATA cards as I've read some motherboards can, some can't.

---

### Post by oldfred on 2016-05-21
It was my understanding that you have to have AHCI on for trim to work. And AHCI is not used for USB external drives.
It may be used for the eSATA drives.

Supports trim is not the same as doing its own trim.

---

### Post by .Ricky. on 2016-06-07
Hello all,

I have a similar issue - not sure whether I should open a new thread instead.

Currently my laptop runs Ubuntu 16.04, and my external HD (connected via USB 3.0) is living its last days.

I thought about switching to an SSD external drive, however I am unsure about this TRIM issue.

Is there any particular make or model I should look at? Or are there going to be problems regardless of which SSD I buy? In this case, would TRIM work or not at all, if I connect the SSD via USB 3.0?

Thanks

---

### Post by oldfred on 2016-06-07
New SSDs have there own internal ways to manage things.
Not sure which models, someone else may.

---

### Post by yoshii on 2016-06-07
I hope I'm not disturbing this conversation.  I wanted to mention that the filesystem type selection I think also has some effect upon TRIM/garbage collection.  
As I understand it, ext4 has some minor built-in support for this type of thing, but I don't know how sophisticated it is or how it is activated or if it's automatic.  
But I remember reading about it.  The information is somewhere on the internet.  Also, I don't remember if it's also active for say ext2 or ext3 drives mounted via ext4 since ext4 is backwards compatible.  As far as I know, FAT32, which is used for most flash drives doesn't have any TRIM/garbage collection support.  And yet this is how most flash drives are used.  But if you are using an SSD or similar you could benefit from having an ext4 based OS and/or an ext4 formatted drive or partition.  

But this stuff is worth finding out if you guys want to know.

---

