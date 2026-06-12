---
title: "System often gets too sluggish to use.  Must reinstall."
date: 2008-10-27
forum: General Help
---

### Post by bilijoe on 2008-10-27
I installed Ubuntu 8.04.1 very soon after it was released.  At first, everything seemed fine.  Then I thought I was noticing things slowing down, just a little bit, but decided it was my imagination.  As time passed, it became obvious, it was NOT my imagination.  :sad:

The sluggish behaviour happens primarily when scrolling through long documents, web pages, or folders, and, when it happens the window(s) involved turn Black & White.  Sometimes it will even stop scrolling altogether for a few seconds.  It stores up all the mouse wheel movements I make, so it often ends up by scrolling up and down, up and down, until it has exhausted the queue.  

In any case, I've no longer the patience to deal with trying to figure out what's going on and fix it--I am going to have to do a reinstall so I can get back to work. ](*,)

So, my question is this: How can I reinstall the operating system while preserving as much of my installed programs, FireFox add-ons, preference settings, bookmarks, panel layout, etc.  How much of this stuff is stored in "Home"?  

If I make a copy of my home directory, reinstall the OS, then write the backup of the Home folder over the one created by the install, will I get any of the preferences, bookmarks, etc., etc. back?  Or will I just confuse and confound (and possibly crash?) the system?  :frown:

Any help or suggestions of any kind would be appreciated.  

Also, is there a way I can set up the new install to facilitate retaining all that configurable stuff, should I have to reinstall the OS again in the future?  Again, any suggestions will be greatly appreciated. :popcorn:

---

### Post by fooman on 2008-10-27
just curious...have you tried turning off the visual effects?

give it a shot if you have not tried it already.  go to system > preferences > appearance > visual effects....set to "none"

see if the problem goes away.

also...on a new install,  just set up a separate /home directory during the partitioning and if you ever have to reinstall...all your settings and data will be as you left them.

---

### Post by cariboo on 2008-10-27
Have you tried **top** in a terminal to see which program is using all your resources?

Jim

---

### Post by bilijoe on 2008-10-28
> **fooman said:**
> just curious...have you tried turning off the visual effects?

give it a shot if you have not tried it already.  go to system > preferences > appearance > visual effects....set to "none"

see if the problem goes away.
Wow! :-o  That might actually have fixed it!  I've been battling with this for months!  Curiously though, it did get progressively worse with time.  What might explain that?  And what on earth do the "visual effects" do?  And what kind of high horsepower, supercharged, nitro burning machine do you need to support them?  I've got a DELL Optiplex 270, with a 2.8GHz Multithreading Pentium 4, and 4 Gb of ram (of course, the P4 can only access about 3.5 Gb), along with a fast 250 Gb SATA HDD.  Since I had the Visual Effects turned on at the lower of the two levels, I'd think the horsepower I've got would be enough to satisfy.  Guess not.  I don't even see any difference in the display with the Visual Effects turned off.  Go figure.  Must be you need a Hot Video Card to run the Visual Effects.  I don't know what I've got for video hardware.  I think it's on the MB (computer is jammed into a very hard to access space, or I'd check).

In answer to the question about what the processes are that are using up the CPU's time: OK, the top four applications according to both top and the System Monitor are: Nautilus, FireFox (running Pandora Radio), totem, and gnome panel. They exchange positions often, but are consistently the top four, and all show between 25% and 85% processor use (it varies for each one, over time). Everything else in the list shows 0% processor use--most show "sleeping". The Resources graph in the System Monitor shows both CPU1 and CPU2 at a constant 99% to 100%, most of which is shown as "user", a small amount as "system". 

After turning off the visual effects, only Xorg and FireFox seem to take up any CPU time, and they and both CPU usage graphs stay around 40% to 50% while I am scrolling through a long page.  When I stop scrolling, they drop to 5% or 6%.  Pretty interesting.  

It'll take a while before I am truly convinced that the Visual Effects was the problem--only because I can't see how the problem would have become worse over time, if the Visual Effects were the problem.  But I gotta say, it sure looks like things are running at "normal" speed now (though I really don't remember what that was like--it could still be somewhat slow, but I don't think so).

---

### Post by bilijoe on 2008-10-30
Well, I thought it was too good to be true.  Things ran fast for a couple of days, now the system is slowing down again.  So the visual effects are involved somehow, but it was only a temporary fix.  Any more ideas?  Anyone? :confused:

---

### Post by El Chupacabras on 2008-10-30
I don't know... I'm still downloading 8.10. I may run it on the livecd for a while now that I see all these claims.

About your issue, do you have Beagle search or Tracker search installed? Indexing services can be quite slow while they're indexing the root directory structure (and they take a long time, too!). That's one common source of slowdown for me, whether I'm using Ubuntu Hardy or Vista.

---

### Post by bilijoe on 2008-10-31
No, no indexing stuff running.

---

### Post by cariboo on 2008-10-31
How about low hard drive space?

Jim

---

### Post by bilijoe on 2008-10-31
> **cariboo907 said:**
> How about low hard drive space?

JimYea, that's been mentioned, and is often a good guess and something I all too often forget to think about, so thanks for the suggestion.  However, I don't think that's the problem here.  I have a little over 225Gb of available space.  I did notice one thing though, that has me curious--maybe it's just the way the reporting works, I dunno.  The "Disk Usage Analyzer" (Applications>Accessories>Disk Usage Analyzer) shows Root (/) at 100%.  That doesn't make sense.

parted reports:
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  20.0GB  20.0GB  primary  ext3         boot 
 2      20.0GB  24.0GB  3997MB  primary  linux-swap        
 3      24.0GB  250GB   226GB   primary  ext3              

Information: Don't forget to update /etc/fstab, if necessary.             
< end of report >

gparted reports sdb1's mountpoint as "/", and sdb3's mountpoint as "/home"

gparted also reports sdb1 (root) as being 18.63Gb in size, 3.45Gb or 18% used, whereas the Disk Usage Analyzer shows root as being only 13.1Gb in size and 100% used! :confused:

gparted reports sdb3 (/home) as being 210.53Gb in size, 11.84Gb or 6% used, whereas the Disk Usage Analyzer shows /home as being only 10Gb in size, and 76.4% used. :confused:

First of all, does anyone know how or why these two tools should give such different reports?

Second, what would have set a "size" for /home at 10Gb, when it actually has the entire sdb3 partition of 210Gb?

If the Disk Usage Analyzer is correct, and root IS 100% used (and /home 76.4% used), then no wonder the system is struggling.  If any part of the OS thinks the root partition is full, it's a wonder the system can run at all!

Before I hose this system and install 8.10, can anybody explain what in the name of Rocky Balboa is going on here?  parted and gparted almost certainly are running closer to the heart of the system than the Disk Usage Analyzer, and their results are in keeping with what I think the disk is set up like.  But where does the DUA get the idea that root is only 13.1Gb in size--or /home only 10Gb?

If anyone can shed any light on what is going on here, please do, as I do intend to hose this system tomorrow night, at the latest.  After that, I won't be able to retrieve any more data from the system, or check anything else out (obviously, because the system will be GONE).

Since I intend to replace this with an installation of 8.10 anyway, this has really beccome a moot point, but, for future reference, I'd really like to know just what is happening here, and how/why it came to be as it is.  What part of the system thinks root is 13Gb and full?

PLEEZE!  Enlighten me, if you can.  I'd REALLY appreciate it.

---

### Post by bilijoe on 2008-10-31
Aargh!  I may have just answered part of my question.  I just looked at fstab.  The following is its contents:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c91946c1-bcab-4b51-8d9e-ef3d0a2e353f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=24a18ddc-ac90-40d0-ba3a-99808422dc9c /home           ext3    relatime        0       2
# /dev/sda2
UUID=c270e77f-31c0-421e-a281-92f0489ee841 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
< end of ftab >

I don't see any entries in there, at all, for sdb.  sdb is where the system is.  sda doesn't even get mounted, in normal running.  If I click on its icon, under "Computer", the system will mount it, and display its contents, but, under normal conditions, it just sits there, taking up space.  If there are no entries in fstab for sdb, how can the system even run?  And where is it getting it's information about the physical dimensions, partitionong, etc., for the disk (dsb) that it is running from?  Now I'm REALLY confused! :confused::confused::confused:

---

