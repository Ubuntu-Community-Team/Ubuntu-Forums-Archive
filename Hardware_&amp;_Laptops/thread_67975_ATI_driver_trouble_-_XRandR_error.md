---
title: "ATI driver trouble - XRandR error"
date: 2005-09-21
forum: Hardware &amp; Laptops
---

### Post by Dorfl on 2005-09-21
Clean installation of Ubuntu 5.04, a Pentium 4 with a Radeon 9800 on it. I installed the drivers for said Radeon exactly as instructed by some guide I was pointed at by the moderator of the official Ubuntu IRC channel (weak memory, faulty Firefox history).  Directly downloaded from some repository, anyhow. Now, when I do:

System -> Preferences -> Screen Resolution

I get:

Error: The X Server does not support the XRandR extension. Runtime resolution changes to the display size are not available.

This new resolution is killing me, plus, this problem may go down deeper than I can now see. Help?

---

### Post by krak on 2005-09-21
[http://www.ubuntuforums.org/showthread.php?t=66445&highlight=ati+tutorial](http://www.ubuntuforums.org/showthread.php?t=66445&highlight=ati+tutorial)

---

### Post by mlomker on 2005-09-21
You can't change the resolution while running.  That is mentioned in a number of threads on here.  You need to run **sudo dpkg-reconfigure xserver-xorg** at a command prompt to reconfigure the resolution.

If the output of **fglrxinfo** is correct then the driver is installed fine.

I'm also dissapointed that Krak didn't contact me if he was having trouble with my how-to, but I appreciate the link at the top his post.  I have updated the how-to almost every day to keep it accurate and to account for new issues.

---

### Post by Dorfl on 2005-09-21
So, just to be absolutely certain, I'm supposed to see this error message?

---

### Post by mlomker on 2005-09-21
[QUOTE=Dorfl]So, just to be absolutely certain, I'm supposed to see this error message?[/QUOTE]

Yes, if you trust other posts on this forum.  I personally never change my resolution and my xorg.conf file only has one option in it.

Did you try to change the resolution using ATI's control panel applet or the gnome control panel?  If you are using the stock fglrx driver then the control panel applet comes in the **fglrx-control** package.

---

### Post by Dorfl on 2005-09-22
Ah, you should have said there was a control applet from the start. Thanks. Are there any other packages I should know of? And how do I access that fglrx-control now that I've apt-got it? Should it have left something on my Desktop?

---

### Post by mlomker on 2005-09-22
[QUOTE=Dorfl]Ah, you should have said there was a control applet from the start. Thanks. Are there any other packages I should know of? And how do I access that fglrx-control now that I've apt-got it? Should it have left something on my Desktop?[/QUOTE]

In KDE it puts the icon in my menus.  /usr/X11R6/bin/fireglcontrolpanel

I didn't mention it because I have no idea how you went about installing the driver.  It would have been installed using my [how-to](http://www.ubuntuforums.org/showthread.php?p=348911), whether using the built-in driver (which you are using) or by using ATI's package.  It actually doesn't seem to work at all on 64-bit systems, so I'm not sure what it is capable of doing.

---

### Post by Dorfl on 2005-09-22
This method of communication is awfully slow. Can we talk on IRC, ICQ or Skype (or Skype-like program) please?

In case you're too busy for that, but still want to help - just ran glxgears, and I got 2300 FPS, and from your howto I understand that's fine. So I probably have the drivers installed. Also, by editing the high resolutions out of xorg.conf, I got myself back to my good old 1024*768, but now I have a poorer refresh rate. H:68.5 V:84.9. I used to work at 100 in WinXP, I'm not sure whether that was horizontal or vertical. I'm working with GNOME now, btw, and I can't find whatever control applet I installed by apt-getting fglrx-control. I installed my drivers according to the instructions in this page:

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

Any more information I can provide?

Edit: /etc/X11R6/fireglcontrol is working, but all it lets me do is decide what to do with the secondary monitor and adjust gamma. As well as knowing I've installed the drivers properly, I want to be able to change the resolution more conveniently, and be able to change the refresh rate (scale it up) at all.

---

### Post by mlomker on 2005-09-22
[QUOTE=Dorfl]This method of communication is awfully slow. Can we talk on IRC, ICQ or Skype (or Skype-like program) please?[/quote]

The links on my profile should work, but I don't think I have any answers for you.  I'm also at work during the day, so I'd have to keep chats short.

> 
Edit: /etc/X11R6/fireglcontrol is working, but all it lets me do is decide what to do with the secondary monitor and adjust gamma. As well as knowing I've installed the drivers properly, I want to be able to change the resolution more conveniently, and be able to change the refresh rate (scale it up) at all.

You can look at your /var/log/xorg.0.log for insight on how it is detecting your monitor settings.  I don't see anything in the docs regarding supported refresh rates.  You could jump on the  [ATI forum](http://www.rage3d.com/board) and ask some questions there.

---

