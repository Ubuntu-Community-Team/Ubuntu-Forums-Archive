---
title: "updrade HDD to SSD cloning?"
date: 2011-11-18
forum: Hardware
---

### Post by scratch178 on 2011-11-18
hi

i bought a 128 gb ssd from samsung

I already modified my partitions on my hdd to 

40 gb Windows
50 gb Data
20 gb Ubuntu

im running ubuntu 11.10 gnome-shell

1.) 
i have the ssd in a external drive and the hdd in my laptop, 
how can i clone the hdd to the ssd?

2.)
is there something i have to know about ssd and ubuntu, do i have to tweak around or does it just run out of the box?

thx scratch178

---

### Post by tartalo on 2011-11-18
> **scratch178 said:**
> how can i clone the hdd to the ssd?


[http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/19141/clone-a-hard-drive-using-an-ubuntu-live-cd/)

---

### Post by scratch178 on 2011-11-18
> Note: dd gets a bad rap, because like many other Linux utilities, if misused it can be very destructive. If you&#8217;re not sure what you&#8217;re doing, you can easily wipe out an entire hard drive, in an unrecoverable way.


I thought about something like clonezilla, parted magic, acronis or norton ghost

i'm afraid i loose my data, when im doing it with terminal

---

### Post by oldfred on 2011-11-18
Why not just a new install. I prefer new installs as it avoids issues with UUID, fstab, grub and other copying type issues.

You will need to use rsync or cp -a to copy /home and may want some settings from /etc if you made any system wide settings manually. You can export a list of installed applications and reinstall or if you have not houseclean you may be able to copy the .debs but only if you are reinstalling the same version.

My back up procedure is for my home system, so nothing is totally vital or has to be working to keep a business going. So I plan on a clean install and recover backed up data.

Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
backup the following:

1. /home (Users' personal files and settings)
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup
5. list of installed applications

Location of downloaded debs
/var/cache/apt/archives/
sudo apt-get install --no-download <package name>

---

