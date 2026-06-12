---
title: "DMA on a DVD DRIVE doesn't work with HDPARM ?!"
date: 2006-09-30
forum: Hardware &amp; Laptops
---

### Post by Shinkan on 2006-09-30
Hi everyone :)

I have an IDE DVD drive on the first IDE channel of my motherboard IDE controller (Intel ICH7).
I have a SATA HDD on the first SATA channel of my motherboard SATA controller (Intel ICH7).
I have an IDE HDD on the 2 IDE channel of my motherboard third-party second IDE controller (ITE i821x).

I experience problems during DVD playback sometimes, so I wanted to activate DMA on my DVD drive, which is detected as /dev/scd0 by Ubuntu Dapper, and mounted on /media/cdrom0

I've just tried hdparm -d1 /dev/scd0, or config-file based device blocks.
I've got this error :

```
/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
```

My main HDD (sata) is /dev/sda1, and I have same problems when I try to use hdparm.
My data HDD (ide) is /dev/hdc and everything works perfeclty.
Here is its hdparm line :

```
hdparm -X udma6 -A1 -B255 -M0 -c1 -m16 -W0 -d1 /dev/hdc
```

My OS is Ubuntu Dapper Drake (updated).
My motherboard is Gigabyte GA-8I955X Royal ([here is specs page]("http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=1897&ProductName=GA-8I955X%20Royal")).

Thanks in advance for any kind of help.

---

### Post by tommcd on 2006-09-30
Well, for the hard drive, I don't DMA is necessary for SATA drives. What is the output of:
'cat /etc/hdparm.conf'. If there is no mention of DMA on or off on the hard drive, and if performance is ok, I would not worry about it.
See the response to this thread:
[http://www.linuxforums.org/forum/slackware-linux-help/62630-dma-problem-sata-hard-drive.html](http://www.linuxforums.org/forum/slackware-linux-help/62630-dma-problem-sata-hard-drive.html)
As for the DVD drive, I don't know why it is detected as /dev/scd0 if it is IDE. IDE drives are usually /dev/hd**. Is it listed that way in /etc/fstab? what does it say about DMA in /etc/hdparm.conf for the DVD drive?

---

### Post by tommcd on 2006-09-30
Also, for the DVD drive, if it is the only device  on that IDE channel,make sure it set to master, or master with no slave present. (whatever the manufacturer recomends for a single IDE device). Som drives can have poor performance if set to cable select.
Hope this helps.

---

