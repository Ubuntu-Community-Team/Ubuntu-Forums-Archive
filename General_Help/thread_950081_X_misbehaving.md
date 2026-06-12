---
title: "X misbehaving"
date: 2008-10-16
forum: General Help
---

### Post by dcampbell on 2008-10-16
This week me and Ubuntu have not been getting along.  First the java update broke java, which was a minor fix to get NetBeans up and running again.  Then the kernel updated destroyed my X.org setup, and wifi driver.  I eventually got everything worked out.  But I've been frustarted with X automatically starting when I log in.  I want to be able to use just consoles at times to save memory.  So I removed gdm from all runlevels.  So I log into the terminal, and can type "startx" when I need graphics.  Which is about 60/70% of the time.  The Problem is that when I try to stop x either with alt+ctrl+backspace, or hitting the quit button then clicking "logout", it only actual takes me back to the terminal maybe within the first 10 minutes of X running.  Otherwise it just goes to a black screen and hangs, there, nothing I can do but a hard reboot.  Any ideas on how I can safely get X to quit mostly all of the time. :)

---

### Post by phidia on 2008-10-16
The problem is as stated briefly [here]("https://help.ubuntu.com/community/Gnome/FAQ?highlight=%28runlevels%29").

> Runlevels have no effect on X in ubuntu/debian, gdm is started in levels 2-5.

I'm not sure but I think you need to reinstall gdm and than find or write a script that stops it. You can put that in /etc/init.d anyway that's my best shot at this.

---

### Post by dcampbell on 2008-10-16
I have gdm disabled.  It doesn't start at all.  I can login to the console fine (which is what I want).  I can start X and it runs fine (also good) but after X runs for a period of time when I try to log out or hit alt+ctrl+backspace, I get a black screen.  And I have to do a hard reboot.  I hope that clarifies my problem.  Also the system shutdown fine with gdm enabled.

---

### Post by phidia on 2008-10-17
I understand what you did I just don't think removing gdm is the correct way to accomplish what you want.

You may need to try a server install and add the packages you want to that.

---

