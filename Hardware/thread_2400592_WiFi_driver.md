---
title: "WiFi driver"
date: 2018-09-07
forum: Hardware
---

### Post by agemini68 on 2018-09-07
I have an RTL8811AU dual band wifi adapter. It states it supports Linux and specifically mentions ubuntu but it came with a tar.gz file and won't install. Has anyone come up with a debian install for this? I don't know what to do with tar files . Command line suggestions are all failing.

---

### Post by dt3 on 2018-10-11
have You tried unpack Your file? 
Basically command:
```
 tar -xvvf packagename
```
should do the job.

If it won't work, just paste here the output.

---

### Post by erikoma on 2018-10-12
Pardon me for butting in. I have tried a card that was said to be Ubuntu compatible, but it was only supported by the desktop version (with Network Manager), and NOT by the server version. I have three Ubuntu servers, as web server, mail server and regular backup. Because I need to move them to another room in order to operate them, I would prefer to have them all on WiFi (with only a power plug to connect), and they should be operable after boot, without any login. So is this card compatible with Ubuntu 18.04 Server (or newer), or can anyone recommend a card that's available today, and that can be used for this purpose? The faster the better (=>150 Mb/s). I have a script that can identify and configure the card if the correct driver is available.
Thanks!

---

