---
title: "Display completely corrupted after GPU driver install"
date: 2008-08-03
forum: Hardware
---

### Post by Cyber Akuma on 2008-08-03
I have a toshiba laptop, it came with ATI Radeon X1200 3D hardware.

I downloaded the latest version of their drivers ( [http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html) ) and tried to install them.

Everything seemed to go smoothly, however, after the install when I rebooted the laptop the display was corrupted.

The cursor still worked fine, as did the login screen, but after I loaded the desktop the screen was sorta split half-way with a checkerboard-shape making up my displaying, the squares alternating from each "half" of the screen.

Text looks like completely gibberish.

A few months ago, I had attempted to install these drivers before. IIRC, they didn't have a GUI-based installer like this time and required I use several shell commands.

Does this problem sound familiar with anyone?

Is it possible this previous install attempt conflicted with the new drivers I attempted to install?

How do I remove both of them and attempt to re-install the drivers?

---

### Post by Cyber Akuma on 2008-08-04
Anybody?

---

### Post by phidia on 2008-08-04
There is a thread [here]("http://ubuntuforums.org/showthread.php?t=823281&highlight=ati+x1200") on ATI cards of that series. Unfortunately the last post in the thread didn't contain a link to the mentioned bug, but I have seen problems mentioned with that card. 
You can [report a bug]("https://launchpad.net/ubuntu"). In fact I recommend it.

---

### Post by Cyber Akuma on 2008-10-01
Damn, I seriously need to come here more often.

Anyway, the problem is I had previous drivers installed in a different way before, and I just want to make sure those aren't intefering with the new drivers I installed before reporting a bug.

Plus I want to get my Ubuntu install working again so I can actually use the GUI.

How can I revert back so I can get the GUI to work again?

---

### Post by Cyber Akuma on 2008-10-03
Umm, does anybody have any advice about this?

---

### Post by markbuntu on 2008-10-03
Did you remove the old drivers before installing the new one?
If not, you may have the wrong kernel modules installed which can generate unpredictable behavior. I would recommend removing previous drivers completely and then using this guide:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

