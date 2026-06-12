---
title: "[SOLVED] Mobo RAID vs. Ubuntu RAID ?"
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by BassKozz on 2008-01-13
I am building a new rig, here are the spec's I've come up with so far:
**_Case_**: [Antec P180]("http://www.newegg.com/product/product.asp?item=N82E16811129154")
**_CPU_**: [Q6600]("http://www.newegg.com/product/product.asp?item=N82E16819115017") (OC'ed to 3ghz using [Thermalright Ultra-120 Extreme]("http://www.newegg.com/Product/Product.aspx?Item=N82E16835109140"))
**_MoBo_**: Still undecided (will probably go with P35 chipset to save $$$)
**_Ram_**: 2x [G.SKILL DDR2 800 (PC2 6400) 4GB kit (2x2GB)]("http://www.newegg.com/product/product.asp?item=N82E16820231122") [8GB total]
**_HDs_**... **OS**: [WD Raptor 150GB]("http://www.newegg.com/product/product.asp?item=N82E16822136012") / **Storage**: 3x [WD Caviar 750GB]("http://www.newegg.com/product/product.asp?item=N82E16822136131") (RAID5) [1.5TB of storage]

I will Dual Boot this rig with WinXP 32-bit, and Ubuntu 64-bit OS's (I am trying to phase out M$ completely, so it will mainly be used for Ubuntu), I am using the 64-bit version of Ubuntu so that I can use >4GB of ram.  I will mainly be using Ubuntu to Virtualize other OS's (i.e. XP, Vista).  This will mainly be a workstation and won't be used for gaming.

Anyways, I want to run the 3x750GB HD's in a RAID 5 array for Storage, and I was wondering if I should run this Array from the MoBo's BIOS (meaning I would purchase a Mobo with RAID 5 support and setup the array via the MoBo's Bios).  Or if I should run a software "mdadm" array in Ubuntu.

Obviously one of the downsides to creating the array in Ubuntu would be that I couldn't use it when I booted to WinXP, but leaving that issue aside (for the purposes of this thread):[LIST=1]
[*]Which would give me better performance?
I realize that both of these options are "software" raid, but which one will work better (less cpu useage, and better I/O)?
[*]Also would it be possible to expand the array using the Mobo's bios (because I know I can do this in Ubuntu)? 
For example if I wanted to add a 4th 750GB drive thus bumping my total storage to 2.25TB.
[/LIST]

Also am I forgetting anything else, any other issues that may arise using either scenario?
REMEMBER the 150GB Raptor will **_NOT_** be in an array, so there won't be an issue their.

Thanks in advance for any/all comments,
-BassKozz

---

### Post by BassKozz on 2008-01-13
:BUMP:

Is this question not worded right?
Can someone give me some input so I can better phrase my question?

---

### Post by kubug on 2008-01-13
Hi BassKozz,

from my experience (and having a P35 mobo myself) go for software raid (mdadm). Simply because all the chipsets integrated on the motherboard are "software" raid (fakeraid) anyways, so there will be no performance difference. 

The only difference you will feel is in the install. Getting dmraid (driver for fakeraid) working is somewhat tricky. I did get mine working for a Dual Boot and RAID 0 with dmraid, but it took me way too long to get it all working right.

Software RAID with mdadm is much more simple (if you understand the concept) and I have setup a few systems like that.

Now, the only thing to be aware of is that RAID 5 is not very good for write speed. On one of my setups I have 3x 500GB (soon to add another) drives, which can do ~100MB/sec each. When I had them do RAID 0 they got around 320MB/s, which was awesome. As soon as I switched them to RAID 5, they only did ~55MB/s. It is the parity calculation that makes it so slow. 

If you need better performance you may want to look at RAID 1+0, but you loose more space. It's up to you.

---

### Post by kubug on 2008-01-13
Oh, I forgot.... on the other hand if you want Windows to access the RAID storage, give dmraid a shot. I know the P35 chipset was just getting somewhat stable with the latest 1.0.0.RC13 of dmraid (at least that was my experience).

---

