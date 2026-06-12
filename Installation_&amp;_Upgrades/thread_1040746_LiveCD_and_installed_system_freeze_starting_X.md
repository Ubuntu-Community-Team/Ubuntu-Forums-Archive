---
title: "LiveCD and installed system freeze starting X"
date: 2009-01-15
forum: Installation &amp; Upgrades
---

### Post by nafai1 on 2009-01-15
Hello, I have had a bit of experience with various Linux distributions in the past, but I stopped using it for a while. I've decided to try it out again, hoping it might be ready for the desktop. Unfortunately, the one system I've been trying it out on has been giving me a great deal of difficulty, which isn't helping my opinion.

I'm going to detail this problem, hoping someone can give me tips on how to fix it. The system in question is a Dell Optiplex GX150, 512mb ram, P3 1.13ghz, 82815 chipset. Ideally, I'd like to get Xubuntu 8.10 working on it.

This first part is common to the Xubuntu 8.10, Ubuntu 8.10, Mint, and FC10 LiveCDs: None of them boot properly. They will go up until the point where X is supposed to start, then they hang. Changing terminals, ctrl+alt+bksp, ctrl+alt+del, and power button do not do anything. Interestingly enough, Xubuntu 8.04 boots just fine. There must have been a regression of some sort that more than one distro was affected by.

I ended up installing Xubuntu 8.10 using the Alternate CD (worked absolutely fine). If I boot up normally though, X doesn't start. More specifically, the progress bar reaches the end, the screen clears, I see the cursor flashing in the top left for one second, then it switches between shades of black for a few seconds before deciding on just one. So I try booting into recovery mode. I use the xfix option and resume, but it hangs.

I restart again into the recovery console. I get into the root prompt. Here's what I see:

1. There is no xorg logfile in /var/log
2. If I type "startx" as root, it will actually start up perfectly fine, resolution is good enough (1024x768?), but the mouse and keyboard don't work. So I go back to the root console and ctrl+c it.
3. Just to check, there is now an Xorg.0.log with no errors.
4. The Xorg.conf file is very sparse. There are no drivers present, just three sections (Device, Monitor, Screen with default values left in)
5. I run dpkg-reconfigure xserver-xorg (seriously, this is not very intuitive) and go through it. Because I'm using all "normal" hardware (us keyboard [ps2], usb mouse, etc), I go through the default options. I reexamine Xorg.conf. It looks like it's the same, but there's a backup of the old one.
6. I hand-edit Xorg.conf and add in a keyboard and mouse section
7. I run startx again, and the mouse and keyboard work.
8. I restart the computer, and there's a black screen waiting for me when it finishes. Same problem as before.

I've reached a dead end, and now I'm asking the community for help. I don't know what logs are kept of the bootup process, so if someone can tell me where they're kept I'll post them. Any help will be appreciated. Thanks in advance.

[Edit]
In the root console, I started up GDM (/etc/init.d/gdm start) and it seems to work. However, it gives me an error: "Internal Error" / "failed to initialize HAL!". I don't know if this is related, though. But one thing this tells me: The error might be in the bootup process somewhere between where it would start the recovery console, and where it starts GDM, because GDM comes up just fine now.

[Edit2]
Bringing up hal and dbus manually keeps me from getting errors in xfce, but to reiterate, gdm only starts when I bring it up manually from the root console. Regular boots just hang.

---

### Post by nafai1 on 2009-01-20
Bump, I hope someone can help me with this... TIA

---

