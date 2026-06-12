---
title: "Copying Installation to Blank Partition"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by Osteo on 2008-12-04
Hi,

This is an installation question, but perhaps it's an easy question that should go in the beginning forum.

I've got a 500GB hard drive that has about 250GB for Windows Vista, 40GB for 8.10 32bit, 1GB swap, and I just created a 4GB partition for 64bit 8.10.

4GB was of course a mistake; I meant to create a 40GB partition but I forgot a zero :mad:. I have unpartitioned space left on my drive for a new partition - how can I transfer my 4GB partition to my new (bigger) partition such that I can continue using 64bit ubuntu without reinstalling?

Thanks!


EDIT: I probably could have looked a little harder to find answers. [http://it.toolbox.com/blogs/locutus/how-to-copy-linux-to-a-different-partition-12865](http://it.toolbox.com/blogs/locutus/how-to-copy-linux-to-a-different-partition-12865)
Are there any objections to doing it that way? with 'cp -a', changing grub, and changing fstab.

---

### Post by caljohnsmith on 2008-12-04
One way you could do it would be to boot your Live CD, and then copy over the entire file system from your 4 GB partition (sdaX) to your 40 GB partition (sdaY) as follows:
```
sudo mkdir /mnt/sdaX /mnt/sdaY
sudo mount /dev/sdaX /mnt/sdaX
sudo mount /dev/sdaY /mnt/sdaY
sudo cp -ax /mnt/sdaX/* /mnt/sdaY
```
Then to make the transition as easy as possible, what you can do is transfer the UUID of your sdaX partition to the sdaY partition; that way you won't have to modify Grub's menu.lst or /etc/fstab. You could do that with:
```
sudo blkid | grep sdaX
```
And then using sdaX's UUID, do:
```
sudo tune2fs -U "<sdaX UUID>" /dev/sdaY
```
Then do:
```
sudo blkid -c /dev/null
```
And first make sure the UUID of sdaY is now the same as sdaX, and if so, change sdaX's UUID:
```
sudo tune2fs -U random /dev/sdaX
```
Then you might need to reinstall Grub if your current Grub uses the sdaX menu.lst. If you decide to use this method, see if you can get this far first, and also be sure to post the output of all the above commands. We can work from there if you want.

---

### Post by jenkinbr on 2008-12-04
Why not just resize the partition using a live CD - or in your case, you could use your ubuntu 8.10 32 bit version with the gparted app installed)?

---

### Post by Osteo on 2008-12-04
Hi,

Everything worked up to rebooting from the live CD. Linux started to load - it go to fsck and said something about superblocks changed so a check was forced. This turned up some errors; Rebooted.

When I selected the same grub item I got Error 15: file not found.

I figured this was a grub issue so I fell back to 32bit ubuntu, compared blkid with menu.lst, made changes, sudo grub-install, and here I am, with everything working peachy.

As far as I can tell, I'm very pleased and I have no more problems with hard drive space. Thank you very much!

---

