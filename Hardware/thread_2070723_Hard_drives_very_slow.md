---
title: "Hard drives very slow"
date: 2012-10-13
forum: Hardware
---

### Post by veaviticus on 2012-10-13
I have a number of drives that are acting very weird. 
There are 7x [Seagate Barricuda 2TB 5900 RPM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822148681") hard drives and 1 WD 750 GB Black. 

They are currently in a SAS-to-SATA expander, connected to an LSI raid card.

They used to each get at least 100 MB/s read/write speeds. For the last few weeks the read/write speed has dropped to 10 MB/s or less. 

The speed stays the same under Ubuntu 12.04 (live USB), Linux Mint 13 (SSD), Windows 7 and Windows Server 2008. The speed stays the same after complete formats, and under multiple file systems.
The speed stays the same if they are in the expander, or connected directly to the raid card, or connected directly to the motherboard. I have also tested an AMD motherboard and an Intel motherboard.

Gnome-Disk-Utility says the SMART data is all green. Self-tests all pass. The read benchmark gets a range between 20-100 Mb/s (bits).

A SSD connected to the motherboard gets normal speeds.

The entire setup got pretty warm over the summer when my room fan died and it was 100 degrees outside. Also the server crashed when the power went out last month before I got a UPS for it.

Any ideas what to test next? Or why my drives have all randomly died?

---

