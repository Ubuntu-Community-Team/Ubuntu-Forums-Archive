---
title: "LITE-ON DH-401S not working"
date: 2008-12-12
forum: Hardware
---

### Post by oxyis on 2008-12-12
Hei

Just setup my new computer with ubuntu 8.10, but I am having problems getting my new LITE-ON Black SATA Blu-ray DVD-ROM Drive Model DH-4O1S to work. I did the actual installation on older Lite-on dvd-rom. So I am trying to get my blu-ray drive to work. I am able to mount the disc and look at the content, but when trying to copy something, I only get this.

```

[619712.659014] end_request: I/O error, dev sr0, sector 12655428
[619712.659019] Buffer I/O error on device sr0, logical block 3163857
[619712.659024] Buffer I/O error on device sr0, logical block 3163858
[619712.659026] Buffer I/O error on device sr0, logical block 3163859
[619712.659029] Buffer I/O error on device sr0, logical block 3163860
[619712.659031] Buffer I/O error on device sr0, logical block 3163861
[619712.659034] Buffer I/O error on device sr0, logical block 3163862
[619712.659036] Buffer I/O error on device sr0, logical block 3163863
[619712.681931] end_request: I/O error, dev sr0, sector 12655428
[619712.681936] Buffer I/O error on device sr0, logical block 3163857
[619712.706819] lirc_imon: vfd_write: no iMON device present
[619712.759087] end_request: I/O error, dev sr0, sector 12656040
[619712.759092] Buffer I/O error on device sr0, logical block 3164010
[619712.759096] Buffer I/O error on device sr0, logical block 3164011
[619712.782007] end_request: I/O error, dev sr0, sector 12656040

```

So far I have tried the following;

[LIST]
[*]Change SATA cable, several
[*]Try different SATA ports on the motherboard
[*]Plug BD-rom into my old windows xp machine, works like a charm
[*]Tried different media, cd, dvd, original data cd'es and 
burned ones
[*]Use speeddrive to turn down speed, not helping
[/LIST]

This leads med to believe this might be a software problem. Have tried googling around, but it doesn't look like there's alot of people have this drive, or are having problems with it. 

I would really appriciate som suggestions on how to test further, are there any hdparm settings which could help? 

oxyis

---

