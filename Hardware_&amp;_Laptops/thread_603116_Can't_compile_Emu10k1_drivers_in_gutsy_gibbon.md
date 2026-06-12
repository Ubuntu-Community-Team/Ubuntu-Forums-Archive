---
title: "Can't compile Emu10k1 drivers in gutsy gibbon"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by harker on 2007-11-04
Hi,

I guess I should start by saying I am not a complete newb but you may aswell treat me as one.

I am trying to get AC3 Passthrough to wrok on my sound blaster live. Now I know it works becuase when I tried out LinuxMCE on Feisty it was able to get passthrough working.

For some reason I can't get this to work with mplayer or xine.

So I decided to try to install the Enu10k1 drivers, even though I believe the drivers should already be installed. (??)

Anyway I can't compile using make install (see Output A).

Now what's interesting is that the second time I run the same make install command (because that's what I do), I get Output B. Does this indicate something is just a little wrong??

Anyway if anyone can help me that would be great. If I am going down the wrong track, please let me know also.

Basically for some background I am running mythbuntu, and it suceesfully getting stereo output, but cannot get Dolby Digital and DTS to pass through to my receiver. Know like I said I know I can atleast get DD to work on my system atleast on LinuMCE (feisty). 

Any help would be great

Thanks in advance


**_Output A_**
> cc    -M audio.c cardmi.c cardmo.c cardwi.c cardwo.c efxmgr.c emuadxmg.c hwaccess.c irqmgr.c main.c midi.c mixer.c recmgr.c timer.c voicemgr.c ecard.c passthrough.c > .depend
audio.c:34:26: error: linux/module.h: No such file or directory
audio.c:36:24: error: linux/slab.h: No such file or directory
audio.c:38:26: error: linux/bitops.h: No such file or directory
audio.c:39:20: error: asm/io.h: No such file or directory
audio.c:41:28: error: linux/smp_lock.h: No such file or directory
audio.c:42:27: error: linux/wrapper.h: No such file or directory
In file included from audio.c:45:
hwaccess.h:43:25: error: emu_wrapper.h: No such file or directory
In file included from cardwo.h:38,
                 from audio.c:46:
timer.h:31:29: error: linux/interrupt.h: No such file or directory
cardmi.c:33:24: error: linux/slab.h: No such file or directory
In file included from cardmi.c:36:
hwaccess.h:42:20: error: asm/io.h: No such file or directory
hwaccess.h:43:25: error: emu_wrapper.h: No such file or directory
In file included from cardmi.c:38:
cardmi.h:37:29: error: linux/interrupt.h: No such file or directory
cardmo.c:33:24: error: linux/slab.h: No such file or directory
In file included from cardmo.c:35:
hwaccess.h:42:20: error: asm/io.h: No such file or directory
hwaccess.h:43:25: error: emu_wrapper.h: No such file or directory
In file included from cardmo.c:37:
cardmo.h:37:29: error: linux/interrupt.h: No such file or directory
In file included from cardwi.c:33:
hwaccess.h:40:24: error: linux/slab.h: No such file or directory
hwaccess.h:42:20: error: asm/io.h: No such file or directory
hwaccess.h:43:25: error: emu_wrapper.h: No such file or directory
In file included from cardwi.c:34:
timer.h:31:29: error: linux/interrupt.h: No such file or directory
In file included from cardwo.c:33:
hwaccess.h:40:24: error: linux/slab.h: No such file or directory
hwaccess.h:42:20: error: asm/io.h: No such file or directory
hwaccess.h:43:25: error: emu_wrapper.h: No such file or directory
In file included from cardwo.h:38,
                 from cardwo.c:36:
timer.h:31:29: error: linux/interrupt.h: No such file or directory
efxmgr.c:32:26: error: linux/bitops.h: No such file or directory
In file included from efxmgr.c:33:
hwaccess.h:40:24: error: linux/slab.h: No such file or directory
hwaccess.h:42:20: error: asm/io.h: No such file or directory
hwaccess.h:43:25: error: emu_wrapper.h: No such file or directory
In file included from emuadxmg.c:33:
hwaccess.h:40:24: error: linux/slab.h: No such file or directory
hwaccess.h:42:20: error: asm/io.h: No such file or directory
hwaccess.h:43:25: error: emu_wrapper.h: No such file or directory
hwaccess.c:33:20: error: asm/io.h: No such file or directory
In file included from hwaccess.c:35:
hwaccess.h:40:24: error: linux/slab.h: No such file or directory
hwaccess.h:43:25: error: emu_wrapper.h: No such file or directory
In file included from irqmgr.c:32:
hwaccess.h:40:24: error: linux/slab.h: No such file or directory
hwaccess.h:42:20: error: asm/io.h: No such file or directory
hwaccess.h:43:25: error: emu_wrapper.h: No such file or directory
In file included from irqmgr.c:34:
cardmi.h:37:29: error: linux/interrupt.h: No such file or directory
main.c:91:26: error: linux/module.h: No such file or directory
main.c:92:24: error: linux/slab.h: No such file or directory
main.c:93:24: error: linux/init.h: No such file or directory
main.c:94:25: error: linux/delay.h: No such file or directory
main.c:95:27: error: linux/proc_fs.h: No such file or directory
In file included from main.c:97:
hwaccess.h:42:20: error: asm/io.h: No such file or directory
hwaccess.h:43:25: error: emu_wrapper.h: No such file or directory
In file included from cardwo.h:38,
                 from main.c:100:
timer.h:31:29: error: linux/interrupt.h: No such file or directory
midi.c:33:26: error: linux/module.h: No such file or directory
midi.c:35:24: error: linux/slab.h: No such file or directory
midi.c:38:28: error: linux/smp_lock.h: No such file or directory
midi.c:39:25: error: asm/uaccess.h: No such file or directory
In file included from midi.c:41:
hwaccess.h:42:20: error: asm/io.h: No such file or directory
hwaccess.h:43:25: error: emu_wrapper.h: No such file or directory
In file included from midi.c:42:
cardmo.h:37:29: error: linux/interrupt.h: No such file or directory
mixer.c:34:26: error: linux/module.h: No such file or directory
mixer.c:36:25: error: asm/uaccess.h: No such file or directory
In file included from mixer.c:39:
hwaccess.h:40:24: error: linux/slab.h: No such file or directory
hwaccess.h:42:20: error: asm/io.h: No such file or directory
hwaccess.h:43:25: error: emu_wrapper.h: No such file or directory
In file included from cardwi.h:36,
                 from recmgr.h:36,
                 from mixer.c:41:
timer.h:31:29: error: linux/interrupt.h: No such file or directory
recmgr.c:32:23: error: asm/delay.h: No such file or directory
In file included from recmgr.h:35,
                 from recmgr.c:34:
hwaccess.h:40:24: error: linux/slab.h: No such file or directory
hwaccess.h:42:20: error: asm/io.h: No such file or directory
hwaccess.h:43:25: error: emu_wrapper.h: No such file or directory
In file included from cardwi.h:36,
                 from recmgr.h:36,
                 from recmgr.c:34:
timer.h:31:29: error: linux/interrupt.h: No such file or directory
In file included from timer.c:31:
hwaccess.h:40:24: error: linux/slab.h: No such file or directory
hwaccess.h:42:20: error: asm/io.h: No such file or directory
hwaccess.h:43:25: error: emu_wrapper.h: No such file or directory
In file included from timer.c:34:
timer.h:31:29: error: linux/interrupt.h: No such file or directory
In file included from voicemgr.h:35,
                 from voicemgr.c:32:
hwaccess.h:40:24: error: linux/slab.h: No such file or directory
hwaccess.h:42:20: error: asm/io.h: No such file or directory
hwaccess.h:43:25: error: emu_wrapper.h: No such file or directory
In file included from ecard.h:30,
                 from ecard.c:32:
hwaccess.h:40:24: error: linux/slab.h: No such file or directory
hwaccess.h:42:20: error: asm/io.h: No such file or directory
hwaccess.h:43:25: error: emu_wrapper.h: No such file or directory
In file included from ecard.c:32:
ecard.h:31:24: error: linux/init.h: No such file or directory
passthrough.c:33:26: error: linux/module.h: No such file or directory
passthrough.c:35:24: error: linux/slab.h: No such file or directory
passthrough.c:37:26: error: linux/bitops.h: No such file or directory
passthrough.c:38:20: error: asm/io.h: No such file or directory
passthrough.c:40:28: error: linux/smp_lock.h: No such file or directory
passthrough.c:41:27: error: linux/wrapper.h: No such file or directory
In file included from passthrough.c:43:
hwaccess.h:43:25: error: emu_wrapper.h: No such file or directory
In file included from cardwo.h:38,
                 from passthrough.c:44:
timer.h:31:29: error: linux/interrupt.h: No such file or directory
make: *** [.depend] Error 1


**_Output B_**
> audio.c:1312: error: âstruct woinstâ has no member named âstateâ
audio.c:1314: error: âstruct woinstâ has no member named âbufferâ
audio.c:1315: error: âstruct woinstâ has no member named âbufferâ
audio.c:1316: error: âstruct woinstâ has no member named âbufferâ
audio.c:1317: error: âstruct woinstâ has no member named âdeviceâ
audio.c:1317: error: âstruct emu10k1_cardâ has no member named âaudio_dev1â
audio.c:1318: error: âstruct woinstâ has no member named âtimerâ
audio.c:1319: error: âstruct woinstâ has no member named ânum_voicesâ
audio.c:1322: error: âstruct woinstâ has no member named âvoiceâ
audio.c:1323: error: âstruct woinstâ has no member named âvoiceâ
audio.c:1326: error: âstruct woinstâ has no member named âwait_queueâ
audio.c:1328: error: âstruct woinstâ has no member named âmmappedâ
audio.c:1329: error: âstruct woinstâ has no member named âtotal_copiedâ
audio.c:1330: error: âstruct woinstâ has no member named âtotal_playedâ
audio.c:1331: error: âstruct woinstâ has no member named âblocksâ
audio.c:1332: error: âstruct woinstâ has no member named âlockâ
audio.c:1333: error: âstruct woinstâ has no member named âtimerâ
audio.c:1335: error: âstruct woinstâ has no member named âformatâ
audio.c:1338: error: dereferencing pointer to incomplete type
audio.c: At top level:
audio.c:1343: warning: âstruct fileâ declared inside parameter list
audio.c:1343: warning: âstruct inodeâ declared inside parameter list
audio.c: In function âemu10k1_audio_releaseâ:
audio.c:1345: error: dereferencing pointer to incomplete type
audio.c:1353: error: dereferencing pointer to incomplete type
audio.c:1356: error: âstruct woinstâ has no member named âlockâ
audio.c:1357: error: âstruct woinstâ has no member named âformatâ
audio.c:1358: error: âstruct emu10k1_cardâ has no member named âptâ
audio.c:1359: error: âstruct woinstâ has no member named âformatâ
audio.c:1359: error: âstruct emu10k1_cardâ has no member named âptâ
audio.c:1360: error: âstruct emu10k1_cardâ has no member named âptâ
audio.c:1362: error: âstruct emu10k1_cardâ has no member named âptâ
audio.c:1364: error: âstruct woinstâ has no member named âstateâ
audio.c:1365: error: âstruct woinstâ has no member named âstateâ
audio.c:1366: error: dereferencing pointer to incomplete type
audio.c:1366: error: âO_NONBLOCKâ undeclared (first use in this function)
audio.c:1367: error: âcurrentâ undeclared (first use in this function)
audio.c:1368: error: âstruct woinstâ has no member named âtotal_playedâ
audio.c:1368: error: âstruct woinstâ has no member named âtotal_copiedâ
audio.c:1370: error: âstruct woinstâ has no member named âlockâ
audio.c:1371: error: âstruct woinstâ has no member named âwait_queueâ
audio.c:1372: error: âstruct woinstâ has no member named âlockâ
audio.c:1388: error: âstruct woinstâ has no member named âlockâ
audio.c:1390: error: âstruct woinstâ has no member named âtimerâ
audio.c:1394: error: dereferencing pointer to incomplete type
audio.c:1397: error: âstruct wiinstâ has no member named âlockâ
audio.c:1399: error: âstruct wiinstâ has no member named âstateâ
audio.c:1412: error: âstruct wiinstâ has no member named âlockâ
audio.c:1413: error: âstruct wiinstâ has no member named âtimerâ
audio.c:1419: error: âstruct emu10k1_cardâ has no member named âopen_waitâ
audio.c:1420: error: âstruct emu10k1_cardâ has no member named âopen_waitâ
audio.c:1422: error: âMOD_DEC_USE_COUNTâ undeclared (first use in this function)
audio.c: At top level:
audio.c:1428: warning: âstruct poll_table_structâ declared inside parameter list
audio.c:1428: warning: âstruct fileâ declared inside parameter list
audio.c: In function âemu10k1_audio_pollâ:
audio.c:1430: error: dereferencing pointer to incomplete type
audio.c:1434: error: âu32â undeclared (first use in this function)
audio.c:1434: error: expected â;â before âbytestocopyâ
audio.c:1439: error: dereferencing pointer to incomplete type
audio.c:1440: error: âstruct woinstâ has no member named âwait_queueâ
audio.c:1442: error: dereferencing pointer to incomplete type
audio.c:1443: error: âstruct wiinstâ has no member named âwait_queueâ
audio.c:1445: error: dereferencing pointer to incomplete type
audio.c:1446: error: âstruct woinstâ has no member named âlockâ
audio.c:1448: error: âstruct woinstâ has no member named âstateâ
audio.c:1450: error: âbytestocopyâ undeclared (first use in this function)
audio.c:1450: error: too many arguments to function âemu10k1_waveout_getxfersizeâ
audio.c:1452: error: âstruct woinstâ has no member named âbufferâ
audio.c:1457: error: âstruct woinstâ has no member named âlockâ
audio.c:1460: error: dereferencing pointer to incomplete type
audio.c:1461: error: âstruct wiinstâ has no member named âlockâ
audio.c:1463: error: âstruct wiinstâ has no member named âstateâ
audio.c:1465: error: too many arguments to function âemu10k1_wavein_getxfersizeâ
audio.c:1467: error: âstruct wiinstâ has no member named âbufferâ
audio.c:1471: error: âstruct wiinstâ has no member named âlockâ
audio.c: In function âcalculate_ofragâ:
audio.c:1479: error: âstruct woinstâ has no member named âbufferâ
audio.c:1480: error: âu32â undeclared (first use in this function)
audio.c:1480: error: expected â;â before âfragsizeâ
audio.c:1482: error: âstruct waveout_bufferâ has no member named âfragment_sizeâ
audio.c:1485: error: âstruct waveout_bufferâ has no member named âossfragshiftâ
audio.c:1486: error: âfragsizeâ undeclared (first use in this function)
audio.c:1486: error: âstruct woinstâ has no member named âformatâ
audio.c:1486: error: âstruct woinstâ has no member named âformatâ
audio.c:1490: error: âstruct waveout_bufferâ has no member named âossfragshiftâ
audio.c:1494: error: âstruct waveout_bufferâ has no member named âossfragshiftâ
audio.c:1495: error: âstruct waveout_bufferâ has no member named âossfragshiftâ
audio.c:1497: error: âstruct waveout_bufferâ has no member named âfragment_sizeâ
audio.c:1497: error: âstruct waveout_bufferâ has no member named âossfragshiftâ
audio.c:1499: error: âstruct waveout_bufferâ has no member named âfragment_sizeâ
audio.c:1500: error: âstruct waveout_bufferâ has no member named âfragment_sizeâ
audio.c:1506: error: âstruct waveout_bufferâ has no member named ânumfragsâ
audio.c:1507: error: expected â;â before ânumfragsâ
audio.c:1509: error: ânumfragsâ undeclared (first use in this function)
audio.c:1509: error: âstruct woinstâ has no member named âformatâ
audio.c:1509: error: âstruct woinstâ has no member named âformatâ
audio.c:1510: error: âstruct waveout_bufferâ has no member named âfragment_sizeâ
audio.c:1512: error: âstruct waveout_bufferâ has no member named ânumfragsâ
audio.c:1516: error: âstruct waveout_bufferâ has no member named ânumfragsâ
audio.c:1520: error: âstruct waveout_bufferâ has no member named ânumfragsâ
audio.c:1521: error: âstruct waveout_bufferâ has no member named ânumfragsâ
audio.c:1523: error: âstruct waveout_bufferâ has no member named ânumfragsâ
audio.c:1523: error: âstruct waveout_bufferâ has no member named âfragment_sizeâ
audio.c:1524: error: âstruct waveout_bufferâ has no member named ânumfragsâ
audio.c:1524: error: âstruct waveout_bufferâ has no member named âfragment_sizeâ
audio.c:1526: error: âstruct waveout_bufferâ has no member named ânumfragsâ
audio.c:1529: error: âstruct waveout_bufferâ has no member named âsizeâ
audio.c:1529: error: âstruct waveout_bufferâ has no member named âfragment_sizeâ
audio.c:1529: error: âstruct waveout_bufferâ has no member named ânumfragsâ
audio.c:1530: error: âstruct waveout_bufferâ has no member named âpagesâ
audio.c:1530: error: âstruct waveout_bufferâ has no member named âsizeâ
audio.c:1530: error: âstruct waveout_bufferâ has no member named âsizeâ
audio.c: In function âcalculate_ifragâ:
audio.c:1540: error: âstruct wiinstâ has no member named âbufferâ
audio.c:1541: error: âu32â undeclared (first use in this function)
audio.c:1541: error: expected â;â before âfragsizeâ
audio.c:1544: error: âstruct wavein_bufferâ has no member named âfragment_sizeâ
audio.c:1547: error: âstruct wavein_bufferâ has no member named âossfragshiftâ
audio.c:1548: error: âfragsizeâ undeclared (first use in this function)
audio.c:1548: error: âstruct wiinstâ has no member named âformatâ
audio.c:1552: error: âstruct wavein_bufferâ has no member named âossfragshiftâ
audio.c:1556: error: âstruct wavein_bufferâ has no member named âossfragshiftâ
audio.c:1557: error: âstruct wavein_bufferâ has no member named âossfragshiftâ
audio.c:1559: error: âstruct wavein_bufferâ has no member named âfragment_sizeâ
audio.c:1559: error: âstruct wavein_bufferâ has no member named âossfragshiftâ
audio.c:1561: error: âstruct wavein_bufferâ has no member named âfragment_sizeâ
audio.c:1562: error: âstruct wavein_bufferâ has no member named âfragment_sizeâ
audio.c:1568: error: âstruct wavein_bufferâ has no member named ânumfragsâ
audio.c:1569: error: âstruct wavein_bufferâ has no member named ânumfragsâ
audio.c:1569: error: âstruct wiinstâ has no member named âformatâ
audio.c:1569: error: âstruct wavein_bufferâ has no member named âfragment_sizeâ
audio.c:1571: error: âstruct wavein_bufferâ has no member named ânumfragsâ
audio.c:1572: error: âstruct wavein_bufferâ has no member named ânumfragsâ
audio.c:1574: error: âstruct wavein_bufferâ has no member named ânumfragsâ
audio.c:1574: error: âstruct wavein_bufferâ has no member named âfragment_sizeâ
audio.c:1575: error: âstruct wavein_bufferâ has no member named ânumfragsâ
audio.c:1575: error: âstruct wavein_bufferâ has no member named âfragment_sizeâ
audio.c:1577: error: âstruct wavein_bufferâ has no member named ânumfragsâ
audio.c:1580: error: âbufsizeâ undeclared (first use in this function)
audio.c:1580: error: âstruct wavein_bufferâ has no member named âfragment_sizeâ
audio.c:1580: error: âstruct wavein_bufferâ has no member named ânumfragsâ
audio.c:1584: error: âstruct wavein_bufferâ has no member named âsizeâ
audio.c:1585: error: âstruct wavein_bufferâ has no member named âsizeregvalâ
audio.c:1587: error: âstruct wavein_bufferâ has no member named âsizeâ
audio.c:1588: error: âsizeâ undeclared (first use in this function)
audio.c:1596: error: âstruct wavein_bufferâ has no member named âsizeâ
audio.c:1598: error: âstruct wavein_bufferâ has no member named âsizeregvalâ
audio.c:1602: error: âstruct wavein_bufferâ has no member named âsizeâ
audio.c:1603: error: âstruct wavein_bufferâ has no member named âsizeâ
audio.c:1604: error: âstruct wavein_bufferâ has no member named âsizeregvalâ
audio.c:1609: error: âstruct wavein_bufferâ has no member named âsizeâ
audio.c:1609: error: âstruct wavein_bufferâ has no member named âfragment_sizeâ
audio.c:1610: error: âstruct wavein_bufferâ has no member named âfragment_sizeâ
audio.c:1612: error: âstruct wavein_bufferâ has no member named ânumfragsâ
audio.c:1612: error: âstruct wavein_bufferâ has no member named âsizeâ
audio.c:1612: error: âstruct wavein_bufferâ has no member named âfragment_sizeâ
audio.c:1613: error: âstruct wavein_bufferâ has no member named âpagesâ
audio.c:1613: error: âstruct wavein_bufferâ has no member named âsizeâ
audio.c:1613: error: âstruct wavein_bufferâ has no member named âsizeâ
audio.c: In function âemu10k1_wavein_bhâ:
audio.c:1626: error: âu32â undeclared (first use in this function)
audio.c:1626: error: expected â;â before âbytestocopyâ
audio.c:1632: error: âstruct wiinstâ has no member named âlockâ
audio.c:1634: error: âstruct wiinstâ has no member named âstateâ
audio.c:1635: error: âstruct wiinstâ has no member named âlockâ
audio.c:1640: error: âbytestocopyâ undeclared (first use in this function)
audio.c:1640: error: too many arguments to function âemu10k1_wavein_getxfersizeâ
audio.c:1642: error: âstruct wiinstâ has no member named âlockâ
audio.c:1644: error: âstruct wiinstâ has no member named âbufferâ
audio.c:1645: error: âstruct wiinstâ has no member named âwait_queueâ
audio.c:1646: error: âstruct wiinstâ has no member named âwait_queueâ
audio.c: In function âemu10k1_waveout_bhâ:
audio.c:1657: error: âu32â undeclared (first use in this function)
audio.c:1657: error: expected â;â before âbytestocopyâ
audio.c:1663: error: âstruct woinstâ has no member named âlockâ
audio.c:1665: error: âstruct woinstâ has no member named âstateâ
audio.c:1666: error: âstruct woinstâ has no member named âlockâ
audio.c:1671: error: âbytestocopyâ undeclared (first use in this function)
audio.c:1671: error: too many arguments to function âemu10k1_waveout_getxfersizeâ
audio.c:1673: error: âstruct woinstâ has no member named âbufferâ
audio.c:1674: error: âstruct woinstâ has no member named âlockâ
audio.c:1677: error: âstruct woinstâ has no member named âlockâ
audio.c:1679: error: âstruct woinstâ has no member named âbufferâ
audio.c:1680: error: âstruct woinstâ has no member named âwait_queueâ
audio.c:1681: error: âstruct woinstâ has no member named âwait_queueâ
audio.c: At top level:
audio.c:1688: error: variable âemu10k1_audio_fopsâ has initialiser but incomplete type
audio.c:1690: error: unknown field âownerâ specified in initializer
audio.c:1690: error: âTHIS_MODULEâ undeclared here (not in a function)
audio.c:1690: warning: excess elements in struct initialiser
audio.c:1690: warning: (near initialisation for âemu10k1_audio_fopsâ)
audio.c:1692: error: unknown field âllseekâ specified in initializer
audio.c:1692: error: âno_llseekâ undeclared here (not in a function)
audio.c:1692: warning: excess elements in struct initialiser
audio.c:1692: warning: (near initialisation for âemu10k1_audio_fopsâ)
audio.c:1693: error: unknown field âreadâ specified in initializer
audio.c:1693: error: âemu10k1_audio_readâ undeclared here (not in a function)
audio.c:1693: warning: excess elements in struct initialiser
audio.c:1693: warning: (near initialisation for âemu10k1_audio_fopsâ)
audio.c:1694: error: unknown field âwriteâ specified in initializer
audio.c:1694: error: âemu10k1_audio_writeâ undeclared here (not in a function)
audio.c:1694: warning: excess elements in struct initialiser
audio.c:1694: warning: (near initialisation for âemu10k1_audio_fopsâ)
audio.c:1695: error: unknown field âpollâ specified in initializer
audio.c:1695: warning: excess elements in struct initialiser
audio.c:1695: warning: (near initialisation for âemu10k1_audio_fopsâ)
audio.c:1696: error: unknown field âioctlâ specified in initializer
audio.c:1696: warning: excess elements in struct initialiser
audio.c:1696: warning: (near initialisation for âemu10k1_audio_fopsâ)
audio.c:1697: error: unknown field âmmapâ specified in initializer
audio.c:1697: warning: excess elements in struct initialiser
audio.c:1697: warning: (near initialisation for âemu10k1_audio_fopsâ)
audio.c:1698: error: unknown field âopenâ specified in initializer
audio.c:1698: warning: excess elements in struct initialiser
audio.c:1698: warning: (near initialisation for âemu10k1_audio_fopsâ)
audio.c:1699: error: unknown field âreleaseâ specified in initializer
audio.c:1699: warning: excess elements in struct initialiser
audio.c:1699: warning: (near initialisation for âemu10k1_audio_fopsâ)
make: *** [audio.o] Error 1

**** Sorry thought I was posting in multimedia and video, this is relevant to this section also I guess. Feel free to move it, not sure if I can though ****

---

