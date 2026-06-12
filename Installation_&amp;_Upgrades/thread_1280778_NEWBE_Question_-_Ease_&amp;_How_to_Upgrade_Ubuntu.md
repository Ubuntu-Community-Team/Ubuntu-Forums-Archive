---
title: "NEWBE Question - Ease &amp; How to Upgrade Ubuntu"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by tecknomage on 2009-10-02
OK, I am running **Ubuntu 9.04** on my **Notebook**.

I see the count-down to **Ubuntu 9.10** on the **Home page**.

So, how easy is it to upgrade Ubuntu without loosing anything installed in older version :confused:

**How do you upgrade?**

As a Windows (ugh!) expert, you upgrade Windows by inserting the Setup CD for the new version AT THE WINDOWS DESKTOP. You do NOT boot to the CD. So this is why I'm asking about upgrade procedure for Ubuntu.

---

### Post by slakkie on 2009-10-02
How would one upgrade? That is pretty easy, you have a graphical upgrader and a cli upgrader.

```

sudo aptitude install update-manager update-manager-core
sudo do-release-upgrade # cli only
sudo update-manager # GUI upgrader

```

This will upgrade your current OS to a newer version. This however will not work at this moment when you want to upgrade to Karmic, since it is still a development release. 
I won't tell you how that is done, since I don't trust you to figure out any failures that might occur running a development release. Wait a month for Karmic to hit the shops on Oct 29th.

Also have a look at this page: [https://help.ubuntu.com/community/JauntyUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD](https://help.ubuntu.com/community/JauntyUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD)

It is for Jaunty, but every Ubuntu upgrade works the same.

---

### Post by tecknomage on 2009-10-05
Assume the final release of **Ubuntu 9.10** will include **upgrade instructions**?

**Detailed ones**?


Your reply seems good, but you say " graphical upgrader and a cli upgrader"  then proceed to give 3 commands. I assume if I want the GUI, I would use **sudo update-manage**r, correct?

Would I still use **sudo aptitude install update-manager update-manager-core**?

**OR**, would I need to use ALL 3 commands?

---

### Post by slakkie on 2009-10-05
> **tecknomage said:**
> Assume the final release of **Ubuntu 9.10** will include **upgrade instructions**?

**Detailed ones**?


Your reply seems good, but you say " graphical upgrader and a cli upgrader"  then proceed to give 3 commands. I assume if I want the GUI, I would use **sudo update-manage**r, correct?

Would I still use **sudo aptitude install update-manager update-manager-core**?

**OR**, would I need to use ALL 3 commands?

It will have upgrade instructions just like Jaunty and the other had. The upgrade via the cli is done like this:

```

# I usually do this step, there is no absolute need for it
sudo aptitude update && sudo aptitude safe-upgrade
# The upgrade
sudo aptitude install update-manager-core && sudo do-release-upgrade

```

---

### Post by doomsword2001 on 2009-10-05
check this out 
[http://ubuntuforums.org/showthread.php?t=1283547](http://ubuntuforums.org/showthread.php?t=1283547)
:)

---

### Post by mick222 on 2009-10-05
If you want to use the gui just check the box in software sources -> update for distribution updates, when you run update manager it should give you the option to upgrade to Karmic once it is released.
 Remember to back up your data in case anything goes wrong.

---

