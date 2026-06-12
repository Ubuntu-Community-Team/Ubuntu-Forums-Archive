---
title: "Western Digital WD3200AAKS NCQ issue on Ubuntu"
date: 2011-05-30
forum: Hardware
---

### Post by scott_thomas007 on 2011-05-30
Bonjour All,

I am trying to enable NCQ on my Western Digital WD3200AAKS**.** I have confirmed that this hardware supports NCQ.
output of dmesg command shows that it supports NCQ [    1.044972] ata4.01: ATA-8: WDC WD3200AAKS-75L9A0, 02.03E02, max UDMA/133
[    1.044974] ata4.01: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
But when i try to enable NCQ and run
**echo 31 >   /sys/block/sda/device/queue_depth**
I get an error : 
bash: /sys/block/sdc/device/queue_depth: Permission denied

Kindly help me in this regard

Regards
Scott Thomas

---

### Post by lidex on 2011-05-30
I don't understand what you mean by "when i try to enable" but this:```
bash: /sys/block/sdc/device/queue_depth: Permission denied
``` probably needs to be run as root - ie, with sudo.

This for reference:
[http://www.google.com/search?client=ubuntu&channel=fs&q=ncq&ie=utf-8&oe=utf-8#hl=en&sugexp=crnk_fspiked&pq=ncq&xhr=t&q=ncq+ubuntu&cp=5&qe=bmNxIHU&qesig=AzpBRIAu1Ng1aDei3UKRPg&pkc=AFgZ2tm2rXs325mQA9tY_-DkWQkGXzu8KcYAE0Rie7zC6l9FjRfPxFj2ergDBGzxF7k9pURHIlGAocis61hTPRcUaK_626VLCw&pf=p&sclient=psy&newwindow=1&safe=off&client=ubuntu&hs=8bW&channel=fs&source=hp&aq=0&aqi=&aql=t&oq=ncq+u&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=f17ae772ca1ea813&biw=1680&bih=804](http://www.google.com/search?client=ubuntu&channel=fs&q=ncq&ie=utf-8&oe=utf-8#hl=en&sugexp=crnk_fspiked&pq=ncq&xhr=t&q=ncq+ubuntu&cp=5&qe=bmNxIHU&qesig=AzpBRIAu1Ng1aDei3UKRPg&pkc=AFgZ2tm2rXs325mQA9tY_-DkWQkGXzu8KcYAE0Rie7zC6l9FjRfPxFj2ergDBGzxF7k9pURHIlGAocis61hTPRcUaK_626VLCw&pf=p&sclient=psy&newwindow=1&safe=off&client=ubuntu&hs=8bW&channel=fs&source=hp&aq=0&aqi=&aql=t&oq=ncq+u&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=f17ae772ca1ea813&biw=1680&bih=804)

---

### Post by scott_thomas007 on 2011-05-31
Bonjure,

I am running this command as a root user. So no worries about it. The permissions on this file are r--r--r--

It means that root does not has permissions on this file. I have used this disc in open SUSE, where i found its NCQ is enabled and can be modified.

I think that SATA driver of UBUNTU does not support this disc thats why it shows NCQ disabed. How can i enable it in UBUNTU?

Regards
Scott Thomas

---

