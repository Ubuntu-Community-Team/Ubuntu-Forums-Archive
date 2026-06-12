---
title: "Partition sizes?"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by pointyblue on 2009-07-07
Hi,

Installing Ubuntu 9.04 on a netbook. (WinXP dualboot.)

So far I've used the default live cd partitioning when installing Ubuntu. This time I'd like to create a /home partition to make it easier to upgrade in the future. (And to learn how it's done.)

The drive is 69,5 gb. I've read somewhere that /swap should be 1,5 times the amount of ram. The machine has 1 gb ram so I'll let /swap have 1,5 gb. (Isn't that too much?)

Then there's root: How much space should I give it?

Remaining space will be given to /home.

What are your thoughts on ext4? Is this system stable enough or should I go with ext3 for now?

:cool:

---

### Post by PureLoneWolf on 2009-07-07
When you say that the drive is 69.5gb, do you mean including Windows or that this amount is entirely available to Ubuntu?

For the swap partition, I believe the preference is up to 2xram - Up to being operative, so 1.5xram should be fine.

Ext4..after doing a lot of reading, I decided to wait..it is stable for a lot of people, but equally I see many having issues aswell..I am waiting for Karmic before looking into it again - Just a personal preference though.

---

### Post by anystupidname on 2009-07-07
I like the idea of a separate /home partition but have never done so myself for no particular reason. The only problem I've ever heard of with doing that were permission problems after upgrading to another distro (if I remember correctly) because they used a different default permission schema or something... Bearing in mind that you can easily resize partitions with unetbootin' PartedMagic (for example) you shouldn't stress too much on what size to make your / partition. I suppose 10-20 would work for 95% of users but I don't know if you're a CAD operator or doing other crazy things. [-X I have been using EXT4 without problems since Hardy supported it on several computers. Just my 2 cents worth...

---

### Post by Pogeymanz on 2009-07-07
All of my Linux installs ever have always been under 10GB in /. I would make it 15GB to be safe.

Swap should be 1.5xRam, especially on a netbook that will be suspending.

The rest should be /home. I recommend to ALWAYS have a separate /home. It makes upgrades/reinstallations much smoother.

I personally really like ext4 and have not had any problems at all, but I actually prefer JFS. It's probably wishful thinking, but it seems like it just works a little quicker than ext3 at least.

---

### Post by raymondh on 2009-07-07
My ubuntu root (/) has always been 15-20GB.  Swap for me is 1.5GB.  My /home is as much as I want.

On another install, I use /data as opposed to /home.  That is because it (a test machine) has multiple distros/OS'.  See Bodhi's thread about partitioning and his opinion/s about using /data (about a third of the way down)

[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

Good luck.

---

### Post by pointyblue on 2009-07-08
Thanks for the input guys.

The 69,5 gb is for ubuntu, xp has 69,5 gb too. Thought about erasing it but for now I'm gonna let it stay just in case.

I'll give / 10 gb, /swap 1,5 gb and the rest to /home. Will give ext4 a try - just for fun.

Again, thanks guys.

):P

---

### Post by Murdock on 2009-07-08
i got an 80Gb only ubuntu tho and got it stup like this:

/boot = 200Mb
/     = 10Gb
/swap = 2Gb (Same amount as my RAM)
/home = rest (around 62Gb where left)

All running ext4 since i haven't had a problem with it yet.

---

