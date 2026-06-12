---
title: "Please advise on options for upgrade!"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by FokkerCharlie on 2009-04-28
Hi all

I recently upgraded my system from 8.10 to 9.04, but really, I think it's time for a fresh install.  I don't think that I am getting the full benefit of Jaunty, after hitting 'Upgrade' since the Hardy release.  Also, I would like to make the move to 64 bit OS that did not seem a good idea when I bought my laptop.  It think that I would like to move to having a separate home partition for future upgrades, too.

Anyhoo, it strikes me that I have a couple of real options:

- Format my current Ubuntu partition, and start again.  In this case, what is the best way of setting up the separate home partition?

- Keep my existing partition, but add an extra one.  This way, I'd start dual-booting 32 and 64-bit OSs until I got things tidied up, but that's not a big problem.  Could I leave the stuff for all users where it is for easy access from the new root partition?  Currently /home/<username>.

I can restore my installed apps using dselect in either case, I think.

Is there a third way that I have missed?  Am I walking into a trap?

Your advice is much appreciated.

Charlie

---

### Post by lovinglinux on 2009-04-28
I don't know about 64 bits, but I did a fresh install and completely formatted all partitions using ext4. Works great so far.

To create a separate home see  [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

To restore your installed applications...

> **lovinglinux said:**
> 
To replicate your packages selection on another machine (or restore it if re-installing), you can run this:

```
dpkg --get-selections > ~/my-packages
```

This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages" to new home partition and run this code in the terminal:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```

It will download and install all the programs for you, except those that you installed manually, if they are not in the new repository

---

### Post by FokkerCharlie on 2009-04-28
Cool.

I see the way to do it now, many thanks for that.

Charlie

---

