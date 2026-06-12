---
title: "Ubuntu Freezes After Startup"
date: 2011-05-30
forum: Hardware
---

### Post by rectec794613 on 2011-05-30
Hey guys. First of all I wanna say how much I've missed Ubuntu and Ubuntu Forums. It's been a long time since I've posted anything. 

Now, on to the problem. This is all the details of my problem, but you can skip down to my specs real quick and respond if you can draw a logical conclusion.

Here's a little background (this is not exactly the situation I'm in now, but nearly the same):

I recently got a new laptop with Windows 7 on it. I love Windows 7 and all, but I also like Ubuntu. So I finally decided to install it. The thing is, my pc doesn't seem to like Ubuntu. Whenever I try to boot the Live CD, or try to run the actual system, it freezes within a few seconds after the login screen/desktop shows. Now I ran Ubuntu on my old desktop pc (which I still have) relatively well, with no freezes. It seems like when my laptop runs even a hint of Ubuntu, it freezes for no reason. Input freezes, nothing moves, etc. 

I'm a pretty experienced Ubuntu user, and have been working with Ubuntu since 2007, but this problem just baffles me. Could it have something to with the AHCI mode setting in my BIOS? I've noticed OS's like Windows XP simply crash on startup with this setting on. (UBCD4Win) 

I've tried both 32 and 64 bit versions of Ubuntu 11.04 and 10.10, using both USB and CD but they all freeze. So I decided to use the Alternate CD version of Ubuntu 11.04 AMD64, and it installed with little error, until it got to the login screen. The second I clicked my username, it completely froze. Why is this? Can someone help me out? I've looked all over the forums but couldn't find an answer. I've tried unplugging my USB drive and taking the CD out, but it doesn't help.

**Here's my laptop's specs (the one I'm trying to install to):**
MSI A5000 Laptop ([Product page]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834152240&T"))
Intel Pentium (Dual Core) T4500 @2.3GHz
Nvidia GeForce 8200m g
Nvidia nForce Motherboard (or is it MSI?)
Nvidia nForce 10/100/1000 mbps ethernet
RealTek HD Audio
802.11bgn 1T1R Mini Card Wireless Adapter (Internal WiFi adapter, currently using wireless internet)


I'll be happy to provide more info as requested. Thanks in advance!

---

### Post by prshah on 2011-05-31
> **rectec794613 said:**
> Could it have something to with the AHCI mode setting in my BIOS? I've noticed OS's like Windows XP simply crash on startup with this setting on. (UBCD4Win) 

it installed with little error, until it got to the login screen. The second I clicked my username, it completely froze. 

Nope, AHCI mode has no effect on Windows Vista+ and Ubuntu 7.10+. For Windows XP, AHCI mode requires additional drivers (Press F6 during installation when prompted).

I think your problems stem from Unity, Ubuntu's new interface. Boot to your installed system, switch to a virtual terminal (Ctrl+Alt+F1) and install Unity2D```
sudo apt-get install Unity2D
```

Then, restart GDM ```
sudo service gdm restart
``` and switch back to your login screen (Ctrl+Alt+F7..F9) if it does not do so automatically. 

At the bottom of the screen, you will find a list of options; look for Unity2D in one of the dropdown boxes. Select it, and login as normal. (You may have to enter your username before being allowed to select Unity2D as your desktop environment).

Once you are logged in, run the restricted drivers installer, install recommended drivers for your nVidia graphics.

Once done, you can attempt to login using Unity (instead of Unity2D). Unity uses OpenGL, which support is only activated with the correct drivers.

---

### Post by rectec794613 on 2011-05-31
Hey thanks for the reply but I think it's fixed. After a few more unsuccessful tries, it finally started without freezing forever. The trackpad didn't work so I plugged in my USB mouse and restarted, and now it works just fine. If I get the problem again I'll post about it.

Thanks for the help, and wish me luck! :D

---

### Post by rectec794613 on 2011-08-28
Hey guys, just a little update here.

Found out the source of the problem: bad wifi drivers. People with the rt2800pci/sta drivers on Ubuntu will face some problems with freezing. There's 2 drivers/modules working for one network card. That means any time the networking system is disabled (e.g. shutdown, sleep, first startups), the computer will completely lock up. After much investigation I found this handy page on bugs.launchpad.net that shows how to remove and blacklist the module. Anyone who has had the same problems give it a look and see if that doesn't fix it. Also, I keep this page bookmarked and synced for fresh installs of Ubuntu, and I suggest you should too if you have this problem.

Here it is: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620/comments/103](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/541620/comments/103)

Good luck! : )

---

