---
title: "Laptop crashing after startup, fresh install"
date: 2011-10-21
forum: Hardware
---

### Post by Ika-Ika on 2011-10-21
Hello. I hope this is the right board to ask this. I also looked through existing threads and didn't find one that fits my problem well. And I'm fairly new to Ubuntu and Linux so please go easy on me.

My old Toshiba Satellite A100-528 running Windows XP started crashing down on me so I decided it's a good opportunity to switch it to Ubuntu. I salvaged all important files in safe mode, wiped the drive, set filesystem to ext4 and installed 11.04 (didn't have a blank CD to make 11.10 disk). It started up nicely but as soon as I opened some configuration windows, it crashed. I didn't even change anything, didn't have a chance for that. Recovery console worked fine so I restarted the system. I browsed my system files in Nautilus for a while but running Firefox crashed the system again. I even reinstalled the whole system again but it still crashes.

I thought it might be a overheating problem so I cleaned the heatsink. I even bothered to bust open the case and clean the whole mainboard (it was covered with a thin layer of dust), still crashed like before.

Funny thing is, it seems to work just fine in safe mode. What could be the problem? Should I finally buy a new Laptop?

---

### Post by followurdrmz on 2011-10-21
Posting your laptop specs might be helpful.

---

### Post by Ika-Ika on 2011-10-21
Sorry, forgot about that.

Intel Celeron M 1.60GHz
431 MB RAM

That's all that system monitor says (apart from software versions), if there's anything else that could help in solving this, just tell me.

---

### Post by followurdrmz on 2011-10-22
I see your laptop specs are very close to the minimum hardware requirements for ubuntu 11.04 which might result in bad perfomance. ubuntu 11.04 uses unity 3D desktop which i think needs a better processor and graphic card (Please mention make and model).
Try logging in with classic desktop at logon prompt or use xfce desktop and lowering your screen resolution will help.
RAM is less so try disabling unwanted startup items and processes.
You can find a lot of stuff in here for tuning ubuntu. Please search.

---

### Post by Ika-Ika on 2011-10-23
I tried running classic mode with and without effects. With effect it crashes instantly, without them it seems to work just fine. I didn't test running more demanding apps yet though. But I guess no effects is far better than nothing at all so thanks for the tip.

---

### Post by varunendra on 2011-10-25
> **Ika-Ika said:**
> I tried running classic mode with and without effects. With effect it crashes instantly, without them it seems to work just fine. I didn't test running more demanding apps yet though. But I guess no effects is far better than nothing at all so thanks for the tip.
You may like (maybe love!) [Xubuntu]("http://www.xubuntu.org/"). Default Ubuntu 11.04 (even in classic mode) is a "torture" for your hardware :). Xubuntu being lighter does not mean it is less capable or less friendly. Give it a try via live cd, then install if you like it.

---

### Post by followurdrmz on 2011-11-13
> **Ika-Ika said:**
> I tried running classic mode with and without effects. With effect it crashes instantly, without them it seems to work just fine. I didn't test running more demanding apps yet though. But I guess no effects is far better than nothing at all so thanks for the tip.

Seems like your laptop is doing good. Did you try Lubuntu? If not, you should try it out. It a a lightweight version of ubuntu. Only thing you'll miss will be the 3D or aero kind of stuff. I am using it now on my dell inspiron and I have completely moved from windows to ubuntu. I wish i had done this before.
 There are a lot of customization stuff in Lubuntu too. I think your laptop might like it. Look for the official download [LINK]("https://wiki.ubuntu.com/Lubuntu").

---

