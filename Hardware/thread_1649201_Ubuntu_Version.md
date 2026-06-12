---
title: "Ubuntu Version"
date: 2010-12-19
forum: Hardware
---

### Post by wakin125 on 2010-12-19
Hi, i am new to ubuntu. i currently have ubuntu 10.10 64-bit installed. i watched youtube tutorials on how to set everything up. Everything works fine except some games i installed with wine dont work. At first my CoDMW worked with the 1.0 patch but lagged very bad. then when i installed the 1.7 patch it just crashes on startup. My graphics card is fully capable of playing cod4 maxed out (at least on windows) but lags very bad even in lowest settings on ubuntu. Does anyone know how to fix this? and Microsoft Office Powerpoint 2007 crashes too. all of the other MS office programs work perfectly. and when i try installing call of duty game of the year edition, swapping discs doesnt work. Can someone help?

---

### Post by Fafler on 2010-12-20
Theres an application database at appdb.winehq.org. It has specific info for almost any program or game you can imagine. The CD change issue can be solved by using winecfg to setup your CD drive and running ```
wine d:\Install.exe
```
instead of
```
wine /path/to/file/Install.exe
```

---

### Post by wakin125 on 2010-12-22
does it matter what letter i use for the code? i have wine installed on my c: drive.

---

### Post by Fafler on 2010-12-23
No, you have to setup your CD drive as D: in the wine config. wine C:\Install.exe would equal to the wine ~/.wine/drive_c/Install.exe. D: should point to where Ubuntu mounts the CD-ROM.

[https://help.ubuntu.com/community/Wine#Adding%20CD%20and%20DVD%20drives%20to%20Wine](https://help.ubuntu.com/community/Wine#Adding%20CD%20and%20DVD%20drives%20to%20Wine)

---

### Post by rotave on 2010-12-23
If you haven't tried it, check out playonlinux. It makes it easier to install games and apps made for windows especially for noobs. You can get it here [http://www.playonlinux.com/en/]("http://www.playonlinux.com/en/")

---

