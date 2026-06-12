---
title: "Recover FAT32 disk"
date: 2007-01-02
forum: Hardware &amp; Laptops
---

### Post by christooss on 2007-01-02
Windows XP has ****** up something on my FAT32 disk. And now when I try to run fsck.vfat i get this output:

```
sudo fsck.vfat -a /dev/hdd5
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  1:50/58, 3:45/4d, 7:46/4e, 9:26/2e, 21:f0/f8, 29:37/3f, 33:02/0a, 37:91/99
  , 65:03/00, 69:f6/fe, 71:20/00, 72:20/00, 73:20/00, 74:20/00, 75:20/00
  , 76:20/00, 77:20/00, 78:20/00, 79:20/00, 80:20/00, 81:20/00, 93:86/8e
  , 95:b4/bc, 97:73/7b, 101:70/78, 113:81/89, 117:46/4e, 121:f4/fc, 125:d1/d9
  , 131:f6/fe, 133:83/8b, 135:10/18, 139:30/38, 147:b3/bb, 157:32/3a
  , 163:33/3b, 165:82/8a, 167:f4/fc, 171:c2/ca, 173:80/88, 181:b7/bf
  , 185:76/7e, 193:83/8b, 195:16/1e, 199:41/49, 207:e0/e8, 213:f0/f8
  , 217:83/8b, 225:33/3b, 229:83/8b, 231:06/0e, 233:c6/ce, 243:16/1e
  , 247:03/0b, 251:76/7e, 257:f5/fd, 259:b6/be, 271:34/3c, 277:b3/bb
  , 283:e6/ee, 287:e3/eb, 289:b6/be, 295:c5/cd, 297:56/5e, 303:11/19
  , 307:62/6a, 313:62/6a, 315:62/6a, 317:83/8b, 321:76/7e, 323:06/0e
  , 329:15/1d, 343:c2/ca, 347:82/8a, 349:82/8a, 355:c4/cc, 359:82/8a
  , 365:85/8d, 377:03/0b, 383:10/18, 387:02/0a, 389:66/6e, 393:61/69
  , 397:71/79, 401:65/6d, 407:f7/ff, 409:02/0a, 411:61/69, 413:63/6b
  , 415:41/49, 417:47/4f, 425:05/0d, 443:24/2c, 461:66/6e, 467:05/0d
  , 473:47/4f, 481:51/59, 483:45/4d, 499:46/4e, 501:47/4f, 511:a2/aa
  Not automatically fixing this.
File system has 5024638 clusters but only space for 4762622 FAT entries.

```

What can I do?

---

