---
title: "[SOLVED] &amp;quot;The list of changes is not available&amp;quot; - Recurring 8.10 Update Manager Probl"
date: 2008-11-06
forum: General Help
---

### Post by aaaantoine on 2008-11-06
Ever since I upgraded to Ubuntu 8.10, there have been quite a few package updates.  Not a single one of them has had a change log.

I know to go to [http://packages.ubuntu.com/intrepid](http://packages.ubuntu.com/intrepid) if I want to see the change log, but today there are 19 packages receiving updates, and it takes me that much longer to see what was updated.

I almost want to post this on Launchpad as a regression.

*grumble grumble.*

---

### Post by Twilight in Zero on 2008-11-06
Unfortunately, I can contribute no more than a "me too" post.

I too am experiencing this.

---

### Post by philinux on 2008-11-06
> **aaaantoine said:**
> Ever since I upgraded to Ubuntu 8.10, there have been quite a few package updates.  Not a single one of them has had a change log.

I know to go to [http://packages.ubuntu.com/intrepid](http://packages.ubuntu.com/intrepid) if I want to see the change log, but today there are 19 packages receiving updates, and it takes me that much longer to see what was updated.

I almost want to post this on Launchpad as a regression.

*grumble grumble.*

This needs a bug raising. On my fresh install it works fine. Have you both tried completely removing update-manager then reinstalling.

---

### Post by Fazer2 on 2008-11-07
Same problem here, upgraded from 8.04 to 8.10.

---

### Post by aaaantoine on 2008-11-07
> **philinux said:**
> This needs a bug raising. On my fresh install it works fine. Have you both tried completely removing update-manager then reinstalling.

I waited for today's batch of updates before reinstalling.  I ran [FONT="Courier New"]apt-get purge update-manager[/FONT] -- which also removed update-notifier and ubuntu-desktop -- and then [FONT="Courier New"]apt-get install update-manager update-notifier[/FONT].

The list of changes is still not available.

---

### Post by Fazer2 on 2008-11-07
I found the solution to this problem. I installed proposed updates for update-manager and update-manager-core. The changelogs are visible again.

---

### Post by SamNSane on 2008-11-07
> **Fazer2 said:**
> I found the solution to this problem. I installed proposed updates for update-manager and update-manager-core. The changelogs are visible again.

I just have the backports repository enabled and am not getting the lists of changes with updates. I'd like to be getting the lists, but I'd rather not enable proposed.

Are you saying that you only enabled proposed for long enough to get its updates for update-manager and update-manager-core? Or do you normally have the proposed repository enabled?

---

### Post by aaaantoine on 2008-11-12
It appears this problem is fixed (for me) as of the latest update.

---

### Post by SamNSane on 2008-11-12
Yeah, my update-manager is behaving itself now, too.

Of course -- I cheated. I went back to 8.04.

[grin, duck, and run]

---

### Post by aaaantoine on 2008-11-12
> **SamNSane said:**
> Yeah, my update-manager is behaving itself now, too.

Of course -- I cheated. I went back to 8.04.

[grin, duck, and run]

I'm sometimes tempted to do this, but I don't because...

1. I'm too lazy.
2. I like having newer software.
3. The latest xorg-driver-ati supports acceleration in the Radeon Xpress 1100, meaning I no longer have to depend on the buggy fglrx driver in 8.10.  I think this might be my favorite reason to stick with 8.10.
4. Hardy had weird regressions, too, but most of them were resolved within the first few months.

---

### Post by SamNSane on 2008-11-12
> **aaaantoine said:**
> I'm sometimes tempted to do this, but I don't because...

1. I'm too lazy.
2. I like having newer software.
3. The latest xorg-driver-ati supports acceleration in the Radeon Xpress 1100, meaning I no longer have to depend on the buggy fglrx driver in 8.10.  I think this might be my favorite reason to stick with 8.10.
4. Hardy had weird regressions, too, but most of them were resolved within the first few months.

1. I'm lazy, too, but I was running into quite a few issues with Intrepid that were making it just a bit more work than fun.
2. I can get the apps that matter to me almost as up-to-date on Hardy as with Intrepid using the various Launchpad PPAs and getdeb.
3. I noticed that drive support for my nVidia FX Go 1400 was improved a little in Intrepid, but I'm not going to be impressed until I see basic functions like multimonitor and docking/external configurations supported at least reasonably well.
4. Yeah, I started using Hardy about 4 months after it was released. I'm thinking maybe 4 months from now...

Anyway, I'm glad you're at least getting your lists of changes in the updater now. It's just downright rude for an updater to not tell you the basic information you need to know whether or not it makes sense to install the update!

The folks on Linux Mint have kind of a nice slant on how updates should be handled. I wonder if the Ubuntu development community is considering a similar rating system to help users assess risk vs gain when updating.

---

### Post by fsando on 2008-11-12
> **SamNSane said:**
> I just have the backports repository enabled and am not getting the lists of changes with updates. I'd like to be getting the lists, but I'd rather not enable proposed.

Are you saying that you only enabled proposed for long enough to get its updates for update-manager and update-manager-core? Or do you normally have the proposed repository enabled?

Simple: enable 'proposed', find and mark only update-manager for upgrade, do the upgrade, disable 'proposed'.

---

### Post by SamNSane on 2008-11-12
Thanks, I figured that was it, but I was just asking that poster to be sure that was what had been done. Moot point to me now, as I went back to 8.04 because of the number of issues like this. There were a number of features that I just needed to have working right now.

---

