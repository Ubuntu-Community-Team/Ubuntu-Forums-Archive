---
title: "partition fun, command line experts wanted"
date: 2006-01-09
forum: Installation &amp; Upgrades
---

### Post by trinaryouroboros on 2006-01-09
Good times, but silly me decided to go gung ho originally and went forth with wonderful Dapper - testing as my only linux partition. I had a meager 30gb windows xp partition to play with (didn't expect to use it much either), and let the rest of the hard drive (SATA-3.0gb/s 250GB) be dedicated to Dapper.

As of late, there have been supreme changes in MOD-X and many other developments of which eventually knocked Ubuntu Dapper Drake for a loop, and with great troubleshooting I fear that this partition may be only barebones usable temporarily. This means most hardware (except, ironically the very important stuff, that includes running SATA and all) is unusable, including the onboard NICs - so officially there is no updates/upgrades via networking until a patch is found/made eventually.

Post mortem, I've decided that now I have finally enough time to play with linux again, and am actually going to try a different route for a change - at least until April when Dapper is scheduled for RC and official release.

Now just to rewind to the topic at hand, I'd like to partition things for brighter and better things:

30gb partition dedicated to WinXP, untouched and chilling - it saddens me, but it's obvious I've needed this partition once since testing dapper...

The rest of the partition is presently dapper drake ubuntu, but what I would like to accomplish is managing the partition, from the command line, so the partition would be diced up like this:

70gb of hibernating dapper drake, pending hopeful workarounds in the future, and yes the space taken is not nearly 70gb anyway.

25gb for a good old stable breezy badger install.

25gb for a working Daily ISO of Kubuntu/Dapper Drake, for testing only.

25gb for playing with the latest DragonFly BSD 1.4

25gb for playing with the latest FC5 development

50gb for Ubuntu/Dapper Drake (working Daily ISO)

...and to be up front about this, there is another Hard Drive...

I also have a BUSLINK 120GB External USB1/2/1394 hard drive that's a free-for-all; acceptable for all file sharing purposes b/w these partitions.

So!

I want to essentially keep the existing Windows XP partition, and the existing Dapper OS, but repartition the Dapper OS via command line so I can start getting breezy back on as well as test other realms for fun.

All recommendations, great or small, are highly appreciated in advance!

---

### Post by emperor on 2006-01-09
Easest way for most people is to use Partion Magic 8.

---

### Post by Kipper on 2006-01-09
I would strongly NOT recommend using PM8. I repeat DO NOT USE PM8. See elsewhere on the forums for the real trouble this can land you in. There are perfectly good partitioning tools available within Linux.

I'm a little confused when you say, "The rest of the partition is presently dapper drake ubuntu, but what I would like to accomplish is managing the partition, from the command line, so the partition would be diced up like this:"

Should "managing the partition" be "managing the disc"? What command line are talking about, and used in what operating system and when?  Do you mean a partitioning tool used at the time of install, or post-install? How do you propose/want to boot all these different flavours of Linux and BSD as well? Are you going to use GRUB and are you happy that it should be installed on your MBR? Do you need to resize your Winodws XP partition or not?

Ok, this is more questions than answers, but it is best to get things straight before going on.

One other thing, I'm a little surprised you intend to install each variety of Linux on a single partition. Most would recommend you have at least a seaprate partition for / and /home and /swap per Linux install The same swap partition could be used by all the different Linux installs, I'm not sure about BSD as I have never used it.  This could lead you into another gothca. Linux treats a SATA drive like a SCSI drive and has a limit of 16 partitions. Not great if you want to have multiple Linux installs. Whereas good old PATA can have up to 64 partitions.

---

### Post by trinaryouroboros on 2006-01-13
[QUOTE=Kipper]I would strongly NOT recommend using PM8. I repeat DO NOT USE PM8. See elsewhere on the forums for the real trouble this can land you in. There are perfectly good partitioning tools available within Linux.

I'm a little confused when you say, "The rest of the partition is presently dapper drake ubuntu, but what I would like to accomplish is managing the partition, from the command line, so the partition would be diced up like this:"

Should "managing the partition" be "managing the disc"? What command line are talking about, and used in what operating system and when?  Do you mean a partitioning tool used at the time of install, or post-install? How do you propose/want to boot all these different flavours of Linux and BSD as well? Are you going to use GRUB and are you happy that it should be installed on your MBR? Do you need to resize your Winodws XP partition or not?

Ok, this is more questions than answers, but it is best to get things straight before going on.

One other thing, I'm a little surprised you intend to install each variety of Linux on a single partition. Most would recommend you have at least a seaprate partition for / and /home and /swap per Linux install The same swap partition could be used by all the different Linux installs, I'm not sure about BSD as I have never used it.  This could lead you into another gothca. Linux treats a SATA drive like a SCSI drive and has a limit of 16 partitions. Not great if you want to have multiple Linux installs. Whereas good old PATA can have up to 64 partitions.[/QUOTE]

Well, I certainly avoided partition magic, actually I think it was kinda disgusting for someone to recommend such a dinosaur for this task. In leui of things, I ended up using disk druid included with Ubuntu Dapper's install CD, used it several times, was a real snap.

Live and learn, I s'pose. I had success on all, but Fedora Core 4 for some reason is being a bizom, probably display driver trouble, haven't had time for it yet.

OH, and Gentoo is still tougher to install, but wow DragonFly took me for a spin to get operating!

---

