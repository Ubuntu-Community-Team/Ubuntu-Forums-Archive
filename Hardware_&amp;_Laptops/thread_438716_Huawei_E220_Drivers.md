---
title: "Huawei E220 Drivers"
date: 2007-05-10
forum: Hardware &amp; Laptops
---

### Post by NovaNine on 2007-05-10
Hi guys.
I'm looking if there exists Huawei E220 drivers for Ubuntu ? I have googled and [found people]("http://www.mail-archive.com/linux-usb-devel@lists.sourceforge.net/msg48419.html") who've installed it on slackware, but I want to stick with Ubuntu :D 

Anyone knows anything ?

---

### Post by NovaNine on 2007-05-13
B.u.m.p

---

### Post by JockeTF on 2007-05-14
Hello, this post helped me to get my Huawei e220 working:
[http://ubuntuforums.org/showpost.php?p=1772796&postcount=8](http://ubuntuforums.org/showpost.php?p=1772796&postcount=8)

Link to the whole topic:
[http://ubuntuforums.org/showthread.php?t=262867](http://ubuntuforums.org/showthread.php?t=262867)

However you might want to send the device your pin-code before you use wvdial to connect to the internet, you can do that with the following command:

```
sudo echo AT+CPIN=[PIN-code] > /dev/ttyUSB0

```

Without the "[" and "]" ofcourse.
Oh and remember to search the forums as well, not just google. ;)

// JockeTF :mrgreen:

---

### Post by mormor on 2008-03-04
[https://forge.vodafonebetavine.net/frs/?group_id=12&release_id=19](https://forge.vodafonebetavine.net/frs/?group_id=12&release_id=19)

vodafones drivers works fine in norway

---

### Post by exWin4eva on 2008-03-11
it's really easy if you still stuck just bump I will get you online sameday service

---

