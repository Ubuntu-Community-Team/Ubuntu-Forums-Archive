---
title: "Quick Question: Adding a new HDD (SATA)"
date: 2010-03-14
forum: Hardware
---

### Post by thegreenblob on 2010-03-14
Hey everyone, I'm about to buy a new hard drive, and I had a quick question, I was looking inside my case, and noticed the SATA power cable that's connected to my current hard drive, has another input, like I could hook up another hard drive with that same cable, and my question was, can I use that or is that just there for show? :P

And if so, can anyone confirm this is all I need to install it:

1. Hard Drive (This one in particular: [http://www.newegg.com/Product/Product.aspx?Item=N82E16822136319](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136319))
2. SATA Cable (Maybe this one: [http://www.newegg.com/Product/Product.aspx?Item=N82E16812270093](http://www.newegg.com/Product/Product.aspx?Item=N82E16812270093))

Thanks.

---

### Post by srs5694 on 2010-03-14
The connector is almost certainly real; however, there are a few caveats:


[list]
[*]There are two types of hard disk power connectors: One for older SCSI and PATA drives and another one for newer SATA drives. The old-style connectors usually have four wires and the new ones usually have five wires, in my experience. Old SATA drives often supported both types, but the last few SATA drives I've bought have only had the new-style connector. Thus, if the free connector you've got is for the old style, you'll need an adapter.
[*]Old-style power connectors for hard disks have four wires, but fans only need two wires, and sometimes power supplies include an old-style connector with two wires for fans. If you've only got spare connectors with two wires, you'll need a splitter.
[*]Some cheap computers have power supplies that are just barely adequate. Adding a new hard disk could conceivably overtax them and cause system errors. There are ways to read the specs (usually printed on the power supply) and add up the power specs for the components, but you might not have all the latter, so in the end you may just need to try it, and if you have problems, upgrade the power supply.
[/list]


Drives usually come with mounting screws, but it's conceivable they'll be omitted if you buy a "bare drive" like that. If so, you should be able to remove a screw that holds your current drive in and find something that matches at a hardware or local computer store.

Other than the SATA cable, possible power splitter or adapter, and mounting screws, that's all you should need.

---

### Post by medphys on 2010-03-14
I am going to install a second Sata Drive I bought today for backup.  What is the best way to use the second drive?  How do I partition it for use with rsync or do I use a mirror using raid 1 with mdadm?  Both drives are 1 Tr a seagate Baracudda and a WD caviar Black.  I am running (.10 64 bit Ubuntu. 

MSI P55-GD80 1156 RT
INTEL |CORE I7 860 2.8 G
SEAGATE 7K ST3100052
4 GIG CORSAIR CMX4GX3M2
MSI N94GT MD512 9400 GT


Thanks,

---

### Post by thegreenblob on 2010-03-15
> **srs5694 said:**
> The connector is almost certainly real; however, there are a few caveats:


[list]
[*]There are two types of hard disk power connectors: One for older SCSI and PATA drives and another one for newer SATA drives. The old-style connectors usually have four wires and the new ones usually have five wires, in my experience. Old SATA drives often supported both types, but the last few SATA drives I've bought have only had the new-style connector. Thus, if the free connector you've got is for the old style, you'll need an adapter.
[*]Old-style power connectors for hard disks have four wires, but fans only need two wires, and sometimes power supplies include an old-style connector with two wires for fans. If you've only got spare connectors with two wires, you'll need a splitter.
[*]Some cheap computers have power supplies that are just barely adequate. Adding a new hard disk could conceivably overtax them and cause system errors. There are ways to read the specs (usually printed on the power supply) and add up the power specs for the components, but you might not have all the latter, so in the end you may just need to try it, and if you have problems, upgrade the power supply.
[/list]


Drives usually come with mounting screws, but it's conceivable they'll be omitted if you buy a "bare drive" like that. If so, you should be able to remove a screw that holds your current drive in and find something that matches at a hardware or local computer store.

Other than the SATA cable, possible power splitter or adapter, and mounting screws, that's all you should need.

Alright thanks, I bought the drive, a SATA cable, and a SATA power cable just in case it's an old connector and the drive doesn't accept it.

If I have an issue with power I'll just replace the old 320GB drive instead of adding the 640GB as a second drive. (At least until I can get a better power supply, which I'll then add the 320GB back as a second drive)

And my current drive isn't mounted with any screws, it just slides in an out and there's a locking mechanism to lock it in place. So I assume that means I don't need any mounting screws for the new drive either? :P

Thanks again.

---

