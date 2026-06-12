---
title: "Two Problems"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by lanman64 on 2009-05-19
Hey everyone. I installed Ubuntu 9.04 yesterday and am now having two problems with my computer. I am dual-booting with WinXP, and although I had several problems with that, I think I have fixed them. However, there are two problems that I am having that I am clueless on.

The first problem happens for sure in WinXP, but I am unable to see if it will happen in Ubuntu for the reason that will be listed in problem two. When I shut down my computer, it goes through the regular steps. It saves my files, then I hear what sounds like the hard drives turning off, and then the monitor turns off. However, my tower no longer turns off. I shut down my computer five minutes ago, and my tower was still on. I have no clue why this is happening or how to fix it, but I would love it if I could get my tower to turn off on its own again.

The second problem is with Ubuntu itself. I booted into Ubuntu three times after installing it and every time I had the same result. Ubuntu does a hard freeze within a minute. The first time I was just seeing what programs there were, the second time I was trying to use the terminal, and I don't remember what I was doing on the third try. I installed it with ext4, but I do not know if this is the problem.

If anyone has any suggestions on how to fix these problems, I would be grateful.

---

### Post by dstew on 2009-05-19
Does the tower turn off when you shut down a Live CD system?

---

### Post by lanman64 on 2009-05-19
Okay, I just booted into the LiveCD and shut down. When I shut down, the tower turned off, which leads me to believe that it is a problem with Windows. However, something else happened. The first time I booted into the LiveCD, I let it sit for a second. I was about to shut it down when it froze again. This makes me wonder if it's a hardware problem rather than an install problem.

As for the tower not turning off, I should probably mention one of the problems I fixed yesterday in case that had something to do with it. After I installed Ubuntu, I tried booting XP up again. When I did this, it said that hal.dll was missing and that I needed to reinstall it. I tried several solutions and none of them worked, but I finally found a website that told me to type this command in the Recovery Console on the XP installation disk: bootcfg /rebuild. I did everything that I was prompted to and it finally worked. However, when I rebooted, acted as if I had just reformatted without losing any of my files or programs. Windows proceeded to find and install all the drivers for basically all of my hardware. In addition, I see that the "Standby" option in the shutdown menu is no longer lit up indicating that I cannot use it. Is any of this an indication of what the problem might be?

---

### Post by dstew on 2009-05-19
It is possible that you damaged the Windows system somehow when you first installed Ubuntu, and that the Recovery Console did a semi-reinstall of Windows. If the Standby mode is greyed out, perhaps you need to do something special to re-install that feature. I do not know much about Windows, but maybe there is a "Install Windows Components" menu or something like that you can check to see if the power management control panel can be upgraded to do standby. Or, maybe to do standby Windows needs a separate partition to put its memory into when it goes into standby. Maybe you accidentally removed that partition when you installed Ubuntu. You might need to check on some Windows forums.

---

### Post by lanman64 on 2009-05-19
Alright, I've posed my shutdown question on another forum, but does anyone have any ideas why both my installed and LiveCD Ubuntu keep freezing on me?

---

### Post by dstew on 2009-05-19
Do you have a Live CD of a different distribution, like 8.04? If that one doesn't freeze, then it is probably some aspect of the 9.04 software that is causing the problem. If 8.04 freezes, that would sound more like hardware. For example, ext4, which is on 9.04, can cause problems with some applications.

---

### Post by lanman64 on 2009-05-19
I don't have any other versions, but I will definitely try that.

---

