---
title: "Need more SATA ports to attach ZFS pool drives"
date: 2014-03-16
forum: Hardware
---

### Post by 65 mustang on 2014-03-16
Software:
[LIST]
[*]    I am running 12.04 LTS
[*]    ZFS kernel module added (http://zfsonlinux.org/")
[/LIST]
Problems:
[LIST]
[*]    I have ran out of SATA ports on my motherboard and need more for my ZFS drives
[*]    I do not know the correct term for the card I am looking for. It is either called "SATA port expander" or "sata port multiplier" or "SATAController Card"?
[*]    I do not know what card I should buy
[*]    I have a HighPoint RocketRAID 620 but its a pain to install and i really want something that i can just plug in and my drives will show up in gparted without tainting the kernel with binary blobs
[/LIST]
Research:
[LIST]
[*]I have found that the LSI cards advertize Linux support but i dont know if they are going to allow me to access the disks dirrectly or are going to force me to use them with its hardware raid. I want to use software ZFS. Also these seem really expencive for what i am trying to accomplish or are less expencive cards just junk?
[/LIST]

---

### Post by Yellow Pasque on 2014-03-16
> I do not know the correct term for the card I am looking for. It is either called "SATA port expander" or "sata port multiplier" or "SATAController Card"?
What you probably want is a controller card. How many drives are you looking to add? What PCI and/or PCI-e slots are available on your mobo?

> Also these seem really expencive for what i am trying to accomplish or are less expensive cards just junk?
Cards with hardware RAID controllers are going to be notably more expensive

---

### Post by 65 mustang on 2014-03-16
> **Temüjin said:**
> What you probably want is a controller card. How many drives are you looking to add? What PCI and/or PCI-e slots are available on your mobo?
I have a 16x PCI-E open and i believe it has a old PCI slot as well.  I would like to add one drive.

---

### Post by lukeiamyourfather on 2014-03-17
> **65 mustang said:**
> I have a 16x PCI-E open and i believe it has a old PCI slot as well.  I would like to add one drive.

Typically ZFS storage pools are expanded with at least two drives at a time (mirror) or more (RAID Z/Z2/Z3). If you add a single drive then what's the point of using ZFS because there will be no redundancy and thus all of the data integrity features of ZFS are a moot point (block checksums, parity RAID, mirrors).

What you're looking for is called HBA (host bust adapater) which provides no RAID functionality since ZFS doesn't need it. If you're using SATA disks then look for a SATA HBA. Most will have support in Linux out of the box with a few exceptions like HighPoint. A controller with RAID functionality will work if the drives are setup as JBOD but is not necessary and RAID controllers are typically more expensive than HBA. Something like this would do the trick but there are lots of other options out there.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16816124063](http://www.newegg.com/Product/Product.aspx?Item=N82E16816124063)

---

### Post by lukeiamyourfather on 2014-03-17
EDIT: Double post.

---

### Post by 65 mustang on 2014-03-22
[COLOR="#FF0000"]Nevermind the reviews say these are flawed chipsets and dont work with linux correctly.
[COLOR="#FF0000"]SYBA SI-PEX40062 PCI-Express 2.0 x2 Low Profile Ready SATA III (6.0Gb/s) Controller Card  **(4 port)**
[http://www.newegg.com/Product/Product.aspx?Item=N82E16816124062](http://www.newegg.com/Product/Product.aspx?Item=N82E16816124062)
SYBA SI-PEX40071 8 Internal SATA III Ports PCI-Express Card, PCI-e x2 Slot, Specification V2.0 Plus Low Profile Bracket **(8 port)**
[http://www.newegg.com/Product/Product.aspx?Item=N82E16816124070](http://www.newegg.com/Product/Product.aspx?Item=N82E16816124070)[/COLOR][/COLOR]

This is the new hotness
HighPoint Rocket 620 PCI-Express 2.0 x1 SATA III (6.0Gb/s) Controller Card 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16816115072](http://www.newegg.com/Product/Product.aspx?Item=N82E16816115072)

---

