---
title: "gparted won't touch ntfs partition to resize it, citing errors on filesystem"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by arsmith on 2009-03-07
Hi all, I've been trying to install ubuntu on a lenovo x300, but when I get to the partitioning step of the installation process, the installer just flashes an error about not being able to resize my NTFS (windows) partition.  My only option from there is to quit the installer and then try to do the same thing with gparted.  From there, I get some more information (gparted is a little bit more descriptive in the error messages it spits out):  

It tells me that there's a problem with the filesystem, and that its going to refuse to touch it.  It suggests booting into windows and running the command ```
chkdsk /f
``` from there, then restarting twice.

When I try running the windows command, it gives the message 

```
Chkdsk cannot run because the volume is in use by another
process.  Would you like to schedule this volume to be
checked the next time the system restarts? (Y/N)
```

I've tried both ```
Y
``` and ```
N
```, but neither does anything.

Some other miscellaneous (and hopefully relevant) information about the system:

[LIST]
[*]I've taken a peak at the windows partition manager (Right-click on My computer > manage > disk management) and there appears to be an extra partition that's about three gigs.  It doesn't show under My Computer, but the ubuntu partitioner picks it up.  I assume this is some sort of recovery utility that lenovo packages in (called thinkvantage or something?).  Maybe whatever it is that they do to hide it in the "My computer" view is also confusing gparted?
[*]The computer doesn't actually have a hard drive, it's a 60(55.6) gig SSD
[*]When I go to C: -> properties -> tools -> defragment, it loads a custom lenovo partitioning utility, not the windows one.
[/LIST]

Thanks ahead of time :P,

ARS

---

### Post by Rallg on 2009-03-08
In Windows, the message about chkdsk not running, due to another process, is not an error. Scheduling the check (Y) then re-booting will run chkdsk, which is happening outside of Windows. Then when boot completes, things should be OK there, unless there is a real problem.

I don't know about lenovo, but if it is using a custom defragmenter, that may be a good thing. The one built into Windows has sometimes bee criticized as being too slow.

In Windows, do the defrag. Afterwards, ask Windows how much free space it thinks it has on C:. CORRECTION: You have solid-state drive, you say. Although defrag might be useful this one time, generally SSD does not benefit from defrag.

You didn't say whether you had XP or Vista. If Vista, it has a built-in ability to shrink the Windows partition. It is not a full-featured partitioner. But presumably, in your situation, it would work to shrink the Windows partition, then put Ubuntu into the unallocated space (which is no longer within Windows).

Did you computer come with Windows re-installation CD or DVD? If not, that 3G partition is almost certainly used for recovery.

---

### Post by arsmith on 2009-03-08
Alright, so I've told it to schedule the check AND restarted a bunch of times (about five), but nothing happens when it boots up, and when I try defragging, it tells me that chkdsk is scheduled to run the next time windows boots, and that it won't be able to defrag until that happens.  The defrag utility that I've been using (the one that came packaged with the computer), btw, is called Diskeeper Lite.  I'm using XP :(, so too bad I can't take advantage of that feature in vista.  

I have some ideas that I'm going to try, but I'd be glad to have some input as to whether people think they would work or not:

Boot up to an XP install disc, resize the C: partition from there, and then shut the computer off before it gets to installing the OS.  Also, an error pops up when I select the C: partition from within that diskeeper tool.  For some reason the attachment wasn't uploading right, so I've posted it to [tinypic]("http://i44.tinypic.com/6ifigy.jpg")

Maybe I should use Wubi? From my understanding, the only disadvantage to wubi over a regular install is disk read/write times.  Is this right?  If so, I have an SSD, so it shouldn't really be that big of a problem for me.

If anyone has other work-around ideas, please let me know.

Thanks.

---

### Post by arsmith on 2009-03-08
I've just tried booting up from an XP install disc to use chkdsk from its recovery console, but something really interesting happened:

The recovery console wouldn't start, claiming that it couldn't find any hard disks on the system.  Does anyone know what this means?

Is it not finding my C: drive because its not actually a hard disk but an SSD?

---

### Post by Mark Phelps on 2009-03-08
Would be very careful using any Windows utilities to mess with your SSD -- unless they specifically say they have been updated for that purpose.  You might have to get hold of something like Pargon or Acronis Disk Director.  I wouldn't trust any "Lite" version or any freeware with an SSD.

---

