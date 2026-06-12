---
title: "Need repartitioning help with Ubuntu/Vista dual-boot"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by tgeer43 on 2009-01-24
Hi. Here's the situation:

I recently installed Ubuntu 8.10 as a dual-boot with Vista Home Premium on an HPDV9500T Core Duo 2.8GHz 4Gb with 2) 100Gb drives. With the partitioning utility on the Ubuntu Live CD I initially set aside only 20Gb for Ubuntu.

What I want to do:

Now that I realize how much Ubuntu makes Vista look like the piece of **** that it is, I want to shrink the NTFS partition on the boot drive and use the space for Ubuntu. I'm also going to reformat the entire second drive for Linux.

What I've done so far:

I do want to keep a minimal install of Vista just in case so I booted Windows and uninstalled a lot of stuff, cleaned up the drive, cleaned, defragged and compacted the registry, and defragged the drive. Now I think I'm ready to adjust the partitions but I want to be careful about it.

I've seen a lot of recommendations for gparted and I have it installed but it doesn't let me shrink or grow any partitions on any drive - the option to do so is dimmed out. Perhaps it has to be run from the live CD? If so, how does one add it the the Live CD? Or is it already on there? I don't see it. I'm also wide open to any other suggestions for getting the drives repartitioned. The more instructions, the better :)

Thanks in advance for any help from a new and highly satisfied Linux convert.

Tom

---

### Post by logos34 on 2009-01-24
The general rule is to use Vista's own built-in disk utilities to resize it. You'll avoid potential problems that way.

You can't shrink a mounted partition using Gparted--especially /, which is probably why it's grayed out.  Do it from the live cd...it's hidden under >System>admin>'Partition editor'

good luck

---

### Post by tgeer43 on 2009-01-24
Update:

I thought I had it licked running gparted from the live cd. Shrunk the ntfs partition down to 25Gb and grew the ext3 partition to 70Gb. After it's like 99.9% done (after almost 3 hours) it issues the following commands:

e2fsck -f-y-v /dev/sda5

resize2fs /dev/sda5

The resize2fs command bombs stating, "try running e2fsck -f /dev/sda5 first", which of course it has already done without errors.

This resulted in all of the reclaimed space somehow being marked as in use so I'm showing the same 9Gb free as I was before instead of the 60Gb free that it should be showing now.

If I enter those same command lines in the terminal (as root), I get the same result - resize2fs recommends running e2fsck first even though it has been run without errors.

So apparently resize2fs is finding something about the disk that it doesn't like and that e2fsck hasn't detected or corrected.

This really bites. I'm really hoping that you veterans out there can help me find a way out of this pickle without data loss or reinstallation.

Tom

---

### Post by tgeer43 on 2009-01-25
Final Update:

Well, I sorted things out for myself. Had to run resize2fs with the -f option to force it. Lotsa fun today.

Tom

---

