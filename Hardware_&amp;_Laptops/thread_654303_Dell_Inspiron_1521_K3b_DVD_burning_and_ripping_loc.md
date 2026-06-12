---
title: "Dell Inspiron 1521 K3b DVD burning and ripping lockup freeze TS-L632H"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by nealron on 2007-12-30
My problem has been burning DVDs and ripping audio CDs. On some occasions Kubuntu Gutsy 7.10 would lockup with the CAPS and Scroll Lock lights flashing and other times Kubuntu would just stop responding. Either way the write/read light on the CD/DVD burner (Toshiba Samsung TS-L632H) would flash at a constant rate and would not eject. Each time the ordeal would end up in two hard resets before the Toshiba Samsung TS-L632H CD/DVD drive would reinitialize.

I found there was a [[COLOR="Red"]**_critical**[/COLOR] firmware upgrade_]("http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R173097&SystemID=INS_PNT_PM_1521&servicetag=&os=WLH&osl=en&deviceid=14182&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=32&fileid=235346") to the Toshiba Samsung DVD burner, assuming this would fix the problem I applied the firmware upgrade, from versions D200 to D300.

NO, the firmware upgrade DID NOT WORK. Although it seemed to allow me to recover from the lock ups occasionally, it didn't fix the problem.

Luckily, I had another Inspiron 1521 on hand with a Pioneer DVD burner, one of the two other brands (Pioneer DVR-K17YA and the HLDS GSA-T21N) that could end up in a Dell system that requires a slim form factor DVD burner.

The Pioneer works great with NO problems! If you're having other problems with burning or ripping and or possibly other hardware anomalies, have Dell replace your defective DVD burner, the Toshiba Samsung model TS-L632H. Dell will want to run through a lot of crap and will flip out if you tell them you put Linux on it, so just stick to the story that it freezes every time you burn a DVD and ask them to replace the DVD burner with a Poineer (the other might work too, but I haven't tested it). 

The firmware upgrade _DOES NOT HELP_. After replacing the Toshiba with the Pioneer I haven't had anymore problems burning OR ripping and oddly enough my wireless card isn't dropping connection anymore (could be coincidence, but I'm happy:))

NOTE:
The firmware upgrade ONLY works in M$ Windows/DOS, **don't try it in FreeDOS**. It will fry the firmware on your Toshiba DVD burner, however, if you run the firmware updater from M$ Windows it will restore the firmware so your DVD burner isn't a total loss if you have already tried and failed a firmware upgrade. There really isn't a point in attempting the upgrade anyway, it doesn't solve the problem.

Here are all the systems that could potentially have this CD/DVD burner.

XPS/Dimension 210/9200C
Inspiron 1501
Inspiron 640m / E1405
Inspiron 9400/E1705
Inspiron 1420
Inspiron 1520
Inspiron 1521
Inspiron 1720
Inspiron 1721
Inspiron 1300/B130
Inspiron 6400/E1505
Latitude D530
Latitude D531
Latitude D631
Latitude D420
Latitude D430
Latitude 120L
Latitude 131L
Latitude ATG D620
Latitude ATG D630
Latitude D520
Latitude D620
Latitude D630
Latitude D820
Latitude D830
Dell Precision Mobile WorkStation M65
Dell Precision Mobile WorkStation M90
Latitude D630c
OptiPlex GX520
OptiPlex GX620
OptiPlex 740
OptiPlex 745
OptiPlex 755
Dell Precision Mobile WorkStation M2300
Dell Precision Mobile WorkStation M6300
Vostro Notebook 1000
Vostro Notebook 1400
Vostro Notebook 1500
Vostro Notebook 1700
Dell Precision Mobile WorkStation M4300
XPS M1730
XPS M1210
XPS M1710 

I wrote this up because I figured not many people had another laptop of the exact same model with a different branded DVD burner to test on. It took me a long time to sort all this out and wanted to help the community that has helped me SOOOO many times before. I hope this helps!

---

### Post by luckyluca on 2008-02-06
I have this slimdrive on my m6300 and I get a weird loud noise when I load some dvd video discs.
The led light would start blinking and the eject button would stop working.
It's very frustrating, however all data discs work fine.

Has anybody found a solution/workaround? the last thing I wanna do is get on the phone with dell tech support.....:(

Thanks
Luca

> **nealron said:**
> My problem has been burning DVDs and ripping audio CDs. On some occasions Kubuntu Gutsy 7.10 would lockup with the CAPS and Scroll Lock lights flashing and other times Kubuntu would just stop responding. Either way the write/read light on the CD/DVD burner (Toshiba Samsung TS-L632H) would flash at a constant rate and would not eject. Each time the ordeal would end up in two hard resets before the Toshiba Samsung TS-L632H CD/DVD drive would reinitialize.

I found there was a [[COLOR="Red"]**_critical**[/COLOR] firmware upgrade_]("http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R173097&SystemID=INS_PNT_PM_1521&servicetag=&os=WLH&osl=en&deviceid=14182&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=32&fileid=235346") to the Toshiba Samsung DVD burner, assuming this would fix the problem I applied the firmware upgrade, from versions D200 to D300.

NO, the firmware upgrade DID NOT WORK. Although it seemed to allow me to recover from the lock ups occasionally, it didn't fix the problem.

Luckily, I had another Inspiron 1521 on hand with a Pioneer DVD burner, one of the two other brands (Pioneer DVR-K17YA and the HLDS GSA-T21N) that could end up in a Dell system that requires a slim form factor DVD burner.

The Pioneer works great with NO problems! If you're having other problems with burning or ripping and or possibly other hardware anomalies, have Dell replace your defective DVD burner, the Toshiba Samsung model TS-L632H. Dell will want to run through a lot of crap and will flip out if you tell them you put Linux on it, so just stick to the story that it freezes every time you burn a DVD and ask them to replace the DVD burner with a Poineer (the other might work too, but I haven't tested it). 

The firmware upgrade _DOES NOT HELP_. After replacing the Toshiba with the Pioneer I haven't had anymore problems burning OR ripping and oddly enough my wireless card isn't dropping connection anymore (could be coincidence, but I'm happy:))

NOTE:
The firmware upgrade ONLY works in M$ Windows/DOS, **don't try it in FreeDOS**. It will fry the firmware on your Toshiba DVD burner, however, if you run the firmware updater from M$ Windows it will restore the firmware so your DVD burner isn't a total loss if you have already tried and failed a firmware upgrade. There really isn't a point in attempting the upgrade anyway, it doesn't solve the problem.

Here are all the systems that could potentially have this CD/DVD burner.

XPS/Dimension 210/9200C
Inspiron 1501
Inspiron 640m / E1405
Inspiron 9400/E1705
Inspiron 1420
Inspiron 1520
Inspiron 1521
Inspiron 1720
Inspiron 1721
Inspiron 1300/B130
Inspiron 6400/E1505
Latitude D530
Latitude D531
Latitude D631
Latitude D420
Latitude D430
Latitude 120L
Latitude 131L
Latitude ATG D620
Latitude ATG D630
Latitude D520
Latitude D620
Latitude D630
Latitude D820
Latitude D830
Dell Precision Mobile WorkStation M65
Dell Precision Mobile WorkStation M90
Latitude D630c
OptiPlex GX520
OptiPlex GX620
OptiPlex 740
OptiPlex 745
OptiPlex 755
Dell Precision Mobile WorkStation M2300
Dell Precision Mobile WorkStation M6300
Vostro Notebook 1000
Vostro Notebook 1400
Vostro Notebook 1500
Vostro Notebook 1700
Dell Precision Mobile WorkStation M4300
XPS M1730
XPS M1210
XPS M1710 

I wrote this up because I figured not many people had another laptop of the exact same model with a different branded DVD burner to test on. It took me a long time to sort all this out and wanted to help the community that has helped me SOOOO many times before. I hope this helps!

---

