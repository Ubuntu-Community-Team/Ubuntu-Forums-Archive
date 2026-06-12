---
title: "Setting up a USB hard drive to use with both Linux and Windows"
date: 2005-11-23
forum: Hardware &amp; Laptops
---

### Post by WebDrake on 2005-11-23
Hello all,

Slightly off-topic, this, as it's not completely specific to Ubuntu.  But here goes:

I want to set up an external USB drive to store data files that I use in work (quite large ones---the current amount, on my hard disk alone, adds up to ~20Gb and more is coming...).  I would like it to be usable from Windows as well as Linux.

This potentially creates a problem, because FAT32 (the only disk format easily compatible with both) doesn't like having to deal with large partitions (the disk has an 80Gb capacity) and I'd rather not break up this disk into separate partitions of 32Gb or less.

Is there any way round this?  I've heard something about ext2 or ext3 drivers available for Windows, but I'm not sure about how effective they are.  There's also the question of formatting the drive in the appropriate format since Windows will only let me do it in NTFS.  Although I could (and probably should) shell out on a copy of Partition Magic, I'd rather not do so right this moment.

Any thoughts or advice?

Many thanks,

        -- Joe

---

### Post by markr on 2005-11-23
I had a similar problem with an 80gig USB HDD.

I formatted mine with ext3 (it can be done within Ubuntu using something like Q_Parted I think).

Obviously Linux will now pick this up automatically.  In order for a WinXP machine to use it you need to install IFS which is basically a WinXP driver for reading/writing ext3 filesystems.  With the driver installed,  WinXP thinks that the drive is native and so will let you use it as if it was an NTFS partition (i.e. explorer, all applications etc).

The only drawback is that IFS needs installing on every WinXP machine you are likely to need to use the HDD on.

I've been using this setup for a couple of months now with no problems.

Mark.

ps.  You might need to read the FAQ as it has troubleshooting advice should you run into problems.

Link to website is [http://www.fs-driver.org/](http://www.fs-driver.org/)

Have fun.

Mark.

---

### Post by MetalMusicAddict on 2005-11-23
You can also format large FAT32 drives but your still limited to 4gig filesize limit.

Thanx for the info markr. ;)

---

### Post by WebDrake on 2005-11-23
[QUOTE=markr]I formatted mine with ext3 (it can be done within Ubuntu using something like Q_Parted I think).
[/quote]

Great, thanks for the advice; I'll try doing that.

Would I be able to do the ext3 format of the USB drive via the Live CD?  I don't yet actually have Ubuntu installed on my machine---getting this external drive is part of the Long Term Plan to free up space so I can resize partitions on my internal drive. ;-)  If it's possible to do, how would I go about it?

(Precise instructions if possible, I'm still a relative novice with Linux...:rolleyes: )

Best wishes,

      -- Joe

---

### Post by WebDrake on 2005-11-23
Here's the situation: I have a USB hard disk, capacity 80GB, that I would like to format in ext3.

I don't currently have Linux installed on any of my systems but, by booting from the Ubuntu 5.10 Live CD, I can get a basic version of Breezy Badger up and running.  Then, if I go to System -> Administration -> Disks, it detects the USB drive as /dev/sda1/ with filesystem "Unformatted" (just as you would expect ;) ).

If I click on the "Format" button, I am asked for a format type---obviously extended 2 or extended 3, and I will probably go for the latter---but also an access path.  What should I select for the latter, bearing in mind this USB drive is just going to be for storing data files, and that I want it to work like just another disk drive?

Many thanks,

        -- Joe

---

