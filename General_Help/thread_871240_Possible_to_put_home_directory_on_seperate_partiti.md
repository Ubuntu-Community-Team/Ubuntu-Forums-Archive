---
title: "Possible to put home directory on seperate partition and share with another Linux OS?"
date: 2008-07-26
forum: General Help
---

### Post by phil81uk on 2008-07-26
Hi,

I have an Ubuntu installation. I want to achieve two things. Are they possible? Are they advisable?

My friend recommended having a third partition for the home folder. He said it makes it easier to do upgrades. Can I still create one and set my current Ubuntu install to use it?

If I do the above, then can that partition be shared with another Linux Flavour (I was thinking of SUSE running KDE), so that they can share documents?

Thank you.

---

### Post by unutbu on 2008-07-26
According to [http://books.google.com/books?id=-jzcJkXTLuUC&pg=PA93&lpg=PA93&dq=SUSE++UID&source=web&ots=vG4JcdRNpq&sig=3KiJchbDgl18T0lGoCTDhLdhkKg&hl=en&sa=X&oi=book_result&resnum=8&ct=result](http://books.google.com/books?id=-jzcJkXTLuUC&pg=PA93&lpg=PA93&dq=SUSE++UID&source=web&ots=vG4JcdRNpq&sig=3KiJchbDgl18T0lGoCTDhLdhkKg&hl=en&sa=X&oi=book_result&resnum=8&ct=result), SUSE creates its first user account with UID=500. Ubuntu creates its first user account with UID=1000. This creates a problem when trying to share files, because the filesystem knows you (determines ownership) by your UID. 

A workaround solution is to create your SUSE user account normally, but then after the install has been completed, you issue (as root) the command

```
usermod --uid 1000 USERNAME
```

This will change your SUSE user's UID from 500 to 1000. You can have an Ubuntu user named Harry, and your SUSE user named Joe and they can share files as though they both own them as long as their UIDs match. 

Secondly, configuration files can be a problem when sharing a home account between two different distros.

For example, suppose you have a configuration file which refers to a file outside of home (like a theme, an image, or a sound file). The location of this file may differ between Ubuntu and SUSE. This can potentially be a problem.

Applications often put "hidden" configuration files in your home directory. For example, application XYZ might create a configuration file called ~/.xyzrc. Sometimes these configuration files are version specific, and if you run XYZ version 2.0 with a configuration file ~/.xyzrc which was built for version 1.9, then XYZ might only complain, but in some instances XYZ might even crash.

The way to get around this second issue is to have a separate /data partition, instead of a separate /home. 

For example, you would move /home/user/music to /data/music. Everything you want to share  between distros would end up in /data, and everything that is OS specifiy would stay in separate /home/user accounts.

To make it easier for you to access your music directory from your home account, you can make symlinks:

```
ln -s /data/music /home/user/music
```

You would want to make such a symlink for each distro.

By doing so, you will be able to continue accessing and writing to the directory /home/user/music even though the music is really in /data/music.

---

### Post by Oldsoldier2003 on 2008-07-26
unutbu gave a very good answer.  I no longer think that a separate /home is a good idea at all. (this comes from installing several distros on the same machine.) 

My opinion on the matter is to create a separate data partition and link it into your home directory. This will make your data easily accessible across distributions and will also prevent the possibility of corrupting your configs in the case of different versions of applications between your different linux distros.

Using the same username on each distro, linking a data directory and changing the UID on your accounts in RH/Fedora/Suse will make things run smoothly.

---

### Post by oneporter on 2008-07-26
I did this a few days ago and have really liked it so far.  Durring the new installation, I told the new install to use the new partition as my home folder, and when I loaded up the new install for the first time all my settings and whatnot were there -- very convenient.  I used [this website]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/") for reference.

---

### Post by aysiu on 2008-07-26
I would highly recommend against sharing a /home partition between two distros. There will be breakage, even if it's minor.

If you must, go with the separate data partition.

---

### Post by CarlosNYB on 2008-07-26
It's one thing to have a separate home directory for easy re-installation/upgrade with the same distro, but it's another to use the same home directory for several different installations.

---

