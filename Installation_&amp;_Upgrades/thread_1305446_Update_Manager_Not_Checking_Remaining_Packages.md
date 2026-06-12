---
title: "Update Manager Not Checking Remaining Packages"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by KoffeeKup on 2009-10-29
Well I've tried updating to Karmic via Update Manager and I kept having to cancel while it was downloading packages. I managed to get it up to past 1000 of my needed packages out off 1300 something. Now when I try running through to get the packages again, it ends an error saying that it cannot get x.yz packages from ubuntu.archive.org (or something). Can anyone provide a workaround to this issue so that I can get a more faster speed and/or reliable connection?

---

### Post by running_rabbit07 on 2009-10-29
> **KoffeeKup said:**
> Well I've tried updating to Karmic via Update Manager and I kept having to cancel while it was downloading packages. I managed to get it up to past 1000 of my needed packages out off 1300 something. Now when I try running through to get the packages again, it ends an error saying that it cannot get x.yz packages from ubuntu.archive.org (or something). Can anyone provide a workaround to this issue so that I can get a more faster speed and/or reliable connection?

First thought is to download, burn and insert the Alternate installer ISO and upgrade from there. That is the way I upgraded.

---

### Post by flipper9 on 2009-10-29
On the first tab of preferences/settings for upgrade-manager, you can specify where you download your packages from.  Try selecting a different mirror source other than the main server, since it is getting hit hard right now.

---

### Post by joewski on 2009-10-29
> **KoffeeKup said:**
> Well I've tried updating to Karmic via Update Manager and I kept having to cancel while it was downloading packages. I managed to get it up to past 1000 of my needed packages out off 1300 something. Now when I try running through to get the packages again, it ends an error saying that it cannot get x.yz packages from ubuntu.archive.org (or something). Can anyone provide a workaround to this issue so that I can get a more faster speed and/or reliable connection?

I had the same issues but they are not difficult with each in place upgrade. 

You probably have enough of the upgrade to proceed with the upgrade anyway. The problem you encountered has to do with the repositories being updated when you are trying to download your files. If you switch repositories you can keep collecting the remaining files tell you have an almost complete set.

Eventually you will be able to run update-manager -d and press the upgrade button and start upgrading. Once you have upgraded as much as you can and installed Karmic. Reboot the machine. You will then need to switch any third party repositories over to Karmic. The process is pretty simple replacing jaunty with karmic. Then run the update-manager again. Proceed to update. You may also then finally need to switch to Ubuntu's main server to pick up any stray packages that haven't been updated.

In the updating of repositories be prepared to lose a few. I lost three of them, and will need to manually re-establish the correct web site links etc.

---

