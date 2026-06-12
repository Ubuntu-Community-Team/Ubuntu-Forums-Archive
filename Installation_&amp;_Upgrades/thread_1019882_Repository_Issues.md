---
title: "Repository Issues"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by Failtacular on 2008-12-23
Whenever AddRemove or Software Sources is checking the repositories for new packages, it gives me an error message:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/main/source/Sources.gz:) 404 Not Found [IP: 91.189.88.31 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]


I'm not quite sure why it's doing this all of the sudden. I never had this problem [I]before[I] reinstalling the OS. My computer is running Ubuntu 7.04 Feisty Fawn

---

### Post by MarblePanther on 2008-12-23
Maybe because you are using an old version...maybe it is no longer supported

Try updating to at least 8.04


edit: I just checked, it is no longer supported--the repos for it are closed

support ended in october

update to 8.10 or 8.04

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Failtacular on 2008-12-23
That brings up another problem. We must have gone through about five disks trying to update the OS, but the disc drive never works with it. I know it's the drive because we tried with other computers and it worked flawlessly.

---

### Post by upchucky on 2008-12-23
change repositories to main server

system>administration>software sources

---

### Post by ugm6hr on 2008-12-23
> **upchucky said:**
> change repositories to main server

system>administration>software sources

No

Feisty is no longer supported.  I believe the repos are off-line now.

You need to upgrade.

There are ways to do this without a CD drive.  You could mount a Gutsy alternate iso and upgrade sequentially to Hardy.  Or use a LiveUSB.

---

### Post by Failtacular on 2008-12-23
> **ugm6hr said:**
> No

Feisty is no longer supported.  I believe the repos are off-line now.

You need to upgrade.

There are ways to do this without a CD drive.  You could mount a Gutsy alternate iso and upgrade sequentially to Hardy.  Or use a LiveUSB.

That sounds great! Unfortunately, I don't know how to do that, or for that matter, what that means. Could you tell me how to do that?

---

### Post by ugm6hr on 2008-12-24
Lets start at the beginning:  a fresh install may be easier than sequential upgrades that would require a Feisty, Gutsy & Hardy Alternate CD.

Can you boot from a USB stick?  And do you have a 1GB+ USB to use?

Do you have a separate /home partition?  Would a fresh install be acceptable?

---

### Post by Failtacular on 2009-01-16
> **ugm6hr said:**
> Lets start at the beginning:  a fresh install may be easier than sequential upgrades that would require a Feisty, Gutsy & Hardy Alternate CD.

Can you boot from a USB stick?  And do you have a 1GB+ USB to use?

Do you have a separate /home partition?  Would a fresh install be acceptable?



I have a 2GB USB drive. How do I boot from that?

---

### Post by ugm6hr on 2009-01-16
> **Failtacular said:**
> I have a 2GB USB drive. How do I boot from that?

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I would recommend the Unetbootin method with the Hardy LiveCD (32-bit / i386).

I am not sure if Unetbootin will work on Feisty - worth a try.  If not, try borrowing someone's Windows PC to install to the USB (Unetbootin works better in Windows for some reason).

---

