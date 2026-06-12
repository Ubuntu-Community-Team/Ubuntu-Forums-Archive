---
title: "PIONEER DVD-RW DVRTD08 is disabled"
date: 2009-05-08
forum: Hardware
---

### Post by mano_cz on 2009-05-08
My PIONEER DVD-RW DVRTD08 is disabled if i dont put CD/DVD in my drive before boot. Iam using Ubuntu 9.04.
If my drive is empty, iam recieving this errors:
```
Starting up...
[7.xxxx] ata2.00: Failed to set xfermode (err_mask=0x4)
[17.xxxx] ata2.00: Failed to set xfermode (err_mask=0x4)
[27.xxxx] ata2.00: Failed to set xfermode (err_mask=0x4) 
```dmesg:
```
[    2.235838] ata2.00: ATAPI: PIONEER DVD-RW  DVRTD08, 1.00, max UDMA/33
[    7.232011] ata2.00: qc timeout (cmd 0xef)
[    7.232017] ata2.00: failed to set xfermode (err_mask=0x4)
[   17.560007] ata2.00: qc timeout (cmd 0xef)
[   17.560013] ata2.00: failed to set xfermode (err_mask=0x4)
[   17.560063] ata2.00: limiting speed to UDMA/33:PIO3
[   27.888015] ata2.00: qc timeout (cmd 0xef)
[   27.888021] ata2.00: failed to set xfermode (err_mask=0x4)
[   27.888069] ata2.00: disabled
```My drive is disabled, so i cant use it at all.

If my drive contain some CD/DVD boot will pass ok. 
Dmseg:
```
[    2.625513] ata2.00: ATAPI: PIONEER DVD-RW  DVRTD08, 1.00, max UDMA/33
[    2.627554] ata2.00: configured for UDMA/33
```Than i can use my drive.

I was looking at some threats and i found this:
```
http://markmail.org/message/emstksocfotj73jk#query:+page:1+mid:o2szb4y55xuudhgq+state:results
```There is my problem too. There is some patch in programming language C. But i dont know how to use it. Also i dont know if its safe.

I have on my new notebook windows vista too. There was problem with drive too. I could read media with drive but i couldnt burn CD/DVD. So i downloaded this driver *Intel(R) ICH9M-E/M SATA AHCI, *in windows was *Intel(R) ICH9M/M-E Family 4 Port SATA AHCI Controller - 2929. *With these new driver i can burn in win. vista. But i want use ubuntu too...
Btw. my notebook is Sony Vaio VGN-NS21Z.

Thanks for any answer.

---

