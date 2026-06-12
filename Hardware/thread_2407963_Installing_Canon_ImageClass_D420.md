---
title: "Installing Canon ImageClass D420"
date: 2018-12-11
forum: Hardware
---

### Post by G0at1 on 2018-12-11
Hello,

I'm new to Ubuntu and have no clue what I'm doing! I've spent hours blindly trying to install my Canon ImageClass D420 printer but nothing is printing. I've read posts and watched videos on youtube to no avail. Can someone show me step by step please?

I've installed Ubuntu 18.04 LTS and have the printer connected via a USB cable. I've also downloaded the drivers from Canon's website (linux-UFRII-drv-v360-usen.tar.gz).

Thank you!

---

### Post by malangaman on 2018-12-11
Did you per chance look at this link?
[https://askubuntu.com/questions/348041/how-do-i-make-canon-imageclass-d420-work-in-ubuntu](https://askubuntu.com/questions/348041/how-do-i-make-canon-imageclass-d420-work-in-ubuntu)

---

### Post by G0at1 on 2018-12-12
That’s one of the first posts I read but I don’t know how to switch to that folder to even get started. I have the drivers on my Desktop. I’m typing cd Desktop. My knowledge is literally 0. &#65533;&#65533;

By the way when I go to the printers that I have, I see D400-450-(UFRII-LT) but again, nothing prints. I’ve done a bunch of code and double clicking. I don’t know what the heck I did.

---

### Post by howefield on 2018-12-12
If you right click on the downloaded file and select the "extract here" option, it should extract to a new folder on your Desktop. Then from a terminal type in the command..

```
sudo apt install -s /home/USER/Desktop/linux-UFRII-drv-v360-usen/64-bit_Driver/Debian/*.deb
```

Substitute your actual username in the path above instead of using "USER"

---

### Post by G0at1 on 2018-12-12
You gotta be kidding me. That&#8217;s all it took? I spent over 9 hours on this. Thank you thank you! [-o

---

### Post by howefield on 2018-12-12
Apologies, a small typo in the command I gave you, you won't need the -s option which means the install is simulated. I tested the command with that switch but to actually install you won't want to use it.

```
sudo apt install /home/USER/Desktop/linux-UFRII-drv-v360-usen/64-bit_Driver/Debian/*.deb
```

---

### Post by G0at1 on 2018-12-12
It still worked though. Should I redo?

---

### Post by slickymaster on 2018-12-13
*Thread moved to **Hardware**.*

---

### Post by G0at1 on 2018-12-20
Hi there... I had to reinstall Ubuntu and now don't know how to reinstall my printer. Can you help please? I ran the above command, then went into Printers and clicked Add. Now I have CUPS-BRF-Printer, which is not working.

---

### Post by G0at1 on 2018-12-21
Ready to pull my hair out :D Please help me :)

---

