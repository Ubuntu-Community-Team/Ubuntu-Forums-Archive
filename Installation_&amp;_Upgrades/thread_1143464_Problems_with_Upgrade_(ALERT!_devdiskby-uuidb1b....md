---
title: "Problems with Upgrade (ALERT! /dev/disk/by-uuid/b1b...) does not exsit"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by captincrash on 2009-04-29
Hi guys,  I am new to Linux and recently tried to upgrade from 8.10 to 9.04, after downloading a bunch of upgrades got a warning saying some of the files could not be downloaded. I thought no worries restart with this and get the missing files once it reboots.  Well after rebooting I ended up with this error.

Boot from (hd0,4) ext3 b1bb69bc-...
starting up ...
Loading, please wait ...
Gave up waiting for root device. Common problems:
-Boot args (cat/proc/cmdline)
-check rootdelay= (did the system wait long enough?)
-check root= (did the system wait for the right device?)
-Missing modules (cat/proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/b1bb69bc-... 
does not exist. dropping to a shell!

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell(ash)
enter "help" for a list of built-in commands.

(intiramfs)

I was going to try the fix in this post [http://ubuntuforums.org/showthread.php?p=7067298#post7067298](http://ubuntuforums.org/showthread.php?p=7067298#post7067298)  however I can't seem to log into a terminal in order to run his commands. I tried loading in from a CD to run the commands in that terminal but that didn't work.

I was going to try windows style fix (reinstall) but when i got to the partition stage of the setup I found that I could either install 9.04 alongside my Vista and bad 9.04 install or rewrite everything. Now I don't really want to reinstall everything because there are a lot of programs already installed in Vista that I do not want to have to re-setup, and I could not see where to only write over the existing 9.04 set-up.

Other info:  System Gateway Laptop M-6864FX, Core 2 duo processor, 4 gigs ram, Ati Mobility 2600HD graphics card,  200gb 7200RPM SATA hard drive.  running the 64-bit version of Ubuntu and Vista.

If there is any other info that is required let me know.  
Thanks for the help.

---

### Post by hg21 on 2009-04-30
My posting of 3 days ago

jaunty - /dev/disk/by-uuid problem and solution

may help

---

### Post by captincrash on 2009-04-30
I quickly tried the ls /dev/disk/by-uuid/ however I got an error message saying that location did not exist.  It looks like there are some other fixes that I can try from that same thread though.  I am in the process of moving to Victoria right now, so might be a while before I can post again, I'll repost on here once I get internet and all that good stuff set up again.

---

### Post by hg21 on 2009-05-04
Sounds like the upgrade has failed to set up correctly. I would think you may need to re-install from CD or USB stick.

---

### Post by captincrash on 2009-05-09
Well, I don't seem to be having any luck getting this problem fixed.  I have booted Ubuntu using a Live CD.  After browsing to Computer and looking through the drives present I mounted the drive that held my busted Ubuntu installation.  Right clicked on the Icon that appeared on my desktop, went to properties, then under the volume tab created the mount point to be /media/System.  I then opened a terminal used sudo chroot /media/System,  now when I type apt-get update I get this big message: 

root@ubuntu:/# apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty Release.gpg
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty/main Translation-en_US
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty/restricted Translation-en_US
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty/universe Translation-en_US
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty/multiverse Translation-en_US
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-updates Release.gpg
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-updates/main Translation-en_US
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-backports Release.gpg
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-backports/main Translation-en_US
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-backports/restricted Translation-en_US
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-backports/universe Translation-en_US
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) jaunty-backports/multiverse Translation-en_US
  Could not resolve 'ca.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/Release.gpg)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/main/i18n/Translation-en_US.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/universe/i18n/Translation-en_US.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/i18n/Translation-en_US.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/jaunty-backports/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'ca.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

Typing apt-get update continues to produce the same errors.  Anyone got some ideas on what I am doing wrong?

---

### Post by captincrash on 2009-05-09
Thanks for the help guys, I tried some of the tips you guys had suggested, as well as searching google for some ideas.  Couldn't seem to get it fixed, and got fed up with it and decided to just reinstall.  The re-installation seems to have worked fine.  thanks for the help though.

---

### Post by deuscapturus on 2009-05-13
Boot into a different kernel and run:

apt-get dist-upgrade

---

