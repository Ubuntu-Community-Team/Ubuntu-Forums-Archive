---
title: "How to know new Ubuntu defaults"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by El_Matthews on 2009-07-22
I just read a little bit on the new Ubuntu 9.10 release and I noticed that some packages won't be upgraded but are installed with a new release. This is the case for the new Filesytem EXT4 and for grub (upgraded to grub2).

This rises some questions for me; my system was installed with release 5.10 and I always upgraded my system to the latest release. How can I know that everything on my system has the latest version? Maybe in the past other packages weren't upgraded but added as standard in the fresh install and I didn't noticed them.

Anybody an idea?

---

### Post by Mark Phelps on 2009-07-22
Applications are bundled with releases, so a release comes with a given set of packages, each at a particular version.  Over time, the applications get updated and the version in the repositories (known as repos) gets repackaged.  If you run Update Manager and do Check for Updates, it will check the repos to see if any newer versions of the packages exist.

But realize, that packaging takes time and thus, it's not uncommon for the actual latest version of an app to be newer than the one in the repos.  Also, different repos (i.e., Jaunty vs Intrepid vs Hardy) also contain different versions of the packages, meaning that the Jaunty repos might have a newer version than the Intrepid repos.

And finally, there are different repos for each distro, for example, the "testing" repos will generally have newer versions of the apps than the "stable" repos.

The only way to have absolutely the latest version of each app is to download the source and build the executables yourself -- but that's a lot of work.

---

### Post by El_Matthews on 2009-07-22
Mark, thanks for the reply but this isn't really the answer I was looking for :). It isn't easy to explain what I mean.

Lets try it with an example:
[LIST]
Somebody installed in the past version 5.10
[/LIST]
[LIST]
after a while some upgrades are performed and the system is now 9.04
[/LIST]
[LIST]
Suppose that in version 8.04 ext3 was launched but old systems with ext2 weren't upgraded by default in the upgrade process. 
[/LIST]
So now in the end, the end-user has a pc with version 9.04 and ext2 while if you would do a fresh install with 9.04 you would get ext3 by default.

My question was; how does an end-user is notified about this? Is there some way to know this and are there documents on how to manually update those components?

Can we know what component isn't the standard version? If not we are obliged to do a fresh install from time to time to benefit from new developments. But I really don't want to reinstall my system every year (I don't want to go back to my Windows period).

Is this explenation better?

---

### Post by El_Matthews on 2009-07-29
Nobody that can help on this? Maybe an admin can guide me to the persons responsible for the Upgrade Architecture of Ubuntu?

---

### Post by chriswyatt on 2009-07-29
Well, there are utilities that tell you whether you have EXT2, EXT3 etc., and if you want to upgrade there are ways, just Google.

But a notification like on Windows would be nice as well e.g. I think Windows XP asked if you would like to convert from FAT32 to NTFS.

Like the first poster pretty much said, package software should be up-to-date (matching what's in the repos anyway) unless I guess something went wrong in the update process or you have bad dependencies or what not.

---

### Post by coffeecat on 2009-07-29
I very much doubt if the actual filesystem would be "updated" at a version upgrade. The filesystem the OS is running on is a very different matter to application packages. Besides, even though the installer might "recommend" a particular filesystem, it's up to you the user to make the choice. For instance, in Hardy (8.04) - if my memory is correct - the installer defaulted to ext3 for the root filesystem. But you did have an opportunity to choose another, say reiserfs for example. So the actual filesystem on the hard disk is not going to change. If you installed 5.10 on ext2 and dist-upgraded all the way to 9.10, you'd have Karmic running on ext2.

But what would get upgraded are the filesystem drivers, which are in the kernel. Each Ubuntu version comes with a newer version of the kernel, together with any upgrades, bugfixes, etc to the filesystem drivers. And, during the life of a particular version, you are going to get at least two kernel updates (within a kernel version number), which may or may not upgrade the fs drivers.

Finally, I believe you can convert ext2 to ext3, and ext3 to ext4 with a terminal command. But ext2 all the way through to ext4 might be problematic because of inode sizes. But now I'm getting out of my depth with water lapping around my neck, so I'll stop there. :wink:

---

### Post by mikewhatever on 2009-07-29
> **El_Matthews said:**
>  ...
So now in the end, the end-user has a pc with version 9.04 and ext2 while if you would do a fresh install with 9.04 you would get ext3 by default.

And what's wrong with that? Having managed to upgrade your system for nearly 4 years without trouble is not a simple fit. Would you rather have all the latest packages at the price of instability?

> My question was; how does an end-user is notified about this? Is there some way to know this and are there documents on how to manually update those components?

A package or program wouldn't be upgraded only if there is a high probability for breaking the system. If that's the case, it is usually mentioned in the release notes. Upgrading such programs manually would also be dangerous.

> Can we know what component isn't the standard version? If not we are obliged to do a fresh install from time to time to benefit from new developments. But I really don't want to reinstall my system every year (I don't want to go back to my Windows period).

Is this explenation better?

I don't know of a way to check, not what 'the standard version' is. You should probably do a fresh install with 9.10 to get grub2 and ext4, and I think a reinstall once in 4 years isn't a big deal.

---

### Post by El_Matthews on 2009-08-03
> **mikewhatever said:**
> 
You should probably do a fresh install with 9.10 to get grub2 and ext4, and I think a reinstall once in 4 years isn't a big deal.

Sorry but I don't agree with you, one reboot every 4 years is to much ;). I have different pc's (one is a mediacenter with acpi wake-up etc) and this could be a lot of work to reconfigure. Even when I changed my Hardware I just copied my disk to the new system.

I checked the release notes and there isn't mentioned what isn't upgraded or what the new defaults are. If I get this info somewhere/somehow I would have no problem to do it by hand. Example I upgraded from EXT2 to EXT3 on all my pc's. Now I know that grub 2 is comming and I will upgrade it myself.

What worries me are the softwares I didn't know and by this aren't handled. Maybe I missed something great with the upgrades. 


PS: I always use GRUB and EXT2 to EXT3 as examples because that are the ones I am aware of but my question should be expanded to the whole OS.

---

### Post by El_Matthews on 2009-08-17
Nobody with an interesting Point of view on this topic?

---

### Post by El_Matthews on 2009-08-31
Maybe we can start by building a list of what should manually be update if you always want to update your distribution without re-installing?

[LIST=1]
[*]migrate from EXT3 to EXT4
[*]migrate from Grub to Grub2
[/LIST]

What about xinetd and splashy? can we consider them as upgrades or not?

---

