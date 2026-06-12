---
title: "restore usb stick to original  (erase everything, partitions, EVERYTHING!)"
date: 2020-11-04
forum: Hardware
---

### Post by jgw on 2020-11-04
I have a usb stick upon which I put ubuntu 20.04.1    That was a while ago.  Now I want to do that again, this time with a newer 20.04.1  I just thought I could reformation it but there are three partitions.  So then I thought I would delete them with gparted - nope couldn't get that done as I couldn't find a delete button.  I tried whilst mounted and whilst not mounted.  So, I would really appreciate it if somebody could aim me someplace that will take my hand and walk me through it.   I, obviously, don't have a clue!

Thank you.....................

---

### Post by ajgreeny on 2020-11-04
Use mkusb which has an option to restore a USB back to a mass storage device.
You can then use mkusb again to create the install USB of the new .iso.

However, I question why you want to reinstall 20.04.1 over an existing version? Only when starting with 20.04.2 iso is there any real advantage as from the .2 point version you will automatically be on the hwe pathway to newer kernel versions and xorg versions.

I'll  try to get the links for more info about this for you later as I'm on an Android tablet now and getting them to copy and come back here to paste is just too much palaver.

---

### Post by C.S.Cameron on 2020-11-05
To delete a partition using GParted right click the partition and select **Delete** from the drop down menu. 

20.04.1 is the same no matter when you download it.

---

### Post by kurt18947 on 2020-11-05
I could be mistaken in this and if so could someone correct me. I've used Gparted and created a new partition table. That results in a clean drive.

---

### Post by ajgreeny on 2020-11-05
> **kurt18947 said:**
> I could be mistaken in this and if so could someone correct me. I've used Gparted and created a new partition table. That results in a clean drive.
Yes, that should also do it whereas just deleting the partitions, if you can, will not work!

I suggested ***mkusb*** simply because that can be run to restore the USB then to create a new install USB.

---

### Post by sudodus on 2020-11-05
- In many cases it is enough to
. 'restore to a Standard storage device' or to
. 'wipe the first mibibyte' to remove the partition table with [mkusb](https://help.ubuntu.com/community/mkusb) (mkusb-dus).

- If you want to make the drive more responsive too, 'wipe the whole drive', overwrite it with zeros all the way to the tail end. There is an option for this action too in [mkusb](https://help.ubuntu.com/community/mkusb).

A USB pendrive that has been written to a lot will get unresponsive and slow when writing. Overwriting the whole drive with zeros will restore it to almost the original write speed. But don't do it too often because of the wear of memory cells (only if/when the write speed is less than half of the original speed).

---

### Post by jgw on 2020-11-05
Thank you for all the replies!

Everybody seems to think that re-installing 20.04.1 would probably be a waste of time I think I will just let the sleeping dog sleep, at least for now.  My main problem with the installation I have right now is that there is a wait, from 10 to 30 seconds anytime the computer wants to do something.  It takes about a half a minute, for instance, to go from a link, in an email, to the link in firefox.  It also takes a long time for any program to start (up to 1 minute).   I can live with this I was just hoping a re-installation might help.  Given that there are no newer versions of ubuntu 20.04.1, which is already on the usb stick I suspect I should just leave it alone for now.  I also think I will mess with mkusb just for the heck of it.  

Thanks again!  (I will mark this one as solved)

---

