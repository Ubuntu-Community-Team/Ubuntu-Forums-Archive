---
title: "Un-hide my recovery partition?"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by Nordfjord on 2009-09-22
I'm trying to un-hide the recovery partition that came with my computer so that I can make some kind of installation media.

Here's what I did: I was trying to resize my Vista partition to make some room for Ubuntu. However, the system crashed during the resize. When I booted into the Ubuntu Live CD (actually a USB drive) again, it told me that my ntfs partition was toast. So I wiped it out. Now I have a working Ubuntu install with three partitions: a 4gb Swap, a ~480gb Ext3 part., and a ~15gb Recovery partition.

The recovery system gives me a wacky error when I use it (sorry, I can post the exact error tomorrow), and doesn't do anything. I'm hoping that if I'm able to un-hide the partition and make my own media, I'll be able to reinstall windows.

If anyone knows how to un-hide these recovery partitions and make bootable media from them, I'd really appreciate a tip or two.

---

### Post by Bartender on 2009-09-22
I'm just guessing here, but it seems unlikely that you'll be able to access the recovery partititon and make discs without vista on the PC.  Maybe contact the manufacturers and ask them?

You might be able to buy a set of recovery discs from the manufacturer.

It's too late to say this, but AFAIC burning the recovery discs is the first thing to do after unwrapping a new PC.

---

### Post by Mark Phelps on 2009-09-22
In some cases, what appears to be a hidden partition is not actually a partition but a compressed file masquerading as a partition.  Wubi install does the opposite kind of thing when it creates a file in MS Windows that behaves as a partition to Linux.

If you mess up your recovery partition, you most probably will not be able to recover your MS Windows OS.

As Bartender suggested, you should contact the PC vendor to see about getting recovery disks.

---

### Post by raymondh on 2009-09-22
Sometimes (depending on the manufacturer), a windows re-install requires both the recovery CD that the OEM provided in conjunction with the recovery CD.  Try your recovery CD.

Note that there are set-ups where a windows re-install wipes the whole HD clean and installs as a sole-boot/OS (no option to choose where to install windows).

Good luck.

---

### Post by presence1960 on 2009-09-22
> **Bartender said:**
> 

You might be able to buy a set of recovery discs from the manufacturer.

It's too late to say this, but AFAIC burning the recovery discs is the first thing to do after unwrapping a new PC.

+1

That is just like backing up. It is a must. Unfortunately most people don't practice good computing habits. They never even think about it until it is too late.

Contact your manufacturer. You will probably be able to get a set of bootable CDs/DVDs to restore your system, at a premium of course.

---

### Post by Nordfjord on 2009-09-22
@Mark:

I'm thinking not. I can boot into it through Grub, even after deleting my ntfs partition.

So, this brings me to an unrelated question. Does anyone know if the Free Windows 7 Upgrade disks that are going to be shipped out by OEMs soon can do installs, or just upgrades? I'm probably going to just cheap out of getting the ($20!!!!) Vista disks, since I qualify for the upgrade.

Yeah. I'm a moron. Oh well! At least I didn't brick it. I like Ubuntu better anyways.

---

### Post by sklyer on 2009-09-22
I don't know that asking folks on a linux forum about Windows 7 upgrade disks will get you a good answer. (I got my copy of Windows 7 free from my university, so I have no idea. It's sooo much better than Vista and still got nothin' on Ubuntu!)

I recently ended up sticking in the Ubuntu LiveCD to mess around with my partitions when Vista gave up the ghost--I don't know if you could try something like that to solve your problem. Good luck.

---

### Post by presence1960 on 2009-09-22
> **Nordfjord said:**
> @Mark:

I'm thinking not. I can boot into it through Grub, even after deleting my ntfs partition.

So, this brings me to an unrelated question. Does anyone know if the Free Windows 7 Upgrade disks that are going to be shipped out by OEMs soon can do installs, or just upgrades? I'm probably going to just cheap out of getting the ($20!!!!) Vista disks, since I qualify for the upgrade.

Yeah. I'm a moron. Oh well! At least I didn't brick it. I like Ubuntu better anyways.

it is called an upgrade disk for a reason. You must have whatever valid version of windows that qualifies for an upgrade installed and activated  to be able to upgrade. I am not sure that XP qualifies and w2k definitely does not. When you go to do the upgrade it will either check for a valid version of windows (that qualifies for the upgrade) or ask you for the product key of the version you already have installed.

If you need to know what versions qualify for the windows 7 upgrade consult Microsoft's documentation.

---

### Post by raymondh on 2009-09-22
> **Nordfjord said:**
> @Mark:

I'm thinking not. I can boot into it through Grub, even after deleting my ntfs partition.

So, this brings me to an unrelated question. Does anyone know if the Free Windows 7 Upgrade disks that are going to be shipped out by OEMs soon can do installs, or just upgrades? I'm probably going to just cheap out of getting the ($20!!!!) Vista disks, since I qualify for the upgrade.

Yeah. I'm a moron. Oh well! At least I didn't brick it. I like Ubuntu better anyways.

I think (same as presence1960's) that they just do the upgrade and not an install.  And I agree that it'll have to come from either Vista or the RC7.

No, you are not a moron.  There are lot's of us who have learned the hard way .... and it's a heck of an education ;)

---

### Post by moster on 2009-09-22
Are you maybe installing linux on EeePC? They have that "secret" partition and you ususally boot from it selecting IT as startup in BIOS. So you do not need to touch that from Ubuntu or other tools.

---

