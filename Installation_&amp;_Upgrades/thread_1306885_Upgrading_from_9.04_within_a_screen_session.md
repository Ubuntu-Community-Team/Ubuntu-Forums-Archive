---
title: "Upgrading from 9.04 within a screen session"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by sk8er3810 on 2009-10-30
I think I just hosed my system.  Remember kids always backup.  I was at work and decided I would upgrade my system at home.  In order to allow the upgrade to run I ran 

```
sh /media/cdrom0/cdromupgrade
```

from within a screen session so that I could log out and not worry about it.  I logged back in a few times to check the status and all seemed to be going other than having to press enter to continue through a few ncurses screen for a few packages.  Got back from work and tried to log in to my screen session using

```
screen -x
```

and got

The program 'screen' is currently not installed.  You can install it by typing:
sudo apt-get install screen
screen: command not found
bash: screen: command not found

I tried installing screen but of course I get

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

No mystery there.

I looked for screen but its actually /usr/bin/screen.real. I ran

```
/usr/bin/screen.real -x
```

Lo and behold I was able to get my screen session back.  I continued the upgrade without any more issues.
After rebooting the login screen came up however the fonts were huge/big.  Mind you my display is a 40" HDTV.  I also had AutoLogin enabled for gdm before upgrading.  Ok thats fine.  AutoLogin should be easy to fix. Don't know about the fonts.  The resolution looks good and MythTV came up with it's new interface.  Not sure if I like it or not but we will see.

Anyway the upgrading seemed to work pretty well...for Linux but still needs work. Also, I shouldn't have been within a screen session...oh well.

Long story short.  Clean installs are always the safest.  Only do an upgrade if you absolutely have to.  Upgrading always has it's little quirks no matter which OS you are upgrading.  And don't do upgrade distro versions within a screen session.

Anyway just thought I would post my upgrade experience.

---

