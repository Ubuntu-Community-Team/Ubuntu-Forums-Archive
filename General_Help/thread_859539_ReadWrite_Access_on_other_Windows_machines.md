---
title: "Read/Write Access on other Windows machines"
date: 2008-07-14
forum: General Help
---

### Post by TroyDowling on 2008-07-14
Hey,

    So, I'm getting frustrated with how Linux seems to handle outgoing file permissions. I've tried multiple ways to get a file onto another Windows machine from my Ubuntu Desktop and each time the Windows machine reports that it cannot open the file because it doesn't have permissions. I have chmod'd the file to 777, chown'd the file to $USER:users, emailed it like that, uploaded it to my external file server, edited the permissions remotely on the file server, put it on a flash drive (mounted with read/write permissions), and mounted my machine as a Windows share. NOTHING I do can make that file readable to the Windows machine.&#65279; I've also tried manipulating it on the Windows machine with some CACLS magic, but still no go. Am I crazy? Am I missing something?

Troy.

---

### Post by coffeecat on 2008-07-14
I'm really quite mystified why permissions should be an issue in sending a file to Windows. Windows simply doesn't support Linux/Unix permissions - end of story. I have no problem copying files to my Windows system. One question? What filesystem were you using on the flash drive?

Here's what I would do:

For an external drive I would format with a Windows filesystem - fat32 or NTFS. With Ubuntu 8.04, NTFS read/write works out of the box, and I'm slowly converting my external hard drives to NTFS precisely because I **don't** encounter permission problems. For a flash drive you may prefer fat32 because a journalling filesystem like NTFS may cause premature failure of a flash drive. Ubuntu automounts both fat32 and NTFS drives for me and I can write to them no problem at all and then read off them with my Windows box.

Or

I use my home fileserver with a Windows share. Linux box > fileserver > Windows box.

I've never tried setting up a Linux box as a Windows share, but I've managed to read from and write to my Windows share on my Windows box with Linux. Again permissions were a non-issue.

I'm still puzzled by the Windows machine saying it doesn't have permission. Can you post the exact message. I'm wondering if this is a completely different Windows problem, nothing to do with file permissions as understood in the Linux/Unix world.

By the way - slightly irrelevant but mildly amusing. Mac OSX can read NTFS (but not write). If I want to transfer a file from Linux to my Mac Mini I can do so via a NTFS-formatted USB drive. That's:

Linux box > Windows filesystem > Mac Box.

Which at least demonstrates that permissions shouldn't be getting in the way because Mac OS is a Unix OS and my UID in my Mac Mini is different from my UID in Ubuntu. Which is why I **do** get permission problems going Mac > Linux using a hfs+ formatted drive.

---

### Post by TroyDowling on 2008-07-14
Yeah, that's what I thought as well. Checking the ACLs of the file in Windows, it seems like it should be completely usable for any user. However, when I try to modify/run it in anyways, Windows pushes this in my face: "Cannot execute file. You may not have permissions to modify it" (wording could be slightly different, same meaning though). All partitions are NTFS save the flash which is fat32 (registered as vfat in fstab). It automounts normally, but I have tried manually adding a line into fstab so it mounts with root permissions.

I tried the file server approach to! Both on a machine in my house, and on a file server that I rent. To me that discludes any outside source other than my PC. I also tried running files on different Windows machines, all to the same end.

Out of curiosity, where is the security information stored for a UNIX file? Is it in the file table itself, or actually part of the file? I presume it's written into the filesystem?

---

### Post by coffeecat on 2008-07-14
> **TroyDowling said:**
>  However, when I try to modify/run it in anyways, Windows pushes this in my face: "Cannot execute file. You may not have permissions to modify it"

I have an idea, but it's very late here so my brain isn't really working properly. Windows does support one or two things that are covered by Unix permission. Read only/read write for example. If my memory serves me correctly, I once transferred some read only (Windows style) files from Windows to Linux and they were still read only in Linux. I'm wondering whether, with all your chmodding and chowning, you've triggered something that's picked up in Windows as something or other. :? Sorry, it really is late here. Or alternatively, I might just be bs-ing. :wink: Just a thought anyway. Why not right-click on one of those files in Windows and look through properties. Can't remember where everything is in Windows and I'm in Ubuntu atm. **Edit:** Ah yes. You've looked at the ACLs. I said it was late.

> **TroyDowling said:**
> All partitions are NTFS save the flash which is fat32 (registered as vfat in fstab). It automounts normally, but I have tried manually adding a line into fstab so it mounts with root permissions.

The Ubuntu fstab line for my shared NTFS internal drive in this Windows/several Linux multiboot is:

```
/dev/sdb1    /media/sdb1    ntfs-3g    defaults    0    0
```That's how the Ubuntu installer set it up. I have no problem with Linux > Windows > Linux file copies. No permission problems. If I look at file properties in Ubuntu it tells me that the file is owned by root, but I think that is some sort of hal magic going on. So I don't bother to fiddle with it. Ditto for automounting external NTFS drives. Works ootb for me.

> **TroyDowling said:**
> Out of curiosity, where is the security information stored for a UNIX file? Is it in the file table itself, or actually part of the file? I presume it's written into the filesystem?

I haven't a clue! :lol: But it's an interesting question and, if only for my own satisfaction, I'll do a bit of digging around tomorrow. Must go now. I'll look at this thread in the morning when you'll still be abed on your side of the Atlantic. :p

---

### Post by Daverobb on 2008-07-15
I don't know if my issue relates to the above either but in my system (hardy)  I've been having file permission problems as well.  When i use my external flash drive (ie. my phone/memory stick)  the drives mount and i can read and delete but not write to them. They are FAT32/vfat - i've been playing around with them in fstab for a long time but keep hitting a dead end.

---

### Post by TroyDowling on 2008-07-16
Well, if it's mounted with write permissions for all users you shouldn't have a problem. In your /etc/fstab file, it should look something like this:

```

/dev/fd0  /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

The first thing is the physical device. The second is where it's mounted. 'auto' means it is available to mount at boot. 'rw' means read/write. 'user' means for all users. 'noauto' means it doesn't automatically mount. 'exec' means you can execute files on the filesystem. 'utf8' is just the character encoding. I could be wrong on some of those descriptions; correct me gurus if I'm wrong. Substitute your values in for your device and see how it works. Just an FYI, I have had that problem before and it was because I didn't have the 'user' or 'exec' options flagged. That made it so that only the root could manipulate the filesystem. It's a pretty safe bet to just imitate the fstab entry for your hard drive. Let us know how it works out.

---

### Post by Daverobb on 2008-07-17
This is my current fstab file - I've noticed though that the phone/memory stick icons aren't even showing on the desktop anymore - ie. not mounted, which is different than previous:

 ```
cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=dda2ffed-bb6f-49fc-b71e-a82b8c5e84cf / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sdb5 :
UUID=8f5368e0-4e5d-4d68-8136-c98c8cb78c57 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0
/dev/sda2 /media/HP_PAVILION ntfs-3g defaults,locale=en_US.UTF-8 0 0

```

---

### Post by MobiusNZ on 2008-07-17
Sometimes windows with SP2 does weird things to "help" us.

Could it be related to this? [http://kerpau.net/windows-has-blocked-access-to-these-files-to-help-protect-your-computer-workaround/](http://kerpau.net/windows-has-blocked-access-to-these-files-to-help-protect-your-computer-workaround/)

---

