---
title: "How have your upgrades gone?"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by Nopposan on 2009-10-22
[COLOR="Navy"][B][U]** Please vote in this poll AND THEN INVITE ALL OF YOUR FRIENDS.  Thanks! **
[/U][/B][/COLOR]
Hello all.  I am still sitting on the fence between Ubuntu and Debian.  I install both depending on circumstances.  The only thing that's keeping me from switching entirely to Ubuntu/Xubuntu as my OS of enthusiastic first choice is that I've had problems upgrading it in the past. Version 6.10 on, I think, have always given me one problem or another after upgrading; whereas I've never had problems upgrading Debian -- However, I have no idea why this is really, and it could just be my bad luck.  As I typically install systems for other people, not for my personal use, and as my users are generally first-time Linux users, I want to make sure that their experience is a good one.  This is especially an issue with Ubuntu as a new release comes out so frequently; I know that folks can go on using the old system, but they'll feel like they are using something second-rate and out of date after awhile.

So, I'm posting this poll to get an idea what you all think of the Ubuntu upgrade system; Has it worked for you?  Without a hitch?

---

### Post by dkknight593 on 2009-10-22
That crazy partial upgrade thing ain't working for me.  It showed up even in my fresh install.

---

### Post by dkknight593 on 2009-10-22
I think part of the problem is working things out as gnome and Ubuntu are depricating a few systems.

---

### Post by slakkie on 2009-10-22
> **Nopposan said:**
> 
So, I'm posting this poll to get an idea what you all think of the Ubuntu upgrade system; Has it worked for you?  Without a hitch?

It has worked for me every time I've done it. The only issue I had was an Xorg/Intel issue when upgrading from 8.04 to 8.10. But I'm convinced this would have happened also with a fresh install (never tested it, went back to 8.04). 

I even did upgrades from 4.10 to 8.04 (in a VM, but nevertheless, it worked like intended). The upgrades with Ubuntu can be done the same way as one would upgrade Debian, although the do-release-upgrade script (which is the cli version of update-manager, can be retrieved by installing update-manager-core).

The upgrades from 4.10 to 6.06 are done on the Debian way, by doing dist-upgrade. Everything from 6.06 upwards is done via the update-manager/do-release-upgrade.

Somewhere around the alpha 2 release of Karmic I've upgraded from Hardy to Karmic alpha 2, this is an upgrade from 8.04 to 8.10 to 9.04 to 9.10. Which went fine. 

If you use clonezilla (or some other tool which allows you to backup/restore images) you can easily roll back when you encounter to much problems. I only needed it once ;)

---

### Post by AK Dave on 2009-10-22
Upgrades almost always work well for me, if I do a little work ahead of time to make sure that the system is ready for a dist-upgrade. Little things, like backing out of that PPA intel video driver, for example. 

Nevertheless, I still routinely recommend OTHER people to do a full reinstall. 

My usual advice is: plan to do a reinstall, backup everything you would want to backup for a reinstall, then go ahead and prep and perform the upgrade since you're already planning to reinstall the system anyways. If anything goes wrong with the upgrade, you're ready with a fresh backup to do a reinstall. If everything goes right, you save the backup as a snapshot of that date and drive on.

---

### Post by KhanTG on 2009-10-22
> **AK Dave said:**
> Upgrades almost always work well for me, if I do a little work ahead of time to make sure that the system is ready for a dist-upgrade. Little things, like backing out of that PPA intel video driver, for example. 

Nevertheless, I still routinely recommend OTHER people to do a full reinstall. 

My usual advice is: plan to do a reinstall, backup everything you would want to backup for a reinstall, then go ahead and prep and perform the upgrade since you're already planning to reinstall the system anyways. If anything goes wrong with the upgrade, you're ready with a fresh backup to do a reinstall. If everything goes right, you save the backup as a snapshot of that date and drive on.

+1

I agree with AKDave completely..  I have hit-or-miss luck with upgrades in Ubuntu.. so I just do a clean-install every time.

---

### Post by Mark Phelps on 2009-10-23
Have been doing upgrades on one machine since 7.04 and never had a problem.

However ...

Lots of folks got burned upgrading from 8.10 to 9.04 if they had ATI restricted drivers in place and one of the cards for which those drivers were no longer supported in 9.04.

So, a good general guide is to remove any restricted drivers BEFORE you do an upgrade.

---

### Post by markbuntu on 2009-10-23
Hardware issues and non-standard-repository software can kill you in an upgrade. I find it easier to just do a clean install into a separate partition. Them migrate /home and resize etc with gparted after it works. Also put the new grub in the partition and chainload to it from the MBR grub.

People with ati were not the only ones with problems. Broadcom drivers failed, nvidia drivers failed, atheros driver failed, pretty much every restricted/proprietary driver not from the ubuntu repositories. Unsupported really does mean unsupported in an upgrade.

I have one stable install at the MBR that I never mess around with. Debian is great for that, so is Hardy.

This never leaves me with no working system, I can always boot something and fix stuff in other partitions. I can also move my personal stuff to another distro as I want/need to. I have 6 distros on my machine and room for many more. You only need 10GB or so for a trial distro install.

karmic comes with grub2 and a lot of people have been complaining about/having problems with it for months. I did not put it on my MBR, I put it in the karmic partition where it cannot cause me trouble.

---

### Post by BoredOutOfMyMind on 2009-10-24
> **markbuntu said:**
>  Broadcom drivers failed, nvidia drivers failed, atheros driver failed, pretty much every restricted/proprietary driver not from the ubuntu repositories. Unsupported really does mean unsupported in an upgrade.

I wish I had video from 9.10 fresh install where live enabled Broadcom worked perfect and then through install to flashing login with errors for Broadcom at boot. 

Desktop is 9.04 and last kernel upgrade lost Nvidia..... Low graphics are the pits when you are used to a 22 inch desk space!  :mad:

---

