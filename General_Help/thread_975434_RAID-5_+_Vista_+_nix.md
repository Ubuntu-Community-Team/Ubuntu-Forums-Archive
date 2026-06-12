---
title: "RAID-5 + Vista + *nix"
date: 2008-11-08
forum: General Help
---

### Post by Th3Professor on 2008-11-08
Hello World.

I'd like to use RAID-5 amongst my various operating systems, though am currently having some difficulty accessing the drives with any linux or unix install disc. My first hunch is that I'll need drivers, that is, if I am to use the mainboard's RAID. However, I'm not familiar with any alternatives other than if I purchase a hardware RAID card for the computer. "True" hardware RAID is presently not an option.

The following are the components that I am using on a new computer and how I currently have them set up:

ASUS M3N-HT Deluxe motherboard with onboard RAID.
500GB x3 hdd.
RAID-5 set up via mainboard.
Partitions set up via Vista's "diskmgmt.msc":
1st Partition/Primary, Vista.
2nd Partition/Primary, formatted/empty (for use with / on Solaris).
3rd Partition/Primary, formatted/empty (for use with / on *BSD).
4th Partition/Extended:
1st through 5th Logical: formatted/empty (for use with *nix).
6th through 9th Logical: formatted/empty (for use with Solaris).
10h through 14th Logical: formatted/empty (for use with *BSD).

I've tried various Linux and Unix install CDs/DVDs but to no avail, they don't recognize the hard drives.

How can I use the mainboard's RAID-5 with my 3 HDDs with both Windows and Linux/Unix?

Use of a RAID card is not presently possible, so I'm only curious about either motherboard RAID or operating system RAID. I am under the impression that if I use Vista's RAID it won't work with *nix. Similarly, if I use *nix RAID it won't work with Vista. Though I might be wrong. That's the primary reason I'm going off of the motherboard's RAID, though am not sure if there are drivers available or a kernel that recognizes it. It is a fairly new motherboard, though I believe the NV RAID (nvidia) has been around for a while.

Thank you!

---

### Post by fjgaude on 2008-11-08
The only way to see BIOS fakeRAID arrays is through the use of a Linux program called **dmraid**. But, AFAIK, it doesn't handle raid5, only raid0 and raid1.

The normal way for folks in the Linux world is to use **mdadm** to create just about anykind of raid array. The BIOS-type of raid is really only for Windows users. <sigh>

Here's a bunch of stuff on software raid:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
/usr/share/doc/mdadm/FAQ.gz  and md.txt.gz
[http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)
[http://tldp.org/HOWTO/Software-RAID-HOWTO.html](http://tldp.org/HOWTO/Software-RAID-HOWTO.html)

---

### Post by Th3Professor on 2008-11-08
I'm not sure if there is a way to use dmraid or mdadm without first booting into a system. I am currently having some difficulty accessing the drives with any linux or unix install disc, which is also preventing me from accessing the use of apps like dmraid or mdadm.

RAID 5 is the specific version I'm looking into using. If neither dmraid nor mdadm handle RAID 5 then I don't know if there is a purpose in either of those apps.

Most of the websites I've found with support on RAID between Vista and Linux/Unix has supported 0 and 1 but not 5.

Are there linux-based drivers for nvraid?

Before I was able to install Vista I had to put in the ASUS disc to add the necessary drivers so Vista would recognize the RAID5 set-up.

I'm assuming that before I will be able to install Linux/Unix that I will have to add the necessary drivers so *nix would recognize the RAID5 set-up.

I'm not sure if there is a BIOS update available that allows for *nix+nvraid or if there is something I must do during the actual *nix install process to allow *nix to see the hdd/storage space.

Apparently Gentoo has BIOS-based RAID working with it. Though I'm not sure if that includes RAID 5, it does include NVRAID, though. BIOS RAID does work in OS other than Windows, I'm just not sure how to get RAID 5 working cross-platform.

EDIT:
I see this in a gentoo thread:
"If you want to have Windows and Linux on the same array, then both OSes need to use the same array format. This is the reason dmraid exists, to provide Windows compatibility."
...however that thread is on raid1... not raid5.

---

### Post by fjgaude on 2008-11-08
Well, **mdadm** raid handles all raid types in software. There is nothing I know of that can handle BIOS raid5.

I know of no drivers for **nvraid** that works with Linux.

---

### Post by Th3Professor on 2008-11-08
I am curious, do you (or does anyone) think that this might be the solution:
[http://forums.gentoo.org/viewtopic-t-258981.html](http://forums.gentoo.org/viewtopic-t-258981.html)

EDIT:
It says put windows on 2nd partition and /boot on 1st partition; I installed windows (vista) before doing anything else, thinking it would require 1st partition in that "windows-ish" way. Can I just put /boot on the 2nd partition?

Plus, the iso link to the gen2dmraid is broken, is it available still somewhere?

EDIT2:
One mention of partitions in that thread is like this:
1, /boot
2, ntfs (vista)
3, / (linux)
4, [their logicals]

If I have /boot on 1st primary, can I still boot into Unix if Unix is on extended/logical?

I understand that Linux can boot from extended, though *BSD (and possibly SysV also) cannot. I may be wrong.

Though, if /boot is on a primary, then can I actually boot *any* Unix (not just Linux) from extended/logical partitions?

This is a secondary topic to what I'm trying to achieve with RAID5, though it is important that I sort it out in advance as I'll be setting partitions in addition to RAID, that is, if I want to multi-boot... which I do.

EDIT3:
I originally planned on BSD & SysV each getting their own primary since I am under the impression that both require primaries to boot.

---

### Post by fjgaude on 2008-11-08
I boot from a secondary partition with both Ubuntu 7.10 and 8.10. Works fine.

Whenever I've had a multi-boot system with Windows on one partition, usually on the first partition. Then I'd install Ubuntu on another partition without issue, using the auto installed grub to boot into either Windows or Linux. I never separate the / and /boot partitions, don't see the use or need.

---

### Post by Th3Professor on 2008-11-09
> **fjgaude said:**
> I boot from a secondary partition with both Ubuntu 7.10 and 8.10. Works fine.

Whenever I've had a multi-boot system with Windows on one partition, usually on the first partition. Then I'd install Ubuntu on another partition without issue, using the auto installed grub to boot into either Windows or Linux. I never separate the / and /boot partitions, don't see the use or need.

*BSD & Solaris both require primary to boot, right? Or...
If /boot is on primary, though the actual / for *BSD and / for Solaris are both on extended (logical) partitions, would they still boot?

The Gentoo forums thread I linked says "prerequisites" include partitioning prior to setting up RAID. Before I get into the nitty gritty details of RAID-5 via something like a Linux-based application I'd like to make sure the partitions are right.

I'd assume that it doesn't matter if /boot is on a primary other than the 1st, though would there be a problem booting into Vista if I do have /boot on the 1st (primary) partition?

I'm guessing that if I have all my operating systems booting off of /boot that I'll be fine. In fact, that would lead me to believe that as long as the booting partition, or /boot in this case, is on a primary, then perhaps ***all*** operating systems can go anywhere (including extended/logical).

However, I know that Windows has a history of being colicky and, although it cooperates with apps like grub or lilo, it still has to at least "think" it is being given absolute #1 priority in the line-up (even if tricking it via bootloading set-ups). I wouldn't want to take my chances in any case.

Perhaps it's not a norm for Ubuntu users, though it appears to be a commonplace among several other Linux users who are also using RAID... putting /boot in the 1st (primary) partition.

I've used /boot partitions for some time now, though haven't had it set up on the 1st partition. There are advantages to using /boot partitions, though... Windows can have the MBR (which, thus, searches for the bootable partition, aka /boot); it's a lifesaver when multi-booting and having to reinstall an OS like Windows (as long as /boot is set to boot ("active")); and it holds other OSs together even if formatting a *nix root.

The bit that boggles me is, why does it (/boot as boot (active) partition) *have* to go on any particular primary partition at all?

Won't it work fine as long as it is on one of (any of) the primaries?

I'd think so, though I'm not positive.

Anyway, back to RAID...

It is a tad bothersome that there are not as many RAID-5 +Vista+Linux/Unix "HOWTOs" out there as there are for cross-platform multi-booting with RAID-0 and RAID-1... and, personally, I believe that RAID 5 is much more effective than 0 or 1. (At least as it pertains to softraid.)

Apparently the dmraid has a bug fix that now works with RAID5... though, is it stable?

It appears that dmraid is the best choice for using RAID5 with Vista and *nix (and partitions within either).

Do I have to set RAID via the motherboard (NVRAID to RAID5) prior to using a Linux RAID utility like dmraid?

Or, should I deliberately *not* set up the RAID on the motherboard?

At present the default install CDs/DVDs for most Linux systems do not automatically recognize the hard drives if I have motherboard RAID set up. I don't know, though, if I must still use onboard RAID to achieve compatibility between Vista and *nix. I read somewhere that Gentoo install requires, at install, not just typing a simple "gentoo" command to load/install but to type "gentoo dodmraid". (Confusion...) [http://en.gentoo-wiki.com/wiki/HOWTO_Install_Gentoo_with_NVRAID_using_dmraid](http://en.gentoo-wiki.com/wiki/HOWTO_Install_Gentoo_with_NVRAID_using_dmraid)

---

### Post by fjgaude on 2008-11-09
Gosh, why don't you just try the various ways and see what works and what doesn't. 

There are so many issues... **dmraid** doesn't write parity to drives, thus doesn't do raid5. It's not a bug!

Gentoo is not Ubuntu... I do believe they are so different as to be in different classes.

When using raid0 or raid1 using the BIOS you set it up before booting into Ubuntu, and you run dmraid.

I stopped using dmraid years ago and only use **mdadm**. It is great!

With grub the **menu.lst** file will be in the /boot/grub directory off the / partition.

That's about it for me... maybe others will have more to say.

---

### Post by Th3Professor on 2008-11-09
> **fjgaude said:**
> There are so many issues... **dmraid** doesn't write parity to drives, thus doesn't do raid5. It's not a bug!

There's a recent patch that has raid "45" for 32-bit and raid "456" for 64-bit. It appears to be physically possible to use raid5 in dmraid now, though I have read in various places online - albeit questionable reliability, as with most sources online - and the different sites preferred mdadm over dmraid.

> **fjgaude said:**
> When using raid0 or raid1 using the BIOS you set it up before booting into Ubuntu, and you run dmraid.

I'll go ahead and abandon the idea of using dmraid, I'll see if I can stick to mdadm for raid5 and my systems. Though, I really don't know if there's a work-around for using Windows Vista along with *nix... so... I'm considering a specific $$$ alternative.

> **fjgaude said:**
> With grub the **menu.lst** file will be in the /boot/grub directory off the / partition.

I understand that, thank you. I was just a bit confused as to the possibility of booting into systems that otherwise require primary partitions. I know that if I separate /boot from / (as in partition separately), then I'll have added security in accessing the computer in the event that one of my multi-booting OSs crashes. I was unsure if I could still install Windows and Unix (non-Linux) systems on logical partitions if I still have a /boot primary partition set up. Anyway, that likely won't even matter considering what I'm... uhm... considering. lol


> **fjgaude said:**
> That's about it for me... maybe others will have more to say.

Thank you for your feedback. I actually recently came across another thread in these forums where you provided some input on raid (albeit raid0) that actually introduced an idea I had not yet considered.

What if... I get a 4th hdd, still 500gb (same brand, etc.) in case I ever want a 4 disk raid, though for now dedicate 3 hdd to *nix and 1 hdd to windows?

Could I run raid5 with 3 hdd *nix (linux and unix) and just a generic non-raid win.vista 4th hdd?

The trick is, getting multiple *nix systems within the raid5. I know they're mostly posix compliant/etc. though am unsure how they handle raid (or raid5 specifically) together.

:)

EDIT:
My motherboard's RAID is either "all raid" or "no raid", meaning if I use RAID on any HDDs I have to an all HDDs. Will that conflict with using mdadm within only 3 HDDs (for *nix raid) and 1 HDD (for windows non-raid)?

---

### Post by fjgaude on 2008-11-09
With **mdadm** and raid5, three drives, you can easily work with Linux there, and have a Windows drive in which you partition for a boot to Linux, a dual partition disk. You can't boot into Linux using software raid5.

Install Windows first and then install Linux, and grub will show a menu to boot to either.

When in Linux you can have full access to your Windows partition and all of its files.

Yes, it's a good idea not to use RAID from your BIOS... Linux has little regard for such.

---

### Post by Th3Professor on 2008-11-09
> **fjgaude said:**
> ...and have a Windows drive in which you partition for a boot to Linux, a dual partition disk. You can't boot into Linux using software raid5.

By that do you mean that I would have 2 partitions on the Windows-only hard drive, one being /boot and the other being Vista? Or do you mean the entire Windows hard drive is only Vista and HDDs 2,3,4 (with Linux/Unix) contain the /boot? (Or does it matter.) I understand the boot, MBR, should be near the beginning of the main disk that is intended for booting. I haven't used multiple hard drives simultaneously for completely separate operating systems, not really sure on that point.

> **fjgaude said:**
> When in Linux you can have full access to your Windows partition and all of its files.

That has been a handy feature from time to time, albeit in the past I've had to use odd Windows programs to access Linux partitions when in Windows. Though, I don't have much need for accessing one while logged into the other, so it's not much to worry about.

> **fjgaude said:**
> Yes, it's a good idea not to use RAID from your BIOS... Linux has little regard for such.

Excellent!

It's good to know that onboard/BIOS RAID is not required in order to achieve RAID via *nix. I called ASUS about that "all or none" RAID business with the motherboard and they said it is a more recent change in their boards, that their older boards allowed selection of which SATAs/etc. could be used with or without RAID.

I ordered the 4th HDD today, will get it in a couple days. I look forward to setting this up. :)

I think this is the procedure now, please correct me if I'm wrong...

1. Install Windows on disk #1, don't partition it.
2. Set-up RAID 5 on disks #2,3,4 via mdadm.
3. Partition the necessary *nix primaries/logicals on #2,3,4.
4. Install *nix.
5. Boot to access either Vista or *nix via GRUB.

---

### Post by fjgaude on 2008-11-10
I think you are missing the philosophy.

1. Install Windows on disk #1, don't partition it.

No, partition it in two. One for Windows, the other will be left with no filesystem for now.

2. Set-up RAID 5 on disks #2,3,4 via **mdadm**.

No, install Windows on disk #1, then install Ubuntu from LiveCD on unallocated partition.

3. Partition the necessary *nix primaries/logicals on #2,3,4.

Prepare, while in Ubuntu the three drives that are to be raid5 array. You have to use this command after you have installed mdadm from the repository:

```
sudo mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sdd1
```

This assumes that your disk #1 is /dev/sda. The three drives will have had one partition placed on each using something like **gparted**, which is in the repository.

4. Install *nix.

No, already done in 2. above.

5. Boot to access either Vista or *nix via GRUB.

This happens after you have installed Ubuntu in 2. above. Nothing need be done except select from menu either Windows or Ubuntu.

Please, please, read, study:

**[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)**

before doing any of this.

Let us know how you are doing.

---

### Post by Th3Professor on 2008-11-10
Okay...
1. Install Windows on disk #1 and make 2 partitions (1st=Vista, 2nd=nothing yet).
2. Boot Linux livecd, set up equal partitions (gparted) on disks #2,3,4.
3. Install Linux, via livecd, onto disk #1, 2nd partition.
4. Boot to Linux, install mdadm, set-up RAID5 (create, l5, d3, +three devices).
5. Reboot and select either Vista or Linux/Unix/etc.

I've already read the shsc.info softraid page. It helps a little though appears to be outdated with use of raidtools. Unless you are saying those should still be used. I was under the impression that mdadm replaces them. The layout of that web page is confusing, leading the reader to think both are required. In any case, skipping down to the mdadm section... I've read the man pages on mdadm and am aware of the syntax for using the application, the options, and similar. I will likely use chunk size 128 since I'm running RAID 5.

I understand I have to remove them with the -r option (mdadm <md device> -r <device>) if I have a bad drive. Do I assemble/stop (start/stop) arrays mostly for the purpose of swapping out bad with good hard drives without damaging data in the process? I'm not quite sure why the mock-fail code on that web page has loops near the end.

I'm guessing I can leave the config file alone since mdadm (unlike predecessors) auto configs.

In any case, while waiting for the 4th DHD, I thought I'd experiment with the RAID that is compatible with both Vista & *nix, and dmraid works with RAID 5 now (I'm currently using dmraid raid5 with windows+linux). However, when my 4th HDD comes in I'll go ahead and change things.

I'm considering putting all operating systems on disk 1 and using disks 2,3,4 for everything else, unless people recommend RAID'ing actual operating systems too.

---

### Post by fjgaude on 2008-11-10
Yes, in the write-up mdadm is to be used. It replaced the old raidtools, etc.

You can --fail a bad drive, --remove it, and then --add the new one without doing anything else... the new one will re-sync automatically in most cases I've been involved in.

Yes, do play around with the three drives in raid0 and raid5 and see how things work.

I never put an OS on a software raid array.

So you are good to go.

---

### Post by Th3Professor on 2008-11-14
Here's what I've done so far:
1. I started with fdisk - each of the 3 disks, sdb, sdc, and sdd; deleted old partitions, added 1 new primary per disk, set type on all 3 disks to linux raid auto - I did not designate partitions within each disk (using lvm, so I'm guessing I don't need to define partitions? ...notsure).
2. sudo mdadm --create /dev/md0 --chunk=128 --level=5 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sdd1 
3. sudo mdadm --detail /dev/md0 (every so often to check on the % status)
4. sudo mke2fs -t ext3 -b 4096 -E stride=32 /dev/md0 (tldp.org recommended the bytes and stride (i.e., 4*32=128 chunk-size) for improved performance on RAID 5)
5. sudo pvcreate /dev/md0
6. sudo vgcreate -s 32M lvm-raid /dev/md0
7. sudo vgdisplay lvm-raid (to get number of PEs available for volume creation)
8. sudo lvcreate -l 29808 lvm-raid -n lvm0
9. sudo lvdisplay /dev/lvm-raid/lvm0
10. sudo mke2fs -t ext3 -b 4096 -E stride=32 /dev/lvm-raid/lvm0
11. sudo mount /dev/lvm-raid/lvm0 /mnt/
12. df -h /mnt/ (and it shows 917GB size, 200MB used, 871GB available)

Why is it not showing 931GB for the size (as it is after setting up RAID5)?

Is it because I created ext3 two times? (Should I only create ext3 one time (after creating lvm0?))

How would I put this into fstab?

And last but not least... the parts within vm0 that I'd like to create are:
/studio/vault
/zone (for Solaris /zone/home - though I'm not sure if this will work with Solaris)
/home (for my "other linux" install)
1 additional linux swap and 1 additional unix swap

Of my 4 hard drives, #1 = OS (Windows, Linux, etc.), #s 2,3,4 = the above mentioned RAID+LVM.

I'm doing this now so that I can redo it all, hopefully correctly, before I start using/storing/etc. ;)

---

### Post by fjgaude on 2008-11-14
I never use LVM so I can't help you there...

You might try for the fstab file:

```
/dev/lvm-raid/lvm0 /mnt/ ext3 defaults 0 2
```

Though I think /mapper/ will have to be added because of LVM. Must be somewhere in the man pages, eh?

When watching an array build or re-sync use this command instead of the **mdadm -D**:

```
sudo watch cat /proc/mdstat
```

That works so well.

---

