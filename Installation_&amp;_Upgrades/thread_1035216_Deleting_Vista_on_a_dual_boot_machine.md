---
title: "Deleting Vista on a dual boot machine"
date: 2009-01-09
forum: Installation &amp; Upgrades
---

### Post by tmurf99 on 2009-01-09
I have a Toshiba Portege 2000 with ubuntu installed inside of Vista. The machine is terribly under powered to run Vista, and I would like to delete it without deleting ubuntu. is this possible? Thanks

---

### Post by Hooya on 2009-01-09
So you installed Ubuntu through Wubi?  And now you just want to run Ubuntu...

I don't think there's a way to get your Ubuntu installation out of the Windows OS while keeping it intact.

My suggestion is this:  Copy your /home directory to a CD or DVD or USB drive or something.  This might require more than just dragging the one folder, although under Wubi it might be that simple.  The folders are cross-linked and other various things.

Once you have your home folder backed up, wipe your system and install Ubuntu using the install disk.

Once you have Ubuntu installed, look for a tuturoial online about restoring a backed up /home directory.  Actually, I'd do that first, to make sure that this method will work, although it should.

You'll have to re-install your programs you want, but all your settings will be maintained.  If you've manually isntalled fonts those will need to be re-loaded, but othewise, you should be all good to go as long as you install all the programs you were using.

If you actually have a dual boot (separate partitions for each OS; GRUB is your boot manager) just boot into Ubuntu, run gparted, and use that to delete your windows install and expand the file system to fill the drive.  Obviously back up anything you want before you do this!  Then you can edit your GRUB settings to remove the Vista entry there and automatically and quickly load Linux.

---

### Post by avtolle on 2009-01-09
> **tmurf99 said:**
> I have a Toshiba Portege 2000 with ubuntu installed inside of Vista. The machine is terribly under powered to run Vista, and I would like to delete it without deleting ubuntu. is this possible? Thanks
No, you cannot. However, in addition to the suggestions in the above post, you might take a look at the Wubi subforum, and in particular the sticky about LVPM. Good luck.

---

### Post by tmurf99 on 2009-01-12
Thanks for the help.

---

### Post by meindian523 on 2009-01-12
You can migrate your Ubuntu install to a full fledged standard install to your hard disk using [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591) Then boot into your new dedicated-partition Ubuntu install,install Gparted,```
sudo apt-get install gparted
``` and then delete your Windows install,which would be on your ntfs partitions.

---

