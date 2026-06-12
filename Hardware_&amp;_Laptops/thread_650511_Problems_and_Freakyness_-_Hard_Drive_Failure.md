---
title: "Problems and Freakyness - Hard Drive Failure?"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by markekeller on 2007-12-26
A month ago or so, I found out (from using [FONT="Monospace"]smartmontools[/FONT]) that my hard drive was on the verge of death, so I backed everything up and replaced the drive (with one that I had from another computer that had suffered a motherboard failure).  I ran [FONT="Monospace"]smartctl[/FONT] on it, and it said that the disk was very nearly brand new.

So I used it happily for several weeks, until it began displaying *the symptoms*.  It told be that my hard drive was read-only, and it automatically ran [FONT="Monospace"]fsck[/FONT] on bootup, once.  I recognized both of these as signs of impending death, but it seemed awfully strange, since, when I installed it only a month ago, it said that it was nearly brand new.  I decided to install [FONT="Monospace"]smartmontools[/FONT] , though, to make sure.

*And then apt-get wouldn't work!*  It gave me errors:
```
mark@kellerboys:~$ sudo apt-get install smartmontools
Reading package lists... Error!
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_gutsy-updates_multiverse_binary-i386_Packages (1)
E: The package lists or status file could not be parsed or opened.
```

I asked for help on a different forum, and while we were trying to find out what was causing the difficulties, other odd things happened.  Like [FONT="Monospace"]bash[/FONT] said that it had 1 error, which prevented Konsole or Kate from starting, and messed things up when I tried running a text-only virtual desktop (courtesy of Ctrl-Alt-F6).  Rebooting fixed that sort of thing, though, until just yesterday, Christmas, when it really blew a gasket.

The computer had completely locked up (which it's done 6 or 7 times in the past month), and I rebooted it.  The operating system loaded part of the way, and then switched from the loading bar to text mode, and displayed what appeared to be a bunch of errors with /dev/hdb, which is the drive I've got Kubuntu installed in.

I then reset it again, and it loaded all the way (or at least the bar went all the way across), and *then* switched to text, showing that kdb and cups had been loaded . . . but there was no bash prompt, no X, and no KDE.  After a few different tries, I found that starting it normally will have it load all the way, and then either display those last two lines of startup output, or show nothing at all, and hang.  *But* if I boot in recovery mode, it all comes up fine, and what's more, touch works perfectly, without saying that the medium is read-only, like it usually does if there's errors.  And what's more, [FONT="Monospace"]fsck[/FONT] never came up, like it always had before, whenever there were filesystem errors.

So I decided to try running my live CD, to test the disk with [FONT="Monospace"]smartmontools[/FONT] from there, and also back up my newer files, that I've created since I installed the new hard drive.  A run of [FONT="Monospace"]smartctl[/FONT] seemed to say that everything was in perfect condition - which I find extremely odd, since it's really having some problems.  Maybe I judged the ouput wrong, though; if any of you want to have a look at it, I've pasted the output [here]("http://pastebin.ubuntu.com/3013/").  And I tried mounting the filesystem, too - and it says:

```
ubuntu@ubuntu:~$ sudo /dev/hdb /home/ubuntu/Linux
sudo: /dev/hdb: command not found
ubuntu@ubuntu:~$ sudo mount /dev/hdb /home/ubuntu/Linux -t ext3
mount: wrong fs type, bad option, bad superblock on /dev/hdb,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ dmesg | tail
[  131.560372] [drm] Setting GART location based on new memory map
[  131.560388] [drm] Loading R300 Microcode
[  131.560428] [drm] writeback test succeeded in 1 usecs
[  135.309772] eth0: no IPv6 routers present
[  380.456340] cramfs: wrong magic
[  380.457206] VFS: Can't find ext3 filesystem on dev hdb.
[  380.463461] Unable to identify CD-ROM format.
[  380.464035] SQUASHFS error: Can't find a SQUASHFS superblock on hdb
[  429.134570] VFS: Can't find ext3 filesystem on dev hdb.
[  727.810471] VFS: Can't find ext3 filesystem on dev hdb.

```

So perhaps it's all gone, permanently.  The last time I tried booting in recovery mode, though, it worked fine, so perhaps my filesystems is still there.  I'm not about to try, however, unless I have something specific to do, since it seems the more I do, the worse it gets, and I don't want to push it over the edge (unless, of course, it's already done so).

What ought I to do?  Is this really a hardware issue?  Or is it something else?  Please help (!), and thanks.

---

### Post by Payteer on 2007-12-26
This has just started to happen to me today, what is going on? I am on Gutsy. I have a four month old Lenovo.

---

### Post by markekeller on 2007-12-26
You've got the same problem as I do?  Perhaps I should also mention that the computer I'm having trouble with is running Gutsy, with KDE (not Christian Edition).

Now . . . can anyone help us?

---

### Post by markekeller on 2007-12-26
Okay, I solved one of my problems.  The reason I couldn't mount my partition is that I was going about it the wrong way, not because the filesystem's destroyed.  If I mount it like this:

```
sudo mount /dev/hdb1 /media/hdb1
```

It works.  But I still can't start my computer normally . . .

---

