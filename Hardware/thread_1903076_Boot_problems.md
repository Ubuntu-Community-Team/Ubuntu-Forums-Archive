---
title: "Boot problems"
date: 2012-01-01
forum: Hardware
---

### Post by srem on 2012-01-01
I have a 5 years old Dell laptop with an NVIDIA video card. I have installed on it Ubuntu 10.04 (Unity is not supported by the graphic card).

Recently my IDE hard disk crashed and I have changed it for a new larger IDE model. I have partitioned it and reinstalled Ubuntu 10.04, including the proprietary NVIDIA driver.
Even if the installation completed successfully, the laptop doesn't boot, i.e. the hard disk led gets stuck on and the screen stays black, without prompt, where I can type/see any character.

After few changes in the Grub confiuration which I read in the forums, I managed to make it boot up, In order to make it boot I need to press shift after the Bios, which makes the Grub multi boot menu show up, where I select the first entry. This way it works 80% of the times, going to the graphic ubuntu boot screen, a quick NVIDIA boot screen and then finally into my Ubuntu environment.

Do you think it may be related to the new hard disk? I doubt it as when it boots, everything works out fine. Could it be the Nvidia driver?
Any suggestions on how to fix it? I am kind of tired having to reboot it 4-5 times before entering into my account. Thanks!

---

### Post by Mark Phelps on 2012-01-02
IF manually selecting the first GRUB entry works, and letting the GRUB boot default does not, I would suggest installing Grub-Customizer and using it to set the first GRUB entry as the default.

See below:

[http://ubuntuforums.org/showthread.php?t=1664134&highlight=Grub+Customizer]("http://ubuntuforums.org/showthread.php?t=1664134&highlight=Grub+Customizer")

---

### Post by srem on 2012-01-06
Thanks for the suggestion, but I doubt the problem is there:

1) when I boot, the grub screen never shows up. (90% of the times I get the black screen, 10% i get the correct boot)

2) when I press shift while booting, I get he grub screen. The first entry, is the default one.

---

### Post by anushcbe on 2012-01-07
when i boot up the ubuntu is taking an alot of time in loading it's kernel & it's infrastructure(Ubuntu) to get an lodging screen.

Sys config:

DELL XPS L401X
Intel core i7 cpu Q740 @ 1.73GHz / 8GB RAM
Graphics: GeForce GT 425M / 2GB on board
Hard_disk: 650GB
Single OS: Ubuntu 11.10.

---

### Post by Mark Phelps on 2012-01-07
> **anushcbe said:**
> when i boot up the ubuntu is taking an alot of time in loading it's kernel & it's infrastructure(Ubuntu) to get an lodging screen.


It's rude to hijack someone else's thread for your problem.  Please start your own thread for your problem.

---

### Post by anushcbe on 2012-01-07
My apologies.

I am new to this so didn't know what or how to post the problems.
As you have mention, i shall open an thread up for my problem sorry again.

---

