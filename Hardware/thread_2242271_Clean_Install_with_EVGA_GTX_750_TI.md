---
title: "Clean Install with EVGA GTX 750 TI"
date: 2014-08-31
forum: Hardware
---

### Post by matthew31 on 2014-08-31
I can't install Ubuntu with my graphics card in, I just get a black screen.

Ubuntu installs fine with my intel graphics, so I tried to install 'nvidia-current-updates' and then reboot with my graphics card plugged in, but nothing.

Is there any way to do a fresh install while using the proprietary nvidia driver?

---

### Post by grahammechanical on 2014-08-31
The Ubuntu live session uses an open source video driver. Which for Nvidia cards is called Nouveau. When we install and tick the box "install third party software" we get a proprietary video driver installed.

So, if we run the live session and we get to a working desktop and then we install and tick the box to install third party software and then get a black screen when we reboot for the first time, then logically the problem must be to do with the proprietary video driver. That is my reasoning.

So, to answer your question. Just tick the box to install third party software. But my advice would be not to tick the box. Get to a working desktop and then install Ubuntu Restricted Extras and then open System Settings>Software and Updates>Additional Drivers tab and wait for the system to find some drivers and experiment.

If you get past the login screen but get to a desktop with just wallpaper background and without a top panel and the launcher, then right click the background and select Change Desktop Background. That will open System Settings and from there you can get the Additional Drivers and continue with the experiment.

Edit: re-reading your post I would suggest that your problem might be to do with the fact that your have hybrid graphics. Do you have Nvidia Optimus technology?

Regards

---

### Post by matthew31 on 2014-08-31
My exact card is the 02G-P4-3753-KR if that helps. Nouveau crashes whenever it tries to load this card. Other Nvidia cards I own work fine.

I'm unable to even get Ubuntu to boot period with it plugged in. The screen just goes black.

It works fine with Intel graphics, and I tried out Debian with the command line installer which also worked until I loaded up my window manager.

The card also works fine under Windows.

I just need to somehow install the software from command line before X loads at all. It seems Ubuntu no longer has a CLI installer.

---

