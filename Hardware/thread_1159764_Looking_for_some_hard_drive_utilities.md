---
title: "Looking for some hard drive utilities"
date: 2009-05-15
forum: Hardware
---

### Post by amps2volts on 2009-05-15
Anybody know of some good system tools for hard drives?  I work at a busy computer shop and I do a lot of data recovery and disk checking on drives all day.  My boss is moving the whole computer shop to a new building and I'm converting all the bench computers I do work on to ubuntu.  I love linux and use at home all the tme.  Right now I use check disk in windows to test drives and get data back NTFS from [www.runtime.org]("http://www.runtime.org")  for data recovery.

I have done a search on the forums and found a utility for linux TestDisk at [www.cgsecurity.org]("http://www.cgsecurity.org")  its all command line though.  Is there any GUI utilities that can do the same things windows check disk and get data back can do?  It does not have to be free or open source software.  Any help would be great I can't find anything on the internet.

---

### Post by logos34 on 2009-05-15
Check out the hdd tools on [Ultimate Boot CD]("http://www.ultimatebootcd.com/")--it seems to have it all.

smartmontools (-> smartctl)

hdparm

---

### Post by amps2volts on 2009-05-15
Wow that was a fast reply.  Hmm that does seem like the ultimate boot cd lol.  Thanks for the link.  Looks like most of those utilities can run within ubuntu.  That is what I'm aiming for mainly a NTFS recovery program that I can run within ubuntu and has a GUI interface.  Would make my life a 100 times easier.

---

### Post by steve01832 on 2009-05-15
The fsck utility is integral with Linux and will run automatically at predetermined start ups. This is similar to Windows CHKDSK.

Steve

---

### Post by logos34 on 2009-05-15
> **amps2volts said:**
> That is what I'm aiming for mainly a NTFS recovery program that I can run within ubuntu and has a GUI interface. 

definitely check out 

[Sleuthkit]("http://www.sleuthkit.org/sleuthkit/") + autopsy (gui)

and

[ntfsprogs]("http://man.linux-ntfs.org/") (lots of tools in that pkg)

both are in the ubuntu repositories

and, yes, a lot of the UBCD apps can be run from the hdd

hope that helps

---

### Post by amps2volts on 2009-05-16
Yeah that helps a lot.  I was reading the wiki on fsck says you can manually run it logged into system administrator.  How do you do that?  Does it work on different file systems?  Sounds like it only works with linux file systems.

Ntfsprogs sounds wicked cool says it can decrypt ntfs encrypted files?  That is crazy and its built into the ubuntu repositories.  Sleuthkit says "Tools for forensics analysis" sounds pretty neat.  Well I just put together my new bench computer today.  I put in a brand new intel motherboard d975xbx and I'm going to throw a quad core on it and put two new 15,000 rpm seagate drives my boss has in raid 1 and through in a 1TB sata drive.  Then install ubuntu :-)  I'm forcing him to use linux he love's microsoft.

Should be able to a bunch of data recovery on that beast and then throw the recovered files on the 1tb temporarily before moving it to our file server.  Well I will play around with some of those utilities tomorrow if I get the pc up and running.

---

### Post by steve01832 on 2009-05-16
Since you like the cool toys, maybe in your spare time you can check out Backtrack3. That has quite a few goodies on it.

Steve

---

### Post by logos34 on 2009-05-16
> **amps2volts said:**
> I was reading the wiki on fsck says you can manually run it logged into system administrator.  How do you do that?  Does it work on different file systems?  Sounds like it only works with linux file systems.


actually fsck/e2fsck is just a frontend, which supports a number of linux-type filesystems, i.e. fsck.ext2 or  fsck.ext3   or   e2fsck,   cramfsck,   fsck.minix, fsck.jfs, fsck.xfs, fsck.xiafs, reiserfsck, etc.

But it even supports DOS and fat32 through **dosfsck** -- fsck.msdos and fsck.vfat.  Check out the dosfsck man page for specifics.

enjoy ubuntu

---

