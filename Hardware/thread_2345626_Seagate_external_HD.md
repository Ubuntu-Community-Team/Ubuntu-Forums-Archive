---
title: "Seagate external HD"
date: 2016-12-06
forum: Hardware
---

### Post by linden-e on 2016-12-06
I intend to buy a Seagate 5 TB external hard drive but as most queries posted on this forum clearly show that problems might be expected with this type of hardware, I first would like to make sure that it is fully compatible with** Ubuntu 14.04** (and later). Here are the hardware specifications:

Type of Hardware: 5 TB external hard drive for desktop, Interfaces: USB 3.0
Hardware Maker: Seagate
Model:Backup Plus 5 TB black high gloss 3.5 ", STDT5000200, Seagate

Also, can it be partitioned with both ext4 (for Ubuntu *) and ntfs (for Windows 10)?

Any help or advice would be much appreciated.

---

### Post by TheFu on 2016-12-06
Welcome to the forums.

Seagate has *earned* a poor reputation for reliability. Be very, very careful deploying those drives. The corporation has a history of denying design flaws too.  Be very careful.  I know it is hard to justify the extra costs for other vendors, until the disk fails and $20 doesn't seem like much anymore.

For your consideration: [https://www.backblaze.com/blog/hard-drive-failure-rates-q2-2016/](https://www.backblaze.com/blog/hard-drive-failure-rates-q2-2016/) ; I'd target less than 1% failure disks for my purchase.  My last seagate failed a few months ago.  Bought 2, 1 died after 13 months, the other after 25 months. 1 yr warranty for each. I had buyers remorse 1 day after purchasing.  Running 5 other HDD brands here. NONE have failed within 5 yrs of use while most have 1, 3 yr warranties. A few have 5 yr warranties.  I need to be fair - also have some very old Seagates (320G) that are over 10 yrs old and still going strong. Something broke inside that company with the release of their 750G and larger HDDs. I was very loyal to Seagate, seeking out their HDDs.  But don't believe my anecdotal account - look at the statistics.

Most hard drives use standard interfaces.  These are supported by all OSes. Not really an Ubuntu question, since that support comes from the Linux kernel.  You'll have more issues with USB3 (if there are any issues) ports and chips.  There have been some USB3 chips that didn't work well with Linux. Don't know if those are still an issue or not. My newer system with USB3 don't show the same issues 5 yr old USB3 add-on cards displayed. Actually have a new system and older add-on card using the same USB3 chips, but the new system handles it perfectly while the older one effectively locks up the entire computer for 30-90 seconds at a time during high USB3 use.  There are a number of possible solutions - of the 4 I've tried, none have worked.  I believe it is a design flaw with that specific motherboard.

You can use MBR or GPT partition types and use any file system within those partitions that you like. Just be aware of the capabilities and limitation of those file systems.

Should go without saying but you also need a way to backup that 5TB of data.  I usually buy 2 disks at a time - a primary and a backup.

---

### Post by linden-e on 2016-12-06
Thank you very much for your thorough evaluation. From the statistics tables (both semestrial and annual), it appears that HGST drives come first with regard to reliability, followed by WDC and Toshiba (but this is just a personal impression). I will therefore inquire there for further details.

I will definitely look for possible issues with USB3. And, of course, backing up data goes without saying. 

Thank you again for your help. I am happy to be accepted on this forum.

---

### Post by linden-e on 2016-12-07
I received an offer for the following external hard disk:

Type of Hardware: 6 TB (6000 GB) external hard disk
Hardware Maker: Toshiba
Hardware Model: TOSHIBA Canvio Desk [HDWC260EK3J1]

I would be very grateful if it could also be verified for compatibility with Ubuntu 14.04.

---

