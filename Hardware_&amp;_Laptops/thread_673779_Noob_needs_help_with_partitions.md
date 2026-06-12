---
title: "Noob needs help with partitions"
date: 2008-01-21
forum: Hardware &amp; Laptops
---

### Post by spacegravity4me on 2008-01-21
Hey everybody. I'm new here and I need some quick help. I've got a laptop with a 100 GB HD which under normal circumstances will just barely get me by. I just recently installed ubuntu 7.10 on my laptop and am dual booting it with vista. I was using vista today and I discovered that I only had about 500 mb of space left. Upon install I partitioned the drive and gave vista 50GB. Ubuntu got about 47 I think and after that i dunno. I was really surprised today when I went into the drive manager under vista and saw that I have like 5 or 6 partitions! I don't know why they are all there but I need to be able to use and share as much space as possible. Vista won't even see the other partition under my computer, it just show's 50 GB. I was hoping that I could put my files on both partitions that way they'd be available to both OS's and they would be evenly distributed across the computer and I wouldn't have probs like this. Please help, I think all the partitions may have something to do with it. 50 GB for vista is not gonna be enough and I don't want to have to uninstall ubuntu even though I can't think of any practical use for it right now. It's really more of a modding adventure/hobby that I've just begun exploring. Any help is appreciated. Thanks.

---

### Post by spacegravity4me on 2008-01-21
also, i forgot, here is what i'm looking at

[IMG]http://farm3.static.flickr.com/2025/2208895624_a6f7a2f6b6_o.jpg[/IMG]

---

### Post by c0met on 2008-01-21
Hi,

If you want to get a good look at the size of your partitions, etc, It would be easiest to do by booting from the Ubuntu Live CD and then going to the[COLOR="Purple"] Partition Editor[/COLOR] under [COLOR="Purple"]System >> Administration[/COLOR]. It might be possible to condense some of these partitions into a single one, but more information is needed if you want some suggestions.

Windows will not see the ext3 (or ext2) format of Linux whereas Linux will see the Windows NTFS format. A little Windows (freeware) program called ext2ifs.exe can be installed that will allow XP to read/write on Linux drives. I do not know if it works in Vista. I'm not too sure how successful the program is although a number of people here in the forums have spoken about it; it might pay to do a "search" for thread on it.

Both Windows and Ubuntu can read/write onto a FAT32 formatted drive. The disadvantage of this is that FAT 32 has a maximum single file size of 4 gigs (less than a DVD). It's also not a highly efficient file-storage format. (Out of interest, the ext2 or 3 format of Linux is self-defragmenting. You never need to defrag :) )

A month ago, I began like you. I wanted to install Ubuntu just to get a feel for Linux. I have discovered it's amazing and I spend more time in that OS now. 

If I was in your situation, I'd simply delete all partitions and re-install. It sounds like it's early days after your having installed your system so you won't loose too much. If you do decide to re-install, I suggest using the partition editor on the Live CD (as mentioned above) to organise partitions before installing. During the installation process, you would then choose to set the partitions "manually" rather than let Ubuntu do it. If you want 50 gigs for Ubuntu, I'd create 
[LIST]
[*]a 50 gig partition and then subdivide into 3 partitions 
[*]one for "/" - say 20 gigs 
[*]one for "swap" - 2 gigs maximum 
[*]one for "/home" remainder of your 50 gigs.
[/LIST]
As I said, though, that's just my approach. I was so impressed with Ubuntu, that I went out and bought a second hard drive to install it on and dedicate it wholly to Ubuntu.

---

### Post by c0met on 2008-01-21
Hi again,

I see you have posted your partition information while I was typing to you! :) I agree with you in that there are definitely better ways to partition your system. It reinforces my thoughts about deleting everything and reinstalling. If you do reinstall, go with putting Windows on first. Ubuntu will then find Windows and organise boot up menus, etc. If you start with Ubuntu, Windows is will not cooperate the same way.

---

### Post by spacegravity4me on 2008-01-21
So i've been looking at my drive's partitions and while giving everything some thought it occurred to me that what I really need to do is enlarge my windows partition and shrink my ubuntu say down to 15 GB at most. I'd really like to know why the devil ubuntu needs to create 3 partitions! That just seems wasteful and ridiculous. Any way I can do that resizing thing I just mentioned? If not can I just delete the partitions that ubuntu made by using the vista manager and then expand my vista drive to where I want it to be, then go back and install ubuntu on the space that is left? That should work shouldn't it? I don't know. Please let me know. Thanks.

---

### Post by c0met on 2008-01-21
Yep, that sounds like it should work. Sometimes partitions are not easily expanded or shrunk though as it will depend on whether they are extended partitions or logical drives. I don't know anything about Vista so I can't offer any help there. GParted on the Ubuntu Live CD would also do it for you.

Ubuntu doesn't need 3 partitions, it's just that I have found it useful. I'll explain...
[LIST]
[*]/ = root partition; this is where the operating system resides and operational components of program files install. I guess the parallel is that this is kind of like the /Windows directory.
[*]/home = the workspace of the disk where you save files, etc; the configuration settings for lots of programs are also installed in /home. 
[*]/swap = diskspace that is used for memory if needed
[/LIST]
It's not necessary to separate partitions for / and /home. Some people do, some don't. The advantage I have found is that if/when you reinstall Ubuntu, the / is always re-formatted to check for errors and /home is not reformatted  unless it shares a partition with /. This means after a reinstallation my settings for many programs are still intact and thus that little bit easier to install. Whether you want separate partitions for / and /home is up to you.

If you want some Ubuntu installation tips, maybe you should have a look at...

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

