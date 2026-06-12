---
title: "Backuping up Ubuntu packages"
date: 2008-07-31
forum: General Help
---

### Post by alzaf on 2008-07-31
Hi

Due to circumstance I may need to get rid of my home internet connection for a period of time. I'm going through the implications of this and one of them is that if something happens to the partition containing Ubuntu, I will be able to reinstall it but won't be able to download packages that I require. 

With that in mind, I think the best solution is to backup these packages on either my external hard drive or blank CD/DVD. Does anybody know the easiest option to do this.

---

### Post by coffeecat on 2008-07-31
The downloaded .deb packages are in /var/cache/apt/archives. So long as you haven't run 'sudo apt-get clean' at any time, the cache should contain all the packages used for updates since you installed. You can simply copy them out onto whatever media you want for storage. There's a file called 'lock' which can cause problems copying the lot, but there are ways of getting round this.

If you need to reinstall, simply copy the packages back into the new /var/cache/apt/archives. Synaptic or the update manager will detect their presence and not try to re-download them.

**However**, there is one big problem. Synaptic/update manager/apt-get needs the latest package information metadata - what you download when you 'Reload' In Synaptic - and without that it won't know that there are newer packages to install.

Offhand, I don't know how to get round this. Hopefully, someone else will be able to suggest something.

---

### Post by Diabolis on 2008-07-31
This is exactly what you need: [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by chrisccoulson on 2008-07-31
I've got a funny feeling that the contents of /var/cache/apt/archives gets cleaned out over time. However, you can re-download all of the packages currently installed on your system before you lose your internet connection.

To do this, open Synaptic. Click on the 'Status' button in the bottom left-hand side of the window. Then, in the left-hand pane, click 'Installed'. This will list every package installed on your machine.

Select every package, then right-click and select 'Mark for Reinstallation'. Click 'Apply', and **make sure that that 'Download package files only' is checked**. When you click Ok, all of the packages on your system will be re-downloaded but not re-installed.

Once you've done this, it is then just a matter of backing up /var/cache/apt/archives. To do this, you can use AptOnCD, which is available in the repositories.

---

### Post by alzaf on 2008-07-31
Got aptoncd and create an iso image. Will follow steps to fully back up nearly to time. 

Thanks to all who posted.

---

### Post by Yannick Le Saint kyncani on 2008-07-31
> **alzaf said:**
> Due to circumstance I may need to get rid of my home internet connection for a period of time. I'm going through the implications of this and one of them is that if something happens to the partition containing Ubuntu, I will be able to reinstall it but won't be able to download packages that I require.

Hi alzaf, I'm kinda in the same situation.

If you just worry about what will happen to your existing ubuntu partition, you should make backups. Backups will allow you to restore anything if you have a crash. (howtos on the web).

If you also want to be able to install additional packages, then I've dealt with it in the past by downloading the entire archive using debmirror and kept an install cd at hand. (howtos also on the web).

---

