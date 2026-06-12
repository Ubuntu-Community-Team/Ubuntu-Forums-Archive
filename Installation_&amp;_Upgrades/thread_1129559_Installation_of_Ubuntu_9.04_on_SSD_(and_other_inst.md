---
title: "Installation of Ubuntu 9.04 on SSD (and other install questions)"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by Lyuokdea on 2009-04-18
Hi All,

I plan on installing 64 bit Ubuntu 9.04 on a dual processor scientific workstation (will be doing the install after the new ubuntu comes out). I am planning to use 5 HDs with the following configuration:

30 GB ocz vertex SSD  ( / )
640 GB HD ( /home, /root, /swp, /var)
640 GB HD ( /data <-- will be a drive for data writes from executing codes)
dual 1 TB HD raid 1 ( /storage <-- will hold data created by codes, and occasionally have code write directly to it)

As you can see, I have tried fairly hard to separate the user's HD access from that of executed codes, so that the user does not experience lock up if codes are reading or writing a lot of data.

My questions center mostly around configuring the ssd correctly to maximize the system speed, and preserve the system against repeated unnecessary writes. Thus, I believe it will be useful to mount /swp and /var onto the user drive? Are there any other partitions I should mount there? I have thought of either mounting /tmp there, or adding it to a RAM disk, but I'm not sure how big that ramdisk would have to be (I will have 12 GB of RAM, but several of the codes will use large quantities of RAM, thus I definitely don't want to have a RAM disk of any more than 1GB, and no more than 512 MB unless absolutely necessary)

Secondly, should I format the ssd for ext2 (non journalised) instead of using ext3 or 4? Is there a way to turn off the journaling and autodefragmenting, and are there advantages of doing that and using ext3 or 4? What filesystem should I be using on the other HDs in order to maximize their abilities (need support for large files (sometimes > 50 GB)) I've read that i should boot the ssd with noatime in order to prevent small writes every time a file is opened.

Lastly, do I need to do any special configuration in order to get ubuntu to work with a dual processor computer? I assume this should work natively, but is there anyway to make sure all cores (real and hyperthreaded) are being employed correctly?

Lastly, if anybody has any other advice, I would be glad to here it. I've installed linux quite a few times before, but I've never done it on a system of this scope (both in terms of advanced hardware options that need to be supported, as well as the need for end user stability, as i have mostly tinkered with linux on previous builds)

Thanks in advance for your help,

~Lyuokdea

---

### Post by tommcd on 2009-04-18
You should use ext2 on the SSD drive. As far as I know all the new netbooks that come with linux on an SSD drive use the ext2 file system. Various tutorials I have read about installing various distros on netbooks with SSD drives usually recommend ext2.
It is problably a good idea to have swap and /var on one of the other drives as you said. With 12 GB of RAM though, you likely will never use swap.

Ubuntu should detect the dual CPUs, assuming the motherboard chipset is supported by the kernel.

Since you have plenty of RAM you can mount /tmp as tmpfs. See:
[http://tombuntu.com/index.php/2008/09/04/four-tweaks-for-using-linux-with-solid-state-drives/](http://tombuntu.com/index.php/2008/09/04/four-tweaks-for-using-linux-with-solid-state-drives/)
and:
[http://forums.debian.net/viewtopic.php?t=16450](http://forums.debian.net/viewtopic.php?t=16450)

And welcome to the Ubuntu forums!

---

### Post by Lyuokdea on 2009-04-18
Thanks so much for the help... a couple of questions:

1.) A lot of the customization pages talk about changing the I/O scheduler for the SSD from cfq to deadline. Is that also legit for the ext2 filesystem? Or is that ext3 specific?

2.) Here's what I'm thinking of as a complete partition system, let me know what you think

SSD:
/ (30 GB) on the ssd (ext2)

RAM:
/tmp (128 MB) on the tempfs RAMdisk (might not have to set partition size?)

640 GB HD (personal)
/swp (24 GB) (on the outside of the platter)(ext4)
/var (4 GB?) (also on the outside of the platter)(ext4)
/home (~550 GB) (ext4)
/root (~10 GB) (ext4, on inner platter of drive, since it should never be used)

640 GB HD (system)
/fdata (~50 GB) (data read/writes which require high data throughput, and is thus mounted on the outside of the platter) (ext4)
/data (~550 GB) (all other data writes)(ext4)

2 x 1TB HD (raid1)
/storage (~900 GB) - All storage, I don't think it's really worth it to have a fast storage location here...(ext4) 

Is that a reasonable setup? Is there anything else I should split up? I'm thinking of setting the firefox temporary files to write to /var, since that will be the fastest location on the user drive, so I've overdone the size a little bit up to 4GB.

~Lyuokdea

---

### Post by tommcd on 2009-04-19
> **Lyuokdea said:**
> 
1.) A lot of the customization pages talk about changing the I/O scheduler for the SSD from cfq to deadline. Is that also legit for the ext2 filesystem? Or is that ext3 specific?

Well, I really don't know about that. Some quick googleing suggests it might be a good idea:
[http://www.brighthub.com/computing/linux/articles/9170.aspx](http://www.brighthub.com/computing/linux/articles/9170.aspx)
[http://www.alphatek.info/2009/02/02/ssd-performance-vs-linux-kernel-io-scheduler-in-fedora-10/](http://www.alphatek.info/2009/02/02/ssd-performance-vs-linux-kernel-io-scheduler-in-fedora-10/)
Also, the first link in my last post has some stuff about that as well.
> **Lyuokdea said:**
> 
Is that a reasonable setup? Is there anything else I should split up? I'm thinking of setting the firefox temporary files to write to /var, since that will be the fastest location on the user drive, so I've overdone the size a little bit up to 4GB.

With 12GB RAM, you will likely never touch swap. In any case, 24GB swap is way too much. I would go with maybe 2GB unless you anticipate needing a huge swap for some reason.
I don't think you need to specify a size when mounting tmp to tmpfs.

Why do you need a separate 10GB root partition on the 640GB drive?

Since you are planning on using ext4 file system on the large drives, you may be interested in this article about ext4 performance:
[http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1](http://www.phoronix.com/scan.php?page=article&item=ext4_benchmarks&num=1)
And here is an article on SSD drive performance:
[http://www.phoronix.com/scan.php?page=article&item=linux_ssd_performance&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_ssd_performance&num=1)
From what I have read, not all SSD drives are created equal. However, the really good ones are a bit expensive:
[http://www.phoronix.com/scan.php?page=article&item=intel_x25e_ssd_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_x25e_ssd_linux&num=1)

---

### Post by Lyuokdea on 2009-04-19
> **tommcd said:**
> 
With 12GB RAM, you will likely never touch swap. In any case, 24GB swap is way too much. I would go with maybe 2GB unless you anticipate needing a huge swap for some reason.
I don't think you need to specify a size when mounting tmp to tmpfs.


Good point, I was going with the normal 2x RAM specification for swap space. I'll probably push it down to around 10GB, but there is always the possibility that I have a code which hits a fault and needs 15GB or something, so I think it's worth hard drive space to add extra swap space.

> 
Why do you need a separate 10GB root partition on the 640GB drive?


Is root usually under /home? If so, then there's no reason for a separate partition, but I definitely want it to be on the HDD as opposed to the SSD.

Thanks again for the help, I think this is all starting to come together.

~Lyuokdea

---

### Post by tommcd on 2009-04-19
> **Lyuokdea said:**
> 
Is root usually under /home? If so, then there's no reason for a separate partition, but I definitely want it to be on the HDD as opposed to the SSD.

Root is not under /home. The root directory is where all the root user's hidden (the files that start with a dot) configuration files are. If you avoid deleting stuff using **gksudo nautilus**, or by logging in as root and deleting stuff from a nautilus window, then the /root directory will not grow in size. My /root directory on my new Jaunty install is only 152K. The /root directory on my Slackware install is only 8.7mb; and half of that is from some games I installed to /usr/local/games.

---

### Post by Herman on 2009-04-19
In case you're interested, here's a link to a blog by Theodore Ts'o, the main developer of the ext series of file systems. It's about SSD drives and file systems,  [Archive for the &#8216;SSD&#8217;]("http://thunk.org/tytso/blog/category/computers/ssd/").

Regards, Herman :)

---

### Post by Lyuokdea on 2009-04-19
> **Herman said:**
> In case you're interested, here's a link to a blog by Theodore Ts'o, the main developer of the ext series of file systems. It's about SSD drives and file systems,  [Archive for the ‘SSD’]("http://thunk.org/tytso/blog/category/computers/ssd/").


Interesting information.... so it appears that the overall best version is to use the unjournaled version of ext4, though the journaling doesn't make it particularly worse. 

The only problem being that the non-journaled form of ext4 doesn't come out until the 2.6.29 kernel, which, while already released, is not included in the planned release of Ubuntu 9.04.

Is there a way to install 9.04 directly with the 2.6.29 Kernel, and will that cause any other problems that would make it a bad idea for right now?

Thanks,

~Lyuokdea

---

### Post by Herman on 2009-04-19
I don't know.
It depends on how much you value the benefits of journalling compared to whatever extra wear it might cause in your SSD drive. I suppose it depends on your application.

---

### Post by snowpine on 2009-04-19
A journaling filesystem helps with crash recovery and the like. Dell's Mini 9 series comes factory installed with ext3 filesystem on the SSD. You'd think Dell knows enough about hardware not to choose a filesystem that was destructive to the disk. Perhaps ext2 slightly prolongs the lifespan of the SSD, but at what cost?

---

