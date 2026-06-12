---
title: "blank screen after boot up. OS only viewable in safe graphics"
date: 2009-04-06
forum: Hardware
---

### Post by Irishpolyglot on 2009-04-06
Hello! I'm having quite a problem accessing Ubuntu. I don't really know why (I wasn't playing around with settings at all; perhaps an update did it), but since this morning when I get past the Ubuntu logo at boot up, **the whole screen is black**. The log-on music plays so maybe it's all working except for the display. As well as this there are strange lines all across the screen for the initial Dell screen, for the Grub selection screen and for the Ubuntu loading screen. Without using any CD, the only thing I can access is the command line by changing the options at the Grub screen.

When I put in a Ubuntu CD (in this case I'm using 9.04 beta CD, but 8.10 is installed) and select the "Try without installing" option, it gets into Ubuntu and I can sometimes see the background image, and usually see the taskbar, but it hangs and I can't do anything. The only way I can access my computer through a GUI is by selecting the "*safe graphics*" mode (an advanced option) for "try without installing" from the CD.

Is there an easy solution, or should I just try to install the new OS over the old one and hope it works? If the problem starts at the Dell screen it's not actually linked to the OS surely? In safe graphics mode the screen looks fine, so it's not a physical problem as far as I can tell.

I ran a memory and disk scan from the CD and neither showed any issues. I have a Dell Inspiron 9400.

Advice hugely appreciated!!
Thanks

---

### Post by Dark_Stang on 2009-04-06
Which version of Ubuntu are you running? Boot up like you would normally. When you get to the blank screen do a Ctrl+Alt+F1. Then wait a couple seconds and do a Ctrl+Alt+F7. Does that make the GUI come back?

If not, try doing a Ctrl+Alt+F1. Login. And run...
```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```
Did that make it come back?

If either of those worked you might have just updated your video card driver and are having some issues. I have a similar issue with the absolute latest nvidia drivers on my HP laptop, so I run an older driver. If neither of those work a configuration file may be hosed up and your screen can't show the video the graphics card is trying to push to it.

---

### Post by Irishpolyglot on 2009-04-06
Thanks a lot for that! I was about to try it out, but when I rebooted after using Ubuntu in safe mode... the original installation (8.10) was working again! It's very strange. It's been working all day, but then the screen went blank after a few uses (when I left the computer for a few minutes and the screensaver took over) and I had to reboot, but it is working again. This is the most inconsistent problem I've had so far...
I might just install 9.04 beta, since I was going to install it anyway, and hopefully that will get around the problem. If I have problems after boot up I'll try what you suggested!!
Thanks :)

---

### Post by Irishpolyglot on 2009-04-08
Everything working that time was only temporary (only after the first time I tried the Ubuntu CD) ... in the last few days I have not been able to view the screen in normal mode. 

I formatted the whole computer and started over again, but the problem is still there :( I am still seeing a strange screen on Dell and the Ubuntu start up, but the screen is crisp and clear as it should be on the grub selection screen now (it wasn't before). [I have a dual boot with Windows; the Windows loading screen has the lines, but it boots into Windows fine (I still have to update the drivers in Windows though; it's still in 600x800 mode)].

Trying what you recommended usually doesn't work (any key combination doesn't get me out of the black screen), but for some reason I could see (just) the mouse at one boot into my newly installed Ubuntu 9.04 beta, so the graphics were somewhat working, and when I did gdm stop/start that time then it was processed and the following message was displayed:

> Could not start the X server (your graphical environment) due to some internal error. Please contact your system administrator or check your syslog to diagnose. In the meantime this display will be disabled. Please restart GDM when the problem is corrected.

My work-around without needing the Ubuntu CD is to go to "recovery" option in grub and select xfix and resume. That cancels the NVIDIA driver I would have just installed and I have a basic 600x800 screen. The problem resumes after rebooting whenever I install the NVIDIA driver from the Hardware Drivers option. I even tried selecting the older ones (versions 173 and 96, instead of the "recommended" 180), but the result is always the same.

Is the computer somehow physically damaged? Why did it work that one time after the problem started?? I really hope there is a way out of this... should I try other drivers? Any help appreciated!!

---

### Post by g1nsu on 2009-04-08
Hi, I'm having the same issue after the recent kernel and nvidia driver (1.80) updates. (AMD64, GeForce 9800GTX). A bug of this nature was noted on the savage driver so this might help you if you use that chip. I don't and will update anything else I find.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=483989](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=483989)
[http://www.linuxforums.org/forum/ubuntu-help/138490-ubuntu-8-10-screen-going-blank-boot-keyboard-lockup.html](http://www.linuxforums.org/forum/ubuntu-help/138490-ubuntu-8-10-screen-going-blank-boot-keyboard-lockup.html)


I solved my issue using this thread.
[http://ubuntuforums.org/showthread.php?t=1115079](http://ubuntuforums.org/showthread.php?t=1115079)

good luck

---

### Post by Irishpolyglot on 2009-04-09
Thanks for the link! That thread didn't solve my issue, but it has given me some room for discussion.
Thanks!

---

