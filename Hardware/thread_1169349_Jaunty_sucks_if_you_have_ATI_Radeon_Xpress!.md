---
title: "Jaunty sucks if you have ATI Radeon Xpress!"
date: 2009-05-25
forum: Hardware
---

### Post by Dipper on 2009-05-25
ATI has dropped support for the Radeon X series of video cards.  The open-source drivers do not work.  Google Earth runs so slow that you might as well say it doesn't work.

At this time, I will NOT be upgrading to Jaunty.  I will be going back to Intrepid.  My question is will this issue be fixed before support ends for Intrepid or are those us with this video card simply going to be screwed?

---

### Post by newman on 2009-05-25
yeah that stinks, my acer laptop with radeon x1250 flickers and standby doesn't work. it's back to 8.10 I guess...

---

### Post by rasmus_ on 2009-05-25
Why not compile an old version from source?

I had to do that for my NVIDIA GTX 280 card since it was too new to function properly on Intrepid using the binary drivers.

I have no experience dealing with ATI but the NVIDIA drivers were pretty easy to install. There must be some kind of driver archive at ATI's or somewhere else.

---

### Post by Dipper on 2009-05-25
Because compiling source isn't something everyone can do.  It's not for the average user.

I am really hoping that somebody from the team that writes Ubuntu can answer my question:  Will support for blacklisted ATI cards be implemented before October 2009, when Intrepid is no longer supported?  This will make a huge difference in whether I and others choose to continue using the *ubuntu family of Linux.

---

### Post by rasmus_ on 2009-05-25
Yeah I know. But it might be your only option :(

It's actually pretty well documented:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

I followed similar instructions for NVIDIA without any problem.

EDIT: You might want to check out Envy. I haven't tried it though.

---

### Post by some_name on 2009-05-25
I've got an ATI Radeon X1250 and was experiencing flickers and glitches, but using these updated drivers seems to have fixed the problem:

[http://www.h-online.com/open/Updated-graphics-drivers-for-Ubuntu-9-04--/news/113261](http://www.h-online.com/open/Updated-graphics-drivers-for-Ubuntu-9-04--/news/113261)

---

### Post by Dipper on 2009-05-28
Is there anyone who knows the answer to the question?   I want to know if I will be able to use my laptop after support ends for Intrepid.  I have a ATI Radeon 200 card that has been blacklisted.  This is a bunch of BS.  Why can't Ubuntu include the version of xorg that supports older video cards?

---

### Post by rasmus_ on 2009-05-28
Did you try the drivers suggested by some_name? Adding a repository IS for the average user ;)

---

### Post by JS_Prom on 2009-05-28
I too have an ati radeon xpress 200M display card on my amd HP nx6115 notebook. With earlier versions of Ubuntu (notably Hardy) I was able to download the driver from ati's website and install it and it took care of a lot of issues such as screen flicker when moving from the default X screen to a console with Alt + Fn keys.

However, since I moved to Jaunty the fglrx driver won't install. If it installs it won't work and I have tried twice and removed it finally. Reconciling to the xorg ati driver.

Ilooked at the link provided by some_name above and enabled the repositories but I don't think this card is covered by the drivers the link provides. Unless I am doing something wrong?

---

### Post by Yellow Pasque on 2009-05-28
> **Dipper said:**
> Is there anyone who knows the answer to the question?   I want to know if I will be able to use my laptop after support ends for Intrepid.  I have a ATI Radeon 200 card that has been blacklisted.  This is a bunch of BS.  Why can't Ubuntu include the version of xorg that supports older video cards?
You can keep Intrepid installed after support ends. There just won't be any security updates after April 2010. Also, I think there are PPA's for Xserver 1.5 in Jaunty

> looked at the link provided by some_name above and enabled the repositories but I don't think this card is covered by the drivers the link provides.
The link contains intel graphics drivers, so it's not applicable to this thread.

---

### Post by BooDaddy on 2009-05-28
I too am having ATI Xpress problems. I have an x1200 in my laptop, and after running the ATI driver and it not detecting my card, I cant boot back into ubuntu.

I am just getting a flashing black and white screen on boot and thats it. I was getting some lines on the screen, but not anymore. I am having to boot back into XP, just so I can troubleshoot.

What can I  do to get ubuntu to display after booting now?

---

### Post by BooDaddy on 2009-05-28
I found a solution. check my post on what worked for my video issues with my radeon x1200

[http://ubuntuforums.org/showthread.php?p=7362450#post7362450](http://ubuntuforums.org/showthread.php?p=7362450#post7362450)

---

### Post by MaximCarnage on 2009-05-28
If you have flickering you should edit you xorg.conf to use the old method.


Section "Device"
	Identifier	"Configured Video Device"
	Driver      	"ati"
        Option          "AccelMethod"  "XAA"
EndSection


You can always resort to recompiling and getting the Catalyst drivers to work. But sooner or later good work in the OpenSource Drivers will be made and your gonna have to undo everything you did.....

---

### Post by newman on 2009-05-31
ubuntu doesn't work well on my laptop. ati x1250 chipset support is not there. also I can't get suspend of hibernate to work, and battery life is horrendous in ubuntu. it's back to vista... :(
vista actually runs smoothly on this laptop, I just hate having to run anti-virus and all the other nonsense that's associated with windows...

---

