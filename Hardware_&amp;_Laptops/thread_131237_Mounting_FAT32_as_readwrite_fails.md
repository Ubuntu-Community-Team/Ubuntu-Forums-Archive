---
title: "Mounting FAT32 as read/write fails"
date: 2006-02-16
forum: Hardware &amp; Laptops
---

### Post by b0rsten on 2006-02-16
good morning,
I'm having some big problems with my fat32-harddisk. I mount it via

```
/dev/hdc1       /music          vfat    rw,uid=1000,gid=1000,umask=077,iocharset=utf8  0       0

```

and it works fine for a couple of seconds... but suddently the harddisk switchs from read-write to read-only

it looks like this:

```
basti@ubuntu:~$ sudo umount /music/
basti@ubuntu:~$ sudo chmod 777 /music
basti@ubuntu:~$ sudo mount /music/
basti@ubuntu:~$ mkdir /music/test2
basti@ubuntu:~$ mkdir /music/test3
basti@ubuntu:~$ mkdir /music/test4
basti@ubuntu:~$ mkdir /music/test5
mkdir: kann Verzeichnis „/music/test5“ nicht anlegen: Das Dateisystem ist nur lesbar
basti@ubuntu:~$
```

mkdir: kann Verzeichnis „/music/test5“ nicht anlegen: Das Dateisystem ist nur lesbar = can't create /music/test5 - device is read-only

can anyone help me? i realy don't know what to do :(

---

### Post by aysiu on 2006-02-16
You can't *chmod* FAT32 partitions. They don't support Linux permissions.

Do this: ```
sudo umount /music
sudo nano /etc/fstab
``` Replace this line ```
/dev/hdc1       /music          vfat    rw,uid=1000,gid=1000,umask=077,iocharset=utf8  0       0
``` with this line ```
/dev/hdc1       /music          vfat    iocharset=utf8,umask=000  0       0
``` **Delete any other line that refers to /dev/hdc1**. Only one line should have /dev/hdc1 in it. Then save (control-x), confirm (y), and exit (Enter). Finally ```
sudo mount -a
```

---

### Post by b0rsten on 2006-02-16
i know that fat32 don't handle chmod...

but the problem is the same... working fine for a couple of seconds and then read-only :(

i can copy about 30mb to my disk and then it switchs to read-only :(


edit:

i found the problem

```
basti@ubuntu:~$ sudo fsck.vfat /dev/hdc1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  90:33/8c, 91:c9/c8, 93:d1/d0, 95:f4/ff, 97:8e/fb, 98:c1/8e, 99:8e/d8
  , 100:d9/8e, 101:bd/c0, 102:00/fc, 103:7c/bf, 104:88/20, 105:4e/00
  , 106:02/33, 107:8a/c0, 108:56/b9, 109:40/15, 110:b4/00, 111:08/af
  , 112:cd/75, 113:13/05, 114:73/af, 115:05/75, 116:b9/04, 117:ff/e2
  , 118:ff/f8, 119:8a/47, 120:f1/47, 121:66/81, 122:0f/7d, 123:b6/fe
  , 124:c6/00, 125:40/c0, 126:66/72, 127:0f/0a, 128:b6/e2, 129:d1/ed
  , 130:80/81, 131:e2/3e, 132:3f/02, 133:f7/01, 134:e2/00, 135:86/c0
  , 136:cd/73, 137:c0/0f, 138:ed/be, 139:06/88, 140:41/7d, 141:66/e8
  , 142:0f/3f, 143:b7/00, 144:c9/33, 145:66/c0, 146:f7/cd, 147:e1/16
  , 148:66/3d, 149:89/00, 150:46/3b, 151:f8/75, 152:83/f7, 153:7e/be
  , 154:16/a7, 155:00/7c, 156:75/bf, 157:38/a7, 158:83/7e, 159:7e/b9
  , 160:2a/71, 162:77/f3, 163:32/a5, 164:66/e9, 165:8b/00, 166:46/02
  , 167:1c/bb, 168:66/00, 169:83/7c, 170:c0/b9, 171:0c/01, 172:bb/00
  , 173:00/be, 174:80/e1, 175:b9/7e, 176:01/e8, 177:00/1c, 178:e8/00
  , 179:2b/33, 180:00/c0, 181:e9/cd, 182:48/16, 183:03/b8, 184:a0/01
  , 185:fa/02, 186:7d/33, 187:b4/d2, 188:7d/50, 189:8b/cd, 190:f0/13
  , 191:ac/58, 192:84/cd, 193:c0/13, 194:74/72, 195:17/e3, 196:3c/81
  , 197:ff/3e, 198:74/fe, 199:09/7d, 200:b4/55, 201:0e/aa, 202:bb/75
  , 203:07/db, 204:00/e9, 205:cd/31, 206:10/fd, 207:eb/50, 208:ee/53
  , 209:a0/51, 210:fb/ac, 211:7d/3c, 212:eb/00, 213:e5/75, 214:a0/04
  , 215:f9/59, 216:7d/5b, 217:eb/58, 218:e0/c3, 219:98/b4, 220:cd/0e
  , 221:16/cd, 222:cd/10, 223:19/eb, 224:66/f1, 225:60/0a, 226:66/0d
  , 227:3b/4e, 228:46/6f, 229:f8/6e, 230:0f/2d, 231:82/73, 232:4a/79
  , 233:00/73, 234:66/74, 235:6a/65, 236:00/6d, 237:66/20, 238:50/64
  , 239:06/69, 240:53/73, 241:66/6b, 242:68/20, 243:10/6f, 244:00/72
  , 245:01/20, 246:00/64, 247:80/69, 248:7e/73, 249:02/6b, 250:00/20
  , 251:0f/65, 252:85/72, 253:20/72, 254:00/6f, 255:b4/72, 256:41/0a
  , 257:bb/0d, 258:aa/49, 259:55/6e, 260:8a/73, 261:56/65, 262:40/72
  , 263:cd/74, 264:13/20, 265:0f/44, 266:82/4f, 267:1c/53, 268:00/20
  , 269:81/64, 270:fb/69, 271:55/73, 272:aa/6b, 273:0f/65, 274:85/74
  , 275:14/74, 276:00/65, 277:f6/20, 278:c1/61, 279:01/6e, 280:0f/64
  , 281:84/20, 282:0d/70, 283:00/72, 284:fe/65, 285:46/73, 286:02/73
  , 287:b4/20, 288:42/61, 289:8a/6e, 290:56/79, 291:40/20, 292:8b/6b
  , 293:f4/65, 294:cd/79, 295:13/20, 296:b0/2e, 297:f9/2e, 298:66/2e
  , 299:58/0a, 300:66/0d, 301:58/00, 302:66/00, 303:58/00, 304:66/00
  , 305:58/00, 306:eb/00, 307:2a/00, 308:66/00, 309:33/00, 310:d2/00
  , 311:66/00, 312:0f/00, 313:b7/00, 314:4e/00, 315:18/00, 316:66/00
  , 317:f7/00, 318:f1/00, 319:fe/00, 320:c2/00, 321:8a/00, 322:ca/00
  , 323:66/00, 324:8b/00, 325:d0/00, 326:66/00, 327:c1/00, 328:ea/00
  , 329:10/00, 330:f7/00, 331:76/00, 332:1a/00, 333:86/00, 334:d6/00
  , 335:8a/00, 336:56/00, 337:40/00, 338:8a/00, 339:e8/00, 340:c0/00
  , 341:e4/00, 342:06/00, 343:0a/00, 344:cc/00, 345:b8/00, 346:01/00
  , 347:02/00, 348:cd/00, 349:13/00, 350:66/00, 351:61/00, 352:0f/00
  , 353:82/00, 354:54/00, 355:ff/00, 356:81/00, 357:c3/00, 359:02/00
  , 360:66/00, 361:40/00, 362:49/00, 363:0f/00, 364:85/00, 365:71/00
  , 366:ff/00, 367:c3/00, 368:4e/00, 369:54/00, 370:4c/00, 371:44/00
  , 372:52/00, 373:20/00, 374:20/00, 375:20/00, 376:20/00, 377:20/00
  , 378:20/00, 392:00/0a, 393:00/0d, 394:00/50, 395:00/6f, 396:00/73
  , 397:00/73, 398:00/69, 399:00/62, 400:00/6c, 401:00/65, 402:00/20
  , 403:00/62, 404:00/6f, 405:00/6f, 406:00/74, 407:00/20, 408:00/56
  , 409:00/49, 410:00/52, 411:00/55, 412:00/53, 413:00/20, 414:00/64
  , 415:00/65, 416:00/74, 417:00/65, 418:00/63, 419:00/74, 420:00/65
  , 421:00/64, 422:00/21, 423:00/0a, 424:00/0d, 425:00/50, 426:00/72
  , 427:00/65, 428:0d/73, 429:0a/73, 430:4e/20, 431:54/3c, 432:4c/46
  , 433:44/31, 434:52/3e, 436:6e/74, 437:69/6f, 438:63/20, 439:68/63
  , 440:74/6f, 441:20/6e, 442:67/74, 443:65/69, 444:66/6e, 446:6e/65
  , 447:64/00, 448:65/0d, 449:6e/0a, 450:ff/50, 451:0d/57, 452:0a/2f
  , 454:61/42, 455:74/20, 456:65/62, 457:6e/79, 458:74/20, 459:72/4b
  , 460:84/49, 461:67/52, 462:65/20, 463:72/56, 464:66/2e, 465:65/20
  , 466:68/28, 467:6c/43, 468:65/29, 469:72/20, 470:ff/50, 471:0d/61
  , 472:0a/72, 473:4e/61, 474:65/67, 475:75/6f, 476:73/6e, 477:74/20
  , 478:61/31, 479:72/39, 480:74/39, 481:20/37, 482:6d/2d, 483:69/31
  , 484:74/39, 485:20/39, 486:62/39, 487:65/00, 488:6c/00, 489:69/00
  , 490:65/00, 491:62/00, 492:69/00, 493:67/00, 494:65/00, 495:72/00
  , 496:20/00, 497:54/00, 498:61/00, 499:73/00, 500:74/00, 501:65/00
  , 502:0d/00, 503:0a/00, 505:ac/00, 506:c3/00, 507:d7/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 3
^[OFReserved field in VFAT long filename slot is not 0 (but 0xef).
1: Fix.
2: Leave it.
?
basti@ubuntu:~$
```

but i don't know what to do :)

---

### Post by leezer3 on 2006-02-16
My inclination here would be to use Winbloat to run a chckdsk /r on the FAT partition- This should be better at repairing them natively.
I'm assuming its a separate drive (As it refers to the boot sector), & this begs the question of what is on there- A Winbloat bootdisk/ WinXP recovery console and doing a fdisk/ mbr would probably fix this.
Finally, I would say that if you are getting problems like this out of the blue, then there is a strong possibility that your HDD could be on its way out- I would run the mfgrs diag utils on it & probably a full check for bad sectors, *as well as* backing up everything on there.

Cheers

-Leezer-

---

### Post by psusi on 2006-02-16
Check dmesg or /var/log/kern.log for errors.  My bet is that there's a bad sector or some other corruption that the kernel runs into so it switches to read only mode to prevent further damage.  

Run badblocks on the partition to check for bad sectors, and if none are found, fsck it to try and repair any logical damage.  

Do this while it is not mounted of course.

---

### Post by aysiu on 2006-02-16
Are you absolutely certain there's only one line about /dev/hdc1 in your /etc/fstab?

---

