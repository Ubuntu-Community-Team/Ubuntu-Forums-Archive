---
title: "[SOLVED] Numlockx?"
date: 2008-11-01
forum: Hardware
---

### Post by mtylerb on 2008-11-01
Hey guys, I just upgraded to Ubuntu 8.10 from 8.04 LTS, and can't get Numlockx to work again.  I also had Advanced Desktop Settings to manage compiz fusion, working on 8.04 and it seems to be gone in 8.10.  I'm pretty new to Linux and I'm not really sure where to find the appropriate configuration files.  8.04 was the first distro I had successfully migrated from Windows to a couple months back.

Any help is muchly appreciated!

---

### Post by Yellow Pasque on 2008-11-01
Are the packages installed?
```
sudo apt-get numlockx compizconfig-settings-manager
```

Can you give a little more detail on what you were doing to use numlockx?

---

### Post by mtylerb on 2008-11-01
> **Temüjin said:**
> Are the packages installed?
```
sudo apt-get numlockx compizconfig-settings-manager
```

Can you give a little more detail on what you were doing to use numlockx?

Nothing special, I just did the sudo apt-get install numlockx and edited the X11/gdm/Default file to use it on startup.  When I try to cp that file now, though, it says it can't "stat" the file.

Your second argument compizconfig-settings-manager doesn't work.

---

### Post by Yellow Pasque on 2008-11-01
I thought numlockx was unnecesary for GNOME (and KDE). My numlock comes on when I log in and I don't have numlockx installed. Is there a reason you need numlockx?

> Your second argument compizconfig-settings-manager doesn't work.
Sorry, that was a "typo" on my part
```
sudo apt-get **install** compizconfig-settings-manager
```

---

### Post by mtylerb on 2008-11-01
> **Temüjin said:**
> I thought numlockx was unnecesary for GNOME (and KDE). My numlock comes on when I log in and I don't have numlockx installed. Is there a reason you need numlockx?


Sorry, that was a "typo" on my part
```
sudo apt-get **install** compizconfig-settings-manager
```

That's perfect, solved the compiz fusion settings problem, now the numlock problem.

I want numlock to stay on when the computer starts up and once I log in.  I had installed numlockx in 8.04LTS because I couldn't find a solution, besides that, that would work.  If there's another way to do this in 8.10, I'd love to hear it.

---

### Post by mtylerb on 2008-11-01
I've encountered another problem in the last few minutes.

Ubuntu won't restart.  It will kill all the processes, but then sits at a black screen without rebooting the computer.

Numlock still does not come on after a reboot, though it will stay on once I turn it on and log in.

---

### Post by doas777 on 2008-11-01
> **Temüjin said:**
> I thought numlockx was unnecesary for GNOME (and KDE). My numlock comes on when I log in and I don't have numlockx installed. Is there a reason you need numlockx?


Sorry, that was a "typo" on my part
```
sudo apt-get **install** compizconfig-settings-manager
```

Just for the record, I do need numlockx (on all 3 ubuntu boxes) to make sure that numlock is on when it's time to login, and stays on after logging in. 

it doesn't seem to be working right with Intrepid though.

---

### Post by Yellow Pasque on 2008-11-01
If numlockx is installed and not working, you should probably report that as a bug on Launchpad.

---

### Post by mtylerb on 2008-11-01
Oh, there was another issue, that I forgot to mention.

Whenever I boot into my profile, it doesn't automatically connect to the wired network.  8.04LTS always did, so I'm not sure what to do about that.

It currently lists the following networks:

Wired Network:
ifupdown (default)

Wireless Network:
Beckett <-- This is my Wireless-N D-Link router
BeckShare <-- This is point-to-point network setup using my laptop when I was using my laptop as a router a while back.

I tried going into System->Preferences->Network Configuration and enabling the Automatically Connect setting.  When I click OK to close, though, I get the following error:

Updating connection failed: nm-ifupdown-connection.c.82
- connection update not supported (read-only)..
[Close]

I'm really not sure what that means.

---

### Post by mtylerb on 2008-11-01
Ok, I think I figured it out.  I read the 8.10 Release Notes and the following:

> X.Org Input Devices

The X.Org configuration file (/etc/X11/xorg.conf) still has InputDevice entries for the mouse and keyboard, but they are ignored now because input-hotplug is used. The keyboard settings now come from /etc/default/console-setup; to change them please use sudo dpkg-reconfigure console-setup. After that, HAL and X need to be restarted (e.g., by rebooting your system). 

Made me think.  I looked in /etc/default for the Default file with no luck.  I noticed as I was scanning through the /etc folder that there was a /etc/gdm.  After going in there, I found the Default file in /etc/gdm/Init/.  There was also a backup of the Default file which had my old changes in there to include numlockx:

```
if [ -x /usr/bin/numlockx ]; then
	/usr/bin/numlockx on
fi
```

So, I'm off to restart and see if that fixed it.

---

### Post by m_l17 on 2008-11-01
I followed this guide and works great :) Give it a try:

[http://blog.clickonline.org.au/2008/03/08/ubuntu-tip-of-the-day-enabling-num-lock-at-boot-in-710/]("http://blog.clickonline.org.au/2008/03/08/ubuntu-tip-of-the-day-enabling-num-lock-at-boot-in-710/")

---

### Post by mtylerb on 2008-11-01
> **m_l17 said:**
> I followed this guide and works great :) Give it a try:

[http://blog.clickonline.org.au/2008/03/08/ubuntu-tip-of-the-day-enabling-num-lock-at-boot-in-710/]("http://blog.clickonline.org.au/2008/03/08/ubuntu-tip-of-the-day-enabling-num-lock-at-boot-in-710/")

That's essentially what I did in my last post, it did work.  I guess the X11 folder is only for the X desktop manager?  Since I'm using gnome, I should have been editing in the gdm folder.  I must have caught that in 8.04LTS, but forgot about it when I switched to 8.10.  Thanks anyway m_l17.

I'll start new threads for the other 2 issues.

---

