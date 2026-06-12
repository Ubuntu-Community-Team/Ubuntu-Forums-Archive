---
title: "External Hard Drive as Backup?"
date: 2013-11-11
forum: Hardware
---

### Post by youroldpalmark on 2013-11-11
I'm thinking about getting an external drive (usb 3.0) for the purpose of backing up music, photos, etc. so that OS changes/updates go smoother. Is this a good strategy, and do I need to worry about some external drives not playing nicely with linux?

---

### Post by sudodus on 2013-11-11
I think it is a good idea. You might even have two external drives, one as a multimedia partition for regular use, and one for backup.

---

### Post by Bucky Ball on 2013-11-11
Good idea. No hard drive doesn't play nicely that I've heard of. It is the filesystem you use to format it that can sometimes cause an issue, but they're generally easily fixed.

My advice when you get the hard drive:

Copy the personal data folders to the new hard drive, delete them from your /home partition and create symlinks to the folders on the new backup /data drive. Then your personal info is off the OS partition / and, like you said, you can reinstall if anything goes pear shaped and your data is somewhere else.

Just a tip/thought. You can move house and move the /home directory to its own /home partition on the new drive, but there's not a lot of point (in effect, you're kinda doing that anyway but with different labels - besides which, if you want to install a second Ubuntu to experiment with, you can simply symlink to the folders on your /data partition in that, too).

---

### Post by youroldpalmark on 2013-11-11
Thanks for the info guys!

---

