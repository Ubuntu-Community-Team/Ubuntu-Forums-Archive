---
title: "Alternate install from USB"
date: 2009-08-16
forum: Installation &amp; Upgrades
---

### Post by Holyaxe on 2009-08-16
I tried to install Xubuntu 9.04 alternate from my USB stick. I used Syslinux 3.82 to make it bootable and put all the files on it. It boots fine, but gives an error:

**Unknown keyword in configuration file: gfxboot**

I assume I have to edit the configuration, but what file and how?:confused:

---

### Post by adamsiddhi on 2010-06-04
I get the same message when I hold Shift and get to the boot line. I realize this is an old post but did you figure out a solution?

---

### Post by Herman on 2010-06-04
What how-to are you following?

There used to be an old how-to, I think probably in Community Docs that  implied it might be possible.
The last time I tried to get the 'Alternate Installation' CD to work in a USB stick it would boot, but the installer would stop at 'Detecting CD-ROM', and I never did solve the problem of how to get past that. 

Now I have looked again  and noticed a new how-to in the official Ubuntu Wiki for Lucid Lynx, or at least one I don't remember seeing before, [Preparing  Files for USB Memory Stick Booting]("https://help.ubuntu.com/10.04/installation-guide/i386/boot-usb-files.html"). There are two methods described on that page, only it doesn't specifically mention what CD they're talking about anywhere on that page that I can see. I presume they mean the 'Alternate CD', because it's a lot simpler to just use 'Startup Disk Creator' to put the 'Desktop' Live/Install CD in a USB. Will anything in that how-to help you?

Let me know how you get along, I'm curious. :)

---

### Post by adamsiddhi on 2010-06-05
> **Herman said:**
> What how-to are you following?

There used to be an old how-to, I think probably in Community Docs that  implied it might be possible.
The last time I tried to get the 'Alternate Installation' CD to work in a USB stick it would boot, but the installer would stop at 'Detecting CD-ROM', and I never did solve the problem of how to get past that. 

Now I have looked again  and noticed a new how-to in the official Ubuntu Wiki for Lucid Lynx, or at least one I don't remember seeing before, [Preparing  Files for USB Memory Stick Booting]("https://help.ubuntu.com/10.04/installation-guide/i386/boot-usb-files.html"). There are two methods described on that page, only it doesn't specifically mention what CD they're talking about anywhere on that page that I can see. I presume they mean the 'Alternate CD', because it's a lot simpler to just use 'Startup Disk Creator' to put the 'Desktop' Live/Install CD in a USB. Will anything in that how-to help you?

Let me know how you get along, I'm curious. :)

So I used this how-to:
[[COLOR="Purple"]**http://www.pendrivelinux.com/put-xubuntu-10-04-on-a-flash-drive-with-windows/**[/COLOR]]("http://www.pendrivelinux.com/put-xubuntu-10-04-on-a-flash-drive-with-windows/")

It worked out fine. I just get the error:
**Unknown keyword in configuration file: gfxboot**
when I press **SHIFT **during the boot process but...

...Any ways it turns out that all i needed to do was at the Xubuntu 10.04 boot options menu screen, press **TAB**. This brings up a bunch of text called the boot string I think. At the end of it after **splash --** I type **i915.modeset=1** to make it load Xubuntu 10.04 Live from the USB stick. From there I can install by clicking the install icon located on the Xubuntu 10.04 desktop (which I have not yet done since I needed to figgure the proper method of partitioning my HD in step 4).

I am curious to know when and where [COLOR="DarkSlateGray"]***Holyaxe***[/COLOR]:guitar: saw that error message. In anycase I detailed my initial problem here:
**Xubuntu 10.04 :: Dual Boot from USB Installation Keeps Failing**
[[COLOR="Purple"]**http://ubuntuforums.org/showthread.php?t=1501040**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1501040")

---

