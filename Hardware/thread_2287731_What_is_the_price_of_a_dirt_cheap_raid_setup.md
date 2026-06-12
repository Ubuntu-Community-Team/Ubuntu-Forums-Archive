---
title: "What is the price of a dirt cheap raid setup?"
date: 2015-07-21
forum: Hardware
---

### Post by Higgins909 on 2015-07-21
I go into daydreams about raid sometimes and how I'm too poor to get it and have to tough it out on my mixed drives.
But how it sounds so nice to have better data protection.

Say you have some basic server hardware already going.
How much would it cost to get some drives + raid card to get into raid 4 5 6 10 but as cheap as possible, maybe going used/refub and a minimum capacity of 500gb?
(yeah that's low.. 1tb sounds better)
     (I only remember raid 1 at this point)(I'm pretty much starting up a virtual datacenter lol and it's wearing me out today)

Thanks,
Higgins909

---

### Post by weatherman2 on 2015-07-21
I can afford a RAID but don't bother with one.  I protect my data with regular backups on multiple devices.  RAID (mirror) only protects against hard drive failure.  It doesn't protect you against file system corruption, accidental erasure, or infection (if by chance your data is accessible by even one Windows client, your data is vulnerable to being destroyed by a nasty infection).

RAID mirror probably makes sense for only a server where the data is changing quickly and often.  If your data changes a few times a day, you probably don't need a RAID - you need a backup a few times a day, perhaps with rsync.  Even if you have one, you still need a reliable backup system.  I would invest extra money in redundancy, not RAID hardware, if I were worried about the cost.  And I wouldn't buy used/refurbished hard drives myself for important data.

If money was any sort of consideration, I'd go with a software RAID and not bother with a RAID card.

---

### Post by SeijiSensei on 2015-07-22
I prefer software RAID 1 over all those options.  Only requires two drives.  For about $100 you can buy a pair of 1 TB drives like this one:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822236339](http://www.newegg.com/Product/Product.aspx?Item=N82E16822236339)

Just install them in the box, then use the software RAID manager, [mdadm]("https://raid.wiki.kernel.org/index.php/RAID_setup#Create_RAID_device"), to create the array.  Format it as ext4 and mount it via /etc/fstab.  You're good to go.

Remember, though, that "RAID is not a substitute for backups."  I can attest to the truthfulness of this statement from unfortunate personal experiences!

---

### Post by Higgins909 on 2015-08-02
Kinda reopening this...  I think I would want to go for something more like a raid 4 5 6 10 (still don't remember the things)
have 3+ drives but the thing is I don't got enough sata ports if I do 4+
I've got pcie x1 and x16 at x4 speeds... but I mainly worry about compatibility with ubuntu server.
edit: I mean software raid too

---

### Post by SeijiSensei on 2015-08-02
Buy a [SATA controller](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007607&IsNodeId=1&srchInDesc=SATA%20CONTROLLER&bop=And&ActiveSearchResult=True&Order=BESTMATCH).  

If you're wondering about Linux compatibility, there's a card on that page for $15 that other customers report works with Linux.

Software RAID is part of the Linux kernel.  It will work on any Linux system.

---

### Post by Yellow Pasque on 2015-08-02
Why do you want RAID? Do you plan to run the root system on it? An SSD might be a better idea for the root system (you can get a 64GB model for the root system for $40 or less...)

If you just want RAID performance cheaply, get two 500GB drives and a 1TB backup drive. ($120

If you're going to use 3 or more drives, RAID 5 seems ideal. You can survive the loss of a single drive and replace it, though it's not completely foolproof because you still have to rebuild the array, and an error while doing that means you lose all your data. Obviously, you will still need backups to cover rebuilding errors and data loss not caused by drive failure.

> Buy a SATA controller.
Unless there are not enough ports on the mobo or one is going to get a hardware RAID card, this doesn't seem necessary to me, and might not be economical if the OP wants more than a 2 drive array.

---

### Post by Higgins909 on 2015-08-17
If I have to buy a sata/raid controller then should I just go for raid?

I was looking at $50~ syba cards in some pcie 1-4 fashion.
Decided on raid 10 for performance or something over 4 5 6.
No idea when I will commit to doing this, but I'm getting sick of my 1tb not doing much (mainly backups) and my 3 small drives doing all the work slowly...
plan to keep one of the drives... the sata one that is boot right now and put what I can on the raid 10 and take the 1tb and format for my windows and use to backup and then store the drive away.
(currently working on the 1tb to windows, my filesystem is a mess right now)

---

### Post by Yellow Pasque on 2015-08-18
Again, an SSD seems like a much better solution to use for the boot/root device if you want performance. You should be able to install both Linux and Windows on a 120GB SSD. (example: [http://www.phoronix.com/scan.php?page=article&item=pny-cs1211-ssd&num=1](http://www.phoronix.com/scan.php?page=article&item=pny-cs1211-ssd&num=1) ). As for the bulk of your data, it would depend on what exactly it is. For me, the bulk (in terms of filesize) of my non-root/system data is media, and I don't change/write the data very often. RAID 1 makes sense for that sort of usage if you only have 2 drives/ports.

It doesn't seem like a good idea to get another small drive and a $50 SATA card when you can get another 1TB drive and an SSD for $120 or so.  I guess it's not "dirt" cheap, but the performance of an SSD is going to run circles around mechanical disks in RAID. Also, two 1TB drives in RAID 1 = 1TB usable space, while four 300GB drives in RAID 10 would be 600GB.

---

### Post by Bucky Ball on 2015-08-18
You could install Ubuntu and Windows on a 60 or 80Gb SSD if you are keeping your personal data on another drive. You wouldn't need to go to 120Gb.

---

### Post by Higgins909 on 2015-08-18
I don't want to get a ssd as I know I will tear it up and raid is terrible for em.
I would one day like a ssd for the boot drive... one day. (when I feel like spending the money)
But right now on 1hdd I have the VM host and 3 VM on it.  They all boot from it and swap on it.
I  then have 2 other drives that are split up for 2 of the VM. 2 qcow2  virtual drives for each VM I got a real 200gb and 80gb. each have a 50gb  proxy qcow2 disk on em and then the rest is used by samba with some to  spare for VM host.

I want to get raid to speed up their cache and boot times without breaking the bank and destroying ssd's
My mobo has sata 2 only and not sure on the raid off hand but I know it has it.
2 1tb for about $50 each sound good.
didn't realize raid 10 was that bad on storage.
$50 + 4 used $20 hdd vs 2 1tb using onboard sata 2 raid? the latter is cheaper but is it as good?

Not sure what I said but I'm not currently dual booting anything.
was taking my 1tb off server and putting on windows for permanent archive use.  I find I rarely use it and am just burning its life and power away.  I originally backed all of its stuff onto my new windows 1tb and then put the usb 1tb back on the server and then made a virtual drive on it to work with my VM samba.... then I decided not to and during that process made a mess of my filesystem.

ssd is a further priority... I'd like to get a new psu as im sure the one I got is trash as it runs so hot vs my new corsair 430m. then a UPS would be nice then more ram as 4gb with a bunch of VM isn't much... still waiting for the moment I get to buy my first vehicle... thats why I don't want to buy anything. But if I get this raid setup I could put the drives back in the old server I ripped them out of and sell it and probably cover the cost of the new 1tb drives.  Dang my rambling.

---

