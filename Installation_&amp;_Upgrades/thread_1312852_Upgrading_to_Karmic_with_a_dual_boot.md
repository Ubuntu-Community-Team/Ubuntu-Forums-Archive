---
title: "Upgrading to Karmic with a dual boot"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by snakeman21 on 2009-11-03
Hi all.  I run only Ubuntu on my computer, so I'm coming here for advice on this.  

I run Karmic Koala, and my wife currently has Jaunty and Windows XP.  She knows virtually nothing about computers, and would be lost trying to upgrade, so she asked me to do it.  

My question is this:  How do I upgrade her existing Jaunty install to Karmic, while leaving her XP partition untouched?  Will doing it from the update manager affect her Windows install?  

Forgive if I sound like a n00b, I am actually a pretty seasoned user.  I just prefer to do a clean install every time I get a new distro.  

Are there disadvantages to using the update manager?  If so, I may just use Gparted to eliminate the Jaunty partition and set up a fresh dual boot.  I would like to avoid this, however, as Windows doesn't like it when you resize its partition.

---

### Post by Kevbert on 2009-11-03
You can do this via Update Manager providing that you have Normal releases selected in System-Admin-Software Sources-Updates Tab (Under Release Upgrade). You'll still see your current Jaunty kernel shown in the Grub menu so if you have problems you can still boot from that. It won't affect Windows.

---

### Post by snakeman21 on 2009-11-03
Cool.  Now, another question:  The new version of GRUB is SO fast.  Will upgrading via the update manager upgrade GRUB as well?

---

### Post by Kevbert on 2009-11-04
Jaunty uses grub, but Karmic uses grub2 by default.  If it doesn't update the grub2 files or you decide to keep your current startup configuration you can manually update it in terminal with
```
sudo update-grub
```

---

### Post by snakeman21 on 2009-11-04
Great.  I decided to go ahead and do it, and guess what?  After the upgrade, sound does not work, and the touchpad does not not work.  I've spent the last 4 hours trying to fix it, with no luck.  I've tried every solution I could find on these forums, and non of them work.  Altogether, I just wasted 6 hours of my day off doing this, only to find out that I have to mess with partitions and do a clean install anyways.  I am NEVER upgrading with the update manager again.  Not to mention that I have to download Ubuntu again.  The only version I have saved is 64-bit, and my wife has a 32-bit processor.  

Lovely.

---

### Post by ratcheer on 2009-11-04
Kevbert, how can I determine whether the 9.04 to 9.10 upgrade updated me to grub2? I have entered "grub help", but I see no option to report the version.

Thanks,
Tim

---

### Post by Kevbert on 2009-11-04
> **ratcheer said:**
> Kevbert, how can I determine whether the 9.04 to 9.10 upgrade updated me to grub2? I have entered "grub help", but I see no option to report the version.

Thanks,
Tim

If you have grub2 the version will be 1.97 and when you reboot the version will be displayed (at the top) as '1.97beta4' when it displays the new grub menu.
You can get the version with the terminal command
```
grub --version
``` only for grub (will show 0.97 for grub) but does NOT work for grub2.
Grub2 does not use the menu.lst file but grub.cfg and grub files amongst others. If you want to modify your boot configuration it may be worth installing Startup Manager (in the repos, via Synaptic).

---

### Post by Kevbert on 2009-11-04
> **snakeman21 said:**
> Great.  I decided to go ahead and do it, and guess what?  After the upgrade, sound does not work, and the touchpad does not not work.  I've spent the last 4 hours trying to fix it, with no luck.  I've tried every solution I could find on these forums, and non of them work.  Altogether, I just wasted 6 hours of my day off doing this, only to find out that I have to mess with partitions and do a clean install anyways.  I am NEVER upgrading with the update manager again.  Not to mention that I have to download Ubuntu again.  The only version I have saved is 64-bit, and my wife has a 32-bit processor.  

Lovely.

Sorry to hear your problems. Upgrading distributions can be a bit of a nightmare, so it is always best to backup all data. If you've just upgraded you can still use the old kernel via the grub menu which should be 2.6.28-16. Clean install is always the best option.
You can get audio information with
```
lshw -C multimedia
```
and then include this info and Ubuntu in a google search (better than the search on here IMHO).
It may be worth reporting a bug on [[COLOR="Red"]Launchpad[/COLOR]]("https://launchpad.net") or asking a question there.

---

### Post by snakeman21 on 2009-11-04
I was still able to use a usb mouse, so I downloaded 32-bit and made a usb startup disk with it.  Then I rebooted her computer with it and used gparted to delete the Ubuntu partition, leaving just her Windows partition.  Then I did a clean install and everything is working.  What a nightmare, though!  I personally always do a clean install on my computer, but I thought it was worth a shot to try it on hers and not have to spend an hour restoring a backup of all of her files.

Live and learn, I guess.  No more upgrades from the update manager for us!

---

