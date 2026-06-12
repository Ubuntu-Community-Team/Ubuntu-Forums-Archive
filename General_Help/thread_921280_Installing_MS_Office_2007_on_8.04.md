---
title: "Installing MS Office 2007 on 8.04"
date: 2008-09-16
forum: General Help
---

### Post by br0kan on 2008-09-16
As much as I hate to admit it, I really need some of the features in Office to get work done.  I've been getting complaints about papers I've been turning in "not quite looking right" because of some quirks in OpenOffice.

Thus, I tried installing MS Office 2007 in Ubuntu 8.04 but to no avail.  I tried following the tutorial located at [http://samanathon.com/how-to-install-microsoft-office-2007-in-ubuntu-804/]("http://samanathon.com/how-to-install-microsoft-office-2007-in-ubuntu-804/")

Which seemed to work right up until I actually click the "Install" button in MS Office 2007 setup.  I am getting the following errors in what seems to be an infinite loop.

fixme:hook:IsWinEventHookInstalled (32773)-stub!
fixme:xrender:X11DRV_AlphaBlend not a dibsection

Any ideas?

---

### Post by Ms_Angel_D on 2008-09-16
Why not just install XP or Vista on virtualbox and run MS Office that way?

---

### Post by kokkus on 2008-09-16
Hehe wine doesn't support MS office.
But which functions do you need that you can not find in openoffice?
Most of the functions are avalable as extra plugins for OO. Maybe if you tell which functions you miss someone here can help you.

---

### Post by geeth on 2008-09-16
I believe office 2003 should install fine through wine.
Is there a reason that you HAVE to have 07?

---

### Post by kokkus on 2008-09-16
> **geeth said:**
> I believe office 2003 should install fine through wine.
But it won't work that stabile.

Try to install verion 2003 if you feel for it, but the bet thing would be to just go to their extensions (plugins) site and see if you can find everything you need there.
[http://extensions.services.openoffice.org/most_pop_ext](http://extensions.services.openoffice.org/most_pop_ext)

An other thing you could do is to download and install the 3.0 version and see if this one solves your needs.

---

### Post by The_pensive on 2008-09-16
If you check in WineHQ office 2007 could work well (it received a gold and bronze medal). There are 2 ways to install the 2007 but nothing worked for me. Actually I don't like openoffice, that's why i'd like to install the 2007. As MetalHellsAngel said, you could install xp/vista in a virtual machine, then install office. Personally i hate that.. Is like to use a 18wheels truck to move a 24hours-bag...
This is the winehq page of office 2007 [http://appdb.winehq.org/appview.php?iVersionId=4992](http://appdb.winehq.org/appview.php?iVersionId=4992) there you could find the 2 howto links.

---

### Post by mb_webguy on 2008-09-16
> **kokkus said:**
> [QUOTE=geeth;5798226]I believe office 2003 should install fine through wine.

But it won't work that stabile.
[/QUOTE]

Under older versions of Wine (including the version in the Ubuntu repositories, I believe), Office 2003 wouldn't install without using some native Windows dll files.  Under the more recent versions of Wine (available through the Wine HQ repository), however, it installs just fine and is quite stable.

I haven't had any luck installing Office 2007 under Wine, though...

---

### Post by pmlxuser on 2008-09-16
you can install office 2007 with wine. however there are several steps that you need to do.
the required dll can be installed nicely using a small script called wine tricks found at 
[http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks) 

follow the instructions on that page you will be able to install office 2007 on your machine.

PS: patience is everything... ;)

---

