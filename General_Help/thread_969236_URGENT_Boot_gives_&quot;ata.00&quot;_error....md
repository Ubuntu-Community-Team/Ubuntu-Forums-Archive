---
title: "URGENT: Boot gives &quot;ata.00&quot; error..."
date: 2008-11-03
forum: General Help
---

### Post by ateamrocks on 2008-11-03
Hey,

I'm a geek, but this is beond me... Please help!


I just updated to 8.10, when booting it can't resume, so it says it will just boot normaly... But when booting each item, I get the following message repeated every 11 or so seconds...

```
[xxx.xxxxxxx] ata1.00: status: { DRDY ERR }
[xxx.xxxxxxx] ata1.00: error: { UNC }
[xxx.xxxxxxx] ata1.00: exception emask 0x0 SAct 0x0 SErr 0x0 action 0X0
[xxx.xxxxxxx] ata1.00: BMDMA stat 0x25
[xxx.xxxxxxx] ata1.00:cmd XXXXXXXXXXXXXXXXXXXXXXXX

```

The x's are random numbers...

Please help, I have a dell Latitude d600...
:confused:

Thanks
az

---

### Post by ateamrocks on 2008-11-03
~Bump~

Also, I found similar bugs, but none of the fixes work for me... Please help this is EXTREMLY important!

Thanks

See Also [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/223014]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/223014")

az

---

### Post by cmittle on 2008-11-05
I just started having a similar problem.  I did not try to update to 8.10 yet, so I don't know what triggered it.  [Here]("http://ubuntuforums.org/showthread.php?p=6110341#post6110341") is the thread.

---

### Post by cmittle on 2008-11-06
My problem ended up being a bad hard disk.  For more information read the link in my previous reply.

---

### Post by batty_whol on 2008-11-14
I'm getting similar errors after having upgraded from 2.6.24-19-Generic to 2.6.24-21-Generic.
I'm running on AMD64 Dual Core
4 Identical 500Gb SATA drives.
sda has / (currently all that is working)
sdb/sdc/sdd are LVM split to provide mirroring and journalling.

It will boot since I switched off adma for the sata_nv module by adding
options sata_nv adma=0
into a file in /etc/modprobe.d and running update-initramfs -k 2.6.24-21-Generic -c (backed up existing initramfs first), then copied new initramfs to new name, and edited grub menu.lst to have a new entry that will boot using this initramfs.

However, when ever I do anything more than view files, it gets incredibly slow.

I'm currently running badblocks on all of the sdb/sdc/sdd drives as I suspect disk damage. However I have seen a lot of comments on forums (mostly referring to an older kernel) that suggest there was a kernel bug. I find it puzzling that this would happen to all of my disks at the same time.

However, badblocks -v /dev/sdb has just completed with 86 badblocks (oouch!).
sdd seems ok, but not quite finished.
Just starting on sdc.

I've also found lots of libdata error messages all for ata4 (which relates to /dev/sdd)
OUtput from dmesg | grep ata4.00 | awk -F']' '{ print $2 }' | sort -u
ata4.00 BMDMA stat 0x25
ata4.00 cmd 25/00:08:17:60:64/00:00:27:00:00/e0 tag 0 dma 4096 in
repeated with 12 times with varying numbers
ata4.00 error: {UNC }
ata4.00 exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
ata4.00 exception Emask 0x10 SAct 0x0 SErr 0x3850000 action 0xa frozen
ata4.00 exception Emask 0x10 SAct 0x0 SErr 0x3950000 action 0xa frozen
ata4.00 status: { BUSY }
ata4.00 status: { DRDY ERR }

I've looked these codes up on
[http://ata.wiki.kernel.org/index.php/libdata_error_messages](http://ata.wiki.kernel.org/index.php/libdata_error_messages)
I'm not sure I'm interpreting the meanings correctly, but this seems to suggest that there may be a cable error for ata4.

It's a bit of a longer reply that I had intended

---

### Post by psusi on 2008-11-14
Rather than badblocks, install the smartmontools package.  Run sudo smartctl -a /dev/sdX to dump a bunch of status information on the drive, sudo smartctl -t long /dev/sdX to start an internal physical diagnostic.  This will take some time but will run in the background and you can check on the status with sudo smartctl -l selftest /dev/sdX.

---

### Post by batty_whol on 2008-11-14
I'm doing just that with smartctl now.
I'm now booted from a Helix CD which has the tools on it. The disk that / was on (sda) has gone perdang!!! now.

fsck (from Helix) certainly had a lot to fix.

I'm still puzzled by how this happens to 4 disks at the same time???

I'll post back in a few hours with the output from smartctl.

---

### Post by batty_whol on 2008-11-14
Hear is the output from the smartctl -a /dev/sdX

---

### Post by batty_whol on 2008-11-14
Here is the output from the smartctl -t long /dev/sdX
However I don't think this was working as (I've appended to the sdb file) I had a message from smartctl -l selftest /dev/sdX saying
'Device does not support Self Test logging.

---

### Post by batty_whol on 2008-11-14
I just tried the
smartctl -S on /dev/sda
Enable autosave (clear GLTSD bit) failed.


I need to order replacement disks I imagine.
I'm still running and logging badblock checks on all partitions.

---

### Post by batty_whol on 2008-11-14
Not sure if there is a benefit to this, but here's my partition table (from fdisk).

---

### Post by batty_whol on 2008-11-14
Here's the summary output of running badblocks -v on all of my partitions (sda I also ran over whole disk as not all partitioned).

badblock command:
badblocks -v /dev/sd[abcd]$X > /tmp/devsd[abcd]$X.badblocks.out

I have create the summary with this command
grep Pass *bad*

I have attached the 4 outputs with badblocks (though I can't see that being useful to anyone else) and the summary.

---

### Post by batty_whol on 2008-11-14
Just had a look at how the badblock out files look on the web. Not nice!!! Sorry. Best to ignore them I think.

---

### Post by batty_whol on 2008-11-15
I think I may have found the problem.

A loose connection in the power cable going to the SATA drives. It was a single point for all 4 drives. The red pin had come loose inside the socket.

I'm just checking 2 of the drives again.

---

### Post by mathewb on 2008-11-15
I have been encountering this error periodically since some point in Hardy 8.04. When I upgraded to 8.10 it seemed to fix it until a couple days ago, this problem came back worst than before.

After searching online for a couple days now and nothing working, I decided to try something on my own. I went into the BIOS and checked out what options Dell had there (this was a Dell Vostro 1500). I found an option that switched the SATA mode between ATA and AHCI. I switched it to ATA and now I no longer get the error and Ubuntu is running faster than it has ever been (Vista still boots up as well, for those who have dual booting machines).

I'm guessing there is just some bug in the implementation of AHCI for Dells since this problem seems to be focused in Dell's computer line.

---

