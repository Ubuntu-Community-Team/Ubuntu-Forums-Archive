---
title: "Ideal Partitioning Scheme for Multi Boot Linux?"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by carmacoma on 2009-07-29
Hi All,

Firstly, apologies if this is covered in detail somewhere else in the forum, so far my searches have turned up part of what I would like, but never the lot! 

I have a brand new computer with 500GB (so actually about 465GB)  HD that I want to use only as a Linux machine - NO Windows at all, EVER. 
What makes my plans difficult however is I want to have a bunch of different distros on the one machine.

My question is what is my best partitioning scheme for, say, six Linux distros, with one common partition for Data, and one for common Swap. Here's what I've come up with:

6 x distro partions of 60GB each (/home, /boot, etc all on one partition for ease and in case I replace it with another)
1x 8GB of Swap (shared)
and
1x /data partition of (roughly) 100GB (shared, hopefully accessible by all distros)

But should only one or more than one be Primary? Which? 
Which should be logicals, inside an extended?
Should I do it all at the very start before any installations of distros (with a GParted LiveCD) or bit by bit as I install various systems? 
Are there any distros that should be installed first, due to the way they install themselves/deal with partitions? 
And lastly, should I install GRUB sperately, or let one of the distros installation procedure take care of it?

Thanks very much, appreciate your help!

---

### Post by coffeecat on 2009-07-29
Hi there - welcome to the forum.

> **carmacoma said:**
> I have a brand new computer with 500GB (so actually about 465GB)  HD that I want to use only as a Linux machine - NO Windows at all, EVER.

Excellent! :wink:

> **carmacoma said:**
> What makes my plans difficult however is I want to have a bunch of different distros on the one machine.

That's not a problem.

> **carmacoma said:**
> My question is what is my best partitioning scheme for, say, six Linux distros, with one common partition for Data, and one for common Swap. Here's what I've come up with:

6 x distro partions of 60GB each (/home, /boot, etc all on one partition for ease and in case I replace it with another)

That's more or less what I do, except those are whopping great big root partitions. You'll never fill those if you're keeping your personal data on a separate partition. My Jaunty partition is 15GB of which I've only used 5.4GB with quite a few extra apps installed. I'd make your root partitions smaller unless you intend to run Windows games in wine which I believe use a lot of HD space

Some people like a shared /home partition. That has certain advantages but one big disadvantage. Some distros (Ubuntu, Suse, etc) allocate a GID of 1000 to the first created user; others (Fedora, Mandriva, etc) use a GID of 500. So you can run into some really irritating permissions problems. That, of course, can crop up with a shared data partition, but more of that in a moment. The other lesser problem with a shared /home is that when different distros use different versions of certain apps, the hidden config files in /home can sometimes be different version-to-version which can give you strange errors.

> **carmacoma said:**
>  1x 8GB of Swap (shared)

Agreed - one shared swap. Unless you intend to suspend to RAM in one distro and then boot up into another. You won't then be able to resume the first suspended session. Also check how much swap you need. 8GB is VAST. The old 2xRAM rule of thumb is a bit obsolete now, with so much RAM available.

> **carmacoma said:**
> 1x /data partition of (roughly) 100GB (shared, hopefully accessible by all distros)

If you rethink your swap and root partition size, you could make a larger data partition. If you format this ext3, you'll run into the permission problems I've mentioned. Ubuntu - Mepis won't be a problem; Ubuntu - Fedora will be. So I have an unconventional suggestion. Use a Microsoft filesystem - NTFS for preference. :shock: :wink: NTFS doesn't support Linux permissions which is a definite advantage in a one-user setup like yours. And every recent distro worth its salt can read/write to NTFS reliably. One caveat only: if the filesystem/journal gets corrupted, ntfstools may be able to fix it, but you may need Windows chkdsk. Worth thinking about.

> **carmacoma said:**
> But should only one or more than one be Primary? Which? 
Which should be logicals, inside an extended?

If Windows doesn't come into the equation, it doesn't matter. Only Windows needs to boot from a primary. Linux is happy with either primary or logical for root, swap, data, /home - you name it. Just be aware that you can have only one extended partition per hard drive in place of one of your ration of four primaries. I can't remember the limit of the number of logicals inside an extended, but it's quite a few.

> **carmacoma said:**
> Should I do it all at the very start before any installations of distros (with a GParted LiveCD) or bit by bit as I install various systems? 

Once you've thought it through, I'd go for setting up your HD with Gparted in advance. All the major distro installers allow you a "manual" or "advanced" choice at the partitioning stage so that you can point the installer to pre-prepared partitions. Although they'll probably reformat the root partition. Beware of the Fedora live CD. There's a gotcha. It insists on creating a separate /boot partition. If you want Fedora, get the full DVD, or do a network install.  Don't bother to download the Gparted live CD - Gparted is on the Ubuntu live CD.

> **carmacoma said:**
> Are there any distros that should be installed first, due to the way they install themselves/deal with partitions? 

Yes - FEDORA! :roll: Every other major distro that I can think of detects all already installed distros and sets up a multi-booting grub menu for you. Fedora detects Windows but ignores other Linux distros, so you get either a Fedora/Windows dual boot menu or a monobooting grub. :-s

> **carmacoma said:**
> And lastly, should I install GRUB sperately, or let one of the distros installation procedure take care of it?

See above, but if you want a pretty grub menu, install Mandriva, Mepis or Suse last.

---

### Post by carmacoma on 2009-07-29
@coffeecat

Thanks for all the great info! I'm off to carve up my HD now.

One more question is on my mind though... ext3 or ext4? 
I know a bit about the "bug"/feature that is dangerous ie: losing data during unexpected shutdown or powerloss, but I believe that now has a work around/patch? 
If so, is there any reason not to go ext4 now?

Thanks again!

---

### Post by coffeecat on 2009-07-30
> **carmacoma said:**
> If so, is there any reason not to go ext4 now?

Perhaps I'm an unadventurous old fuddy-duddy, but yes! Ext3 has given many years of reliable service to home computer users. It works. It's true that ext4 is faster and has some useful features that I would like to see (the more intelligent fsck integrity check for one), but it's still young and you're more likely to suffer data loss with it. (Here follows long sermon on backing up and backing up again. :p ) I'm sticking with ext3 for now, although I'll think about making the jump when Karmic goes final. I believe ext3 can be converted to ext4, although I don't know the details, so it may be possible to install on ext3 and upgrade the fs without data loss later. You'd have to check this - I'm by no means 100% certain.

Good luck!

**Edit:** just to add - actually it doesn't matter much. If you create all your empty Linux partitions with the live CD as ext3, and then decide to install - say Fedora - on ext4, the installer is going to reformat that partition. In fact it's probably better to let the installer reformat the partition that's going to be root. Some installers insist on this anyway. This won't affect your partition layout. You could create partition sda6, say, in July as ext3, reformat it to FAT32 in August, and then reiserfs in September and all the other partitions will be unaffected.

This is more or less what I've been doing for three years or more. I've had multi-boots with 6 or more distros and a partition layout something like:

sda1 - Windows (sorry! :oops:)
sda2 - Data
sda5 - swap
sda6 - Distro 1
sda7 - Distro 2
and so on.

When installing Kubuntu on sda7 which had PCLinuxOS before (for example), sda7 gets reformatted, but all the other partititions are untouched.

**Edit 2:** I just came across this thread about ext3/4. It may be useful to you.

[http://ubuntuforums.org/showthread.php?t=1133719](http://ubuntuforums.org/showthread.php?t=1133719)

---

### Post by rigao on 2009-07-30
Hey, this post helped me a lot aswell.

I made a post here:

[http://ubuntuforums.org/showthread.php?t=1226145](http://ubuntuforums.org/showthread.php?t=1226145)

which actually can be moved to this forum which seems to be the place.

If you can help me there, I would be very gratefull.

Anyways, speaking about this post, there are some things which I don't quite understand (I'm new to linux).

If i make a (say) 32Mb partition for /boot, and I put it the first partition, it will speedup the boot process?

When I'm installing different distros, each distro likes to install its own grub, and the other grub gets deleted, but they like to keep its  /boot folder in /, and sometimes this can produce problems. Wouldn't it  be better to have every distro to share the same /boot?

If so, how can I set the grub after installing the second OS? I suppose i need to modify my menu.lst by hand, but, as a general rule, how do I do this?

Many thanks.

PS: I think I like your NTFS recomendation for the data disk. But it gives funny things too. At least for me, atm, ubuntu likes very much to make every file executable whne i drop it in my data partition. I don't know why, but chmod cannot modify it. THere is no errors, it seems that it changed the permision, but then, you chekc and still executable. It is annoying when you double-click a .abw and asks you if you want to show it or execute it.

---

### Post by coffeecat on 2009-07-30
> **rigao said:**
> If i make a (say) 32Mb partition for /boot, and I put it the first partition, it will speedup the boot process?

No, or if it does, the effect would be marginal. The pros and cons of a separate /boot partition are listed in this Gentoo forums FAQ:

[http://forums.gentoo.org/viewtopic-t-220302.html](http://forums.gentoo.org/viewtopic-t-220302.html)

Bear in mind that that's aimed at Gentoo users who compile their own kernels. And if you're new to Linux, you don't want to be trying Gentoo - trust me!. :wink: Personally, I'd recommending not having a separate boot partition. It's simpler without, but this affects grub - see below.

> **rigao said:**
> When I'm installing different distros, each distro likes to install its own grub, and the other grub gets deleted, but they like to keep its  /boot folder in /, and sometimes this can produce problems. Wouldn't it  be better to have every distro to share the same /boot?

Some people do, but you really have to know what you're doing. The Ubuntu kernel is vmlinuz-2.6.28-14-generic (in Jaunty), and that's what the grub menu calls. But some distros have a symlink in /boot called 'vmlinuz' linking to whatever their kernel image is called - and the grub menu reflects this. So you could end up with a situation where you try to boot openSUSE, say, and the grub entry for Suse has 'vmlinuz', but you've installed Zenworks after Suse and the vmlinuz link now points to the Zen kernel. So you're trying to boot up Suse with the Zen kernel. Not a good idea. Actually, Suse and Zen may not have a vmlinuz link - I can't remember - I'm using that as an example of what might happen. You get the picture.

The next problem with a shared /boot is that if you don't make it big enough, it quickly gets filled. I've answered threads where a 32MB /boot has got full with just Ubuntu updated kernels and the OP couldn't upgrade to the latest kernel.

The last problem I can think of is that you have only one grub menu.lst/grub.conf. That has certain advantages, but with grub 2 on the horizon, with a completely different configuration method, I can see that becoming complicated.

> **rigao said:**
> If so, how can I set the grub after installing the second OS? I suppose i need to modify my menu.lst by hand, but, as a general rule, how do I do this?

Two ways round this. Method 1 is to decide which of your grubs is the "master" and hand edit this. You'll have to edit it not just when you install a new distro, but when you upgrade the kernel with other distros - not all distros use the vmlinuz symlink method.

My way is to keep Ubuntu as the "master" grub (But, of course! :p), and use the chainloading technique. I'll explain. Ubuntu grub stage 1 has been installed to the mbr of the first hard drive as normal. When I install a secondary distro - let's say Fedora - I instruct the installer to install Fedora's grub stage 1 to the first sector of the distro's root partition. So, say Fedora is going to sda7 - that's (hd0,6) in grub-speak - then I tell the installer to install the grub mbr to sda7, **not** to sda, which is the default. Then I hand-edit Ubuntu's menu.lst with an entry like this:

```
title        Fedora
root        (hd0,6)
chainloader    +1
boot
```Disadvantage - you get Ubuntu's grub menu, and then Fedora's. Slightly irritating.

Advantage - Every time the Fedora updater installs a new kernel (which with Fedora is about every 5 minutes), it autoedits the Fedora grub menu for you - you don't have to do anything. The chainloading entry in the Ubuntu grub menu still works.

> **rigao said:**
> PS: I think I like your NTFS recomendation for the data disk. But it gives funny things too. At least for me, atm, ubuntu likes very much to make every file executable whne i drop it in my data partition. I don't know why, but chmod cannot modify it. THere is no errors, it seems that it changed the permision, but then, you chekc and still executable. It is annoying when you double-click a .abw and asks you if you want to show it or execute it.

Neither chmod nor chown will work on a Microsoft filesystem. MS uses a completely different system of permissions and ownerships - MS filesystems do not understand the Unix permissions used in Linux. The Linux filesystem drivers devs have to come up with workarounds. In fact, if you right-click a file on an NTFS partition and Properties > Permissions, you'll see it's owned by root, which is unnerving. Don't worry about it - it still works and you can read and write to it. It's all part of the magic of the ntfs-3g driver working around the limitations of a MS filesystem.

I agree about the irritation of the run/display dialogue window. The executable bit in Unix/Linux is part of the permissions set, so again this is something that NTFS doesn't support. I guess this is a point where the devs weren't able to come up with a more elegant solution - or perhaps they're working on it. I don't know. What I do is to right-click and "open" or "open with".

---

### Post by meka4996 on 2009-10-25
[http://ubuntuforums.org/showthread.php?t=1300461](http://ubuntuforums.org/showthread.php?t=1300461)
Partition Table Design Scheme for Multi Boot Many/Multiple Linux Distro, Windows OS, or Mac, using Grub bootloader

---

### Post by oldfred on 2009-10-25
Instead of a separate /boot consider a separate /grub. You can have one permanent chainboot menu.

chainboot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)

---

