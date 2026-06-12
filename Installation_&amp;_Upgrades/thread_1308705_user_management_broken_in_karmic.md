---
title: "user management broken in karmic?"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by RavanH on 2009-10-31
Hi,

Since I did a fresh install of Karmic without overwriting my /home partition, I am having trouble setting up all the users I had on the system before.

I can create a new user but after that, I cannot change the home folder nor the main group that user belongs to... When I try to change these values via the GUI for user management, it seems to work but after closing the GUI and opening it again, the old values are back.

Hope I explained that clear enough. Can anybody confirm this or has there something gone wrong on my install?

Thanks!

---

### Post by zuehls on 2009-11-01
I have the same issue.  Changing the "Main group" gets reverted back to the user's group after closing.

---

### Post by jborgmann on 2009-11-03
Bump.  Same issue here.  Fresh install of Karmic.  I have my home directories in a separate LVM partition.  Install went fine.  Installed LVM2 and the partition mounted fine.  When I go to Users and Groups, unlock, and change my home directory the setting doesn't stick.

I have tried multiple fresh installs (3) and all are the same.

I have chmod'd the old home dir with no better results.

From the CLI I tried 'sudo usermod --home /other/partition myuser' and I get a message stating "usermod: user myuser is currently logged in".  This in and of itself seems odd.  In all of my years with linux and bsd I have never seen usermod as rood fail for any reason relating to the user being logged in.

I created a new user (through Users and Groups) and gave that user admin permissions.  Logged in as them and then changing my original login $HOME worked.  However, after moving to my new $HOME I have now lost sound and the ability to administer other things (graphics).

Any help?

-jb

---

### Post by Simon Bridge on 2009-11-30
bump - I have a similar effect.
This time creating a user via gui does not set the password.
I can create a user via cli with adduser, even log in, but some time later the password has reset. I see nothing in the logs.
Still googling for the fix.
Has anyone done a bug report?

---

