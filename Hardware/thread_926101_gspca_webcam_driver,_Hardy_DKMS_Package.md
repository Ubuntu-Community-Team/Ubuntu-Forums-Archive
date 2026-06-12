---
title: "gspca webcam driver, Hardy DKMS Package"
date: 2008-09-21
forum: Hardware
---

### Post by IntuitiveNipple on 2008-09-21
I've built a DKMS (Dynamic Kernel Module Support) package containing the gspca driver for Hardy.

It includes support for several recently released cameras such as the Mikomi M6607M and Logitech Quickcam E2500.

This is the complete list of supported USB device IDs:
```

040A:0002 040A:0300
041E:041E 041E:400A 041E:400B 041E:4012 041E:4013 
041E:4017 041E:4018 041E:401A 041E:401C 041E:401D
041E:401E 041E:401F 041E:4028 041E:4029 041E:4034
041E:4035 041E:4036 041E:403A 041E:403B 041E:4051
041E:4053
0458:7004 0458:7006 0458:7007 0458:700C 0458:700F
0458:7025
045E:00F5 045E:00F7
0461:0815 0461:0A00
046D:0890 046D:0892 046D:0896 046D:08A0 046D:08A1
046D:08A2 046D:08A3 046D:08A6 046D:08A7 046D:08A9
046D:08AA 046D:08AC 046D:08AD 046D:08AE 046D:08AF
046D:08B9 046D:08D7 046D:08D8 046D:08D9 046D:08DA
046D:08DD 046D:0900 046D:0901 046D:0905 046D:0920
046D:0921 046D:0928 046D:0929 046D:092A 046D:092B
046D:092C 046D:092D 046D:092E 046D:092F 046D:0960

0471:0322 0471:0325 0471:0326 0471:0327 0471:0328
0471:032D 0471:032E 0471:0330
0497:C001
04A5:3003 04A5:3008 04A5:300A 04A5:300C
04F1:1001
04FC:0561 04FC:500C 04FC:504A 04FC:504B 04FC:5330
04FC:5360 04FC:7333 04FC:FFFF
0506:00DF
052B:1513
0545:808B 0545:8333
0546:3155 0546:3191 0546:3273
055F:C005 055F:C200 055F:C211 055F:C220 055F:C230
055F:C232 055F:C360 055F:C420 055F:C430 055F:C440
055F:C520 055F:C530 055F:C540 055F:C630 055F:C650
055F:D003 055F:D004
0572:0041
05DA:1018
060B:A001
0698:2003
06BD:0404
06BE:0800
06D6:0031
06E1:A190
0733:0110 0733:0401 0733:0402 0733:0430 0733:1311
0733:1314 0733:2211 0733:2221 0733:3261 0733:3281
0734:043B
084D:0003
08CA:0103 08CA:0104 08CA:0106 08CA:2008 08CA:2010
08CA:2016 08CA:2018 08CA:2020 08CA:2022 08CA:2024
08CA:2028 08CA:2040 08CA:2042 08CA:2060
0923:010F
093A:050F 093A:2460 093A:2463 093A:2468 093A:2470
093A:2471 093A:2472 093A:2600 093A:2601 093A:2603
093A:2608 093A:260E 093A:260F
0AC8:0302 0AC8:0321 0AC8:0323 0AC8:0328 0AC8:301B
0AC8:303B 0AC8:305B 0AC8:307B 0AC8:C001 0AC8:C002

0AF9:0010 0AF9:0011
0C45:6001 0C45:6005 0C45:6007 0C45:6009 0C45:600D
0C45:6019 0C45:6024 0C45:6025 0C45:6028 0C45:6029
0C45:602C 0C45:602D 0C45:602E 0C45:6040 0C45:607C
0C45:60C0 0C45:60EC 0C45:60FB 0C45:60FC 0C45:612C
0C45:6130 0C45:6138 0C45:613B 0C45:613C
0D64:0303
102C:6151 102C:6251
10FD:0128 10FD:7E50 10FD:8050
1776:501C
17EF:4802
2899:012C
8086:0110 8086:0630
99FA:8988

```
It is available from my Ubuntu PPA (Personal Package Archive). To install it add my PPA to apt's source list:
```

sudo sh -c "echo 'deb http://ppa.launchpad.net/intuitivenipple/ubuntu $(lsb_release -sc) main' >/etc/apt/sources.list.d/intuitivenipple.list"
sudo apt-get update

```
and then install the package:
```

sudo apt-get install gspca-dkms

```
Remove my PPA from the apt sources to prevent unexpected upgrades of packages I maintain:
```

sudo rm /etc/apt/sources.list.d/intuitivenipple.list
sudo apt-get update

```

---

### Post by lucis on 2008-09-21
I tried downloading the deb file manually (the repository didn't seem to work) and it gave me this error upon install:

Selecting previously deselected package gspca-dkms.
(Reading database ... 160964 files and directories currently installed.)
Unpacking gspca-dkms (from .../gspca-dkms_01.00.20-1ubuntu2~ppa1h_all.deb) ...
Setting up gspca-dkms (01.00.20-1ubuntu2~ppa1h) ...
Loading new gspca-01.00.20 DKMS files...
/var/lib/dpkg/info/gspca-dkms.postinst: 68: dkms: not found
dpkg: error processing gspca-dkms (--install):
 subprocess post-installation script returned error exit status 127

---

### Post by IntuitiveNipple on 2008-09-22
> **lucis said:**
> I tried downloading the deb file manually (the repository didn't seem to work) and it gave me this error upon install:

Selecting previously deselected package gspca-dkms.
(Reading database ... 160964 files and directories currently installed.)
Unpacking gspca-dkms (from .../gspca-dkms_01.00.20-1ubuntu2~ppa1h_all.deb) ...
Setting up gspca-dkms (01.00.20-1ubuntu2~ppa1h) ...
Loading new gspca-01.00.20 DKMS files...
/var/lib/dpkg/info/gspca-dkms.postinst: 68: dkms: not found
dpkg: error processing gspca-dkms (--install):
 subprocess post-installation script returned error exit status 127
What Ubuntu version and kernel are you trying to install it on?

The output above suggests the system doesn't have the **dkms** package installed. 
```

/var/lib/dpkg/info/gspca-dkms.postinst: 68: dkms: not found

```
That is strange since I thought it was installed by default from Hardy onwards.

However that made me check the package's Depends and I found I hadn't changed it from the old gspca-source settings when I converted it to DKMS. I've corrected that now and uploaded the revised package.

The repository installation steps should have worked - maybe the PPA system was having problems when you tried it. When the "apt-get update" command is run you should see " http://ppa.launchpad.net/intuitivenipple/ubuntu" reported as the package lists are downloaded.

---

### Post by beatlefan on 2008-09-29
My friend just got the exact same Mikomi cam, and he cant get it to work either.
He installed the dkms package without any errors, but he still can't get an image.

Anyone having luck with this?

He really loves ubuntu so far, but the cam is one thing that's making him think about windows again which wouldn't be so cool.

---

### Post by Clochard on 2008-10-02
I've installed the package by downloading it (doesn't exist in the Gutsy repo you have, but Hardy's version installs fine).

After installing it ... what do I do now?  Do I also need a special Microdia driver ([http://groups.google.com/group/microdia?hl=en)?](http://groups.google.com/group/microdia?hl=en)?)

Do I rmmod stuff?  Unplug/replug the camera?  Really not clear on what drivers I need to install to get this thing working, though I really appreciate the PPA.  Any further instructions?

Also, how does this relate to this other gspca driver specific to my camera (0c45:60c0): [http://www.pamplast.com/gspca/ubuntuguide.html](http://www.pamplast.com/gspca/ubuntuguide.html)

---

### Post by intel on 2008-10-15
This webcam should be supported by GSPCA v2, if its not file a bug report to get it supported by it

---

### Post by Lampi on 2011-07-02
Is there a new gspca dkms package for lucid? The gspca tree in 2.6.32 contains several bugs concerning my webcam, I already checked it was fixed in the 2.6.39 stable kernel.

Edit: Solved thanks to [Parrameister]("http://ubuntuforums.org/showpost.php?p=10129922&postcount=12")

---

