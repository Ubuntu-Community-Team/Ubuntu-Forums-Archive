---
title: "install on s/w RAID1"
date: 2006-02-02
forum: Installation &amp; Upgrades
---

### Post by davidmaxwaterman on 2006-02-02
Hi,

I'm new to ubuntu - moved from fedora.

I've followed these instructions :

[https://wiki.ubuntu.com/Installation/RAID1](https://wiki.ubuntu.com/Installation/RAID1)

to install ubuntu onto a pair of disk with / and swap as s/w RAID1.

All seems to be working, but I haven't completed the instructions because of some errors. Specifically :

```

$ sudo apt-get install mbr

```

failed, and so I couldn't run the following install-mbr commands.

Also, on my first attempt (I'm on my second), I followed the 'Hoary Update' too, but that completely screwed me and it booted straight into a grub prompt.

Anyone enlighten me on where to get 'mbr' from?

Max.

---

### Post by lha on 2006-02-02
Those instructions are outdated. Raid1 can be set up installer's partitioner. Partition your disks as you wish and select 'create md devices'. Select raid1 and pair up your partitions. Then select mount points and filesystems for those md devices and continue as with normal installation. Grub is installed only one drive. See [this page]("http://deb.riseup.net/storage/software-raid/") to find out how to install grub on the other one.

---

### Post by davidmaxwaterman on 2006-02-02
I think the instructions say pretty much the same as you have said. Most of the work is done in the installer (though it's not particularly obvious).

However, when the installation gets to the lilo/grub part, it does fail/give a big warning message, just as it says on those instructions. This leads me to believe that lilo/grub has not been installed. Am I wrong in this assumption?

Note that I followed the instructions, so I currently have lilo installed. Also, following the instructions at the end of that page (which seem to say the same as the page you mention) caused me to have to reinstall - I guess since it all relates to grub and not lilo - so I'm reluctant to do anything with grub.

Max.

---

### Post by lha on 2006-02-02
[QUOTE=davidmaxwaterman]I think the instructions say pretty much the same as you have said. Most of the work is done in the installer (though it's not particularly obvious).

However, when the installation gets to the lilo/grub part, it does fail/give a big warning message, just as it says on those instructions. This leads me to believe that lilo/grub has not been installed. Am I wrong in this assumption?

Note that I followed the instructions, so I currently have lilo installed. Also, following the instructions at the end of that page (which seem to say the same as the page you mention) caused me to have to reinstall - I guess since it all relates to grub and not lilo - so I'm reluctant to do anything with grub.

Max.[/QUOTE]

Really? I didn't see any warnings. Are you installing Breezy or some older version? Installer put grub on a hd for me and my system was bootable right away.

---

### Post by davidmaxwaterman on 2006-02-02
[QUOTE=lha]Really? I didn't see any warnings. Are you installing Breezy or some older version? Installer put grub on a hd for me and my system was bootable right away.[/QUOTE]

It's the latest one - is it 'breezy badger' or something. I think it was 5.1 (I don't have the disks to hand).

Hrm. Perhaps I should have another go.

The method I did it was to have it automatically partition one disk, then automatically partition the other, then I made two RAID1s of both the two pairs of partitions. I did it this way so I had the default partition arrangements. It then installed the s/w w/o any noticable problems - but then I got the warning at the lilo/grub install stage...(just before the reboot)...so I did the alt-f2 thing and followed the instructions on the above page.

In any case, where can I get this mbr-install package? Alternatively, how should I switch from lilo to grub in a reliable fashion, so I can follow the grub instructions?

Max.

---

### Post by lha on 2006-02-02
[QUOTE=davidmaxwaterman]It's the latest one - is it 'breezy badger' or something. I think it was 5.1 (I don't have the disks to hand).

Hrm. Perhaps I should have another go.

The method I did it was to have it automatically partition one disk, then automatically partition the other, then I made two RAID1s of both the two pairs of partitions. I did it this way so I had the default partition arrangements. It then installed the s/w w/o any noticable problems - but then I got the warning at the lilo/grub install stage...(just before the reboot)...so I did the alt-f2 thing and followed the instructions on the above page.[/QUOTE]

Yep, it's Breezy Badger, version 5.10. I think you should try it again. I made my partitions in advance. I used cfdisk (my favourite partitioner) to do the job. I never liked installers partitioner. Maybe you should try making partitions manually, at least for the other drive to make sure you have identical partitions on your drives. I really didn't have to do anything else besides creating those md devices and give mount points and filesystems for them.

[QUOTE=davidmaxwaterman]In any case, where can I get this mbr-install package?[/QUOTE]

You'll have to enable 'universe' repository to install mbr. Open /etc/apt/sources.list and find section with
```

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://XX.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://XX.archive.ubuntu.com/ubuntu breezy universe

```
and uncomment those two last lines. (Remove the '#' in the beginning of a line.) Then```

sudo apt-get update
sudo apt-get install mbr
``` and you have mbr installed.

[QUOTE=davidmaxwaterman]Alternatively, how should I switch from lilo to grub in a reliable fashion, so I can follow the grub instructions?

Max.[/QUOTE]

I'm a bit lost here. What do you mean with switching in a reliable fashion? I'd skip that mbr-part and use grub as a boot loader. All in all, it is Ubuntu's default boot loader.

---

### Post by davidmaxwaterman on 2006-02-02
[QUOTE=lha]
You'll have to enable 'universe' repository to install mbr. Open /etc/apt/sources.list and find section with
```

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://XX.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://XX.archive.ubuntu.com/ubuntu breezy universe

```
and uncomment those two last lines. (Remove the '#' in the beginning of a line.) Then```

sudo apt-get update
sudo apt-get install mbr
``` and you have mbr installed.
[/QUOTE]

Well that's all in the instructions (it seems that they're not all that out of date after all), so I did that. Only problem is, it said that there was no mbr subsystem...I forget the exact message, but it was something about it not existing or only available somewhere else.

> 
I'm a bit lost here. What do you mean with switching in a reliable fashion? I'd skip that mbr-part and use grub as a boot loader. All in all, it is Ubuntu's default boot loader.

Well, I was trying to avoid installing again, and switch from lilo to grub *without using the installer* (since it's all installed now and working). ...or perhaps I can use the installer to switch from lilo to grub without reinstalling anything?

Yes, I'm more used to grub too - since RedHat & Fedora switched to it a long time ago.

Max.

---

### Post by lha on 2006-02-03
[QUOTE=davidmaxwaterman]Well that's all in the instructions (it seems that they're not all that out of date after all), so I did that. Only problem is, it said that there was no mbr subsystem...I forget the exact message, but it was something about it not existing or only available somewhere else.



Well, I was trying to avoid installing again, and switch from lilo to grub *without using the installer* (since it's all installed now and working). ...or perhaps I can use the installer to switch from lilo to grub without reinstalling anything?

Yes, I'm more used to grub too - since RedHat & Fedora switched to it a long time ago.

Max.[/QUOTE]

Ok. From your first post (and especially from its title) I got the impression you are trying to _install_ Ubuntu with raid, not repair a partially functioning system with lilo as boot loader. No wander my posts haven't been useful to you.

I have installed grub only with the whole system, not afterwards. But as no-one else has responded to this thread, my guess is better than nothing. When you installed grub for the first time, did you use those instructions in Installation/RAID1? Sounds like you didn't have menu.lst which is created during install (if you use installer to install grub) or when you run update-grub. To the best of my knowledge, to install grub one needs to fetch grub from repositories, use grub-install or grub's shell to write mbr/boot sector and update-grub to create menu.lst. Then edit menu.lst to have correct options and finally re-run grub-update. All I'm saying, is that this is much easier if left for the installer.

---

### Post by davidmaxwaterman on 2006-02-04
> **lha]Ok. From your first post (and especially from its title) I got the impression you are trying to _install_ Ubuntu with raid, not repair a partially functioning system with lilo as boot loader. No wander my posts haven't been useful to you.
[/QUOTE]

On the contrary, they have been useful. For a start, I've learned that you have made it work without any trouble. Then the instructions, although applicable in some respects. are intended for an older release and so should be read with that in mind. Etc/etc IE, I do very much appreciate your help, and I thank you for it :)

However, from my point of view, it is still an installation issue, although I can also see that it could be considered a post-installation issue :) IMO, the installation is not complete, and I need to use 'grub' instead of 'lilo' - and the instructions I followed are misleading (even fatally so, since part of them are for lilo and part for grub). What I'm really after, is a version of instructions that have all 'grub' or all 'lilo', not a combination of each.

> 
I have installed grub only with the whole system, not afterwards. But as no-one else has responded to this thread, my guess is better than nothing. When you installed grub for the first time, did you use those instructions in Installation/RAID1?


Yes, I did.

>  Sounds like you didn't have menu.lst which is created during install (if you use installer to install grub)


I guess this is the problem. When I tried to complete the install, it came up with an error said:**
> 
 or when you run update-grub.


I never did that...

> 
To the best of my knowledge, to install grub one needs to fetch grub from repositories, use grub-install or grub's shell to write mbr/boot sector and update-grub to create menu.lst. Then edit menu.lst to have correct options and finally re-run grub-update. All I'm saying, is that this is much easier if left for the installer.

Hrm. Sounds like I should have a go at running just that from the installer. I don't want to actually install the system again, since I've done some more work on it and I'd have to do that all again...

Hrm. I am now wondering if the error I get when the installer gets to the grub/lilo part is actually due to the RAID1 peculiarity or something else - since you don't have any such trouble. I wonder if it is something else that is peculiar to my setup/config. I am using all XFS on a nForce3 250Gb AMD64 architecture - that's all I can think of that's potentially unusual...what do you think?

Thanks!

Max.

---

### Post by lha on 2006-02-04
[QUOTE=davidmaxwaterman]I did notice that the installer, when I pressed 'esc', came up with a menu which included something like 'install grub boot loader'. I wonder if I can do *just* that bit after booting the install cdrom? I mean, insert and boot from the cdrom, hit 'return' to boot into the installer, then press 'esc' to get to that same menu, then just select 'install grub boot loader'. Do you think that would work?[/QUOTE]

Yes it would, see [this.]("http://ubuntuforums.org/showthread.php?t=76652")

[QUOTE=davidmaxwaterman]Hrm. Sounds like I should have a go at running just that from the installer. I don't want to actually install the system again, since I've done some more work on it and I'd have to do that all again...

Hrm. I am now wondering if the error I get when the installer gets to the grub/lilo part is actually due to the RAID1 peculiarity or something else - since you don't have any such trouble. I wonder if it is something else that is peculiar to my setup/config. I am using all XFS on a nForce3 250Gb AMD64 architecture - that's all I can think of that's potentially unusual...what do you think?

Thanks!

Max.[/QUOTE]

No ideas on that.

If you try that grub-reinstall, you'll probably need to create and/or edit menu.lst file. See
```
man update-grub
```
for info. I'll paste here my kopt and groot lines for you to use as a starting point.
```
# groot=(hd0,6)
# kopt=root=/dev/md2 ro
```
I use hda7 and hdc7 as devices for md2, which is mounted as /. So 'root' entries have a real partition as parameter and kernel's root option is set to point to a md device.

---

