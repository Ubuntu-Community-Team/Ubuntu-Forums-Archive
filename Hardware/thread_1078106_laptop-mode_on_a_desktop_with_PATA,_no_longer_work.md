---
title: "laptop-mode on a desktop with PATA, no longer works."
date: 2009-02-23
forum: Hardware
---

### Post by sigmason on 2009-02-23
I've got a pair of Dell Dimension 2400.

On one, Ubuntu 6.06LTS specifically for CUPS and print serving.
On the other, Ubuntu 8.10 specifically for CUPS and print serving.

A while back (more then 1 year ago) I set up the 6.06 box in laptop-mode to power down the WD320GB Green hard drive because for long stretches of time it wouldn't need to be running.

That worked/works fine.

Unfortunately, this no longer works in 8.10.  I can still issue the hdparm commands hdparm -Y /dev/sda and the drive usually spins down.

I can use s3g tools and the drive power down.

However, no matter what I do in acpi-support and laptop-mode.conf I can't replicate the drive powering down.

I tried disabling the smart offline tests and that didn't fix it either.

I don't really want to cron a job to spin down the drive, because I'm afraid that ACPI won't wake it back up when the need is there.

I think this has something to do with the drive no longer being hda, because in 8.10 the drive is sda?

Any ideas?

Sigmason

---

### Post by sigmason on 2009-02-23
I've been playing with this:

[http://blog.mymediasystem.net/uncategorized/simple-way-to-spindown-a-sata-hard-disk-drive-after-being-idle-linux/](http://blog.mymediasystem.net/uncategorized/simple-way-to-spindown-a-sata-hard-disk-drive-after-being-idle-linux/)

This cron job basically checks to see what disk activity is going on and if there isn't any it shuts the disk down.

The shutdown part is fine, but this comparison is turning up minor write differences each time it runs, even if I run it 20 seconds apart.

Therefore something is writing to the disk, but and this is weird, I asked laptop-mode to change the commit to like 21600 and it still does this?  Even with the partition mounted as ext2?

Something is not quite right here, any suggestions on how to identify the source of the drive access?

Sigmason

---

### Post by sigmason on 2009-02-23
So it seems the cause of my writes in that last post was syslogd.

As fast as the system went idle, the script would fire, logging in syslogd, which apparently ignores the (-) in the syslogd.conf files in this version because it immediately commits a write of dirty pages.

This write of dirty pages caused the cron job in the last post to see activity and so it never idles.  Literally, it is it's own worst enemy.

So I turned off syslogd and klogd for now.

This made this script work.

So now the drive idles in at least 2 minutes (the first iteration sets the standard for the second iteration to compare against) so by setting the 2 lines to 0-59/1 I get a 2 minute sleep window at minimum (assuming idle, otherwise it will extend itself.)

Oddly I had to put the 2 lines in backwards or they execute in reverse order?

So now the question is: is syslogd and klogd causing my issue with laptop-mode and if so, why...it didn't cause this problem in my other system.

I also think I'll try running lm-profiler and see what happens.

Sigmason

---

### Post by sigmason on 2009-02-23
syslogd and klogd were not the cause of the issues with hdparm -S or laptop-mode going into idle and spinning down the drives.

Even with those daemons off, the drives don't spin down unless I use the script I was just posting about.

Clearly something has changed because basically the same configuration running 6.06LTS is not doing this.

It would seem my two remaining issues are that syslogd and klogd commit to sync their writes regardless of the commit parameters a volume was mounted with in fstab or in laptop-mode.conf.  Also the drive does not spin down anymore and the only thing that I really notice is different is that 6.06LTS considered the drive hda and 8.10 considers it sda.

The script from above is really a patch.  It makes it work.

I suppose, that what I was doing with syslogd and klogd on the 6.06LTS install was kind of asking for trouble, because it was holding the written data for the log(s) in RAM until the commit expired or something spun-up the disks.  So maybe in the end it's better I put the logs in RAM with a RAM disk or something like RAMLog.  There was always an uncertainty produced because I hadn't altered the levels of the logging in that older installation and therefore there could be quite a bit of data sitting unflushed to the drive right in RAM.  In the event of a power outage log data could be lost or the drive file system corrupted because of the extended commit and sync (though that never seemed to be an issue.)  I suppose if I put the logs in RAM in a more manual manner (RAM disk and scripting), I could then either commit them to sync with a cron job or manual script.

Maybe I should just put them all out on the network instead.

Sigmason

---

