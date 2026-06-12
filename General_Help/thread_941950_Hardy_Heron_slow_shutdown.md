---
title: "Hardy Heron slow shutdown"
date: 2008-10-08
forum: General Help
---

### Post by soylentjosh on 2008-10-08
Hello!

I am having a problem with my version 8.04; when I click on the shutdown (restart, switch user, lock screen, etc.) button at the top right corner, it sometimes takes a long time to display the screen -- perhaps 1.5 to 2 minutes.  When it does show up, the only options presented are for "shutdown" and "restart" (e.g. no "suspend" or "hibernate" option).  When it finally shows up and I choose either shutdown or restart, the actual shutdown process takes a long time, perhaps five minutes.  This happens around 75% of the time, with the operating system responding normally the other 25%.  Does anyone have an idea what is going on or what may be done to fix it?  Thank you!

soylentjosh

---

### Post by Ubunt2u on 2008-10-08
i've had the same issue for about a month or so now.  i resorted to rebooting/shutting down using the terminal. 
sudo reboot
or
sudo poweroff

i figured i would just deal with it until newest version is released then i'll just start from scratch.

---

### Post by Calmatory on 2008-10-08
This happens to me when I lose my sound. By losing I mean that something hooks up the device(Skype is saying that the device is busy, so is Amarok). If that happens and if I try to reboot after it, the menu takes ages to show up. If the sound device works, the menu shows instantly.

At least thats what I've been observing. I doubt it is coincidence. :|

---

### Post by nikosapi on 2008-10-08
Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)
This is a known bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/123078](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/123078)
The workaround from the aforementioned thread is: "Reenable the gnome-power-manager in Administration-Sessions."

---

### Post by fragos on 2008-10-09
Are you doing shutdown with applications open. Each application has it's own shutdown proceedure. Large disk writes are done in the background and those would need to be completed by the system before shutdown. There are parameters for offering suspend and hibernate in the shutdown screen. Hibernate requires a swap partition at least as large as memory.

---

### Post by Ubunt2u on 2008-10-14
No.  I have this issue consistently.  I believe nikosapi is probably correct.  If i remember correctly, I disabled the power-saving settings because I'm not using a laptop.  It's really no problem to me, I just shutdown/reboot using the terminal.

---

