---
title: "Upgrade woes"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by bkline on 2009-10-31
What's up with the upgrade from 9.04 to 9.10?  I've tried it on two machines, with abysmal results.  On the first box I tried the network upgrade, which is the recommended approach.  I started early this morning, and things just got slower and slower.  At one point the dialog window was telling me it would take 24 days before the "Getting new packages" phase was done.  Now (and "now" means late at night) it doesn't even try to estimate how long it would take until it's done; we went down the street for a party after the last trick-or-treater had left, and before we went out the door I saw that the dialog box was saying "Fetching file 1369 of 1833."  Looked again when we got back home and it still says the same thing.

Strongly discouraged by the progress following the "recommended" approach, I decided to fall back on plan 'B' for the other machines, so I downloaded the ISO for the alternate CD, burned it, popped it in the drive, and started the upgrade using the CD, augmented by files from the network which aren't on the CD (at least I assume that's what it was doing; the online description of how this works wasn't as informative as it could have been).  When I came back to see how it was coming along, I saw a dialog window filled with a list of all the files it had tried to download and couldn't, and saying the upgrade was aborted.

I see the little green box at the top of this page, touting Ubuntu 9.10 as "the best version of Ubuntu yet."  Really?

---

### Post by RexRCU on 2009-11-01
Assuming that the cd burned correctly, perhaps you could clarify matters for yourself by using it while disconnected from the Internet and see how that goes?
I was updated last night from the Super OS install that has worked perfectly for me, and it caused over 1400 packages to download and yes it was tending to be much slower than usual but it worked out perfectly as far as I can tell so far. (Super OS is a modified Ubuntu with non free already included. Listed on Distrowatch.):D

---

### Post by Don1500 on 2009-11-01
Took me 3 trys but a complete clean install to 2 partitions (/root & /home) did it for me. SAVE EVERYTING YOU WANT TO KEEP! best on a third drive. Then do the install from a good CD (NOT UPDATE MANAGER) and fromat both partitions (I used etc4, but that's up to you). It is Grub that gave me the most trouble, couldn't get it to load right (Grub Error > No Such Disk) But the third reload got it right and everything is working.......for now. With earlier versions I found that once you get a good install everything works... untill the next upgrade.

---

### Post by bkline on 2009-11-01
Since my last post I stumbled on this [thread]("http://ubuntuforums.org/showthread.php?t=1307482"), and as a result I'm actually glad the upgrade failed on both machines.  I'm not tempted to start all over again with a fresh install of the OS (and reconfigure all of my apps) every time an upgrade comes along (that's one of the reasons I'm using Linux instead of Windows, after all).  I think I'll wait until the dust settles.  I'll skip 9.10 if that's what it takes.

---

### Post by GepettoBR on 2009-11-01
> **bkline said:**
> Since my last post I stumbled on this [thread]("http://ubuntuforums.org/showthread.php?t=1307482"), and as a result I'm actually glad the upgrade failed on both machines.  I'm not tempted to start all over again with a fresh install of the OS (and reconfigure all of my apps) every time an upgrade comes along (that's one of the reasons I'm using Linux instead of Windows, after all).  I think I'll wait until the dust settles.  I'll skip 9.10 if that's what it takes.

You don't have to reconfigure anything if you backup your home directory first. All your configurations are kept there in hidden files and folders. You'll have to reinstall any software that doesn't come with the default installation (for example, Thunderbird) but if you restore your backed up /home/<username> directory, they'll already be configured just as they were before. I just did a clean install and didn't even have to reinstall my Firefox extensions (with the sole exception of Adblock Plus. I have no idea why.) or re-enter my e-mail account information in Thunderbird.

---

### Post by bkline on 2009-11-01
> **GepettoBR said:**
> You don't have to reconfigure anything if you backup your home directory first.

That might be true if it weren't for things like databases, or /etc, or /var/www, or local python packages, etc., and if there were a guarantee that no upgraded version of any application would ever choke on configuration settings created by an earlier version of the software.

---

### Post by bkline on 2009-11-02
Yikes!  I thought when the upgrade processes reported that they had failed the story was over, and the bottom line was I'd just end up waiting until the dust settles for 9.10 (or perhaps skip it altogether, treating this as Ubuntu's answer to Vista).  But the Ubuntu team had more surprises in store.  When I got up this morning Update Manager on one of the machines reported that it had **hundreds** of updates to install.  I was a little suspicious, so I took a peek at /etc/apt/sources.list, and sure enough, even though Update Manager says that the upgrade to 9.10 is "available" as an option, all the sources are pointing to karmic!  So now I'm wondering in what other places the system is left in an inconsistent state.

What could they have been thinking when they released this nightmare?

---

### Post by bkline on 2009-11-02
This gets worse and worse!  Ubuntu kept nagging me to "complete the unfished upgrade" so I caved in and told it to go ahead.  Now the wireless networking doesn't work at all on that machine.  So now I guess I have no choice but to do a fresh install.

Thanks, Ubuntu.
:(

---

