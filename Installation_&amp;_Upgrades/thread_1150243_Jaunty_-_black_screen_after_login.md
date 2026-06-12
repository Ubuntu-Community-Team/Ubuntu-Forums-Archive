---
title: "Jaunty - black screen after login"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by veloce on 2009-05-05
After upgrading to Jaunty on three machines, one has ended up unable to log on.

Everything works fine right up until login. Splash screen, login prompt etc all good.  However, after entering the password, the screen just goes black.  The mouse pointer is visible and moveable but that is the only thing on screen.

The only other thing about this machine is that it is a laptop and I'm only using the second screen (the inbuilt screen has died).  Can't see how that could be the issue when I get the login screen perfectly.

I can login as failsafe gnome and I get no window manager - I get a terminal screen and I can use it to start up a graphical application but the graphical application has no window controls.

Any ideas?

---

### Post by _goatboy_ on 2009-05-05
I had a similar issue on a somewhat older computer when I put a fresh install of Ubuntu 8.10 on it for the first time.  I had exactly the same problem.  I would log in, and the screen would go blank.  Sometimes the mouse would be able to move, sometimes not.  The background would sometimes be the standard Ubuntu tan, and sometimes black.

The issue turned out to be with Compiz, what I now understand to be the main package that runs all the "pretty" effects in Ubuntu, such as the jello-like window option.

What I did first was boot into a terminal.  You do this by pressing Escape during the load process and going into Recovery Mode.  What I did then was run:

```
sudo apt-get remove compiz-core
```This removed all the fancy display things which my card was not able to run.  This fixed the problem for me right away.  Please note however that this may not be the case for you, it is only what I did to fix what seems to be the same problem.

---

### Post by veloce on 2009-05-06
> **_goatboy_ said:**
> 
```
sudo apt-get remove compiz-core
```


Good suggestion but no cigar!  

Tried removing compiz like this but it had no effect.

This is really bizarre.

---

### Post by veloce on 2009-05-06
The upgrade to Jaunty must have hiccuped.

I've found that "gnome-session" wasn't installed.  Not sure how many other packages might be missing, but at least the machine is operational again.

---

### Post by lmmendonza on 2009-05-21
I have the same problem after loging in all i get is a balck screen with the cursor that can be moved
help please..total beginner!!

---

### Post by veloce on 2009-05-21
My problem was that the upgrade had not completed successfully.  I suggest you get a copy of the "alternate" disk and run an upgrade from that.

If this doesn't work then it is a different issue.

---

### Post by michael_gilroy on 2009-06-20
Hi,  

  I've updated 2 separate machines now to Jaunty and not been able to progress beyond the splash screen. The result is I'm stuck with and completely blank screen or some random colours on the screen. 


I've discovered that if I boot into the recovery mode I am able to log in as root. I tried to upgrade to kernel 2.6.30 as some people had suggested this could solve the problem. It did not. In doing o I discovered fglrx was failing to install. I ran the following command:

apt-get remove xorg-driver-fglrx

Then reboot the machine. I'm now able to log in without issue. This has worked for both an Intel 82q963 on board graphics card and nvidia card.

---

### Post by raheel213 on 2009-06-22
I am using ATI Radeon HD 3650 and i applied "apt-get remove xorg-driver-fglrx" which has resolved my problems thanks.....Michael Gilroy but when i am opening Applications-->ATI Catalyst Control Center it says "failed to execute child process amdccle(no such file or directory".

---

### Post by tchalvakspam on 2009-07-05
For me my black screen problem ended up being a driver problem, so another thread recommended that I simply uninstall the fglrx driver to allow ubuntu to fall back on a simpler graphics system.

Not guaranteed to work, but if all you have is a black screen and a recovery console, not like there's anything more to lose:

apt-get remove fglrx

To uninstall the driver, and then reboot.

---

### Post by ravisghosh on 2010-01-14
I get this black screen after logging in but not always. After I get it, i have to restart using the power button of laptop.

Will removing fglrx, disable all the nice stuff of graphic card?

---

