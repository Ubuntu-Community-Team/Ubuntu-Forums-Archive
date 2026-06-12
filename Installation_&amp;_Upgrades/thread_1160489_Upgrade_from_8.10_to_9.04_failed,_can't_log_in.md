---
title: "Upgrade from 8.10 to 9.04 failed, can't log in"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by steve c on 2009-05-15
I tried to upgrade from 8.10 to 9.04 and between 10 and 25 packages failed to install. Eventually the installer gave up and tried to run dpkg --configure -a but that fails, eventually with "too many errors."

The first error I got was
```
Preparing to replace findutils 4.4.0-2ubuntu3 (using .../findutils_4.4.0-2ubuntu4_amd64.deb) ...
install-info: No dir file specified; try --help for more information.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg: - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
```
Then it goes on to say that findutils failed and I get a number of other messages in that vein for things like readline, util-linux, cpio, and others.

At this point, I have no network connection, I can't log in except at a console. I don't have ssh access.

I'd really rather not copy my home directory off and then reinstall. Is there anything I can do to recover?

I'm happy to provide more information, but I have no idea what is relevant at this point.

---

### Post by JovianMisteri on 2009-05-16
I have a very similar problem, yet not likely initiated the same way. After upgrading from Intrepid, I had issues with my nvidia drivers and the display. A simple apt-get update would have solved this- except for the fact that after trying, I can no longer login to a gui, safemode included! I'm a linux beginner stuck in tty/console without networking. Halfway through normal boot I get something of "kinit: no resume image, doing normal boot" (not.) I'm sure this shouldn't resort to fresh installing. Anyone?

---

### Post by steve c on 2009-05-16
After setting up my /etc/network/interfaces file (which something in the upgrade process had decided to change, I think), I was able to run apt-get update and then apt-get upgrade however, I had the same error about install-info.

That lead me to [this post](http://naveendageek.blogspot.com/2009/03/install-info-no-dir-file-specified-try.html). It seems that installing texlive 2008 and including symlinks in /usr/local/bin has the unfortunate effect of installing a symlink to GNU's install-info into /usr/local/bin and since that was in my path (why does apt-get not set the path environment variable appropriately?) before ubuntu's, the install failed.

I renamed GNU's install-info as per the above link. Then I ran
```
apt-get clean
apt-get upgrade
dpkg-reconfigure -a
```
That failed part way though, I restarted and was able to log in normally, although my graphics settings are wrong. Now I'm able to run ```
dpkg-reconfigure -a
``` again. I hope everything will work at this point, but I have no idea what didn't get done by the failed dist-upgrade.

---

