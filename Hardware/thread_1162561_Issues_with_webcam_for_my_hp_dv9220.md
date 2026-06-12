---
title: "Issues with webcam for my hp dv9220"
date: 2009-05-17
forum: Hardware
---

### Post by almightyox on 2009-05-17
I am using Ubuntu 9.04 and am having issues getting the webcam working i've tried instructions from other threads but they didnt seem to work for me. This webcam is built into the monitor so its not being detected at all. Any help will be welcomed and thanks in advance.

Here is my printout from the lsusb command.
Bus 001 Device 003: ID 05ca:1810 Ricoh Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jason@jason-laptop:~$ lsusb
Bus 001 Device 003: ID 05ca:1810 Ricoh Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by samcompton on 2009-05-17
I think I have the same camera as you in my HP notebook dv6000 series.  I have spent way more time than I should trying to get the webcam to work with 9.04.  I don't think I ever got it working in 8.10 as well.  I stayed with 8.04 until 9.04 hoping it would have incorporated the driver into the kernel but, no such luck.  If you want to use this particular camera with Ubuntu you need to install 8.04 fresh install.  Then get the r5u870 driver for Ricoh Webcams.  I found it easiest to Install Easycam 2 and let it compile the drivers for you.  Worked pretty well.  Cheese never worked for me.  Skype and Ekiga both worked fine.  Xawtv worked as far as a sort of replacement for cheese.  I have given up on the cam.  I am staying with 9.04 and going without cam for now.  Good luck.

---

### Post by almightyox on 2009-12-31
I gave up on it too but tried it again when i downloaded, 9.10 and it wasn't working still.  So i downloaded the r5u870 driver for Ricoh Webcams that you mentioned from softpedia and got it to work with skype now which is what i really wanted.

For those having this same issue make sure to download the firmware first than download the regular drivers for it. thats how i got it to work now i am happy.:)

---

