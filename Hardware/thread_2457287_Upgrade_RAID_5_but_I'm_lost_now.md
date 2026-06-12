---
title: "Upgrade RAID 5 but I'm lost now"
date: 2021-01-29
forum: Hardware
---

### Post by chris.arney on 2021-01-29
I've got a ASUS Z87-PRO motherboard, and years ago, I configured a RAID 5 with 4, 1TB drives. I've used up the space, and I'm trying to upgrade it using 4, 4TB drives. Problem is that since then, I've updated the BIOS, reinstalled Ubuntu (currently Ubuntu 18.04 LTS), and I can't remember how I originally configured it. I could have sworn I configured it from within a BIOS level tool. I foolishly thought I could swap out a single drive, rebuild, repeat to upgrade my drives. But it didn't boot. I realized that I had configured fstab with a 2 for the fsck. I changed that to a zero. Struggled around some more. Read that RAID is normally configured from within the BIOS, changed that setting. It recognized my previous RAID. I added that drive to the RAID, and the tool told me that the rest of the configuration would happen in the OS. I booted into the OS, and couldn't figure out where to go from there. I saw lots of posts mentioned mdadm, so I installed that, but realized that there wasn't any /dev/mdx devices installed. I'm lost at this point, and Googling isn't getting me any further anymore. Where should I go next?

---

### Post by chris.arney on 2021-01-29
Update:
I finally found that I do have a /dev/md127. I don't know how/why I didn't see it before?

I also found that I'm getting a EXT4-fs group descriptors error. I found what sounds promising here ([https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)), but I'm still reading/researching to make sure I'm not going to make things worse.

---

### Post by TheFu on 2021-01-29
Motherboard RAID is usually known as "fake-RAID".  There is no good reason to use it. Do some research for why, if you care.
SW-RAID is fast and flexible and preferred on Linux.
HW-RAID uses $250+ RAID HBAs.  Cheaper versions are often fake-raid that has the CPU do all the work. 

If it as me, I'd wipe the array, setup SW-RAID and restore everything from backups.  If you don't have backups, then you have no business using RAID. Backups solve 1000+ issues. RAID solves only 2.  Sometimes the only solution for raid problems is to wipe everything and start over.

---

### Post by chris.arney on 2021-01-30
> **TheFu said:**
> Motherboard RAID is usually known as "fake-RAID".  There is no good reason to use it. Do some research for why, if you care.
SW-RAID is fast and flexible and preferred on Linux.
HW-RAID uses $250+ RAID HBAs.  Cheaper versions are often fake-raid that has the CPU do all the work. 

If it as me, I'd wipe the array, setup SW-RAID and restore everything from backups.  If you don't have backups, then you have no business using RAID. Backups solve 1000+ issues. RAID solves only 2.  Sometimes the only solution for raid problems is to wipe everything and start over.

Thanks for the reply. I'm researching the pros/cons with the Intel RST RAID setup, and seeing if I want to switch to a SW RAID. But I'd really like to get access to some of my data before I make the switch.

I've got backups, but it's complicated. Some of my family pics are cloud backup is in my ex's account. I foolishly decided to upgrade, forgetting I didn't have everything backed up in my own accounts anymore. I'm fine losing much of the data, since I can easily recover it (already backed up in other locations), but I'd really rather not negotiate with my ex to get access to her online photos accounts. I know she is still uploading to it, so I'm sure she's got good reason to be suspicious why I'd want access. But I'd really like to recover all the pics of me and my kids from the past 10 yrs. I know I should have had made sure I had access to all my backups, and I feel foolish learning a lesson I've told others before.

---

