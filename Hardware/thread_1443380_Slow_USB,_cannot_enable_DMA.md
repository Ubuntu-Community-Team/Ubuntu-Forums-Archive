---
title: "Slow USB, cannot enable DMA"
date: 2010-03-31
forum: Hardware
---

### Post by apple123 on 2010-03-31
I have been googling this issue for a while now, but have not been able to get this resolved. 

I have a Toshiba satellite with this spec - (Core duo, 2 GB RAM, Intel ICH7 ). When I try to write on a USB pen drive / passport drive copying speed drops from 10-15 MB/s to 4-5MB/sec with high CPU usage.

I suspect this is because DMA is not enabled. I am not able to enable DMA using the hdparm.

$ sudo hdparm /dev/sdb1
/dev/sdb1:
 HDIO_DRIVE_CMD(identify) failed: Invalid exchange
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 1009/64/62, sectors = 3997696, start = 8192

$ sudo hdparm -d1 /dev/sdb1

/dev/sdb1:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Invalid argument
 HDIO_GET_DMA failed: Invalid argument
 
Please help.

---

### Post by Fafler on 2010-03-31
USB doesn't support DMA in the conventional way. The USB-IDE bridge does DMA on the IDE side of it's possible, but on the host side, the CPU has to du a lot of work bacause of the way USB works. Still, your numbers sound really high.

I have a similar system CD 1.6 ghz, ICH7, 2 gb RAM, so i can post the results of a simple benchmark later.

Have you considered using the FireWire port or getting a ExpressCard - eSATA card of eBay?

---

### Post by apple123 on 2010-03-31
Thanks Fafler for the reply. 

-Is the output of my "sudo hdparm -d1 /dev/sdb1" command normal? Is that what you get when you try to enable DMA for a USB drive?
-I think my system copies faster on windows (~15MB/s), not that it makes me love Ubuntu any lesser, but its annoying nevertheless.
-Isn't there a solution to this with my current hardware?

---

### Post by Fafler on 2010-03-31
Yes, hdparm always gives this kind of errors.

Here, read speed is pretty stable at 18 megabytes/sec, writing is between 6 and 11 using a 200 gb Maxtor drive with NTFS filesystem and a JMicron JM20337 controller. On the host side, i have a ext4 filesystem on top of an encrypted LVM, giving a slight overhead.

So it seems there's room for improvement on your side. But i don't really know what's causing it. Try running top while copying data and see which thread uses most CPU time. Look in /var/log/messages.

[http://cgi.ebay.co.uk/Inside-hide-AKE-Express-To-SATA-eSATA-ExpressCard-Card_W0QQitemZ260549127206QQcmdZViewItemQQptZUK_Computing_LaptopAccessories_PCMCIACards?hash=item3ca9f02c26](http://cgi.ebay.co.uk/Inside-hide-AKE-Express-To-SATA-eSATA-ExpressCard-Card_W0QQitemZ260549127206QQcmdZViewItemQQptZUK_Computing_LaptopAccessories_PCMCIACards?hash=item3ca9f02c26)

[http://cgi.ebay.co.uk/3-5-2-5-SATA-HDD-dock-Docking-Station-Backup-eSATA_W0QQitemZ400104660522QQcmdZViewItemQQptZUK_Collectables_HardDriveEnclosures_RL?hash=item5d28189e2a](http://cgi.ebay.co.uk/3-5-2-5-SATA-HDD-dock-Docking-Station-Backup-eSATA_W0QQitemZ400104660522QQcmdZViewItemQQptZUK_Collectables_HardDriveEnclosures_RL?hash=item5d28189e2a)

Worth considering if you use it alot.

---

