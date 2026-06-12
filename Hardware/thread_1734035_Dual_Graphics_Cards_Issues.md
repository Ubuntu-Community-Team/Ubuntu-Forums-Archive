---
title: "Dual Graphics Cards Issues"
date: 2011-04-19
forum: Hardware
---

### Post by NPX731 on 2011-04-19
I've been having problems with my graphics cards.  My system (an Asus UX50V) has two graphics cards.  When I run Ubuntu on the system, it finds one of the cards and automatically runs it with no issue.  

However, when I use the "additional drivers" tool to install a proprietary nVidia driver for my other card and reboot, the system does not boot into the nVidia card, despite using its driver.  So, the system will just not boot into Ubuntu at all unless I boot using "FailSafeX Graphics" mode or whatever (which is what I'm doing right now :)). 

So, my question is:  How do I get Ubuntu to switch between the cards, once I've booted into Ubuntu?  Is there a program for that?  I can't seem to find one.  The system's native OS is Windows 7, and there is a specialized program by Asus just for switching between the cards in Windows.

Also:  Is there just a way to have Ubuntu initially boot into the graphics card of my choosing?  I can't seem to find info on that either.


Additional info:  The card my system CAN utilize is:  Intel GMA 4500MHD
                       The card my system CAN'T utilize is:  nVidia GeForce G105M
                       I'm running Ubuntu 10.10

---

### Post by or3x on 2011-04-20
I'm afraid I don't think you can get it to work, Nvidia optimus is not yet supported by linux:(, so until then you'll have to stick with the Intel card.
You can read more about it here: [https://launchpad.net/~hybrid-graphics-linux]("https://launchpad.net/%7Ehybrid-graphics-linux")
As you can see there, they're working on it.

---

### Post by NPX731 on 2011-04-20
Oh, Hey, Thanks!  Using the other graphics card isn't dreadfully important to me.  I just wanted to figure out how to do it, since that knowledge may help me out in the future.

---

