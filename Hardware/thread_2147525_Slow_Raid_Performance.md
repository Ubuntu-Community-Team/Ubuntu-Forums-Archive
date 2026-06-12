---
title: "Slow Raid Performance"
date: 2013-05-22
forum: Hardware
---

### Post by StarScript on 2013-05-22
Hi every one,

I have built a little NAS server and the performance is not as expected.

The components i have used are  [AsRock A75 motherboard]("http://www.asrock.com/mb/overview.asp?cat=Specifications&Model=A75M-HVS"), [AMD A4 APU]("http://shop.amd.com/uk/All/Detail/Processor/AD3300OJGXBOX#Details"), 4Gb 1600MHz RAM, [4 Drive Back Plain]("http://www.icydock.com/goods.php?id=48"), [Intel Gigabyte Network Card]("http://www.intel.com/content/www/us/en/network-adapters/gigabit-network-adapters/gigabit-ct-desktop-adapter-brief.html") and 4[x 3TB Seagate Barracuda Hard Drives]("http://www.seagate.com/internal-hard-drives/desktop-hard-drives/desktop-hdd/?cmpid=friendlyurl-_-desktop-hdd-amer")

I frist created the RAID using mdadm in RAID level 5, after doing some testing over the network and on the host I was only abel to achieve around 100MB per second read / wright.
That lead me to the conclusion that maybe RAID 5 was probably to much for the system.

So after backing up my data I deleted my RAID volume and set out to initialise raid 10.

After all the hard drives where ready I repeated the same tests, the read wright speed did increases form 100MB to 110MB per second.

I was expecting faster read speeds, I have tested all the drives individually all averaging 150MB/s +-10MB 

is their some form of bottleneck in my configuration or some software issue preventing me form getting faster speeds?

Or will I have to buy a RAID card to get better performance?
 
Thanks,

---

### Post by SaturnusDJ on 2013-05-22
100MB/s is close to the max on a Gigabit network. 125MB/s is hard to achieve because of overhead.


Internal speeds can be increased with disk/raid parameter tuning.

/sys/block/md0/md/stripe_cache_size
blockdev --getra /dev/md0

These are two I found important for my raid5 setup.
Chunk size helped me also for raid5. I use a massive 2048k.

---

### Post by StarScript on 2013-05-22
This might sound completely stupid but .... really the overhead in a gigabyte network is that much???

I should of gotten a Thunderbolt connection.

can you play with the strip size in a live raid setup?

---

### Post by SlugSlug on 2013-05-22
on local machine what's output of

sudo hdparm -Tt /dev/md0

---

### Post by StarScript on 2013-05-22
> **SlugSlug said:**
> on local machine what's output of

sudo hdparm -Tt /dev/md0
   ```
 /dev/md0
    Timing cached reads: 4176 MB in 2 seconds = 2087.99 MB/sec
         Timing buffered disk reads: 908 MB in 3.00 seconds = 302.46 MB/sec
```

---

### Post by SlugSlug on 2013-05-22
on my 4 disk raid0 I get about 400MB/s using hdparm.

Looks like your issue is network speeds

---

### Post by StarScript on 2013-05-22
I thought that as well till I coped one file to and other folder on the local host and it was getting the same speed.
when I was running raid 5 I could hit 900MBS but then it would drop to around 90.


RAID 0 some one likes to live Dangerous

---

### Post by SlugSlug on 2013-05-22
Its basically just a download drive sees plenty of unrar'ing not to bothered if I lose whats on it :)

That might be the hardware limits your hitting was the file/folder you copied / pasted to on same raid or different drives? If teh drives have to read and write at the same time that'll slow you down

you could try

write speed:
dd if=/dev/zero of=/mnt/raid0/output bs=100k count=20k;
20480+0 records in
20480+0 records out
2097152000 bytes (2.1 GB) copied, 5.27545 s, 398 MB/s



read speed:
dd if=/mnt/raid0/output of=/dev/null bs=100k
20480+0 records in
20480+0 records out
2097152000 bytes (2.1 GB) copied, 3.04066 s, 690 MB/s

---

### Post by StarScript on 2013-05-22
I'm playing with saturnusDJ's advice. But going back to raid5 looks good at the moment but going to have to wait for the drives to compleat setup before I can see some real numbers but got 300MBs in one test

---

### Post by SaturnusDJ on 2013-05-22
Yes the parameters may be changed live! :) Chunk size can not be changed after creating an array.

For testing you can create an array existing of small partitions. Then the resync won't take long. Only keep in mind hard drives drop speed near the end.

---

### Post by Cheesemill on 2013-05-24
You may want to take a look at the RAID tuning script in this thread...
[http://ubuntuforums.org/showthread.php?t=1494846](http://ubuntuforums.org/showthread.php?t=1494846)

---

