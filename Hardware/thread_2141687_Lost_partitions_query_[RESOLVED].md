---
title: "Lost partitions query [RESOLVED]"
date: 2013-05-03
forum: Hardware
---

### Post by essenby on 2013-05-03
I'm pretty sure I already know the answer to this but I'll post anyway as my knowledge is far inferior to many of those who frequent this board.

I have a 250Gb external USB drive that was formatted with a 200Gb Primary partition with all my Windows stuff on and a second  50 Gb Primary partition partition I used for Linux distributions as a play area.  This had 2 logical partitions that I used for "/" and "swap", very simple.  I've had several flavours on there over the years the latest being the latest Mageia 3 Beta3 and decided I would like to look at Ubuntu Studio.

So I booted the Live DVD and started the install process which recognised the existing installation and gave me a number of options.  I think it was something like "Use the whole disk", "Replace Mageia", and "Manual partitioning".  The "Replace" option was checked and I thought "That's clever - will save me some time" and pressed ahead.  I now have a drive with ONLY one 230Gb Primary partition (With Ubuntu Studio installed)  and a smaller Logical "swap" partition, and the question is "Is there ANY way of recovering my lost partitions/data?" 

I have tried TestDisk - with no success and Easeus Data Recovery Wizard.  The Recovery Wizard appear to show me my data (or some of it) but the free version will only recover 1Gb of data and there is at least 5 times that much that I would like to get back if possible.  

Is anyone aware of a free/open piece of software that will do a similar job or do I have to calculate whether my data is worth the $56 they are currently charging?

---

### Post by oldfred on 2013-05-03
It sounds like you did the whole disk install.

I would have though testdisk would have shown old partitions. Since data was written over the Windows partition you would not recover a bootable system, but might recover some data.

Only you can determine value of your data. Some suggest the Windows tools are better for Windows NTFS partitions.

For Linux I have used photorec which is part of testdisk. It is slow, finds only file extensions, finds deleted files as well and needs lots of room to copy found data to. IF photos or music the file has internal data to aid renaming, otherwise you pretty much are only your own. I had saved some text files many times, it found many versions of the same text file and I had to sort thru my text files. I now add the name of a text file inside my files to help in the future.

       [URL="http://www.psychocats.net/ubuntucat/recoverdeletedfiles/"]http://www.psychocats.net/ubuntucat/recoverdeletedfiles/
[/URL]
 [URL="https://help.ubuntu.com/community/DataRecovery"]https://help.ubuntu.com/community/DataRecovery

      [/URL]
 Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

   Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

    [URL="https://help.ubuntu.com/community/DataRecovery"]
[/URL]

[URL="http://www.psychocats.net/ubuntucat/recoverdeletedfiles/"]
[/URL]

---

### Post by essenby on 2013-07-31
Thanks to all who offered advice - but it was all in vain.  I've decided to bite the bullet and forget about what was in there.  Nothing was irreplaceable, or if it was - it was because it's no longer used or required :-)

On thing I will NOT forget is that the "Replace *existing distro *with *this distro* option" doesn't replace it on it's existing partition - but replaces it on the whole disc!

This thread can be CLOSED now

---

