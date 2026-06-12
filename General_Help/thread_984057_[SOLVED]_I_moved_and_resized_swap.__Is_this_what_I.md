---
title: "[SOLVED] I moved and resized swap.  Is this what I need to do?"
date: 2008-11-16
forum: General Help
---

### Post by zacktu on 2008-11-16
I moved my swap file as part of a reorganization.  Hibernate doesn't work any more, and fstab appears to be messed up.  After reading lots of posts that sort of say the same thing, this is what I think is the goal and what I want to do:

According to parted:
/dev/sda5       /boot
/dev/sda6       /home
/dev/sda7       /
/dev/sda8       swap

According to vol_id:
/dev/sda5       849f41fd-b006-46f9-ae8b-93fa9feaa2fb
/dev/sda6       1176f237-c7da-43e5-bc65-d24b54a7d394
/dev/sda7       66fab9c6-de9c-4a00-ade1-b8564b2fef72
/dev/sda8       5c570dc7-471c-4ea9-9061-7ff8d492db2b

Current /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=66fab9c6-de9c-4a00-ade1-b8564b2fef72 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=849f41fd-b006-46f9-ae8b-93fa9feaa2fb /boot           ext3    relatime        0       2
# /dev/sda7
UUID=1176f237-c7da-43e5-bc65-d24b54a7d394 /home           ext3    relatime        0       2
# /dev/sda6
UUID=1fef1938-65c9-4689-ab75-b694f788b3ef none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

What I think fstab should be:
# /dev/sda5
UUID=849f41fd-b006-46f9-ae8b-93fa9feaa2fb /boot           ext3    relatime        0       2
# /dev/sda6
UUID=1176f237-c7da-43e5-bc65-d24b54a7d394 /home           ext3    relatime        0       2
# /dev/sda7
UUID=66fab9c6-de9c-4a00-ade1-b8564b2fef72 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=5c570dc7-471c-4ea9-9061-7ff8d492db2b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I've labeled the various UUIDs correctly and also replaced the UUID for swap.  Is that what I should be doing?

Thanks.

---

### Post by CatKiller on 2008-11-16
That looks OK to me.

As you've realised, the old swap partition (UUID=1fef1938-65c9-4689-ab75-b694f788b3ef) no longer exists, which is why you weren't getting swap. And no swap means no hibernation, since the swap is used to store the contents of your RAM.

I hope it fixes it for you.

---

### Post by bodhi.zazen on 2008-11-16
For hibernation your swap must be at least as large as your RAM (never hurts to have a wee bit more).

---

### Post by caljohnsmith on 2008-11-16
One more thing that you may notice is that if the UUID of your swap partition changes by resizing it or moving it, you won't get the Ubuntu splash screen on start up any more, even if your fstab is correct. Also, if you want to use suspend/hibernate, there is one more file you will want to change:
```
/etc/initramfs-tools/conf.d/resume
```
You'll want to make sure that file has the new UUID for your swap partition. And lastly, to get the Ubuntu splash screen back, just do:
```
sudo update-initramfs -u -k all
```
Hope that helps. :)

---

### Post by zacktu on 2008-11-17
Thanks to all the people who have given very helpful messages.  I've done everything that has been suggested.  I no longer have the message that hibernate can't find swap; the fstab file shows the right labels and UUIDs; and the resume file has been edited.  There's no resume from hibernate, however.

When I hibernate, the system behaves as it did before.  There's a message that "hcio f65960a80 failed to resubmit," but I have always seen that message.  After that, all is quiet, and the system has hibernated.

Old behavior: When resuming from hibernate, the splash screen would have a line in the lower section that said "Waking up" or something like that.  That was a clear indication that the system was waking from a hibernated state.  Hibernate was really cool.  I could hibernate, use Windows for some VPN stuff I can't do with linux, and then wake up my hibernated system.

New behavior: When resuming from hibernate, there is a message that precedes grub's choice of boot options.  It's not visible very long, but one of the lines says "Loading stage 5."  There is no splash screen.  Instead, there's a message that the system is booting from the UUID of the /boot partition and the verbose list of startup activities for a boot.

What next?

---

### Post by CatKiller on 2008-11-17
I haven't really used Hibernate, so I can't really help you fix what's wrong, but did you do the things that caljohnsmith outlined to get your Hibernate configuration updated to reflect the changes you've made?

---

### Post by CatKiller on 2008-11-17
I haven't really used Hibernate, so I can't really help you fix what's wrong, but did you do all the things that caljohnsmith outlined to get your Hibernate configuration updated to reflect the changes you've made?

EDIT: Sorry about the double post. I don't know what was going on with the forum at this point.

---

### Post by zacktu on 2008-11-17
Yes, I've followed all of the suggestions by caljohnsmith and you.  I've marked this post as solved because the question in the title has been solved.  I've started a new post about my hibernate problem.

---

