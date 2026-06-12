---
title: "Floppy mount"
date: 2005-06-27
forum: Hardware &amp; Laptops
---

### Post by chrisndebb on 2005-06-27
I can't mount the floppy drive. When I try, I get the error message "Unable to mount the Selected volume. mount: I could not determine the filesystem type, and none was specified" This happens with any l foppy I put in. Doesn't matter if its .jpgs or .pdfs, etc.
Know anything?
Chris

---

### Post by apollo2011 on 2005-06-27
Sounds like you have a problem in fstab.  Can you post the contents of the file /etc/fstab?

---

### Post by chrisndebb on 2005-06-27
Hey thanks for the reply, but I'm very sorry to say that I don't have a file /etc/fstab. This does not look like a good thing to me! Now what does this newbie need to do?
Chris

---

### Post by apollo2011 on 2005-06-27
Well if you really don't have an fstab, you are in serious trouble  :-? 

I don't think you are looking in the right place.  You have to be in the root directory / (not your home directory) before you go to the "etc" directory, and then find the fstab file.

---

### Post by chrisndebb on 2005-06-27
Went to the / directory and looked in the etc file and still found no fstab. Looks like I got a real situation here. So now we have an opportunity! Anyone got any idea for this newbie?

---

### Post by apollo2011 on 2005-06-28
That is the most bizarre thing I have heard of.  I don't think it is possible for you to not have an fstab.  "fstab" stands for File System Table and keeps track of all the partitions and drives (hd, floppy, cd, etc) and where they get mounted.  Without fstab, your / directory wouldn't load and your whole system technically shouldn't boot.  I don't think you can possibly be looking in the right place,,,although from what you are saying, it sounds like you are.

---

### Post by apollo2011 on 2005-06-28
OK, open up a new terminal, and type "gedit /etc/fstab"  You might not have gedit installed and I would recommend you install it from Synaptic because it is a very useful text editor.  So if the command comes back in error, install the "gedit" package from synaptic.  Then try the command again.  If the file can't be found, then you definitely don't have an fstab file.  I asked some other people and they said fstab isn't necessary but it is useful.  So your system isn't completely trashed without fstab, I just don't know how it got deleted if you had it when you installed Ubuntu

---

### Post by chrisndebb on 2005-06-28
Hey thanks for the efforts you are taking. I've already used gedit and did find this.# 

/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

But it's funny I can't find it in /etc/fstab. Does any thing look out of place with the floppy/
Thanks a million...Chris

---

### Post by apollo2011 on 2005-06-28
No that line looks fine...Its identical to mine.  The "auto" after "/media/floppy0" means that it should autodetect the filesystem type of the media.  It obviously didn't do that.  Are you sure the floppy is formatted properly and not corrupt? What if you read it in another PC? Even if you tried several, you might have gotten unlucky and they're all bad :(

---

### Post by chrisndebb on 2005-06-28
Yes, I've tried several floppies and I get the same error message. I've also tried the one I need in a windows box and it reads fine. This same floppy has worked before on this Ubuntu box and on Fedora Core 3 before that. I'm beginning to think I may have a bad floppy drive. What do you think? 
Thanks a bunch for all your input.

---

### Post by apollo2011 on 2005-06-28
Hmm. I figured you probably had tried several floppies.
Funny thing was, before, I rebooted and the floppy drive didn't work on my system.  I rebooted and then my CD drives and floppy weren't working.  I rebooted again and it all worked again.  That probably doesn't help much though.  I assume you have rebooted. ](*,)

---

### Post by David Haas on 2005-06-28
chrisndebb--I recommend that you first format the floppy, then add the filesytem, and then mount "longhand".
Here are the commands to enter in the terminal. You can enter these at your default home directory:
fdformat /dev/fd0  (this formats the floppy)
mke2fs /dev/fd0    (this adds the filesystem ext2)
mount -t ext2 /dev/fd0 /media/floppy0 (this mounts the file system in the directory floppy0, which is in the media directory below the root directory. You can mount in any empty directory, but to mount in /media/floppy0, you must have this directory. It should be there by default, but check on it. Go to /media and do an ls (list) command. You should see floppy0 listed in the media directory. When the mount is successful, an icon of the floppy will appear on your desktop.

When you can mount this way, then the mounting can be shortened using fstab. 
By the way, when you mount it, you must unmount before shutting down by using the command umount /media/floppy. 

Well, see how it goes.

David

---

### Post by Freer on 2005-06-29
mtools provides a good way to access your floppy drive without mounting it, if you're interested in trying that.

---

