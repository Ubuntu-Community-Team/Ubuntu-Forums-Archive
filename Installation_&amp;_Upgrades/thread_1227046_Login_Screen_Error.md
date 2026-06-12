---
title: "Login Screen Error"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by redenex on 2009-07-30
Hi guys, earlier yesterday I did the upgrade of my Jaunty 64 bit and the new kernel was installed from the repository. The system asked for a reboot, but once I rebooted, I am not able to see the login screen, I guess there is some xserver problem? Can someone guide me to restore the system without a reinstall? Thank you.

---

### Post by redenex on 2009-07-30
bump :P

---

### Post by redenex on 2009-07-30
:confused:

---

### Post by redenex on 2009-07-30
no one to guide?

---

### Post by manlypain on 2009-07-30
I have the same problem.  I have been searching the forums and found a few threads but no definite answers.  I booted into the recovery mode for the default kernel and told it to fix the graphics (last option) it then let me in.  i then reenabled the default nvidia drivers but had to reboot to take affect.  it takes me back to no login but now i have a mouse cursor.  i switched over to tty2 and ran top.  gdmgreeter is using 100%.  it has to be related with that nvidia driver.  a coworker suggested running running the package checker in the recovery list since the error came after the updates, he also said to check if ubuntu-restricted-extras got removed with the update.  it has happened before but its crazy rare.

---

### Post by redenex on 2009-07-30
Thank you but how do I do it in the recovery mode? Using command prompt?

---

### Post by manlypain on 2009-07-30
i figured out my issues

but first to get into recovery you hit escape whe grub starts (right after bios) you have 2 seconds to hit it.



I fixed mine by loading up normally ( but not working) then going over to tty2 ( ctrl-alt-F2) then running

sudo service gdm stop
startx

x started up fine so i knew it was gdm
so i reconfigured gdm automatically after i logged out of gnome ( like normal, it took me back to the prompt)

sudo dpkg-reconfigure gdm


then i rebooted
it worked after that
hope this helps

---

### Post by redenex on 2009-07-30
Well, to me the problem is when I run startx.

Will see what best I can do, else I would go for a clean install. :KS

Thank you.

---

### Post by Dullstar on 2009-07-30
Something's wrong.  Either bad hardware, or a bad installation...  if those suggestions don't work, that is.

---

### Post by redenex on 2009-07-30
Yes I understand. as I mentioned in the first post, everything was perfect untill I installed the latest kernel updates from the repository. :guitar::confused:

---

### Post by redenex on 2009-07-31
I did a clean install. Easy way out, perhaps not a good thing I know, thanks for the help.

---

### Post by redenex on 2009-08-02
The problem is when I install the new kernel 2.6.28-14

With 2.6.28-11 everything works fine. for now I am abstaining from upgrading to the new one.

---

