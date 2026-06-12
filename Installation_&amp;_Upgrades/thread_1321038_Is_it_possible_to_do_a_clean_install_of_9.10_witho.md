---
title: "Is it possible to do a clean install of 9.10 without recreating full-disk encryption?"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by makeyre on 2009-11-09
I was running 9.04 and upgraded to 9.10 on release day.  However, as usual, the upgrade has a few kinks and I think I should probably do a fresh install.  I'm using full-disk encryption, and inside my encryption container I have separate partitions for /, /home, /boot and /swap.  I would like to preserve the contents of /home while doing a clean install of 9.10 to my root partition.

However, as far as I can tell, the alternate installer doesn't have the ability to re-use an existing encryption container.  Is this possible, and if not, why not?  It's a huge pain to have to move my entire /home partition off the disk every time I want to do a fresh install.

---

### Post by tacitdynamite on 2009-11-24
This matters to me too, and to [this guy]("http://ubuntuforums.org/showthread.php?p=8376150#post8376150") and [this]("http://www.uluga.ubuntuforums.org/showthread.php?p=8376252#post8376252") guy, both of whom have had no attention for questions about encryption and upgrades to karmic. What gives, isn't this kind of important? The issue made it to the front page of slashdot, but it's echoes in the dark on ubuntu forum.

Bump!

---

### Post by makeyre on 2009-11-30
Can you pass on a link to the slashdot story?  I'd be interested in reading it.

---

### Post by dhavalbbhatt on 2009-11-30
There are a few good official documents that you need to read up, maybe those will provide the answers that you are looking for. If not, then re-post.

How to Partition:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Creating a home partition:
[https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)

Encrypted FileSystem How to:
[https://help.ubuntu.com/community/EncryptedFilesystemHowto5](https://help.ubuntu.com/community/EncryptedFilesystemHowto5)

---

### Post by makeyre on 2009-11-30
But the alternate CD installer for Ubuntu 9.10 has no ability to open up an encrypted container and install into it, so far as I can tell.

dhavalbbhatt, is this not the case?

---

### Post by dhavalbbhatt on 2009-11-30
> **makeyre said:**
> But the alternate CD installer for Ubuntu 9.10 has no ability to open up an encrypted container and install into it, so far as I can tell.

dhavalbbhatt, is this not the case?

The partition manager (regardless of whether you are using an alternate CD or the regular desktop installation CD) should be able to recognize all partitions. What the partition manager will then do is (in case of a fresh install) format the partition on which you want to install the "/" partition. I don't beleive the partition manager cares about whether the partition is encrypted or not - since it will "format" the partition, my guess would be that it should not matter. You could do the same with GParted, using LiveCD or GParted CD (that is create partitions that make sense to you).

---

### Post by makeyre on 2009-11-30
The standard alternate CD install procedure for creating an encrypted partition is to create a container and within that container put an LVM volume group in which you can put "/", "/home", etc. separately.  If the installer can't recognize the encryption, it can't see the LVM volume group to find the mount points and format "/" but not "/home", as would be practical for an upgrade where the user wants to keep user data.

I think I mentioned this in the original post -- is this not possible then?  From your response it appears the installer has no capability to open encrypted containers using a passphrase.

By the way, the reason for encrypting the volume group rather than each partition separately is that I would assume if you encrypt each partition separately you would have to enter your passphrase multiple times at boot up.  Does anyone actually do this as opposed to using LVM inside a container for encryption?

---

