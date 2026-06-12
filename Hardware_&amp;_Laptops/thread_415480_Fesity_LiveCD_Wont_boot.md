---
title: "Fesity LiveCD Wont boot"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by Loonux on 2007-04-20
Ive done the 'check CD for defects' option and its found no fault. All I get is the orange bar bounding left to right for about a minute, then it dissapears and the screen goes blank/black. The CDRom isn't being read and the machine just sits there. The only key combination that works is CTRL ALT + DEL.

Its a Dell 6400M laptop (C2D) and boots Edgy live CD's fine. Anyone have any idea why this disk wont boot or what i can do to fix it? Ive tried the safe graphics mode and that does the same

Thanks

---

### Post by Rechinica on 2007-04-20
Same here: ATi x1800XL on DVI connection.

---

### Post by thayerw on 2007-04-20
There's a problem with the ATI/Vesa/X config shipped in the final, you can find a workaround here:

[http://ubuntuforums.org/showthread.php?t=414723]("http://ubuntuforums.org/showthread.php?t=414723")

---

### Post by Rechinica on 2007-04-21
Thanks for replying, but for the workaround you need to manually configure your internet connection :(
I think i'll pass, just wanted to give this a try ... not to spend hours searching and configuring stuffs :P

---

### Post by Loonux on 2007-04-21
Yeah, seems a glaring error on a major release.
Will there be a working liveCD released any time soon where this error doesn't stop the OS working? lol!

---

### Post by Rechinica on 2007-04-21
If you follow the link given by thayerw you will find out that the error was known before the final release.

---

### Post by Rechinica on 2007-04-25
I've followed this bug and it seems it's solved: 
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853)

Can i find somewhere an ISO image incorporating the fix so i can boot the LiveCD ?

---

### Post by Loonux on 2007-04-25
> **Rechinica said:**
> I've followed this bug and it seems it's solved: 
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853)

Can i find somewhere an ISO image incorporating the fix so i can boot the LiveCD ?


Is it a case of waiting forr 7.10 perhaps?

---

### Post by strabes on 2007-04-25
Rechinica: It's four commands...

You could do that or just use the alternate install CD.

---

### Post by psusi on 2007-04-25
Try editing the kernel command line and changing the word splash to nosplash.

---

### Post by DeadToad on 2007-04-25
Funny, but I had this same problem loading the Ubuntu Feisty Fawn v7.04 CD using a LCD Flat Panel Monitor.
At the Ubuntu startup screen, after the bars stopped going left to right, and vice-versa, then went solid from left to right, the screen went blank, lockup.
I removed the Flat Panel Monitor and attached a CRT Monitor, rebooted and Ubuntu loaded up, went to the desktop, and installed fine.
Strange.
I can't use my Flat Panel Monitor, only a CRT, on 2 different computers.
:confused:

---

