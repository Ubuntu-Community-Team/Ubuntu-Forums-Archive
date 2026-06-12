---
title: "Before I install"
date: 2009-09-04
forum: Installation &amp; Upgrades
---

### Post by FunkyRes on 2009-09-04
I'm a LONG time Red Hat user currently running CentOS 5.3.

I'm starting to play with multimedia and I've come to the realization that I need something a little more fresh, and decided rather than install Fedora 11 - I'd finally give Ubuntu a shot.

The torrent is coming down the pipe now (nice speed btw, thank you to all who are seeding).

Before I install, a couple critical questions.

A: I will be installing on a partition of a disk that CentOS lives on. I do not want ubuntu to touch the mbr. After install, I want to boot into CentOS, manually edit my grub.conf file to add the ubuntu kernel and root partition, etc. I do have a separate /boot that is ext2 - I will mount the ubuntu install and copy kernel etc. into that /boot and then edit ubuntu fstab to mount that partition as /boot.

What install option do I need to be extra careful of to make darn sure ubuntu does *not* write to the mbr? It's not the end of the world if it does, I'll back up my CentOS grub config, but I'd really rather it didn't.

B: Can ubuntu be installed on an unused partition that is part of a logical volume created by lvm in CentOS or do I need to shrink the CentOS LVM to leave unpartitioned space for ubuntu to do it's own thing?

C: I already have kino etc. working in CentOS. The whole reason for going to something newer is that the bleeding edge libraries needed to compile the latest gtk webkit so I can build epiphany that uses gstreamer for html5 media just are being a real pain to build.

Is there a specific repository I should look at that might have these bleeding edge libs (and maybe even epiphany) already compiled for ubuntu?

Lot to ask, thanks for suggestions.

---

### Post by FunkyRes on 2009-09-04
Got tired of waiting, so I just installed.

The installer was nice, but over simplified.
This is probably the first linux install I have ever done that has not asked squat about the boot loader. That needs to be fixed.

Now I have to boot into CentOS rescue CD to restore grub. Not a good first impression.

It seems ubuntu doesn't know anything about LVM either, at least it did not give me any LVM partitioning options. One of the more useful advancements in desktop linux, it lets you keep /home separate so you can do a clean install without wiping /home yet can adjust the partition sizes as needed later.

But the installer was nice.

---

### Post by bear24rw on 2009-09-04
> **FunkyRes said:**
> 
It seems ubuntu doesn't know anything about LVM either, at least it did not give me any LVM partitioning options. One of the more useful advancements in desktop linux, it lets you keep /home separate so you can do a clean install without wiping /home yet can adjust the partition sizes as needed later.

If you choose manual partitioning you can set /home to be mounted on a different partition..

---

### Post by ad_267 on 2009-09-04
> **FunkyRes said:**
> The installer was nice, but over simplified.
This is probably the first linux install I have ever done that has not asked squat about the boot loader. That needs to be fixed.
It's hiding under an "Advanced" option near the end of the installation.

> C: I already have kino etc. working in CentOS. The whole reason for going to something newer is that the bleeding edge libraries needed to compile the latest gtk webkit so I can build epiphany that uses gstreamer for html5 media just are being a real pain to build.
There's a PPA (personal package archive) for the latest Webkit builds at [https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa). Don't know about using gstreamer for html5 but I assume it must include that. You might also want to try the Midori browser.

---

### Post by presence1960 on 2009-09-05
> **FunkyRes said:**
> Got tired of waiting, so I just installed.

The installer was nice, but over simplified.
This is probably the first linux install I have ever done that has not asked squat about the boot loader. That needs to be fixed.

Now I have to boot into CentOS rescue CD to restore grub. Not a good first impression.

It seems ubuntu doesn't know anything about LVM either, at least it did not give me any LVM partitioning options. One of the more useful advancements in desktop linux, it lets you keep /home separate so you can do a clean install without wiping /home yet can adjust the partition sizes as needed later.

But the installer was nice.

Click the advanced tab in this window (see pic below) which will give you options where to put GRUB. The options are sda - MBR of sda, sda1 - first sector of sda1, sda2 - first sector of sda2, etc.

I feel that that tab needs to be a little more obvious because most people never even look at it. I know what you want to do because I chainload Mint 5 and Sabayon 4.1 off Ubuntu's GRUB. Mint has the same option as Ubuntu, but Sabayon's was more specific as to where you want to put it, it was clear & not hidden.

sabayon also has a nice feature where you can change the order of your disks to match BIOS. This is great because sometimes Linux reads the order of disks differently than what they are in BIOS. Hopefully one day Ubuntu will have these improvements in it's installer.

---

### Post by presence1960 on 2009-09-05
oops - forgot the pic...sorry!

---

### Post by presence1960 on 2009-09-05
> **bear24rw said:**
> If you choose manual partitioning you can set /home to be mounted on a different partition..
> 
seems ubuntu doesn't know anything about LVM either, at least it did not give me any LVM partitioning options. One of the more useful advancements in desktop linux, it lets you keep /home separate so you can do a clean install without wiping /home yet can adjust the partition sizes as needed later.

A separate /home is not LVM. LVM has support in the alternate text based installer. get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate") But you can create a separate /home partition from the Live CD installer using the manual option. Highlight the /home partition & click edit. Then set parameters use as = filesystem, format or don't format and for mount point use the drop down box and set the mount point to /home. For true LVM use the alternate text based installer instead of Live CD.

The alternate text based installer is the installer to use if you want other options than a basic install. It is way more powerful than the Live CD. But because the Live CD can run Ubuntu from the CD and it looks pretty, I would say a lot of people use the Live CD and never even know the alternate text based installer exists or that it has support for way more options than the Live CD

---

### Post by FunkyRes on 2009-09-05
No, a second /home is not LVM but using a volume group allows you to easily resize the volumes in the volume group so if you guess wrong when you partition no biggie.

At any rate - hiding the boot loader is something that should be rethought.
The way CentOS (and at least former Fedora) did it - there was a clear check box you uncheck if you don't want the boot loader written to mbr.

But it's all working now, I can boot into either, just a minor inconvenience.

-=-

Thanks for the reference on webkit repos.
Looks like I have a lot of reading to do, particularly on building debian packages (I like to fiddle with packaging, build options, etc. but prefer to build packages as they make it easier to back out and revert if needed)

Installing nvidia driver was cake, nice that you can do it within supplied repos.

---

