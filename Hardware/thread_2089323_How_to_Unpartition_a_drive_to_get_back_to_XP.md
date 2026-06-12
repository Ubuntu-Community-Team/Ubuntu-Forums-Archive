---
title: "How to Unpartition a drive to get back to XP"
date: 2012-11-28
forum: Hardware
---

### Post by rlntel on 2012-11-28
Hi...new thread.

By mistake, I partitioned completely over my Windows XP partition on my Sony VAIO and installed ubuntu. A lot of files were left on XP.

I've now moved on to a newer computer so I'd like to go back on the old one, unpartition the drive and retrieve the files I left on XP.

Anyone know how I can do this?

Thanks.

---

### Post by agillator on 2012-11-28
Did you actually "partition over" XP, i.e. replace it, or did you create a new partition out of free space and install there? If you don't know, use one of the partition managers to check. Gparted is a good one and should be on the installation disk for Ubuntu, just boot from the installation disk and then run gparted.

If the Ubuntu partition and the swap partition are the only two shown then you are probably out of luck. If there is still an XP partition even though you don't normally see it then you should be able to mount it and access it.

Note, however, that if there is an XP partition GRUB should have found it and it should be listed as an option when you boot your machine, so don't hold your breath. For future reference I find it useful when installing a new system to use a partition manager to make space for it and then load it beside my most recent replacing only older ones that I definitely will not need to get into any more. Of course if I have windows also installed than I hang on to it, too.

---

### Post by rlntel on 2012-11-29
Yeah...it was the very first ubuntu install I did back in 2008, 8.04...maybe? I looked at 8.04 then backed out and then installed. The second time the disk just partitioned the entire drive.

Hoping against hope that there's a chance...but I won't hold my breath. Probably need the FBI lab to get those files. :)

Thanks, ~Rob

---

### Post by ahallubuntu on 2012-11-29
It's still not clear exactly what you did.  So it's really hard to offer you much help.

By "partitioning" do you mean you ERASED the existing XP partition? Or did you SHRINK it to make room for Ubuntu?

If you ERASED it (only two partitions showing as poster above said), then those XP files are probably gone forever.

If you SHRANK the XP partition to make room on the disk for Ubuntu, the XP partition is probably still there and so should be your files.

Try Gparted as mentioned above.

---

### Post by rlntel on 2012-11-29
I believe I completely overwrote the original XP partition. I say that because 8.04, nor any later editions, allowed me to see an additional drive, FAT32 or otherwise.

I'd hope that there may be something 3rd party that would allow me to unpartition 8.04's and attempt to recover the original xp files.

Is that an unrealistic hope?

---

### Post by agillator on 2012-11-29
Yes, it is probably an unrealistic hope. However, to make sure use one of the partitioning programs or disk utilities that show partitions and see what is there. If XP were there GRUB should have picked it up. But there could be reasons it doesn't and the only sure thing to do is to look at the partitions. Once you do that you will know what you are faced with.

---

### Post by oldfred on 2012-11-29
If you just did it yesterday, we would immediately say stop using drive. Everything you do writes over more data.  And there are tools that can scan a drive for anything that looks like a file and save that. But the more you have used it the more that was overwritten. If it was 4 years ago and you have used system,  I am not sure the NSA could get much back.

Post this from liveCD.

sudo fdisk -lu

---

