---
title: "Ubuntu Mate 17.10 can't find wireless scanner (Canon Pixma MX922)"
date: 2018-01-24
forum: Hardware
---

### Post by m63k on 2018-01-24
So I got my all in one Canon printer set up to print okay wirelessly via LDP and a static IPv4 address in Ubuntu Mate 17.10, but I can't seem to figure out how to get it to scan wirelessly via Simple Scan. I get the error *No Scanner Found.* I have looked around the Net and on youtube videos on how to accomplish getting this to work wirelessly, but haven't found anything that seems to work. I looked at this ( [https://help.ubuntu.com/community/ScanningHowTo](https://help.ubuntu.com/community/ScanningHowTo) ) page, but it doesn't talk about Canon printers. My printer is a Canon Pixma MX922 all-in-one printer-scanner-fax. It is powered on when I try to get the scanner connected. Any help getting this to work would be greatly appreciated, including pointing me in the right direction as far as a video, support page, or community forum page. Thanks in advance.

---

### Post by him610 on 2018-01-24
hello m63k and welcome to the forum.

You might get some information from site...
[https://forums.linuxmint.com/viewtopic.php?t=223352]("https://forums.linuxmint.com/viewtopic.php?t=223352")

After you think you have it setup, from the command line, run this command...
```
scanimage -L
```
It will show all scanners that are connected to your system.

---

### Post by pdc on 2018-01-25
there have been quite a few reports of "no scan" with 17.10; if you file a bug report with Ubuntu; please google on how to do this

---

