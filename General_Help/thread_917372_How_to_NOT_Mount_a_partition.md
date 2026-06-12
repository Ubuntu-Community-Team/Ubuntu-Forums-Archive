---
title: "How to *NOT* Mount a partition ?"
date: 2008-09-11
forum: General Help
---

### Post by Rhyader on 2008-09-11
I'll try making a new post/thread, because my searches are not giving me what
I am looking for... perhaps it's unusual?  What I want is to make ubuntu
 ***NOT*** mount the partitions that do not belong to ubuntu. So that if a 
"regular" non-administrator user logs onto Ubuntu, they can *NOT* access the 
other hard drive partitions. That's what I want. 

So far I can't find a way to make Ubuntu NOT mount internal partitions.
If I delete them from fstab, it will mount them anyway. I seem to need to
include them in fstab with read-only (ro) option so that at least you won't
be able to write on these partitions.  I have root login enabled. I added
commands to root's .profile to umount the windows partitions. So when ubuntu
gets booted, they get mounted (ro) and when I log in as root, they get unmounted.
This does not work for any other user however, because umount won't execute
if you are not root. That's one problem. Another is that this is a crazy 
roundabout way of doing things anyway, but I don't know any other way.
So how ... for the non linux geek ... can I make Ubuntu NOT mount partitions
that I don't want it to mount? In a way that I can still mount them later if
I want to by typing the appropriate commands (su, mount) - in other words 
only a user who has the root password can mount the windows partition. 

Failing that... is there a way I can modify the login sequence of non-root
users to dismount the partitions that Ubuntu mounted?

Yes, I know I'm weird.  8)  But this may also be of use to anyone who wants
to set up a computer with multiple users and multiple operating systems, and
keep non-authorized users away from private data you don't want them to see.

---

### Post by SuperSonic4 on 2008-09-11
If you get ntfs-config ```
sudo apt-get install ntfs-config
``` and then load it up (you'll do this as root) and ensure the boxes are unchecked

---

### Post by lswb on 2008-09-11
I can't say if it will work for your purpose, but checking the man page for fstab, "ignore" can be specified for the file type. There is also a grub command, I believe "hide" that may work for this, you'll have to google or read the docs to find the exact syntax & usage.

Also for a fat partition, and maybe for ntfs, not sure about that, there are umask, dmask, and fmask options that will set default permissions for the entire partition. Using these I believe it would be possible to make the partition read/write for root only. Other users might be able to tell it was there but they would have no access.

As for your roundabout method, try putting the umount command in the file /etc/rc.local

---

### Post by Rhyader on 2008-09-11
I'll have to try this "ntfs-config".  I will after work.
However... My question is not limited to just NTFS partitions. 
The partitions I want to NOT mount may be any of ntfs, vfat, or ext2.

---

### Post by mb_webguy on 2008-09-11
Are you sure they're being mounted, and not simply being shown in Nautilus?  If there isn't an entry for a partition in fstab, that partition isn't going to be mounted on startup.  However, Nautilus has a bad habit of displaying unmounted partitions.  (I think it's actually a hal problem, but whatever...)

If this is the case, you can hide these volumes by following these steps:

[LIST=1]
[*]In the terminal, type ```
sudo mkdir /usr/share/hal/fdi/preprobe/95userpolicy
```
[*]Still in the terminal, type ```
sudo gedit /usr/share/hal/fdi/preprobe/95userpolicy/10ignore-disks.fdi
```
[*]In gedit, paste the following text into the new file.```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
<device>
<match key="block.device" string="/dev/hda1">
<merge key="info.ignore" type="bool">true</merge>
</match>
</device>
</deviceinfo> 

```
[*]Still in gedit, change "/dev/hda1" to match the partition you want to ignore.  If you have multiple partitions you'd like to ignore, you'll need multiple <device> sections.  Just copy and paste, and change the text accordingly.
[*]Save the file and exit gedit, then reboot.  When you log back in, the unmounted volumes should no longer show up.
[/LIST]

---

### Post by Victormd on 2008-09-11
Why don't you try force the partitions to mount using fstab but set the permissions **umask and gid** to only the administrator... that way, if someone else logs in, they won't have access...

---

### Post by Rhyader on 2008-09-11
Thanks lswb ...
I noticed the GRUB option to hide a partition. But I don't know
much about grub, except that it is difficult to repair if it breaks,
so I fear GRUB and tended to look for a solution within linux. 
I'll try editing fstab to make partitions type "ignore", or putting
a umount command in /etc/rc.local later and report on the results.

---

### Post by bingoUV on 2008-09-11
Do not remove the entries from fstab, but in the mount options (the 4th column, which is likely 'defaults' for many of your entries) add an option 'noauto'. If the existing mount option for the line is 'defaults', replace it with 'noauto'. If it is something other than 'defaults', ADD noauto to it. e.g. if it is like
```

UUID=9f17495f-7d25-4aaa-8aa1-d0cea5114603             /media/TRASH                   ext3    relatime         1 2

```

change it to 
```

UUID=9f17495f-7d25-4aaa-8aa1-d0cea5114603             /media/TRASH                   ext3    relatime,noauto         1 2

```

This will make it not mount it. Only the administrator can mount it now, by simply 
```

sudo mount /media/TRASH

```

---

### Post by Rhyader on 2008-09-12
Success!
Thank You to those who responded.
I edited the fstab file and made both changes suggested. 
I made the non-ubuntu partitions type "ignore" and added the "noauto" option.
With these changes, the partitions are not mounted when Ubuntu boots.
Also, Ubuntu does not "check" the fat partition, as it was doing before,
and this is a good thing imo. So now it's working the way I want it.
Icons for the non-ubuntu partitions do not appear on the desktop when you
log in. Users who do not have administrative permissions cannot access data
on the non-ubuntu partitions.

---

