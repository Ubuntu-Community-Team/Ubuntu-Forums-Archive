---
title: "Dual monitor works, but there is something wrong with the colors."
date: 2006-01-09
forum: Installation &amp; Upgrades
---

### Post by Renko on 2006-01-09
Hi there,

Today I installed Ubuntu on my computer. However I have limited experience with linux (on server as on desktop) I consider myself als newbie so you know that ;). Anyway, I have two monitors, they are the same model. They are attached on one videocard, the Sapphire Radeon 9800Pro. One is connected trough the VGA port, the other one trough the DVI port with a DVI to VGA converter. With some help of Google (what leads to this forum) I created a working X.org config ([xorg.conf](http://meuk.datafeest.net/xorg.conf)). 
But, There is a problem left. On my right monitor some colors are dropped. I made a screenshot and edited it The GIMP to see what I mean. See [welcometoubuntu.png](http://www.virtual-life.net/img/getimg/welcometoubuntu.png). I also made a picture with a digital camera, check it out [here](http://www.virtual-life.net/img/getimg/P10100372.JPG)
 This problem occurs with the standard config (without dual monitor support) too, also on Suse 9.3 and Suse 10.0. By changing my monitor cables I confirmed this problem has nothing to do with my monitor, and that's quite logical because on Windows 2000 this problem does not occur.

I hope that someone who reads this have a solution (or at least an explanation) of this problem. Thank you very much for your time! :)

(btw, I'm running Ubuntu 5.0.4, just because I had that Cd-rom here. I don't this this matters for this issue)

---

### Post by Renko on 2006-01-10
Ok, I was able to solve the problem by installing the official ATi drivers.
[https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300) I choosed the 'ATI Driver Installer'. It's pretty easy to install. :)

Maybe someone could use this information on a later time. ;)

---

