---
title: "Samsung Syncmaster 710v TFT Optimum Mode Message!"
date: 2009-04-12
forum: Hardware
---

### Post by Rytron on 2009-04-12
Hi. I was given a TFT monitor with an old PC today. I connect the old PC to the TFT monitor but I get this message on the screen.:
[B]'Not Optimum Mode
Recommended 1280 * 1024
60Hz'[/B]
Also it has a 'question mark in a yellow box' under the message.

I cannot actually get into the computer to change the resolution. There are buttons on the front of the monitor but I don't know what to do with them.

To make sure the problem was not with the old PC, I connected the TFT monitor to my current PC and the same message pops up. There must be a problem with the TFT monitor cable or the TFT monitor itself.

Would I need to change something in the BIOS?

Please help.

Thank you.

---

### Post by schmidtbag on 2009-04-13
how old is the pc?  what hardware does it have?  the buttons on the monitor probably don't have anything to do with what you want

---

### Post by Rytron on 2009-04-13
> **schmidtbag said:**
> how old is the pc?  what hardware does it have?  the buttons on the monitor probably don't have anything to do with what you want

The monitor did work for the old PC(6 years old) before but just seemed stop working for an unknown reason. The old PC works fine with my CRT monitor. My newer PC is 2 years old.

---

### Post by schmidtbag on 2009-04-13
6 is old but new enough that you shouldn't get video issues.  do you know what the video card is?  like anything about it?

---

### Post by Rytron on 2009-04-14
> **schmidtbag said:**
> 6 is old but new enough that you shouldn't get video issues.  do you know what the video card is?  like anything about it?

Newer PC: Video Adapter NVIDIA GeForce 7600 GT 256 MB
Old PC: Video Adapter RADEON 8500 SERIES (64 MB)

---

### Post by schmidtbag on 2009-04-14
i had a radeon 7500 and that worked fine, just no 3d support.  maybe you just have to reset xorg because your monitor can't go above 1152x864.  boot up into recovery mode to do this.  if that doesn't help, boot up into recovery mode again, go into root shell, and type "sudo nano /etc/X11/xorg.conf" and then if theres a resolution specified in there somewhere, change it to 1024x768.

---

### Post by bombjack7000 on 2009-05-31
Try this solution:

[http://translate.google.com/translate?hl=en&sl=es&u=http://www.dtforum.net/index.php%3Ftopic%3D55304.msg1010695085%253Btopicseen&prev=/search%3Fq%3DNT68F63LG%2B50%2Bohm%26hl%3Den%26rlz%3D1T4SUNA_enUS219US220](http://translate.google.com/translate?hl=en&sl=es&u=http://www.dtforum.net/index.php%3Ftopic%3D55304.msg1010695085%253Btopicseen&prev=/search%3Fq%3DNT68F63LG%2B50%2Bohm%26hl%3Den%26rlz%3D1T4SUNA_enUS219US220)

For short: bridge pins 5 + 6 of the novatek ic on the lcd board with a 50 ohms resistor. Seems to be a design flaw/ degradation issue with the ic.

---

### Post by Rytron on 2009-05-31
> **bombjack7000 said:**
> Try this solution:

[http://translate.google.com/translate?hl=en&sl=es&u=http://www.dtforum.net/index.php%3Ftopic%3D55304.msg1010695085%253Btopicseen&prev=/search%3Fq%3DNT68F63LG%2B50%2Bohm%26hl%3Den%26rlz%3D1T4SUNA_enUS219US220](http://translate.google.com/translate?hl=en&sl=es&u=http://www.dtforum.net/index.php%3Ftopic%3D55304.msg1010695085%253Btopicseen&prev=/search%3Fq%3DNT68F63LG%2B50%2Bohm%26hl%3Den%26rlz%3D1T4SUNA_enUS219US220)

For short: bridge pins 5 + 6 of the novatek ic on the lcd board with a 50 ohms resistor. Seems to be a design flaw/ degradation issue with the ic.

Thanks bombjack7000. I will give it a try.

---

### Post by bostjan242 on 2010-12-08
Hello

I know this post is old. I have the same problem. I want to setup twin view  on my laptop, it is a Dell Inspiron 1520 with GF8500 MGT. Twin view worked fine until I installed new updates. Then the monitor(Samsung SyncMaster 710T) started showing message "Not Optimum Mode  Recomended Mode : 1280x1024 60Hz". Can anybody please help?

And a little note to the developers of Ubuntu. I know ubuntu is free, but it would be nice if you tested updates, before you give them into production. The latest package of updates crashed eclipse and twin view on my computer.

Thank you

---

