---
title: "EXT4 for /home"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by carloshiga on 2009-10-30
Hi everyone,

I am intending to make a fresh install of 9.10 but I've been reading about some problems regarding the ext4 file system. I have the following partitions in my disk:

/
/boot
/home
swap

What is the best option for this? Set the / to ext4 and leave the others as ext3? Set all partitions to ext4? Wait until all the problems with the ext4 are solved?

---

### Post by sliketymo on 2009-10-30
> **carloshiga said:**
> Hi everyone,

I am intending to make a fresh install of 9.10 but I've been reading about some problems regarding the ext4 file system. I have the following partitions in my disk:

/
/boot
/home
swap

What is the best option for this? Set the / to ext4 and leave the others as ext3? Set all partitions to ext4? Wait until all the problems with the ext4 are solved?

:popcorn: I have been using ext4 for quite sometime,and have had no problems with it.That said,each individual will have a different opinion on the subject.If you are the least bit concerned about using it,use ext3 for your own peace of mind.

---

### Post by paulisdead on 2009-10-30
A lot of the issues were fixed in the 2.6.30 and 2.6.31 kernels, so 9.10 should be fine since it runs 2.6.31.  I've been running on ext4 for everything on my desktop, laptop, and htpc since 9.04 came out.  It's been rock solid for me.  I'm almost tempted to move my home file server to it when I re-do it, just because the fscks run so ridiculously fast on ext4, and I'll be dealing with a 5TB and a 3TB volume.  /home on my desktop is a whole 1TB drive, and fsck only takes a few seconds on it.

What issues have you heard about?  If you're really worried, do ext3.  If you want to test the waters, I'd probably use it on everything but /home.  You can always reinstall and reconfigure your OS, but your personal data can't be unless you've got a fully up to date backup.

---

### Post by carloshiga on 2009-11-05
I've heard that there is a problem with large files (greater than 512M). Is that true?

I am considering to leave my /home as ext3 and the / as ext4.

---

### Post by Junkieman on 2009-11-20
This is one itch I can't scratch either. I know of the delayed write issue, you can lose data if the system crashes [before the file contents are written to disk]("http://en.wikipedia.org/wiki/Ext4#cite_note-8").

Installing 9.10 on my MSI U100 Netbook now, going for EXT4 all the way, I'll let you know if I have any issues.

---

### Post by paulisdead on 2009-11-20
> **carloshiga said:**
> I've heard that there is a problem with large files (greater than 512M). Is that true?

I am considering to leave my /home as ext3 and the / as ext4.

I've not seen any issues with large files, and I regularly have 1-8GB mkv files around.

And as for losing data before it's written to disk, that's a risk with any filesystem, and the reason they invented journaling.

---

### Post by Junkieman on 2009-11-20
I think the issue is that, with EXT3 a crash will cause you to lose your unsaved data, but your original file is kept intact.

EXT4 on the other hand clears the file before write, a crash at this point will lose your unsaved, and your saved data. The original file is empty, 0 bytes.

I would say power-outs and tinkering count for the most of crashes (testing out new graphics drivers, anyone?); The [bug report that got this started]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781?comments=all"), was a result of both of these. (Great comments there, esp #7)

Ubuntu even back ported a patch to Jaunty at the time, to ensure less risk at some performance cost.

My UPS saves me from power failures, common sense makes sure I don't tinker with work open. If you have doubts, stick with EXT3. Get a UPS anyway, they save your work and your hardware :D

---

### Post by Fire_Chief on 2009-11-20
FWIW, all the reported issues I've seen regarding the large file sizes and EXT4 were on the 64-bit platform only. I've not been able to verify any problems if you are on 32-bit. I have EXT4 on my system and have not had any problems with large files (been working with some 2 GB + filesizes just fine.).

cheers!

---

