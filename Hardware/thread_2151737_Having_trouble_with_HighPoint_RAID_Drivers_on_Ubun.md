---
title: "Having trouble with HighPoint RAID Drivers on Ubuntu 12.04 LTS"
date: 2013-06-05
forum: Hardware
---

### Post by RedArmy90 on 2013-06-05
Hello Everyone,

I've never posted here before, so please don't hesitate to let me know if I am doing something wrong (i.e. posting in the wrong place etc.) but please be nice.

Now down to business: I am building a storage server with the following components:
[U-NAS NSC-800 Server Chassis]("http://www.u-nas.com/xcart/product.php?productid=17617")
[ADATA Premier Pro SP600 ASP600S3-32GM-C 2.5" 32GB SATA III MLC Internal Solid State Drive (SSD)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820211717&nm_mc=TEMC-RMA-Approvel&cm_mmc=TEMC-RMA-Approvel-_-Content-_-text-_-")
[ASUS C8HM70-I/HDMI Intel Celeron BGA1023 Intel HM70 Mini ITX Motherboard/CPU/VGA Combo]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131948&nm_mc=TEMC-RMA-Approvel&cm_mmc=TEMC-RMA-Approvel-_-Content-_-text-_-")
[Athena Power AP-U1ATX50 20+4Pin 500W Single 1U EPS Server Power Supply - OEM]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817338054&nm_mc=TEMC-RMA-Approvel&cm_mmc=TEMC-RMA-Approvel-_-Content-_-text-_-")
[HighPoint RocketRAID 2680 8-Channel PCI-Express x4 SAS 3Gb/s RAID Controller]("http://www.amazon.com/dp/B001IZBLC2/ref=pe_309540_26725410_item")

That's all good. I built the server, installed Ubuntu 12.04 LTS 32-bit on the 32GB SSD, turned it on, ran some updates, everything seems to work normally. Then I tried to add hard drives to the server. I don't want to set up a RAID array per say, for now I just need to connect all of the drives separately so that I can see them separately either in /dev/ or the disk utility. I don't want any pools or backups, or anything like that, just the individual drives themselves. I believe I've seen people on different forums referring to this as "using your RAID card as a SATA controller". The problem is that I went here: [http://www.highpoint-tech.com/USA_new/rr2600_download.htm](http://www.highpoint-tech.com/USA_new/rr2600_download.htm) where there are only drivers for 11.04 (That was the start of the problem) and looked at this installation guide: [http://www.highpoint-tech.com/BIOS_Driver/rr26xx/RR268x/Linux/v1.8.12.0823/Installation_Guide/Install_Ubuntu_RR2680.pdf](http://www.highpoint-tech.com/BIOS_Driver/rr26xx/RR268x/Linux/v1.8.12.0823/Installation_Guide/Install_Ubuntu_RR2680.pdf)

I was hoping, in vain, that there would be no issue between 11.04 drivers and 12.04 drivers, but this was not the case. I went through the instructions in the guide, but it did not work because when I added the drives in the pre-BIOS RAID menu they did not appear to be recognized by Ubuntu. On top of this, I do not entirely understand how to just add drives to the card so that it sees them as individual drives since the pre-BIOS menu is pretty unclear.

If someone has encountered this issue, knows where to get the 12.04 driver (I don't really want to go to 11.04, but I can if I absolutely have to), and knows how to properly add the drives in such a way as to not create a RAID but just treat them as regular drives I would really appreciate that. Thank you in advance.

I saw this post which seems to be about something similar but for a different RAID card model: [https://help.ubuntu.com/community/RocketRaid#RocketRaid_26xx_Driver](https://help.ubuntu.com/community/RocketRaid#RocketRaid_26xx_Driver)

---

### Post by misu3108 on 2013-11-10
I have the same card as you on Ubuntu 12.04 and can't get it to work. There's a patch here [http://ubuntuforums.org/showthread.php?t=1899544&page=3](http://ubuntuforums.org/showthread.php?t=1899544&page=3) but I dont know how to apply it.

Thanks.

---

