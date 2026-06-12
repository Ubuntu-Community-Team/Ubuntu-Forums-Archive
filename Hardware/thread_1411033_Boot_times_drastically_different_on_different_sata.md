---
title: "Boot times drastically different on different sata ports."
date: 2010-02-19
forum: Hardware
---

### Post by acroporas on 2010-02-19
Relevant hardware:

[ASUS M4A78T-E AM3 AMD 790GX HDMI ATX AMD Motherboard](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131366)
[ASUS Model U3S6 USB 3.0 & SATA 6Gb/s Add-on card](http://www.newegg.com/Product/Product.aspx?Item=N82E16813995004)
[OCZ Vertex Series OCZSSD2-1VTX60G 2.5" 60GB SATA II MLC Internal Solid State Drive (SSD)](http://www.newegg.com/Product/Product.aspx?Item=N82E16820227394)

While booted into 64bit ubuntu 9.10 running on a regular HD, I plug the Vertex drive into one of the 3B/s SATA ports on the MB and run hdparm -t on it.  Then I unplug the vertex drive an plug it into one of the 6Mb/s SATA ports on the add in card and run hdparm -t again.

On both ports the drive performance is the same.  This is as expected as it is a 3Mb/s drive.  (results are 212)

Now here is where things start to go wrong/unexpected.

I shut down the computer, remove the regular HD.  Installed 64bit ubuntu 9.10 on the vertex drive and applied all updates.

With the vertex drive on the 3Mb/s port and the a regular HD on the 6Mb/s port (this drive has nothing on it, it is just there to equalize the two tests) I boot into Ubuntu(which is installed on the vertex drive)  **Time from end of Bios to desktop:  14 seconds.**  hdparm -t results for the vertex drive: 190 

With the vertex drive on the 6Mb/s port and the a regular HD on the 3Mb/s port (this drive has nothing on it, it is just there to equalize the two tests) I boot into Ubuntu(which is installed on the vertex drive)  **Time from end of Bios to desktop:  50 seconds.** hdparm -t results for the vertex drive: 190

Can anyone explain why even though once booted, hdparm reports identical performance on the two different sata ports, ubuntu takes 4x as long to boot from the 6Gb/s port?

---

### Post by acroporas on 2010-02-19
^

---

### Post by acroporas on 2010-02-20
Does anyone have any ideas?

---

