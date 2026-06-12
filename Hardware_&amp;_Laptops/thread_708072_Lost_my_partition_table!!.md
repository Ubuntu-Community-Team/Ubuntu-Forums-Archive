---
title: "Lost my partition table!?!"
date: 2008-02-26
forum: Hardware &amp; Laptops
---

### Post by psyopper on 2008-02-26
So today I was researching software RAID in Linux with mdadm in preparation for a future build. I came across [a web site]("http://portal.itauth.com/2007/10/07/linux-practical-introduction-linux-software-raid") that benchmarked their mdadm RAID arrays including a way to test throughput with the dd command:

```
dd if=/dev/zero bs=8k count=100000 of=/dev/hdb oflag=sync
```

So I ran it for grins and giggles to see what kind of throughput I was getting. They were testing with varying block sizes so I thought I would try that as well, I tried 4k, 8k and 64k sizes. 

I stopped for dinner and came back to check my email only to discover that Thunderbird wouldn't load. I was getting a warning: *"Thunderbird is already running, but is not responding. To open a new window, you must first close the existing Thunderbird process, or restart your system."* So I open System Monitor looking for a rogue process, but it's not there. I log out and back in and still no joy! I log out, [ctrl][alt][backspace], log back in and still no joy. So I reboot and it still isn't working.

To make a long story short, this is a dual-boot machine with WinXP (that I haven't booted to in 6 months) so I set up a shared FAT 32 partition on a separate drive to store my Thunderbird profile to share between the two OS's. Turns out that the partition table for that drive is missing!
```

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
16 heads, 63 sectors/track, 77545 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Disk /dev/hdb doesn't contain a valid partition table

```

Crap!

So I'm looking around and I see a [URL="http://www.linuxplanet.com/linuxplanet/tutorials/3174/7/"]relatively meaningful set of instructions
[/URL] but I'm still kinda new to the Linux thing and I REALLY don't want to loose my email stores from the last 12 years. Believe me when I say - I have learned my back-up lesson on this one! How bad does it hurt? All of my 20+ GB of music was on that drive as well!

So here's the question - I can't recall how I had this drive set up. I believe I had a 5-10 GB primary and a 30-35 GB extended with a full secondary inside of it. The primary had the Windows shared FAT32 partition, the secondary was also FAT32. 

What are the recommendations of the community on restoring this? Do I follow the instructions on the linked page and try to recover the entire 40 GB on a single partition table? Or will that even work? I know all of the data itself is there, and the vast majority, if not all, should be chunked together and it was all block writes (music and downloaded email).

Help?!?

---

### Post by psyopper on 2008-02-26
OK, I think I know how I lost my partition table. Again, newbie stuff here but I'll treat this thread kind of bloggishly. Anyway, the dd command I used is likely the culprit.
```

dd if=/dev/zero bs=8k count=100000 of=/dev/hdb oflag=sync

```

dd is a file writer, a really REALLY powerful file writer. Here's what I did wrong - 

1. /dev/zero is an empty file. /dev/zero (if I'm not mistaken) is akin to the original /dev/null, which if I had seen /dev/null it would have sparked a little twitch in my memory telling me that I was about to write a bunch of 0's to my hard drive.

2. /dev/hdb is a drive, not a partition on a drive. /dev/hdb1 is the first partition on the drive. By specifying the drive rather than the partition I wrote a bunch of 0's to the drive starting with block 0 on that drive. Guess where the partition table on that drive exists? That's right, sector 0 through about (guessing here) sector 128. Maybe more on a 40 GB drive. 

So not only did I overwrite the partition table, but I wrote about 6.5 GB of 0's starting at sector 0 on that drive (recall that I tried a write of 100000 64k blocks). I don't recall exactly how I had that drive partitioned but that's roughly 50 to 100 percent of the first partition on that drive which is where my Thunderbird indbox file was stored. It was on the second partition that my music was stored.

Here's where I'm at:

1. The email profile was copied from Windows around April-May of 2007 so I should be able to recover my email to that period. 

2. I would still like to try to recover the music on the second partition. Only a fraction of it was downloaded and currently exists on my Ipod so I can restore it from there. In fact a large majority of my music was on my ipod, but my wife's wasn't so restoring that will be up to manually ripping cd's again. Maybe this isn't a bad thing as they were all originally ripped at 128k VBR MP3, now I can rip them at a higher fidelity like 256k CBR MP3 or OGG high quality.

Consider this thread bumped. If anyone knows if I can actually unwrite the 0's and/or at least restore what wasn't 0'd out, please feel free to chime in! Would the insructions for rebuilding the partition table that I referenced in my first post work if I specificed the entire drive instead of the specific partitions?

---

### Post by psyopper on 2008-02-26
Bump... 

Am I the only one stupid enough to have killed their MBR? Or am I just the only one stupid enough to think I can recover from it??

---

### Post by Wamoc on 2008-02-26
Unfortunatley, there is no way to directly rebuild the partition table.  There are a few windows programs that will read the bits from the hard drive and find deleted files and will allow you to copy them from the erased sectors.  You will probably have to do this.  Do know, they will need to be sent to another drive (otherwise it could overwrite the files).  I will look around for the programs to do this (someone I know onetime had a hacker clear half a hard drive and I had to do this for them).
I will get back to you in a few minutes on a program for that.

---

### Post by Wamoc on 2008-02-26
Most the utilities I am finding are expensive, but I found one freeware one called File Recovery 4.  Try that out (remember, it needs to run in windows).  Good luck getting your files back.

---

