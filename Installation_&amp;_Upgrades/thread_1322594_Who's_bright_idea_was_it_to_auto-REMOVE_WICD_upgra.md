---
title: "Who's bright idea was it to auto-REMOVE WICD upgrading to 9.10?"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by Amurko on 2009-11-11
WTF?  This left my comp stranded with NO internet connection cause the only connection I have is WiFi.  And removing the only WiFi manager installed meant no internet connection and NO hope of downloading updates to restore the connection till one gets access to a public computer!  Btw, I even checked Ubuntu's confirmation of removing obsolete software and WICD wasn't listed among them!

This is highly unacceptable to remove such a critical component upon upgrading without any sort of warning!!

---

### Post by wilee-nilee on 2009-11-11
So you removed the network manager instead of choosing wicd and letting it install and remove the manager at the same time. I might suggest that your complaining is not going to get you much help. Most computer problems are user error could this be the case here?

---

### Post by ErwinC on 2009-11-11
Normaly an upgrade removes Wicd and replaces it by the ubuntu networkmananger. So the ubuntu networkmanager should be installed.

---

### Post by wilee-nilee on 2009-11-11
Is the notification area in the top panel and what did you upgrade from to. sorry I missed the upgrade part.

---

### Post by Amurko on 2009-11-11
All I did was upgrade 9.04 to 9.10 and no more Wicd, no warnings!!

And I confirmed in package manager that wicd was indeed uninstalled

---

### Post by Roasted on 2009-12-08
No offense, but why did you upgrade Ubuntu to begin with? I know the option is there and should be supported blah blah but that doesn't take away from the fact that fresh installs are -the- way to go. After all, ever upgrade Windows? Linux isn't the only problematic upgradable OS out there. ;) 

I would suspect that something along the avenue of upgrading removes 3rd party setups like that. I mean, it has to - why else would WICD be gone? Then, as a result, there's no trigger to auto-reinstall network-manager.

The fix I would suspect would be to edit your network interfaces file, and add an entry for your network interface. Then you should be able to hook up (wired) and grab an IP to at least get WICD running again. Unless you just want to flash drive the WICD .deb package from another PC. That might work, but I never tried it.

---

### Post by presence1960 on 2009-12-08
> **Roasted said:**
> No offense, but why did you upgrade Ubuntu to begin with? I know the option is there and should be supported blah blah but that doesn't take away from the fact that fresh installs are -the- way to go. After all, ever upgrade Windows? Linux isn't the only problematic upgradable OS out there. ;) 

**_I would suspect that something along the avenue of upgrading removes 3rd party setups like that._** I mean, it has to - why else would WICD be gone? Then, as a result, there's no trigger to auto-reinstall network-manager.

The fix I would suspect would be to edit your network interfaces file, and add an entry for your network interface. Then you should be able to hook up (wired) and grab an IP to at least get WICD running again. Unless you just want to flash drive the WICD .deb package from another PC. That might work, but I never tried it.

That is exactly the case. When doing an upgrade all third party software installed becomes removed. I remember reading that somewhere in the community documentation about dist-upgrades.

Edit: wicd is in the universe repositories.

---

### Post by presence1960 on 2009-12-08
I always do clean installs. I always do the following so I have a list of packages installed on the current version , so I can reinstall them on the new version. This will work in the case of a dist-upgrade too. I know it is too late now for you but for future reference. here is how to do it:

To replicate your packages selection on another machine (or restore it if re-installing), you can run this:

```
dpkg --get-selections > ~/my-packages
```


This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages" to new home partition and run this code in the terminal:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```


It will download and install all the programs for you, except those that you installed manually, if they are not in the new repository. Make sure you replicate your sofware sources before running command to reinstall your packages.

---

### Post by Roasted on 2009-12-08
> **presence1960 said:**
> That is exactly the case. When doing an upgrade all third party software installed becomes removed. I remember reading that somewhere in the community documentation about dist-upgrades.

Edit: wicd is in the universe repositories.

Rock on man. Thanks for the confirmation!

I don't really see the... point... though. Why would *buntu think this is a good idea? *shrug*

---

### Post by julianb on 2009-12-08
> I don't really see the... point... though. Why would *buntu think this is a good idea? *shrug*

Might be better to give the user a warning that their "universe" software might be broken, might break the entire OS, and then give them the option to keep the software anyway. 

The only argument I can think of against that approach is:
You don't want the software to be asking people questions (do you want to delete this possibly broken software?) is that people might have no idea which answer is best for them. Don't want to overwhelm users with TOO many choices.

---

### Post by i.r.id10t on 2009-12-08
I've upgraded a few laptops and desktops, and wicd has always remained installed...

---

### Post by Clancy_s on 2009-12-08
> **Amurko said:**
> All I did was upgrade 9.04 to 9.10 and no more Wicd, no warnings!!

And I confirmed in package manager that wicd was indeed uninstalled

fwiw this not new: it happens with all upgrades, or does to me - the upgrade installs network manager and wicd is uninstalled because it's not compatible with network-manager.

All 3rd party repositories, including wicd and medibuntu are disabled and the standard ubuntu apps are installed, if there's no conflict your 3rd party apps remain, if there is a conflict with what to be installed they're removed.  Once the upgrade is finished it's up to you to redo your source list and reinstall / upgrade your 3rd party stuff.

I assume it's to make sure people at least start out with the same distro.  On my system wicd has been better with 7.10 and 9.04, network manager with 8.04 and 8.10 (wicd broke my ethernet capability with 8.04), some people have tried to make a case for changing the default from network-manager to wicd but neither is a perfect solution.

---

### Post by Roasted on 2009-12-09
Just to iterate something here : This is why it's a good practice to do fresh installs on all of your Linux (or any OS) computers.

Some people might be like well it sucks to redo Linux every 6 months etc. Not if you do partitioning properly. ;)

Create 2 partitions. One 15-20gb for root and the remainder for /home. When you install the new version, format root, do NOT format home, and bam - new install. Install your apps and you'll be in good shape afterwards. Since your home directory is left untouched, it has all of your personal settings too (theme, settings, etc) so it doesn't even look like a new install when you fire it back up. :)

---

### Post by presence1960 on 2009-12-09
> **Roasted said:**
> Just to iterate something here : This is why it's a good practice to do fresh installs on all of your Linux (or any OS) computers.

Some people might be like well it sucks to redo Linux every 6 months etc. Not if you do partitioning properly. ;)

Create 2 partitions. One 15-20gb for root and the remainder for /home. When you install the new version, format root, do NOT format home, and bam - new install. Install your apps and you'll be in good shape afterwards. Since your home directory is left untouched, it has all of your personal settings too (theme, settings, etc) so it doesn't even look like a new install when you fire it back up. :)

**A HUGE +1**

I wholeheartedly agree. That combined with the process someone shared with me described in post # 8 on this thread makes a clean install painless and way quicker than a dist-upgrade. And of course a whole lot safer that you will have a working OS when complete. How can you beat the combo of a new, clean OS and all your packages from the old install restored back to your clean install in way less time than it takes to do a dist-upgrade.

---

### Post by Tankerdog2002 on 2009-12-26
> **Amurko said:**
> WTF?  This left my comp stranded with NO internet connection cause the only connection I have is WiFi.  And removing the only WiFi manager installed meant no internet connection and NO hope of downloading updates to restore the connection till one gets access to a public computer!  Btw, I even checked Ubuntu's confirmation of removing obsolete software and WICD wasn't listed among them!

This is highly unacceptable to remove such a critical component upon upgrading without any sort of warning!!

Amurko has a legit bone to pick. So please don't flame him.

We installed wicd on two different new notebooks for our field engineers; one MALIBAL, one-Dell XPS. wicd blew out everything else in 9.04.

Everything is gone but wicd......All network connections, etho, wlan, bluetooth.....all of it gone. Nothing left but the wicd box...and it's empty worthless 'schitt. 

Fresh installs of 9.04 on both machines. Had troubles with nm holding a connection. We heard about wicd, decided to give it a try and discovered that it couldn't connect Siamese twins joined at the butt.

Our IT guys are madder than wet-hornets. It trashed the whole network on those notebooks. We couldn't even get online with cat5. 

Before you start flaming Amurko; there are others out there with similar grudges on wicd. wicd doesn't play nice sometimes and auto removes other programs.

Just Google "wicd removes"....you'll figure it out.

---

