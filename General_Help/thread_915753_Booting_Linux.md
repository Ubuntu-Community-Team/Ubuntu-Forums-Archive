---
title: "Booting Linux"
date: 2008-09-10
forum: General Help
---

### Post by ThorX89 on 2008-09-10
Hello, I have a problem. I'm using Linux Mint, standardly booting with a splash image writing down the booting information under it.
What's been happening lately is it always (as if) skipps a few first steps, then hangs on "waiting for resume ..." for a while and then it switches over to text mode where it stays up till the login screen. In the text mode it also displays a table of numbers after checking my second fat32 partition and a note saying something about an error over there and "not fixing this". 

What I would like to do is resume the normal boot with splash image being displayed all the time (no "skipping" initial steps, hanging on "waiting for resume device", and then text mode). (I suspect this is a consequence of a faulty attempt for suspend, it doesn't work, I'm at peace with it, but I just want my normal booting back).
I would also like to somehow correct the errors in in the fat32 partition (being used by freedos and as a data partition for mozilla profiles - web and mail). I tried scanning it in windows but the numbers are still being displayed when booting Linux.


Thankx a lot for any help.

---

### Post by ThorX89 on 2008-09-10
Concerning the numbers I was talking about. Here's what it says:
```

thorx89@atlantis ~ $ sudo fsck /dev/sda2
fsck 1.40.8 (13-Mar-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  3:46/4d, 4:52/53, 8:34/35, 10:31/30, 64:ff/80, 90:fc/33, 91:fa/c9, 92:29/8e
  , 93:c0/d1, 94:8e/bc, 95:d8/f4, 96:bd/7b, 97:00/8e, 98:7c/c1, 99:b8/8e
  , 100:e0/d9, 101:1f/bd, 102:8e/00, 103:c0/7c, 104:89/88, 105:ee/4e
  , 106:89/02, 107:ef/8a, 108:b9/56, 109:00/40, 110:01/b4, 111:f3/08
  , 112:a5/cd, 113:ea/13, 114:7a/73, 115:7c/05, 116:e0/b9, 117:1f/ff
  , 118:00/ff, 119:00/8a, 120:60/f1, 121:00/66, 122:8e/0f, 123:d8/b6
  , 124:8e/c6, 125:d0/40, 126:8d/66, 127:66/0f, 128:e0/b6, 129:fb/d1
  , 130:88/80, 131:56/e2, 132:40/3f, 133:be/f7, 134:c1/e2, 135:7d/86
  , 136:e8/cd, 137:f4/c0, 138:00/ed, 139:66/06, 140:31/41, 141:c0/66
  , 142:66/0f, 143:89/b7, 144:46/c9, 145:44/66, 146:8b/f7, 147:46/e1
  , 148:0e/66, 149:66/89, 150:03/46, 151:46/f8, 152:1c/83, 153:66/7e
  , 154:89/16, 155:46/00, 156:48/75, 157:66/38, 158:89/83, 159:46/7e
  , 160:4c/2a, 161:66/00, 162:8b/77, 163:46/32, 164:10/66, 165:66/8b
  , 166:f7/46, 167:6e/1c, 168:24/66, 169:66/83, 170:01/c0, 171:46/0c
  , 172:4c/bb, 173:b8/00, 174:00/80, 175:02/b9, 176:3b/01, 177:46/00
  , 178:0b/e8, 179:74/2b, 180:08/00, 181:01/e9, 182:c0/48, 183:ff/03
  , 184:06/a0, 185:34/fa, 187:eb/b4, 188:f3/7d, 189:66/8b, 190:8b/f0
  , 191:46/ac, 192:2c/84, 193:66/c0, 194:50/74, 195:e8/17, 196:94/3c
  , 197:00/ff, 198:72/74, 199:4d/09, 200:c4/b4, 201:5e/0e, 202:76/bb
  , 203:e8/07, 204:b7/00, 205:00/cd, 206:31/10, 207:ff/eb, 208:b9/ee
  , 209:0b/a0, 210:00/fb, 211:be/7d, 212:f1/eb, 213:7d/e5, 214:f3/a0
  , 215:a6/f9, 216:74/7d, 217:15/eb, 218:83/e0, 219:c7/98, 220:20/cd
  , 221:83/16, 222:e7/cd, 223:e0/19, 224:3b/66, 225:7e/60, 226:0b/66
  , 227:75/3b, 228:eb/46, 229:4a/f8, 230:75/0f, 231:e0/82, 232:66/4a
  , 233:58/00, 234:e8/66, 235:34/6a, 237:eb/66, 238:d2/50, 239:26/06
  , 240:ff/53, 241:75/66, 242:09/68, 243:26/10, 244:ff/00, 245:75/01
  , 246:0f/00, 247:66/80, 248:58/7e, 249:29/02, 250:db/00, 251:66/0f
  , 252:50/85, 253:e8/20, 254:5a/00, 255:00/b4, 256:72/41, 257:0d/bb
  , 258:e8/aa, 259:80/55, 260:00/8a, 261:4a/56, 262:75/40, 263:fa/cd
  , 264:66/13, 265:58/0f, 266:e8/82, 267:14/1c, 269:eb/81, 270:ec/fb
  , 271:8a/55, 272:5e/aa, 273:40/0f, 274:ff/85, 275:6e/14, 276:76/00
  , 277:be/f6, 278:ee/c1, 279:7d/01, 280:e8/0f, 281:64/84, 282:00/0d
  , 283:30/00, 284:e4/fe, 285:cd/46, 286:16/02, 287:cd/b4, 288:19/42
  , 289:06/8a, 290:57/56, 291:53/40, 292:89/8b, 293:c7/f4, 294:c1/cd
  , 295:e7/13, 296:02/b0, 297:50/f9, 298:8b/66, 299:46/58, 300:0b/66
  , 301:48/58, 302:21/66, 303:c7/58, 304:58/66, 305:66/58, 306:c1/eb
  , 307:e8/2a, 308:07/66, 309:66/33, 310:03/d2, 311:46/66, 312:48/0f
  , 313:bb/b7, 314:00/4e, 315:20/18, 316:8e/66, 317:c3/f7, 318:29/f1
  , 319:db/fe, 320:66/c2, 321:3b/8a, 322:46/ca, 323:44/66, 324:74/8b
  , 325:07/d0, 327:89/c1, 328:46/ea, 329:44/10, 330:e8/f7, 331:38/76
  , 332:00/1a, 333:26/86, 334:80/d6, 335:65/8a, 336:03/56, 337:0f/40
  , 338:26/8a, 339:66/e8, 340:8b/c0, 341:05/e4, 342:5b/06, 343:5f/0a
  , 344:07/cc, 345:c3/b8, 346:66/01, 347:3d/02, 348:f8/cd, 349:ff/13
  , 350:ff/66, 351:0f/61, 352:73/0f, 353:15/82, 354:66/54, 355:48/ff
  , 356:66/81, 357:48/c3, 358:66/00, 359:0f/02, 360:b6/66, 361:56/40
  , 362:0d/49, 363:66/0f, 364:52/85, 365:66/71, 366:f7/ff, 367:e2/c3
  , 368:66/4e, 369:5a/54, 370:66/4c, 371:03/44, 372:46/52, 373:4c/20
  , 374:c3/20, 375:f9/20, 376:c3/20, 377:31/20, 378:db/20, 379:b4/00
  , 380:0e/00, 381:cd/00, 382:10/00, 383:ac/00, 384:3c/00, 386:75/00
  , 387:f5/00, 388:c3/00, 389:52/00, 390:56/00, 391:57/00, 392:66/00
  , 393:50/00, 394:89/00, 395:e7/00, 396:6a/00, 398:6a/00, 400:66/00
  , 401:50/00, 402:06/00, 403:53/00, 404:6a/00, 405:01/00, 406:6a/00
  , 407:10/00, 408:89/00, 409:e6/00, 410:8a/00, 411:56/00, 412:40/00
  , 413:b4/00, 414:42/00, 415:cd/00, 416:13/00, 417:89/00, 418:fc/00
  , 419:66/00, 420:58/00, 421:73/00, 422:08/00, 423:50/00, 424:30/00
  , 425:e4/00, 426:cd/00, 427:13/00, 428:58/0d, 429:eb/0a, 430:d9/52
  , 431:66/65, 432:40/6d, 433:03/6f, 434:5e/76, 435:0b/65, 436:73/20
  , 437:07/64, 438:8c/69, 439:c2/73, 440:80/6b, 441:c6/73, 442:10/20
  , 443:8e/6f, 444:c2/72, 445:5f/20, 446:5e/6f, 447:5a/74, 448:c3/68
  , 449:4c/65, 450:6f/72, 451:61/20, 452:64/6d, 453:69/65, 454:6e/64
  , 455:67/69, 456:20/61, 457:46/2e, 458:72/ff, 459:65/0d, 460:65/0a
  , 462:4f/69, 463:53/73, 464:20/6b, 465:00/20, 466:00/65, 467:00/72
  , 468:00/72, 469:00/6f, 470:00/72, 471:00/ff, 472:00/0d, 473:00/0a
  , 474:00/50, 475:00/72, 476:00/65, 477:00/73, 478:00/73, 479:00/20
  , 480:00/61, 481:00/6e, 482:00/79, 483:00/20, 484:00/6b, 485:00/65
  , 486:00/79, 487:00/20, 488:00/74, 489:00/6f, 490:00/20, 491:00/72
  , 492:00/65, 493:00/73, 494:4e/74, 495:6f/61, 496:20/72, 497:4b/74
  , 498:45/0d, 499:52/0a, 500:4e/00, 501:45/00, 502:4c/00, 503:20/00
  , 504:20/00, 505:53/ac, 506:59/cb, 507:53/d8
1) Copy original to backup
2) Copy backup to original
3) No action
? 1
Leaving file system unchanged.
/dev/sda2: 4933 files, 105572/905898 clusters

```

Unfortunately, whatever action (1|2) I decide to take I end up with
"Leaving file system unchanged."

---

### Post by WRDN on 2008-09-10
I had this problem recently and found it was an issue with the ID's of the disk partitions. There was a mismatch in files that caused the splash (then text) to appear.

To fix it, first open the Terminal and type the 2 commands:

```
sudo fdisk -l
```

and

```
sudo blkid
```

Now, type:

```
sudo gedit /etc/fstab
```

Make sure the UUID's listed in the fstab file correspond to those from the blkid output. If the UUID's do not match, change them to do so.

Now, type:

```
sudo gedit /etc/initramfs-tools/conf.d/resume
```

Make sure the UUID here corresponds to the UUID for the swap partition (found using blkid command).

Finally, type:

```
sudo update-initramfs -u
```

Now, restart the computer.

---

