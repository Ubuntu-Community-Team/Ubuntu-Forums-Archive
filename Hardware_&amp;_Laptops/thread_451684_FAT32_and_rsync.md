---
title: "FAT32 and rsync"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by ericbarch on 2007-05-22
I'm trying to rsync some XFS drives to a FAT32 drive. Every time I rsync, it recopies every single file. I've read that you shouldn't use rsync with FAT partitions, but I have no choice. The drive has to move between multiple OSes and FAT is the only FS that is supported by the major 3 OSes. Any ideas?

---

### Post by quux on 2007-05-22
Hi, you can try to go for the "-c" (skip based on checksum) solution which unfortunately is quite slow; rely on a simple "--size-only" (skip files that match in size) or try to play with "--modify-window=..." since timestamp resolution on FAT32 filesystems is only 2 seconds IIRC.

---

### Post by kebes on 2007-05-22
Actually there are drivers for Windows that give it the ability to read/write drives that are formatted with ext2. I believe Mac OS X can also be configured to read/write ext2. So in principle all three major OSes can read/write an ext2/ext3 partition, which does support all of rsync's features.

However reformatting from fat32 to ext2/3 may not be an option for you. You could try playing with some of rsync's options:
[http://www.die.net/doc/linux/man/man1/rsync.1.html](http://www.die.net/doc/linux/man/man1/rsync.1.html)

For instance, check these options:
--checksum 
--update
--size-only
etc.

There are lots of options, and maybe by performing the check one way instead of another way, you can get it to work properly with a fat32 target.

---

### Post by ericbarch on 2007-05-22
It's no problem to reformat the drive. The only OSes I really need are Linux/OS X, but I need read/write capabilities for both OSes.

---

### Post by ericbarch on 2007-05-22
I've looked into ways to mount ext2/ext3 drives in OS X, but so far the only program I've seen is for older macs. I have a MacBook. So far the only way I see to do this is to use FAT.

---

### Post by kebes on 2007-05-22
Well I've never used it, but this:
[http://sourceforge.net/projects/ext2fsx/](http://sourceforge.net/projects/ext2fsx/)

Claims to give OS X ability to access ext 2 filesystems (and it's in Universal Binary format, so your Macbook should be fine).

Conversely, this:
[http://sourceforge.net/projects/linux-hfsplus](http://sourceforge.net/projects/linux-hfsplus)

Seems to give Linux the ability to access HFS+ (the filesystem used by Mac OS X).

You may already have tried using those programs (if so, sorry!).


Anyways, it's probably easiest to play with the rsync settings first, and see if that fixes it.

---

### Post by pcalvert on 2007-10-21
Hi,

I believe that you can find the answer here:
[http://lists.debian.org/debian-user/2005/03/msg00955.html](http://lists.debian.org/debian-user/2005/03/msg00955.html)

Here's the relevant part:
> 
Another lesson is that the FAT32 partition should be mounted with the "shortname=mixed" option. If not, the rsync gets messed up. The default option is "lower," which means that files and directories with short names will have their names forced to lower case. But then rsync will think they're different from the ones it sees in the source that are upper case, and it will send the upper case ones again, and then delete the lower case ones. But since it's really the same files, the end result is it transfers a bunch of data and then deletes it all! Not good.


Phil

---

### Post by pcalvert on 2007-10-21
I missed the fact that the OP was trying rsync XFS to FAT32 until after I posted that last message.  I'm not sure that's a good idea.  From the little reading I've done on rsync, the impression I have is that the source and target destinations should (preferably) be of the same partition type.  That's probably not a requirement, though.  However, if you want to use rsync to backup files to a different partition type than the one they are on, research (*i.e.*, use Google) and/or experimentation is highly recommended.

Phil

---

### Post by kinson on 2007-11-25
> **pcalvert said:**
> Hi,

I believe that you can find the answer here:
[http://lists.debian.org/debian-user/2005/03/msg00955.html](http://lists.debian.org/debian-user/2005/03/msg00955.html)

Here's the relevant part:


Phil

Hi Phil,

Thanks for that interesting bit of knowledge :) I've always had this main problem :( Cause I backup my photo's from my Ubuntu PC (ext3) to my external HDD(fat32, for obvious portable reasons). So in theory all I have to do is mount it with the mixed filenames and it'll be ok? or will I also have the use the other solutions at the top of this thread?

Btw, if its not too much to ask, how would I mount it in such a way? As Ubuntu auto mounts(i assume) the drive when I plug it into my pc...it shows up on the desktop anyways :/

Cheers,
Kinson

---

### Post by monsieurrigsby on 2008-02-19
Just to (hopefully) complete this information....

I've been doing the same thing (rsync-ing from ext3 to fat32), with the same related problems :-(. The Debian post mentioned above is of relevance but, at least on Gutsy 7.10, USB disk fat32 partitions are mounted as shortname=mixed by default so no worries there (mount extract below):

> /dev/sda1 on /media/<DRIVENAME> type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)

The easiest method for getting the timestamp checks to work properly is as in this Mandriva post:
[http://mandrivausers.org/lofiversion/index.php/t42887.html]("http://mandrivausers.org/lofiversion/index.php/t42887.html")

Just use:
>  rsync -rvt --modify-window=1 --delete <source> <target>

I also use the --update option because I update the backup from different sources and don't want to lose any changes. Haven't had any issues yet with this modify-window level.

I guess there may still be issues with filename characters supported by ext3 but not by fat32 as mentioned in the Debian post, but the backup sources are my files in this case, so I have control of this and really want to avoid the two backup partitions route (kind of defeats the object of a single backup space).

Hope that's of use.

Cheers,
MonsieurRigsby

---

### Post by monsieurrigsby on 2008-02-19
Well, not quite *exactly* the same (original poster was rsync-ing from xfs) but should work the same.

(slightly off-topic) Note that the Debian article also talked about using CygWin, ssh and rsync for backups from Windows hosts to the (fat32) backup medium. Just as an extra tuppence, this is probably an overly cumbersome method. At the risk of offending Linux-heads, there are plenty of decent enough Windows native solutions which do incremental backups e.g. SyncBack (freeware version - see [http://http://www.2brightsparks.com/syncback/compare.html]("http://http://www.2brightsparks.com/syncback/compare.html")).

Of course unless you already have a CygWin build on there.   :-)

---

### Post by monsieurrigsby on 2008-02-19
OK, last addition to this for the mo ;-)
(just for completeness)

Note that, since vfat filesystems are case insensitive, you also have issues if source files (e.g. on ext3) exist with names differing only by case changes. I just had this.

The net result (on my setup anyway) is for rsync to alternate between the two versions: copying one of them, then (next rsync) copying the other (replacing the original one), etc. Bottom line - ensure your source filenames conform to vfat standards (and make sure shortname=mixed or shortname=winnt are used: see man mount).

---

