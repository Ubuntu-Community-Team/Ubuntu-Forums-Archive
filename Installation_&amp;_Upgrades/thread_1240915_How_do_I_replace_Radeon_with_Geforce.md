---
title: "How do I replace Radeon with Geforce?"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by Skara Brae on 2009-08-15
Hello to all,

I have a "noob" question... How do I replace a Radeon 9250 (passive cooling) with a Geforce (a 6600GT)?

I have an old HP Vectra (built into a larger case), which is running Xubuntu w/XFCE. It has only 768 MB SDRAM and a Radeon 9250 (AGP).
Since XFCE is a tiny bit slow, I was wondering if it is possible to replace that Radeon with something better.

I have a Geforce 7600GS from Club3D (worthless fans!) and a Geforce 6600GT (Aopen Aeolus) lying around here, both AGP. The 7600 was used only a few months, the 6600GT is second-hand and worked fine under Windows ME (looong ago).

Installing Linux (Ubuntu, Xubuntu, OpenSUSE) is easy :) But I have never replaced hardware. I know how to do it in Windows (with my eyes closed, so to speak). But how do I replace that Radeon with the Geforce 6600GT (or is the 7600GS a better choice?) under Xbuntu?

(I'll probably have to replace the PSU too, to be safe, but that won't be a problem.)

The Search function gave me only 1 hit, from May 2008:
[http://ubuntuforums.org/showthread.php?t=796898&highlight=replace+graphics+card]("http://ubuntuforums.org/showthread.php?t=796898&highlight=replace+graphics+card")

Is this still/also valid, or is there another/better procedure?

---

### Post by matthewbpt on 2009-08-15
First of all you'll want to uninstall the ATI driver and download the nvidia driver for the new card (but don't install it yet just save it). Then open up the pc and switch the cards, turn the pc back on and make sure ints enabled in the bios, then boot ubuntu but in the GRUB menu choose the recovery mode so that you can boot straight into a command line, install the new driver in the command line and reboot the computer normally. Now it should be working fine :) I think you'll find this works.

---

### Post by Yellow Pasque on 2009-08-15
If you're using the proprietary ATI driver (aka fglrx/Catalyst), follow this to remove it: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver?action=show](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver?action=show)

Before you shut down to make the swap, run this to put your xorg.conf back into a default state (if you're asked to pick a driver, choose vesa):
```
sudo dpkg-reconfigure -phigh xorg-xserver
```

Now you should be able to swap the cards, boot your system, and install the nvidia driver.

---

### Post by khelben1979 on 2009-08-16
> **Skara Brae said:**
> Hello to all,

I have a "noob" question... How do I replace a Radeon 9250 (passive cooling) with a Geforce (a 6600GT)?

I have an old HP Vectra (built into a larger case), which is running Xubuntu w/XFCE. It has only 768 MB SDRAM and a Radeon 9250 (AGP).
Since XFCE is a tiny bit slow, I was wondering if it is possible to replace that Radeon with something better.

But I have never replaced hardware.

I think maybe you could benefit from [this video]("http://www.youtube.com/watch?v=8p2IPyd61ho").

Make sure there is good cooling in the case to avoid problems with overheating, a general advice.

---

### Post by Skara Brae on 2009-08-16
[B]matthewbpt,
Temüjin[/B],
Thank you both for your time & reply: I believe this is what I need.

**khelben1979**,
Thank you for the vid, but I needed to know how to uninstall the (open source) driver of the Radeon. Replacing hardware is the easiests part.

It is all just about knowing: once you know how to do something, everything becomes easy, right?

I'll give it a try.

---

### Post by Skara Brae on 2009-08-22
[*Reporting back in*]

[B]matthewbpt,
Temüjin[/B],
(and of course also **khelben1979** for his answer after my initial posting),

I am pleased to let you know that the Geforce 6600GT (an Asus Aeolus, for those curious) I had lying here is running smoothly.

* The recovery mode has a choice to "change" the xorg.conf file automatically, I saw. (It messed up the keyboard layout on the boot menu - QWERTY instead of AZERTY that I need - but I know how to fix that).

* After login, Xubuntu told me there was a proprietary driver for the Geforce, and I let it install it (I assume Nvidia's driver is better/faster than the open-source one?).

I replaced the PSU too: by an OCZ SilentXtream 700 W, for those reading this and being curious; a little overkill for this old system (not the one in my signature), but oh well :)

And I must say - what a difference in speed a Geforce 6600GT is, compared to the (Sapphire) Radeon 9250!

Now some more RAM (than 384 MB, not the 784 MB I mistakenly wrote) and this old thing is ready for the 22nd century :)

Thanks again for all who replied. You really helped me out!

---

### Post by matthewbpt on 2009-08-22
Good job I'm glad it worked, enjoy your newly invigorated system! =D

---

