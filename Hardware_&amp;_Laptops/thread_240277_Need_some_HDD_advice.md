---
title: "Need some HDD advice"
date: 2006-08-20
forum: Hardware &amp; Laptops
---

### Post by fatsheep on 2006-08-20
I've got a DFI motherboard and a IDE Hard drive, both work fine.  However, I'm running out of space on my HDD so I'm looking into upgrading to a SATA 3GB/s drive:

[http://www.newegg.com/Product/Product.asp?Item=N82E16822135106](http://www.newegg.com/Product/Product.asp?Item=N82E16822135106)

And I'll need a SATA controller for it but I'm worried about compatibility issues:

[http://www.newegg.com/Product/ProductList.asp?N=2010150410+1193212547&Submit=ENE&SubCategory=410](http://www.newegg.com/Product/ProductList.asp?N=2010150410+1193212547&Submit=ENE&SubCategory=410)

Which SATA controllers would you recommend to me?  I really would hate to get my new hard drive and find out that the controller is incompatible...

---

### Post by gerbman on 2006-08-20
I ordered [this]("http://www.newegg.com/Product/Product.asp?Item=N82E16816132006") PCI SATA controller last Friday. It should be here either tomorrow or Tuesday. I'll let you know how it works. :)

---

### Post by fatsheep on 2006-08-20
Ok thanks, I await your review. ;)

---

### Post by neouser99 on 2006-08-21
> **fatsheep said:**
> I've got a DFI motherboard and a IDE Hard drive, both work fine.  However, I'm running out of space on my HDD so I'm looking into upgrading to a SATA 3GB/s drive

maybe there are other reasons for doing this, but if you are going to go this far why don't you just upgrade the motherboard. the cost of a 'good' controller is about as much or more then the cost of a good mobo that has both one/two ide channels and >2 sata 3.0 ports. just my $.02.

on the other hand, if you do get one of the 'good' sata controllers, the ones that are >$40, they usually have excellent support, as large fileservers and the sort run these types of setups. plus, if you are looking at doing raid, this makes it a pure hardware raid which is better than software as it takes unneeded stress of the proc, and it is also faster.

-neo

---

### Post by fatsheep on 2006-08-21
I don't want a really expensive upgrade right now, just some more space.  I'd be willing to stick with IDE actually if a good SATA controller is too expensive...

---

### Post by John.Michael.Kane on 2006-08-22
fatsheep could you give the spec's of the machine? 

I would stick to ide drives if thats what was in to machine, and switch to sata only if it came with the board. 

neouser99 has a point once you go over 60-70$. might aswell plan a semi full upgrade provided you can use most of the othe parts.

---

### Post by fatsheep on 2006-08-22
AMD 64 3000+ (Skt 939)
XFX Nvidia 6600 GT (PCI-E)
1 GB Patriot XBLK Memory

---

### Post by gerbman on 2006-08-22
> **fatsheep said:**
> Ok thanks, I await your review. ;)The SATA controller I linked to works fine. I have software RAID-1 up and running with no hacks or additional drivers. However, it's a little bit slow...not terrible but I can notice it. Right now I have all partitions being mirrored, and I'm going to try mirroring just my home and aux storage partitions, that might help the speed issue. But it works.

---

### Post by John.Michael.Kane on 2006-08-22
fatsheep i have the same setup sans XFX Nvidia 6600 GT (PCI-E) i'm using onboard graphics. 

The only issue you will have with card posted by gerbman is that it downgrades your drives to Transfer Rate of 150MB/Sec if they are sata2. if this ok with your needs then your good to go.

However.if your seeking SATA II/sata3Gbps then you will have to find a card that supports that transfer rate, and is linux compatible.

Sidenote: you could always just get the biggest ide drive in your budget..

---

### Post by gerbman on 2006-08-22
> **gerbman said:**
> The SATA controller I linked to works fine. I have software RAID-1 up and running with no hacks or additional drivers. However, it's a little bit slow...not terrible but I can notice it. Right now I have all partitions being mirrored, and I'm going to try mirroring just my home and aux storage partitions, that might help the speed issue. But it works.Not mirroring the / partition helps the speed issue a great deal. If you only care about backing up your data (mirroring home and other storage) this solution seems to work just fine. Good luck.

---

