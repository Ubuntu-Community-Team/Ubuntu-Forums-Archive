---
title: "WD My Passport Ultra failure?"
date: 2017-01-07
forum: Hardware
---

### Post by mchatzikos on 2017-01-07
I have had a 4TB Western Digital My Passport Ultra external drive for about a month and a half.  When I bought it, I partitioned it with gparted and used a MSDOS partition table with two ext3 partitions.  The drive had been virtually in constant use until today.

Earlier today I tried to reformat it with gparted, using a GPT partition table and one ext3 extension.  On a similar drive, this process lasted about one hour.  With this one, it takes upward of two hours, at which point I abort the operation.  I have also noticed, I think, a subtle noise coming from the drive, that I do not know if it was there before.

It appears that gparted can install other filesystems on the drive; an experiment I did with FAT32 completed successfully, but I haven't tried others.

My interpretation of all this is that the ext3 installer, being more thorough, has run up against a problem on the disk (bad sector?), gets stuck and fails to run to completion.  I have tried to run ```
sudo badblocks -b 4096 -c 4096 -e 1 -w /dev/sdb 
``` on the drive, but I haven't had the patience to sit through it -- it looks like it'll take days.

My guess is that the drive has become unreliable, and given that I wish to use it as backup, I'd be better off getting a new drive (and looking into whether WD would replace it for me).  Would that be the right call to make?  Any other ideas of things to try before completely giving up?  (I'll run the above command overnight and see what happens).

---

### Post by DuckHook on 2017-01-08
Welcome to the forums, mchatzikos.

Assuming that your drive is /dev/sdb (make sure of this), please do as follows:```
sudo smartctl -t short /dev/sdb
```This will run a short version of smartctl test on your drive. It should take anywhere from 1 to 10 minutes depending on your HDD. If successful (some USB drives don't support smartctl calls), then post output of:```
sudo smartctl -H -l error -l selftest /dev/sdb
```

---

### Post by mchatzikos on 2017-01-08
Thanks for the response.

The commands do not appear to work -- they return immediately.  Here's what I get:

```

$ sudo smartctl -t short /dev/sdb
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/


Short Background Self Test has begun
Use smartctl -X to abort test

$ sudo smartctl -H -l error -l selftest /dev/sdb
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/


SMART Health Status: OK


Error Counter logging not supported
No self-tests have been logged
$

```

I should mention at this point that my system is quite old: 10.04.  I have installed smartmontools but maybe the version available on the repository does not work with new drives?

---

### Post by DuckHook on 2017-01-09
Your first and most important order of business is to upgrade from 10.04. That version has been end of life for years now and is both insecure and unsupported. Many of the worst Linux bugs have been discovered since, and will never be fixed in Lucid, so continuing to use it is like playing Russian roulette.

I don't really know how to advise you. Even the commands for Ubuntu have changed in seven years. Ubuntu changed to the Unity DE, which may be too bloated for your hardware, and I have no idea how you got smartmontools installed, since the repositories have been retired for years.

I'm afraid my memory doesn't go back far enough to help with Lucid (10.04). I *was* wondering why you were still using ext3, but your explanation has clarified that.

I can only suggest at this point that you try a modern flavour of 'buntu on a LiveUSB/DVD and see if this does not help. Your symptoms would indicate that your drive is failing, especially since it was working for some time until recent events, but this is nothing more than a wild guess and I have no confidence is being able to help diagnose on an unsupported end-of-life version.

---

### Post by mchatzikos on 2017-01-11
Thanks for the response.  I was running badblocks, which took 80 hours to write the first pattern, so I ended up killing it because then I realized it had to read that pattern, and then repeat for the other three patterns.  For the record, the command was
```

sudo badblocks -b 8192 -c 8192 -s -e 1 -w /dev/sdb

```

I will look into your suggestions, and let you know what happens.

BTW, you are right that my system can't probably handle 16.04: I bought it in late 2007.  (In case you're wondering, I make do with a Mac laptop I have, but I'm not loving it.)

---

### Post by DuckHook on 2017-01-11
For an old machine, try Lubuntu, Xubuntu or Ubuntu-Mate. These are all lightweight versions that are designed to use on older HW, of for those just wanting a fast, responsive and unfussy OS irrespective of HW age. BTW, a ten-year-old laptop may still be quite usable, even with a modern up-to-date OS. I run laptops of that age with no problems, but with the aforementioned flavours.

Try running them from a Live/DVD first. LiveUSB is more responsive, but perhaps your machine will not boot from USB. Only consider installing if the Live session first works smoothly.

I realize that this is a digression from your original problem, but am at a loss how to proceed further with a Lucid install.

---

### Post by mchatzikos on 2017-01-14
Final Update: I used a friend's laptop with 16.04 and installed ext3 on the drive.  I got a warning that the alignment was off, which would affect performance.  There was a second partition of 1MiB, which I guess caused the misalignment, and I should have erased from the start; oddly, that partition doesn't show up on my 10.04.  Other that that, I'd say things look OK.

Thanks for the help, DuckHook!  Feel free to close this thread.

---

### Post by DuckHook on 2017-01-15
Glad it worked out for you. I was no real help at all, but happy that you found your own solution.

*You can mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

### Post by olduse78802 on 2017-01-15
You could always use gparted live.  That is what i use for linux and ntfs.

---

