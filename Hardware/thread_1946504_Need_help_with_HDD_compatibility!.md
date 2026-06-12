---
title: "Need help with HDD compatibility!"
date: 2012-03-24
forum: Hardware
---

### Post by kernelsploit on 2012-03-24
I recently turned my 7 year old HP Pavilion a1030e desktop into a Ubuntu media server.  From what I could find on the HP website it contains a K8S-LA (Salmon) motherboard.  I'm planning on adding a "Western Digital 1 TB Caviar Blue SATA III 7200 RPM 32 MB Cache Bulk/OEM Desktop Hard Drive - WD10EALX" to the default 80 GB HDD.  Could anyone tell me if the HDD is compatible with the mobo and if I could use the 80 GB drive for my Ubuntu 11.10 install and the 1 TB drive for data.  Thanks in advance!

---

### Post by jayshomebrew on 2012-03-25
your motherboard specs say it has 2 sata connectors, or in other words, 2 max drives. If the optical drive(dvd burner) is using one of these sata ports, then no it won't work, without another card.

You have options if the optical drive is on one of the sata ports. Just get a pci card that has a couple more sata ports:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16815124006]("http://www.newegg.com/Product/Product.aspx?Item=N82E16815124006")
[IMG]http://images10.newegg.com/NeweggImage/ProductImageCompressAll300/15-124-006-17.jpg[/IMG]

or you can get one of those sata to pata adapters for the optical drive.

---

### Post by Yellow Pasque on 2012-03-25
The SiS chipset on that mobo might be one of those older southbridges that chokes on SATA300 devices (I'm not sure). If you can't get the BIOS to see the drive, try jumpering the drive to force SATA150 mode.

---

### Post by kernelsploit on 2012-03-25
Thanks guys!  I haven't purchased the HDD yet so I'll see how that works out.

---

