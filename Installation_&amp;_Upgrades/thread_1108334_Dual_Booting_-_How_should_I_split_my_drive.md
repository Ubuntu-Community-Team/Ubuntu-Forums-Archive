---
title: "Dual Booting - How should I split my drive?"
date: 2009-03-27
forum: Installation &amp; Upgrades
---

### Post by cfogelberg on 2009-03-27
Hi all,

I'm new to Ubuntu and somewhat new to Linux (I've used it and installed Mandrake years ago, but haven't done any administration level stuff since then).

I've just bought a Dell XPS M1330, and I'm going to dual boot it. Well, sort of triple boot it, but effectively dual (Vista, for Studio and some games; Dell Media Centre, to stop it crashing when I hit the media centre button by mistake; and Ubuntu, for everything else).

The question I am struggling with is how I partition my drive, especially how big each partition should be. I think I want to do something like this (320 gb drive):
2 partitions for Dell media centre (~300mb I think)
1 partition for Vista and programs(~30gb)
1 partition for / (~30gb)
1 partition for /swap (8gb, twice the ram I have)
1 partition for /home (how much?)
1 partition for /usr/share (all the rest)

/usr/share will be for things like photos, music, data files, just anything that I want to use on both operating systems. I think it should be an ext3 partition, and I'll install FS-Driver

Except for the Dell MC and Vista partition they'll all be ext3, and I'll install FS-View in Vista.

My questions are basically:
* Is 30gb enough for Vista? I plan to set it up, image it, then regularly restore the old image to keep it fairly clean.
* Is 30gb enough for /? I really have no idea how much space I might need, but given I'll be installing Matlab, Eclipse and other big applications it could need more than usual.
* How large a home directory do I need, given that most large files will be stored in /usr/share, as will quite a few of the documents that I might want to use in Vista (e.g. .tex files - I'll put cygwin in Vista)
* Is there better software for using extX in Windows than FS-Driver?

Thanks everyone for all your help, and I'm sorry if these questions have been asked a million times, but I couldn't find much by searching through the forums (only [http://ubuntuforums.org/showthread.php?t=1045634](http://ubuntuforums.org/showthread.php?t=1045634)).

Best,
Christo

---

### Post by graysky on 2009-03-27
> **cfogelberg said:**
> 
My questions are basically:
* Is 30gb enough for Vista? I plan to set it up, image it, then regularly restore the old image to keep it fairly clean.
* Is 30gb enough for /? I really have no idea how much space I might need, but given I'll be installing Matlab, Eclipse and other big applications it could need more than usual.
* How large a home directory do I need, given that most large files will be stored in /usr/share, as will quite a few of the documents that I might want to use in Vista (e.g. .tex files - I'll put cygwin in Vista)
* Is there better software for using extX in Windows than FS-Driver?

320 gig for a media center?  Isn't that too small?  You can get a 750 gig SATA II drive for under $90 shipped these days, just an FYI.

To answer your question.  30 GB for Vista seems okay depending on games.  My / for Ubuntu is 15 GB and I'm only using 3.4 GB with all my stuff installed.  My /home is 50 gig and I'm only using 17 of it.  I have my shared stuff on an NTFS partition in case I need anything under windows so don't feel like you're limited to storing your files in the /home partition.  Just use symlinks (for example I have a link to my NTFS partition for office docs, mail, etc.)

As to your ext3/ext2 support under Windows I have no idea.  Have a look at [my reply in this thread](http://ubuntuforums.org/showpost.php?p=6967615&postcount=6) for a suggestion as to how to carve up your drive.

Also, you probably don't need 8 GB for /swap.  My machine has 4 gig of physical memory and I have 2 GB of /swap space.  In the 4 months that I have been running LINUX, it has never been touched by the OS.

---

### Post by cfogelberg on 2009-03-28
> **graysky said:**
> 320 gig for a media center?  Isn't that too small?  You can get a 750 gig SATA II drive for under $90 shipped these days, just an FYI.


Wow, where? Things might be more expensive because I'm in England but the cost of the 2.5" 320gb external drive and enclosure I bought to go with it (Seagate) was 65 pounds. Just drives by themselves seem to be ~55 pounds.

Anyway, the laptop isn't just going to be a media centre, and thanks for all your other suggestions too, I'll look more into NTFS support in Linux v. using ext3 in Windows :)

Christo

---

### Post by Mark Phelps on 2009-03-28
> **cfogelberg said:**
> 
My questions are basically:
* Is 30gb enough for Vista? I plan to set it up, image it, then regularly restore the old image to keep it fairly clean.

I only have MS Office (home version) and a few other apps loaded on Vista Ultimate and it uses up 28GB of space! And ... I save all my data files, downloads, multimedia files to a separate partition.

I'd give it 35GB to have extra room.

---

### Post by cfogelberg on 2009-03-31
> **Mark Phelps said:**
> I'd give it 35GB to have extra room.

Yeah, I'll do that - thanks for the warning :) xto

---

