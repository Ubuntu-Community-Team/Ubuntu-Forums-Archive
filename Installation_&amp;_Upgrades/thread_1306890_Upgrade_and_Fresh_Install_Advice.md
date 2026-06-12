---
title: "Upgrade and Fresh Install Advice"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by flipper9 on 2009-10-30
Just my 2 cents regarding upgrading/installing Ubuntu 9.10 Karmic (or any other distribution of Linux/Windows)...

Q. Should I backup my data before doing anything?  
A. ALWAYS BACKUP YOUR DATA! It doesn't matter if you are upgrading, doing a fresh install, or just messing with your system. You never know what will go wrong, or if you hard drive will die. Make a backup, always, always, always. Backup data that you can't do without, like personal documents, music, etc.. Don't worry about backing up everything, as you can always reinstall and get those things back. Pictures, music, and documents are hard to recreate.

Q.  But I'm nervous about going to Karmic, whether I upgrade or do a fresh install!
A. Then run the Live CD (or install the Live CD to a USB Key using "unetbootin", or if you are using Windows use the "Wubi" installer) and test it out on your system! This is probably the best way to see if Karmic is right for your system. If everything goes well, at least you'll know that if the upgrade fails, your system will work with a fresh install. Besides, the Live CD is also the installer CD, so you don't have to do any extra work.

Also read the release notes for Karmic to find out about known issues.

Q. Should I upgrade to Karmic or do a fresh install?
A. For this release with the new EXT4 and Grub2 updates, you won't get these things unless you do a fresh install (or go through a lot of manual gyrations to upgrade them manually, and you still don't get all the benefits).

Q. But should I still do upgrading over a fresh install?
A. This is entirely up to you. Just realize that for some people there a major issues that come up with upgrading. Do you want to take that chance? If you have already backed up your data (you did backup your data, right?) then nothing is really lost but some time. If things go wrong, you can delete everything, do a fresh install of Karmic, then restore your backed-up files.

If you wish to do an upgrade, realize that old stuff might still stick around on your drive. Sometimes a fresh start is the way to go. Some people have their systems fine-tuned and setup the way they like it, so it really is a personal decision. IMHO I always do a fresh install so I avoid upgrade problems (even though they might not occur)

Q. Should I upgrade through update-manager?
A. Mmmm...again, a personal decision. What if the install goes horribly wrong? Probably better to download a Live CD version of Karmic to make sure you system will work with a fresh install. If all goes well, you can then use update-manager in your ubuntu install to do the upgrade. If things go wrong, then do a clean install of Karmic, then restore your data (you did backup your data, right?).

---

