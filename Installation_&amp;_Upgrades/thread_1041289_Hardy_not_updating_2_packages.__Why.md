---
title: "Hardy not updating 2 packages.  Why?"
date: 2009-01-16
forum: Installation &amp; Upgrades
---

### Post by quixote on 2009-01-16
Update manager says console-setup and acpi-support can be updated, but they don't update.  (Which also means I have a constant (by now) annoying orange update icon in Notification Area.)

I've tried the string of commands to fix it: ```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
``` but it won't do it from the command line either.

Granted, it's a very minor version increment, and it's no big deal, but I'm curious why apt / update manager is skipping over those files like this.

Anybody out there know?

---

### Post by taurus on 2009-01-16
Have you tried the

```
sudo apt-get upgrade
```

---

### Post by Pumalite on 2009-01-16
Try
```
sudo apt-get dist-upgrade
```

---

### Post by quixote on 2009-01-16
No, I haven't tried that because I thought it would upgrade my system to Intrepid.  Since my 2005 computer suffers what looks like a kernel panic whenever I try to boot an Intrepid LiveCD, I'm phobic about touching anything that might take me down that path.  (I've tried about three or four separate downloads and about five different CDs.  The drive otherwise works.)

I assume sudo apt-get dist-upgrade really would (try to) move me to Intrepid.  

But can I try sudo apt-get upgrade with impunity?

Thanks for your help!

---

### Post by Partyboi2 on 2009-01-16
> **quixote said:**
> No, I haven't tried that because I thought it would upgrade my system to Intrepid.  Since my 2005 computer suffers what looks like a kernel panic whenever I try to boot an Intrepid LiveCD, I'm phobic about touching anything that might take me down that path.  (I've tried about three or four separate downloads and about five different CDs.  The drive otherwise works.)

I assume sudo apt-get dist-upgrade really would (try to) move me to Intrepid.  

But can I try sudo apt-get upgrade with impunity?

Thanks for your help!
This is what the man page says about dist-upgrade
> dist-upgrade
           dist-upgrade in addition to performing the function of upgrade,
           also intelligently handles changing dependencies with new versions
           of packages; apt-get has a "smart" conflict resolution system, and
           it will attempt to upgrade the most important packages at the
           expense of less important ones if necessary. The
           /etc/apt/sources.list file contains a list of locations from which
           to retrieve desired package files. See also apt_preferences(5) for
           a mechanism for overriding the general settings for individual
           packages.
As you can see it retrieves the packages from the repos listed in /etc/apt/sources.list, because you are not changing you sources.list it is only going to retrieve everything from your current repos which I am guessing is Hardy.

For upgrade
 > upgrade
           upgrade is used to install the newest versions of all packages
           currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new
           versions available are retrieved and upgraded; under no
           circumstances are currently installed packages removed, or packages
           not already installed retrieved and installed. New versions of
           currently installed packages that cannot be upgraded without
           changing the install status of another package will be left at
           their current version. An update must be performed first so that
           apt-get knows that new versions of packages are available.
Upgrade does the same as Update Manager except that you are doing it from the command line instead of using the gui.

---

### Post by quixote on 2009-01-16
It looks like ```
sudo apt-get dist-upgrade
``` --the one I was so afraid of :D -- was what I needed.  That finally did it.

Thanks a million, folks!  The ubuntu community is truly a thing of beauty!

---

