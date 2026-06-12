---
title: "Separate Home Partition"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by CaesarLike on 2009-01-02
Hi there,

Just a simple question about creating a separate partition for the /Home directories.  If I used a separate partition for the /Home directories, and I had to reinstall Ubuntu, would the reinstall recognize the accounts on the /Home partition?  I assume I would have to re-created the accounts themselves, but if so, would Ubuntu recognize the existing files etc that are on the /Home directory?  What exactly is the procedure for reinstalling Ubuntu onto its own OS partition, and accessing the accounts on an existing /Home partition?

---

### Post by 2hot6ft2 on 2009-01-02
I think this will answer all your questions.
[http://www.go2linux.org/how-to-move-home-directory-to-another-partition](http://www.go2linux.org/how-to-move-home-directory-to-another-partition)

---

### Post by Sef on 2009-01-02
> If I used a separate partition for the /Home directories, and I had to reinstall Ubuntu, would the reinstall recognize the accounts on the /Home partition?Yes, it will.  I have reinstalled Ubuntu a number of times - usually an update.

> I assume I would have to re-created the accounts themselves, but if so, would Ubuntu recognize the existing files etc that are on the /Home directory?Upon reinstall of Ubuntu, your home patition would be recognized.  

> What exactly is the procedure for reinstalling Ubuntu onto its own OS partition, and accessing the accounts on an existing /Home partition?Reformat the root patition (/) only.   Swap will automatically reformatted.   Leave the home partition alone.

**Back up** your files before upgrading or clean installing.

---

### Post by logos34 on 2009-01-02
Don't forget to point the installer to the separate /home mountpoint (but do NOT check the 'Format' box!).  Like this:

> [Clean Install Upgrade (not recommended)]("https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion")

If your /home directory is contained on a separate hard-disk partition you should be able to upgrade by performing a clean install of the current release of Ubuntu and 'adopting' the old /home directory.

Back-up any important data before following this procedure as data loss is possible, and very well may be likely.

   1. Obtain an installation CD for the release of Ubuntu you wish to install, and boot from it.
   2. Start the installation process. When you reach the Prepare disk space stage of installation, choose the Manual option and press Forward.
   3. Identify your current '/' (root) partition. Select '/' as the mount point and ensure that Format is ticked. You will lose all data on this partition and the new version of Ubuntu will be installed there instead.
   4. Identify your swap partition and set its mount point as 'swap'.
   5. [COLOR="Red"]  Identify your /home partition. Set its mount point as '/home' and make sure that Format is **not** ticked.[/COLOR]
   6. Continue installation as normal until you reach the Who are you? stage, enter a username and password which exactly match your current username and password.
   7. Complete the installation as normal. 

Once the installation has completed, you should be able to log in to Ubuntu and your /home partition with all of your documents and settings should be intact.

---

### Post by Viva on 2009-04-24
Why is it not recommended to clean install using an existing home partition?

---

### Post by Sef on 2009-04-24
> Why is it not recommended to clean install using an existing home partition?


A clean install is the recommended way to update Ubuntu.   Less problems with a clean install than an update.

---

### Post by Viva on 2009-04-24
> **Sef said:**
> A clean install is the recommended way to update Ubuntu.   Less problems with a clean install than an update.

Should I backup and format the home partition then?

---

### Post by logos34 on 2009-04-24
> **Viva said:**
> Why is it not recommended to clean install using an existing home partition?

probably because of the part about possible data loss (overstated IMO, but the risk is always there whenever you manipulate installations, and they just don't want to be responsible)...I think it reflects a bias toward netork upgrade (not all that much safer--plenty of borked installations to prove otherwise!), or just standard fresh install on / only

---

