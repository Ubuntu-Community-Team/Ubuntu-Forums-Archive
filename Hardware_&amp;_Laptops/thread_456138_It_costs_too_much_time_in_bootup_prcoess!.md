---
title: "It costs too much time in bootup prcoess!"
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by tntwo on 2007-05-27
Dear all,
     please help!I find out failure of xfer mode setting on cd-rw and dvd-rw makes the bootup process too slow.The messages below are displayed after the command "dmesg" I typed in terminal:
 ata2.01: failed to set xfermode (err_mask=0x4)
ata2.01: failed to set xfermode (err_mask=0x4)
[ 3.699499] ata2.00: ATAPI, max UDMA/66
[ 3.699503] ata2.01: ATAPI, max UDMA/33
[ 3.863098] ata2.00: configured for UDMA/66
[ 33.792134] ata2.01: qc timeout (cmd 0xef)
[ 33.792142] ata2.01: failed to set xfermode (err_mask=0x4)
[ 33.792188] ata2: failed to recover some devices, retrying in 5 secs
[ 39.598618] ata2.00: configured for UDMA/66
[ 69.527653] ata2.01: qc timeout (cmd 0xef)
[ 69.527660] ata2.01: failed to set xfermode (err_mask=0x4)
[ 69.527709] ata2.01: limiting speed to UDMA/33:PIO3
[ 69.527711] ata2: failed to recover some devices, retrying in 5 secs
[ 75.338134] ata2.00: configured for UDMA/66
[ 105.267164] ata2.01: qc timeout (cmd 0xef)
[ 105.267171] ata2.01: failed to set xfermode (err_mask=0x4)
[ 105.267218] ata2.01: disabled
[ 105.267221] ata2: failed to recover some devices, retrying in 5 secs
[ 110.259364] ata2.00: failed to set xfermode (err_mask=0x40)
[ 110.259411] ata2: failed to recover some devices, retrying in 5 secs
[ 115.906228] ata2.00: configured for UDMA/66

---

### Post by Pragmatist on 2007-05-27
These people had a similar problem:
[http://ubuntuforums.org/showthread.php?t=440122&highlight=xfermode+0x40](http://ubuntuforums.org/showthread.php?t=440122&highlight=xfermode+0x40)

Their solution was to add the word **irqpoll** as a boot option.  Here are some instructions on using boot options:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by tntwo on 2007-05-28
Dear Pragmatist,
        thanks for your kind support,I have fixed it!

---

### Post by Pragmatist on 2007-05-28
> **tntwo said:**
> ...I have fixed it!

How did you fix it?  It is important to post your solution so that it can help others.

---

