---
title: "Would I miss much going from Hardy to Gutsy?"
date: 2008-11-10
forum: General Help
---

### Post by sumpm1 on 2008-11-10
This is my first go around with Linux operating systems and I tried Hardy first. Hardy does not support my graphics tablet (or perhaps associated usb controller), but Gutsy does. I use Compiz, TVTime for television, and Virtualbox for Windows emulation for Photoshop. 

First of all, can anyone vouch for ANY tablet being useful in Linux? I would like to be able to use Photoshop one way or another, but wonder if the tablet integration would work with pressure sensitivity and everything, or even in Gimp. So would it be worth downgrading to Gutsy just for this hardware support? Is software as easily to install and readily abundant packages for Gutsy?

Thanks

---

### Post by LoneWolfJack on 2008-11-10
hm... sounds fishy that hardy doesn't support your tablet but gutsy does. after all, the drivers are written for linux in general, not any specific distro version.

if gutsy works out of the box for you but hardy does not, there's probably a piece of hardware in your machine that's causing troubles with updated drivers ot the new kernel.

even though I personally think hardy wasn't a great release, I'd try to fix the issues rather than going back to an older version. you will probably just have to do some config editing to get it working.

---

### Post by wgrant on 2008-11-10
Ubuntu 7.10 (Gutsy) is only supported for another 5 months, so it's rather inadvisable to downgrade to it at this stage.

Have you tried Ubuntu 8.10? Your tablet's stylus should work without any configuration, but things such as erasers might take a bit of X configuration. See [our Wacom documentation](https://help.ubuntu.com/community/Wacom).

---

### Post by sumpm1 on 2008-11-10
> **LoneWolfJack said:**
> hm... sounds fishy that hardy doesn't support your tablet but gutsy does. after all, the drivers are written for linux in general, not any specific distro version.

if gutsy works out of the box for you but hardy does not, there's probably a piece of hardware in your machine that's causing troubles with updated drivers ot the new kernel.

Well, since I have installed 8.04 on this machine, the power light on the tablet fails to even come on in Ubuntu. And the problem is machine specific because I have 8.04 running on  my laptop, and it has no problems with the tablet, works flawlessly. But I tried 8.10 from Live cd, and the problem is the same as in 8.04 on my desktop. But the 7.10 live cd started the tablet fine; I have read about others having trouble with usb devices and 8.04.

---

### Post by LoneWolfJack on 2008-11-10
I don't think your problems are related to different ubuntu versions. Perhaps you should start a thread about hardy not recognizing USB hardware that gutsy did recognize. I can't really help you there because I never had problems with USB devices and so I never tangled with the USB config. :)

---

### Post by DrMega on 2008-11-10
> **wgrant said:**
> Ubuntu 7.10 (Gutsy) is only supported for another 5 months, so it's rather inadvisable to downgrade to it at this stage.

Has the kernel issue that causes random freezes in Hardy been fixed yet?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/239021]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/239021")

---

